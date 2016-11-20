# Setup Strongback, wpilib and import your first project

## Assumptions

* JDK 1.8
* Eclipse Mars (4.5 or greater)
* WPILIB Plugin

## Install WPILIB, Strongback

The trick for these installs is that they need to be unpacked in your "home" folder. 
There's no getting around this, because the tools (notably strongback.sh and 
eclipse user libraries) look for these files in "~/wpilib" and "~/strongback" (Note for 
those new to Unix - "~" means - *your user folder*. For Windows boxes, it will be 
"C:\Users\<YourUserName>" so "C:\Users\Adam Devoe" or "C:\Users\adevoe"

So install wpilib https://users.wpi.edu/~bamiller/WPILib/Versions.html..  Download and unpack the ZIP file. 

```
$ cd 
$ unzip <path to wpilib.jar> 
$ ls wpilib 
... results 
```
 
Then do the same for strongback

```
$ cd 
$ unzip strongback-1.1.7.zip
$ ls strongback
... strongback folder
```

Again for emphasis - BOTH of these need to be unpacked at your top level or you will 
be _crying tears of bitter frustration_ later.


# Add the strongback_home environment variable and PATH setup.

The *PATH* variable on your computer tells your command prompt (dos window) where to find 
the 

## Windows
>  "My Computer" > "Properties" > "Advanced" > "Environment Variables" :
Name STRONGBACK_HOME
Value C:\Users\<YourUserName>\strongback 

Then use Window Control Panel (e.g., "My Computer" > "Properties" > "Advanced" > "Environment Variables" > "Path") to append the ;C:\Users\<yourUsername>\strongback\java\bin directory to the PATH system path, using a semicolon to separate it from any existing value, and of course using your correct username.

### Verify Path

> 1. Create a new command window
> 2. Try running "strongback.bat -v" which should return the strongback version.

## MacOs/*nix 

Using Terminal and your favorite editor.

in your ".bashrc"
```
$ export strongback_home=/Users/adevoe/strongback
$ export PATH=${strongback_home}/java/bin:${PATH}
```

On Mac, now create a new terminal screen and try this : 

```
$which strongback.sh
/Users/adevoe/strongback/java/bin/strongback.sh
````


# Eclipse Workspace

Eclipse projects are grouped into a Workspace.  For example, I have a workspace for all my IHS First projects and other workspaces for other customers.  The Strongback project creator 
changes your eclipse workspace by adding the Strongback User library into the workspace settings.    Some of you will have the workspace in your user home folder.  

My workspace is here : 

> /Users/adevoe/WorkspacesM/ihsfirst

The Eclipse workspace files are in "/Users/adevoe/WorkspacesM/ihsfirst/.metadata" .  In general, Eclipse files and folders will all be named like this, starting with ".".

Inside the projects, there are a couple of files 

*  .project - indicates that it is (or can be) imported into the eclipse application
*  .classpath - for java projects, where to find the libraries that the project dependes on.

Look at these files - ask questions if you have any.  
 

# Prep eclipse

Open Eclipse, and select your workspace.  


## Add the following classpath variables

 - NOTE - only worry about the 4 variables - your eclipse install will take care of the rest.  Each of the variables should be of type "File:" (see below)
 
* wpilib
* wpilib.sources
* networktables
* networktables.sources
 
![Add classpath variable]
(strongback-setup.resources/edit-classpath-property-file.png)

When you have all the classpath variables added - it will look like this.  

![After adding all 4 classpath variables]
(strongback-setup.resources/view-classpath-variables.png)


# Create the new project using Strongback

NOW, you’re set up to run strongback.sh

*  It creates a project in the folder you're currently "in" (your *Current WOrking Default* )
*  First time, the workspace properties get updated to add the strongback user library.

```
$ cd <Workspace Folder> 
$ strongback.sh new-project -d . -e -n robotex -p edu.ihs5459.robotex
Successfully created new project at: /Users/adevoe/WorkspacesM/ihsfirst/robotex

Project ready for importing into Eclipse workspace.

Added the Strongback user library to your Eclipse workspace at /Users/adevoe/WorkspacesM/ihsfirst/.
Restart this Eclipse workspace and import the project.
```

Note - the new-project command will create 

## Restart and Verify the Strongback User Library

* Restart "Eclipse" like it says (File -> Restart ) 
* Verify that the strongback user library is there

![Strongback User Library]
(strongback-setup.resources/verify-strongback-user-library.png)


# Import the project into eclipse 

Finally, we're ready to import the new project into eclipse.

Now, import the project into the workspace using "General -> Existing projects into workspace"

## View the project in Eclipse

Finally!

![Imported project]
(strongback-setup.resources/import-project.png)

### Potential  errors after import 

#### You might get "classpath errors" with an error icon on the project.
![Classpath Error Markers]
(strongback-setup.resources/import-errors-missing-vars.png)
 


#### The java compiler you have for your project might be wrong.

These projects all require the 1.8 compiler.

Verify that compiler version on the project  is correct (Right Mouse Button click on the project - select properties)

![Verify java Version]
(strongback-setup.resources/verify-java-1.8-compiler.png)





