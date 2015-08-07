---
layout: post
title: Downloading the Citi Bike Data with Python
--- 

Recently I was thinking about creating a visualization project with R and [Pyxley] (https://github.com/stitchfix/pyxley). I was looking for some cool data and selected the [Citi Bike Data] (https://www.citibikenyc.com/system-data) . The data is available as 24 zip files. I thought of writing a script to fetch the data. Here is the script which I wrote.
```python
import glob
import urllib2
import zipfile


def cbd_downloader(url,path):
    """
    Download the Citi Bike Station Data.
    :param url: string url of the data file
    :param path: string - path to save the file
    """
    file_name = url.split("/")[-1]
    outfile = open(path + file_name,'wb')
    tmp_data = urllib2.urlopen(url).read()
    outfile.write(tmp_data)
    outfile.close()
    print "DONE " + file_name


def cbd_unzip(zip_file,extract_path):
    """
    Extract the Citi Bike Data zip files
    """
    with zipfile.ZipFile(zip_file, "r") as zipped_data:
        zipped_data.extractall(extract_path)
        print "Done " + zip_file

if __name__ == "__main__":
    url_list = [
	"https://s3.amazonaws.com/tripdata/201307-citibike-tripdata.zip",
	"https://s3.amazonaws.com/tripdata/201308-citibike-tripdata.zip",
	"https://s3.amazonaws.com/tripdata/201309-citibike-tripdata.zip",
	"https://s3.amazonaws.com/tripdata/201310-citibike-tripdata.zip",
	"https://s3.amazonaws.com/tripdata/201311-citibike-tripdata.zip",
	"https://s3.amazonaws.com/tripdata/201312-citibike-tripdata.zip",
	"https://s3.amazonaws.com/tripdata/201401-citibike-tripdata.zip",
	"https://s3.amazonaws.com/tripdata/201402-citibike-tripdata.zip",
	"https://s3.amazonaws.com/tripdata/201403-citibike-tripdata.zip",
	"https://s3.amazonaws.com/tripdata/201404-citibike-tripdata.zip",
	"https://s3.amazonaws.com/tripdata/201405-citibike-tripdata.zip",
	"https://s3.amazonaws.com/tripdata/201406-citibike-tripdata.zip",
	"https://s3.amazonaws.com/tripdata/201407-citibike-tripdata.zip",
	"https://s3.amazonaws.com/tripdata/201408-citibike-tripdata.zip",
	"https://s3.amazonaws.com/tripdata/201409-citibike-tripdata.zip",
	"https://s3.amazonaws.com/tripdata/201410-citibike-tripdata.zip",
	"https://s3.amazonaws.com/tripdata/201411-citibike-tripdata.zip",
	"https://s3.amazonaws.com/tripdata/201412-citibike-tripdata.zip",
	"https://s3.amazonaws.com/tripdata/201501-citibike-tripdata.zip",
	"https://s3.amazonaws.com/tripdata/201502-citibike-tripdata.zip",
	"https://s3.amazonaws.com/tripdata/201503-citibike-tripdata.zip",
	"https://s3.amazonaws.com/tripdata/201504-citibike-tripdata.zip",
	"https://s3.amazonaws.com/tripdata/201505-citibike-tripdata.zip",
	"https://s3.amazonaws.com/tripdata/201506-citibike-tripdata.zip"
     ]

   for url in url_list:
       cbd_downloader(url,"citi_bike_data")
   zipped_data = glob.glob("citi_bike_data")

   for zip in zipped_data:
       cbd_unzip(zip,"citi_bike_data/csv")
   ```

Soon I will be back with a cool visualizations on the data.

Happy hacking. 
