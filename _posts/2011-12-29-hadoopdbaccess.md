---
layout: post
title: Hadoop Database access experiment
tags: [MySQL, Apache Hadoop]
use_math: true
---
Over a couple of weeks I was reading and practicing the book ["Hadoop in Action"](https://www.manning.com/books/hadoop-in-action). After getting some insight on Hadoop and Map Reduce I worked out a couple of examples from the book and some example problems which I created too. Then I was discussing about features of Hadoop with some of my colleagues over a cup of tea. One of the guy asked a question regarding accessing database from Hadoop and process the data. I saw some discussions related to Hadoop and database access some where in the internet. Finally I digged-out the article "Database Access with Hadoop" for Cloudera blog. After reading the same I decided to work with a sample problem.

To workout the Hadoop database access sample program. Before some times I extracted a bunch of Tweets related to Gmail's new look and feel. I extracted the Tweets for some social media analysis practice. The extraction was done using Twitter4j API. The data is stored in MySQL database. The database table contains one table called NewGamil with following structure.

```sql
        +-----------------+--------------+------+-----+---------+----------------+
        | Field           | Type         | Null | Key | Default | Extra |
        +-----------------+--------------+------+-----+---------+----------------+
        | TweetId        | int(11)      | NO   | PRI | NULL    | auto_increment |
        | Tweet           | varchar(240) | YES  |     | NULL    |                |
        +-----------------+--------------+------+-----+---------+----------------+
        
``` 

The problem which selected to workout is fetch all the tweets from the table 'NewGamil' and perform a word count. The word count result has to be stored in HDFS. In-fact there are ways to write data back to database itself. But I decided first experiment with read from database ;-).

Hadoop provides a handy API for accessing database; the DBInputformat API. The API allows us to read data from RDBMS like MySQL, PostgreSQL of Oracle . To access the data from DB we have to create a class to define the data which we are going to fetch and write back to DB.  In my project I created a class namely GetTweets to accomplish the same. 

```java
    public static class GetTweets implements Writable, DBWritable {
        String strTweet;

        public GetTweets() {

        }

        public void readFields(DataInput in) throws IOException {

            this.strTweet = Text.readString(in);
        }

        public void readFields(ResultSet resultSet) throws SQLException {
            // this.id = resultSet.getLong(1);
            this.strTweet = resultSet.getString(1);
        }

        public void write(DataOutput out) throws IOException {

        }

        public void write(PreparedStatement stmt) throws SQLException {

        }

    }

```
Since I am accessing only one field from the table I defined the same in readFields() method. The write() methods are kept blank because the project does not aims to write back the data to DB. I'll experiment with writing data and post it soon.  In the readFileds() method we have to define how the data had to be extracted from the DB table. Since 'Tweet'  the data which I extractes for processing is VARCHAR() I am reading it as string and casting it to Text() data in hadoop. This class "GetTweets" will be used in our Mapper and Reducer class.

Now lets write our Mapper class:

```java

    public static class TweetWordCountMapper extends MapReduceBase implements
            Mapper<LongWritable, GetTweets, Text, IntWritable> {
        private final static IntWritable intTwordsCount = new IntWritable(1);
        private Text strTwoken = new Text();

        public void map(LongWritable key, GetTweets value,
                OutputCollector<Text, IntWritable> output, Reporter reporter)
                throws IOException {
            GetTweets tweets = new GetTweets();
            tweets.strTweet = value.strTweet;
            TwitterTokenizer twokenizer = new TwitterTokenizer();
            List<String> twokens = twokenizer.twokenize(value.strTweet
                    .toString());

            for (int i = 0; i < twokens.size(); i++) {
                output.collect(new Text(twokens.get(i)), intTwordsCount);
            }

        }

    }

```

In the mapper class ```'TweetWordCountMapper'``` I used the ```'GetTweets'``` class to fetch the values for processing. Then we can access the data by creating object of the class inside the Mapper class. 
NB: The code for TwitterTokenizer is taken from https://github.com/vinhkhuc/Twitter-Tokenizer.

Now we can write our reducer class :

```java
    public static class TweetWordCountReducer extends MapReduceBase implements
            Reducer<Text, IntWritable, Text, IntWritable> {
        public void reduce(Text key, Iterator<IntWritable> values,
                OutputCollector<Text, IntWritable> output, Reporter reporter)
                throws IOException {
            int intTwokenCount = 0;
            while (values.hasNext()) {
                intTwokenCount += values.next().get();
            }
            output.collect(key, new IntWritable(intTwokenCount));
        }
    }
```

This reducer is responsible to sum the word count and produce the final output.

After this we have to configure the job with database connection details and driver class.

```java
        JobConf twokenJobConf = new JobConf(TweetWordCount.class);
        twokenJobConf.setJobName("twoken_count");

        twokenJobConf.setInputFormat(DBInputFormat.class); //Set input format here 
        twokenJobConf.setOutputFormat(TextOutputFormat.class);// Sets the output format 

        Object out = new Path("twokens");

        twokenJobConf.setMapperClass(TweetWordCountMapper.class);
        twokenJobConf.setCombinerClass(TweetWordCountReducer.class);
        twokenJobConf.setReducerClass(TweetWordCountReducer.class);

        twokenJobConf.setOutputKeyClass(Text.class);
        twokenJobConf.setOutputValueClass(IntWritable.class);

        DBConfiguration.configureDB(twokenJobConf, "com.mysql.jdbc.Driver",
                "jdbc:mysql://localhost/GmailTrend", "jaganadhg", "jagan123"); //Specifies the DB configuration

        String[] fields = { "Tweet" }; //Specifies the Fields to be fetched from DB
        DBInputFormat.setInput(twokenJobConf, GetTweets.class, "NewGamil",
                null /* conditions */, "Tweet", fields); // Specifies the DB table and fields

        SequenceFileOutputFormat.setOutputPath(twokenJobConf, (Path) out);

        JobClient.runJob(twokenJobConf);
```

Before compiling and running the program we have to some additional setup in the Hadoop ecosystem. The MySQL connector library has to be put in ``$HADOOP_HOME/lib`` folder. To download the connector .jar file go to ```MySQL Connector/J``` download folder. I used the ```mysql-connector-java-3.1.14-bin.jar``` file in my program. After putting the jar in ```$HADOOP_HOME/lib``` restart the hadoop ecosystem. Viola !! now you are ready to run the program. Convert the code to .jar file and run it. 

The complete project is available in my [bitbucket repository](https://bitbucket.org/jaganadhg/hadooexamples/src/840db7af9abc/HadoopMySQLRead/).

Happy hacking !!!!!!!!!!!!


Migrated from my [old blog jaganadhg.freeflux.net](https://web.archive.org/web/20160323193721/http://jaganadhg.freeflux.net/blog)
