---
author: Brian Ross
email: ML@BrianThomasRoss.com
revised: 28 April 2020
---
# Python Local DevEnv Setup


This purpose of this guide is to help Python developers of all skill levels set up the ultimate Python development environment on their local machines. To that end, it is worth noting that while Python is implemented on all of the major operating systems there are caveats to choosing to develop in a Windows environment. Set up instructions have been provided for all major operating systems, however, it is recommended that one read the following section detailing the differences between Windows and Unix-based systems, as well as reading this guide in its entirety before deciding to use Windows as your OS.

---

## Windows vs Unix


Historically, the Python and Data Science communities have gravitatedtowards UNIX-based systems such as MacOS or any of the various Linux distributions (Ubuntu generally being the most popular). While using one of these systems is not a hard-requirement of the course, nor will it impact your grade in either a positive or negative way, familiarizing yourself with a UNIX-based system can have many benefits, and the 2-3 days spent getting used to your new operating system, will be repaid to you many, many times over your career.

Shell commands from the Bourne Shell(sh), Bourne-Again Shell(bash), and the Z Shell are considered by many to be an integral part of what could be called the Data Science “lingua franca”. Many of the shell commands you used last unit have their roots in, or are exclusively available on UNIX-based systems, and while it may come as a surprise to you, you already have spent some significant time using Linux, since Google Colab is no more than an instance of Jupyter notebooks running on one of Google’s servers.

