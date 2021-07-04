

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

	Continuous Development w/ Continuous Delivery


# Description :

**Maintain.js** is a micro nodejs script meant for rapid development of any git housed project. It performs automated git commands for you in the background while you activily work on your project. This way you can just speed thru your development and not have to worry about saving changes or losing work. 

# How it works :

By running inside your git project folder, it handles commits/push/pull for you automatically. By doing regular checks to the project's folder for any changes and comparing those to the remote, the script automates pushes and pulls on your behalf.

- If the local repo has changes, it commits them and pushes automatically to the remote repo.

- If the remote repo has a change it pulls it down to the local repo folder automatically. This is especially handy if you have a continous integration system that you need to update files on without interruption of services.


# Preconfig :

You need a ssh key for the system the script will be running on. [Follow the instructions from Github to get it.](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)

# Setup :

Maintain.js has been built as a self contained mirco script. So you only need to copy the script file **maintain.js** into your existing github project folder and run it from there. 

###  curl Example :

	cd {YOUR_GIT_PROJECT_FOLDER}	
	
	curl https://raw.githubusercontent.com/kod3000/maintain/main/maintain.js --output maintain.js
	
### wget Example :

	cd {YOUR_GIT_PROJECT_FOLDER}
	
	wget https://raw.githubusercontent.com/kod3000/maintain/main/maintain.js
	

*Note : it must be placed inside the root folder of the project and not inside any subfolder. Maintain.js uses git commands that assume the current path is root where the hidden '.git' folder is located.*


### Folder Structure Example :

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


# Running, Using, Understanding



### To Run : 

~~~text
	node maintain.js
~~~

*Note : The first run will automatically install any missing npm dependencies, after the first run just rerun it and the script will work as expected.*

### Usage :

Keep the srcipt running as long as you need it to watch over the changes you make to your project. Everytime a file is saved, modified or added, the script will load it up as a commit to be pushed onto the remote server. Again, it's meant to run continuously while you work. ;)

### Understanding key Variables :

-	**commitAutoMessage** [string]
	-	This is what will be set as the message for each automated commit.
-	**fileChangeTolerance** [number] 0 = default, which means just one file needs to change.
	-	Controls how many files need to change inside the project folder for an automated commit to be triggered.
-	**allowedGlobalTime** [number] 1000 = 1 second
	-	This controls how long the timer will take for the next status check of the folder.


*Note : This script works both ways.. so you can install it on a target system and run it so that it will do automated pulls from the remote repo.*



# Development Notes :

- This script does not yet support git lfs. Be very careful with commiting automatically single files that are over 50MB (this limit depends on the github subscription, free accounts are default at 50MB.) Github will automatically disable or archive your repo for using large files. At some point I'll setup a trigger to handle this event. If you are already using git lfs then please note, you have to mark the large file manually. After the file is marked as git lfs, the script should work as expected. Again these are basic git push/pull/commit commands that are running inside a timer, nada mas. (^_^)

- Since this is a minimalist script no branch support is given. The script assumes you use the default origin/master to do all changes on. I'm not against adding branch support, its rare that I use them inside my work so I just haven't gotten around to it to implement it here. If you have a PR for this feature, throw it. 

# Contributing :

Refractoring of the code to make it more effecient is always on the table. The script currently is less than 260 lines of code. I'd like to make a version of it where it can do multiple git projects in one instance sometime in the future. If you have any improvements, feel free to hit up the PR.

# Disclaimer : 

Please be aware, I do not make myself responsible for how you use this script. As time passes I will continue to improve it as I use it myself for my daily work, but I do not offer support of any kind. Swim at your own risk.
