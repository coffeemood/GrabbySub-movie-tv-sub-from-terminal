
__GrabbySub - Grab your sub from the terminal, and grab the right one! :v: :collision: __

GrabbySub is a small little tool for you :cinema:/:tv: lovers out there who hates scrolling through all hundreds of choices just to find the right language, resolution and uploading version. 
With a few lines of text you will have gotten yourself the absolute right sub for your watching convenience. 

# Getting Started


__ Disclaimer: _Just a tit bit faster than downloading from Subscene, but a whole lot more convenient. 


### Prerequisite

* `Jq` - The JSON parser needs to be previously installed 
* `Pup` - The HTML parser needs to be previously installed
* If you're using OS X, install brew first in order to install the two mentioned above


### Installation

	#### (OS X users only) Install `brew` 	
	
	Open terminal and type 
	
	```shell
	ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
	```
	
	#### Download JQ & PUP
	
		__OS X 
	
		```shell
		brew install jq 
		brew install pup 
		```
		__Linux (Debian) 
		
		```shell
		apt-get install jq pup -y 
		```
		
		__Linux (RPM) 
	
		```shell 
		yum install jq pup 
		```
			
### Usage
	
	#### Creating an alias for ease of use: 
	
	```shell 
	alias Grabby='~/Downloads/GrabbySub.sh' 
	```
	
	#### Grabbing the sub: 
	
	Open up terminal, go to your desired directory, and just run `grabby` 
	
	
	Type in your `show | movie` & select the correct season/version
	
	![selectmov](http://i.imgur.com/WqJcumd.png) 
	
	Select the `type` of media (TV/Mov), the `Language` and the `Episode` (if there are any)
	
	![selectall](http://i.imgur.com/8rlXSPC.png)
	
	Select your `resolution` & finally pick your encoding version
	
	![selectres](http://i.imgur.com/p1KCyzV.png)
	
	And voila! :angel: :clap:
	
	![download](http://i.imgur.com/V4McI26.png)
	
	
### Adding Languages & Encoding Version 

Your language might not be included, or maybe you want to add some vendor specific stuffs like (HDTV, YIFY, DEMAND...) in the res section, don't worry, just do this: 

	#### Adding Languages
	
	Just fire up your text editor, search for the pattern: `language= ` and add your language there, in quotes of course 
	
	#### Adding resolution
	
	* Do the same with language, but this time search for: `resolution=` and add your resolution there. 
	* !! One more step though, you need to search for all the places with `# Add your res here ` , and follow the instruction there. 
	
	
### Bugs & Improvements


[] Improve speed, this current version uses a lot of heavy-loading manual parsing and work on a database which I might need to find a way to get rid of in the future 
[] Work on a GUI, which allows for quick and easy specs picking from outside the terminal 
[] ... Suggestions? 

### Contact me

If you have any questions, shoot me a message at coffeeforthoughts@gmail.com 

__All done! Enjoy!__ 