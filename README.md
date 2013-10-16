Project Revolution Source
===================

Getting Started
---------------
To get started with the Project Revolution sources, you'll need to get
familiar with [Git and Repo](http://source.android.com/source/version-control.html).


Create the Directories
----------------------

You will need to set up some directories in your build environment.

To create them run:

    mkdir -p ~/bin
    mkdir -p ~/carbon


Install the Repository
----------------------

Enter the following to download make executable the "repo" binary:

    curl https://dl-ssl.google.com/dl/googlesource/git-repo/repo > ~/bin/repo

    chmod a+x ~/bin/repo

You may need to reboot for these changes to take effect. 
Now enter the following to initialize the repository:

    cd ~/carbon


Repositories:
---------------

Before you continue --> run this in the terminal
----------------------------------------
    repo init -u https://github.com/project-revolution/android.git -b jb4.3 && repo sync -f

*PLEASE NOTE THAT YOU MUST USE THE -f flag when repo syncing/initializing if you want to sync with our default -j4 setup as android.googlesource seems to like to reject your requests if you set your -jflag too high. 
if you wish to avoid this issue run it repo sync -j1 otherwise -f (force) is reccomended so it will resync the repos it gets error codes on. Thank you and have a nice day.*


Building the System
---------------

Initialize the environment with the envsetup.sh script. Note that replacing "source" with a single dot saves a few characters, and the short form is more commonly used in documentation.

    . build/envsetup.sh
    lunch


Enter the number of the build you want to start and press enter


Build the Code:

    make carbon -j7 = Run Squisher/Run Opticharger
    make otapackage -j7 = No Squisher/No Opticharger


---------------
Git TrickMarks

    Creating a git branch with no ancestry:
    git checkout --orphan <foo>
    git rm --cached $(git ls-files)
    git add NOTICE
    git commit -m "dummy commit"
    Then u push the goodies ;)