Today it’s easier than ever to start developing in Linux. Ubuntu, probably the most popular recommendation for new Linux users, can be downloaded for free, and installed in less than 30 minutes with ease. Microsoft itself has in recent years developed the Windows Subsystem for Linux, which allows users to install and make use of an actual Linux OS from inside Windows. Many people find this a comfortable first step in experimenting with Linux. After having been a life-long Windows user myself, WSL was actually my first step into the Linux world, and a guide I wrote to setting it up is available [here](https://medium.com/@BrianThomasRoss/windows-for-data-science-part-i-what-is-wsl2-and-how-to-install-it-1187e4367098)

## Step 1 - Git

**from:** [Wikipedia](https://en.wikipedia.org/wiki/Git)

>    Git (/ɡɪt/)[7] is a distributed version-control system for tracking changes in source code during software development.[8] It is designed for coordinating work among programmers, but it can be used to track changes in any set of files. Its goals include speed,[9] data integrity,[10] and support for distributed, non-linear work-flows.[11]

### Installation


#### <u>**MacOS**</u>

**<u>Install [Homebrew](brew.sh)</u>**

```bash
/usr/bin/ruby -e "$(curl -fsSLhttps://raw.githubusercontent.com/Homebrew/install/master/install)"
```
```bash
brew doctor
```
When prompted to select whether or not you would like to install the 
Command Line Developer Tools from Apple click Install. After the 
installation completes you can finish the Homebrew installation by 
clicking <kbd>Return</kbd>

**<u>Install Git</u>**

```
brew install git
```

---



### **<u>Linux</u>**

Easiest of the punch just use your OS package manager to install

**<u>Debian(Ubuntu)</u>**

```bash
sudo apt-get update && sudo apt-get upgrade -yq && sudo apt-get install git -yq
```

**<u>RPM</u>**

```bash
yum upgrade -y && yum install git
```

<u>**Arch**</u>

Git is likely already on your system as it is a dependency of the base-devel package normally configured at OS installation 

```bash
which git
```

---



### <u>Windows</u>

***If you’re unfamiliar with Vim please first install [Notepad++](https://github.com/notepad-plus-plus/notepad-plus-plus/releases/download/v7.8.5/npp.7.8.5.Installer.exe) or another text editor of your choice\***

1. Download the Git for Windows [Installer](https://github.com/git-for-windows/git/releases/download/v2.25.1.windows.1/Git-2.25.1-32-bit.exe)
2. Select the following options as the installer prompts
   - Notepad++ or editor of choice
   
   - Select **default**: Use Git from the command line and also from 3rd-party software
   
   - **Use OpenSSH**
   
   - **Use OpenSSL**
   
   - **Checkout Windows Style, Commit Unix-style Line Endings**
   
   - **Use MinTTY (the default of MSYS2)**
   
   - [**No extra options**]
   
   - Click **Install**
   
   - Launch Git Bash when the installation finishes
   
     

## Configure Git (All Systems)

Get comfortable with navigating your files via command line, if you are completely new to the command line seek out one of the many tutorials available online. If you're on Windows use the git bash console for the following, if on Mac or Linux find a terminal you like, my personal favorites are [Kitty](http://www.9bis.net/kitty/#!index.md) and [Tilix](https://gnunn1.github.io/tilix-web/).

#### Register your user name and email with the git credential manager

```
git config --global user.name <your username>
```



```
git config --global user.email <your email address>
```

---

**Another helpful configuration helps when working with others**

```text
auto.crlf will make sure that when you pull you recieve your OS specific styled line endings, and when pushing you commit unix line endings. Since Windows line endings use \n\r and Unix just \n collaboration can have hurdles when files begin to have invisible characters or formatting is ruined
```

**Windows**

```bash 
git config --global core.autocrlf true
```

**Mac and Linux**

```bash
git config --global core.autocrlf input
```



#### Clone a Repository, Commit Changes and Push

First navigate to the folder that you want the repository to be cloned into. Then go to the repository on GitHub and you will see a green button 

```
git clone https://github.com/<your-github-username>/<repo-name>
```

Once clone navigate down into your local copy of the repository

```
cd <your repo name>
```

Lets create a `diff` by adding a new file locally that doesn't exist on the `remote`

```
touch delete.me
```

now `stage` your `diff`

```
git add .
```

and `commit` the changes to the repository

```
git commit -m "Added change from command line"
```

now lets `push` those changes to the `origin`

```
git push
```

You’ll then be asked for your login information and after you enter it successfully it the changes will be **push**ed to the repositories **origin**

###### You’ve now started using Git from the command line

**Helpful Git Resources:**

|          [Pro Git](https://git-scm.com/book/en/v2)           | [Git Handbook](https://guides.github.com/introduction/git-handbook/) | [GitHub Workflow Video Series](https://www.youtube.com/watch?v=47E-jcuQz5c&list=PLg7s6cbtAD17Gw5u8644bgKhgRLiJXdX4&index=1) |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
| [Git cheat sheat](https://github.github.com/training-kit/downloads/github-git-cheat-sheet/) | [Interactive Cheat Sheet](https://ndpsoftware.com/git-cheatsheet.html#loc=index;) | [Complete List of Commands](https://git-scm.com/docs/git#_git_commands) |

---

# Anaconda

**Conda** is a package manager and environment management system originally designed to specifically address issues faced by the Data Science community, but is now one of the most popular package managers for the entire Python community

**Anaconda** is a distribution of Python which includes Python/R, as well as 7,500+ packages from PyPI (Python Package Index), and also the Conda package management system.

You can choose between **Miniconda**, which includes just package manager, anaconda python, and the basic handful of packages that it requires, or the full **Anaconda** distribution which also bundles together numerous additional packages, editors, and a GUI. In this guide we will install Anaconda.

### <u>**Mac OS**</u>

**Install Wget:**

*Formerly Geturl, Wget is a program for retrieving content from webservers*

```
brew install wget --with-libressl
```

**Download the necessary files and install**:

```
wget "https://repo.continuum.io/archive/Anaconda3-2020.02-MacOSX-x86_64.sh" -O ~/miniconda.sh \
&& bash ~/miniconda.sh -f -p $HOME/miniconda
```

---

### <u>Linux</u>

```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda.sh \
&& bash ~/miniconda.sh -b -p $HOME/miniconda
```

---



### <u>Windows</u>

**Pre-Installation:** 

​	Ensure you do not have another default version of Python on your path. You can check your path in the the command prompt using `echo %PATH%` in PowerShell using `Env:List` or in the Git Bash terminal using `echo $PATH`.  The installation below will become the default Python installation on the system and could disrupt anything dependent on the previous default installation.

​	If you have another version of Anaconda or Miniconda, please right-click the start menu icon and select “Apps and Features” and uninstall the previous version before continuing.

#### Step 1.)

*As of Conda 4.6 There is Official Support for [Python in PowerShell](https://www.anaconda.com/conda-4-6-release/)*



**GUI Install**

1. Download the [Installer](https://repo.anaconda.com/archive/Anaconda3-2020.02-Windows-x86.exe) 
2. Double click to launch
3. Select Install for “Just Me”
4. When prompted to select an installation path make sure to select a directory path containing no spaces.
5. Select both **Register Anaconda as my default Python 3.7** & **Add Anaconda to my PATH environment variable**

 

**Command line install**

1. Download the [**Installer**](https://repo.anaconda.com/archive/Anaconda3-2020.02-Windows-x86.exe)
2. Right click the start menu icon and select Windows PowerShell
3. In PowerShell type the following:

```
start Anaconda3-2020.02-Windows-x86.exe /InstallationType=JustMe /AddToPath=1 /RegisterPython=1 /S /D=%UserProfile%\Anaconda3
```



Which just means:**

- /InstallationType - (Install for User only not entire system)

- /AddToPath - Add Miniconda to the PATH on your system so you can use it from the terminal

- /RegisterPython - Make this install the default version of Python on your system

- /S - Silent installation

- /D - Installation path

  

## <s>Colab</s> … Jupyter Lab

***If you’re in Windows it is advisable to work exclusively out of the Anaconda prompt\***

Anaconda comes pre-loaded with 250+ packages so notebook and jupyter lab are already installed, you can launch jupyter lab from the command line using:

```
jupyter lab
```

If you navigate to a certain directory (*like maybe your repository you downloaded earlier*) before launching jupyter lab, then you’ll start right in the directory you launched from.

***WSL2 Users:***

You may want to do the following before working with Jupyter notebooks.

**Generate a config file for Jupyter**

```
jupyter notebook --generate-config
```

The path to the config file will be printed in the terminal. Open with your editor of choice and paste the following into the top of the file:

`c.NotebookApp.allow_origin = '*' #allow all origins` `c.NotebookApp.ip = '0.0.0.0' #allows all ips`

This will keep the connection from dropping, and having to restart the kernel.

## VS Code

**Download the Installer:**

1. [Windows](https://aka.ms/win32-user-stable)
2. [Mac](https://go.microsoft.com/fwlink/?LinkID=620882)
3. Linux
   1. [.deb](https://go.microsoft.com/fwlink/?LinkID=760868)
   2. [.rpm](https://go.microsoft.com/fwlink/?LinkID=760867)

After you install the editor, you’ll need to install the Python extension, and if you’re using WSL then you’ll be asked if you want to install the Remote: WSL extension to let you use the Windows side editor to code inside WSL. You can find the extensions on the left pane. 

### Congratulations on your brand new development environment!

