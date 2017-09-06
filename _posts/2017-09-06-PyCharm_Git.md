---
layout: post
title: Configuring GitHub with PyCharm Community Edition
---

1)  Download and Install Pycharm Community Edition from https://www.jetbrains.com/pycharm/download/ 

2) Open Pycharm and go to "Preferences"

<img src="https://raw.githubusercontent.com/jaganadhg/jaganadhg.github.io/master/images/0.png" width="50%" height="50%" align="middle" >

2) Go to "Version Control" --> "GitHub" . Enter your github details. 

If you are using enterprice private github provide the URL for the same; like mycrop.devel.github.com .

You can select the auth type as "Password" or "Token".If you select the password you can etenetr your GitHub username and password.

<img src="https://raw.githubusercontent.com/jaganadhg/jaganadhg.github.io/master/images/1.png" width="50%" height="50%" align="middle" >

Click on the "Test" button. If the URL, username and password is correct you will see the following screen. If it is not please check your URL/usernamw/password.

<img src="https://raw.githubusercontent.com/jaganadhg/jaganadhg.github.io/master/images/2.png" width="50%" height="50%" align="middle" >

3) Click "Ok" the pop-up and bottom.

4) Go to "Version Control" --> "Git" .

<img src="https://raw.githubusercontent.com/jaganadhg/jaganadhg.github.io/master/images/3.png" width="50%" height="50%" align="middle" >


Click on the "..." near the "Test" button. It will open a new pop-up window. If you are in Windows browse to "Program Files (x86)" in the case of 64 bit systems else "Program Files". Go to "GitHub"--> "bin" and select "git.exe" and click "Open"

In systems like Ubuntu/CentOS/Fedora or MacOsX this step is not required.

<img src="https://raw.githubusercontent.com/jaganadhg/jaganadhg.github.io/master/images/4.png" width="50%" height="50%" align="middle" >

5) Click on "Test" button. If the correct version of the "git.exe" file is selected it will show test successful message. Else you might not have selected the right git.exe file.

6) Click on the "Apply" and then "Ok" button. 
This will configure the "GitHub" with PyCharm.


### Checkingout Code and Commiting Code 

