

	. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
	. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
	
	_____  ___      _____       _____       _____          ________        
	___   |/  /_____ ___(_)________  /______ ___(_)______   ______(_)_______
	__  /|_/ /_  __ `/_  /__  __ \  __/  __ `/_  /__  __ \  _____  /__  ___/
	_  /  / / / /_/ /_  / _  / / / /_ / /_/ /_  / _  / / /______  / _(__  ) 
	/_/  /_/  \__,_/ /_/  /_/ /_/\__/ \__,_/ /_/  /_/ /_/_(_)__  /  /____/  
	                                                        /___/              
	
	. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
	. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

	Continuous Integration w/ Continuous Deployment


# Description

Maintain.js is a micro nodejs script meant for rapid development of any git housed project. It performs automated git commands for you in the background while you activily work on your project. This way you can just speed thru your development and not have to worry about saving changes or losing work. 

# How it works 

Using git based commands in the background it handles commits/push/pull automatically for you. It regularly checks the project's folder for any changes and also does checks to remote server for changes without any supervision needed.

- If the local has changes, it commits them and pushes automatically to the remote server.

- If the remote server has a change it pulls it down to the local folder automatically as well.

This way you can continuously work on your project without having to worry about the teadious tasks of git commands. 


# Presetup :

Before you can do any git command lines, you need to create a ssh key for that system. Follow the instructions from Github to accomplish it. Once you have the ssh keys setup for your system you can proceed.

# Setup :

Maintain.js has been built as a mirco script. So you only need to copy the script into your existing github project forlder and run it from there.


1) Copy the "maintain.js" file to your git project folder.

~~~text
your_github_project
|
├── somefile 
|
├── maintain.js <<<
|
├── sub-folder
│   ├── other folder
│   │   ├── file
~~~

*Note : it must be placed inside the root folder of the project and not inside any subfolder. Maintain.js uses git commands that assume the current path is the root. Inisde the root is where the hidden '.git' folder is located.*


2) Next run the nodejs script from your terminal : 
~~~text
	node maintain.js
~~~

*Note : The first run will automatically install npm dependencies, and you will need to restart it.*


3) Now work on your project without having to worry about commits for the project.

*Note : This script works both ways.. so you can install it on a target system and run it so that it pulls down anychanges made to the server.*


-------

# Usage :

Keep the srcipt running as long as you need it to watch over the changes you make to your project. Everytime a file is saved, modified or added, the script will load it up as a commit to be pushed onto the remote server. Again, it's meant to run continuously while you work. ;)

# Development Notes :

- As of late this script does not support git lfs, so be very careful with commiting automatically single files that are over 50MB (this limit depends on the github subscription, free accounts are default at 50MB.) Github will automatically disable or archive your repo for using large files. At some point I'll setup a trigger to handle this event. If you are using git lfs then please note, you have to mark the large file manually. After the file is marked as git lfs, the script should work as expected. Again these are basic git push/pull/commit commands that are running inside a timer. (^_^)

# Contributing :

As adjusments are made, so will refractoring of the code to make it more effecient. As of now the script is less than 250 lines of code. I'd like to make a version of it where it can do the maintaince of git projects remotely. As when I use this script its usually running simultainously inside a number of folders. If you have any improvements, feel free to hit up the issues.

# Disclaimer : 

Please be aware, I do not make myself responsible for how you use this script. As time passes I will continue to improve it as I use it myself for my daily work, but I do not offer support of any kind. 
