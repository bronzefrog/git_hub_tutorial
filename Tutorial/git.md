```python
import warnings
warnings.filterwarnings('ignore')

from formatting_width import formatting_width
formatting_width(width=80)
```

# Git

This is a practical guide to git.

It is a barebones approach to getting up and running with git. It contains practical exercises in:  

- Using git on a local repository for version control,  
- Using git on a local local repository for project management, and  
- Using git locally to connect to a remote repository.  
  - The remote repository is: https://github.com/bronzefrog (un: bronzefrog.co@gmail.com pwd: boqnA9-gujdez-vypvab

## Git Application Basics

There is a GUI for git for mac, which is useful for basic commands. It is more common, and easier, to use git on the command line.

git is installed on all macs by default. Type `git --version` on the command line _(for the remainder of this guide, all commands are on the command line)_ and it will return the version that you  have.

<span style='color: rgb(0,0,128);'>**One reason that the command line is easier to use is that git has _amazing_ tab completion. _However, it may need to be set up, or repaired, which you can do [following the steps in this post](https://www.baeldung.com/linux/git-autocompletion)_  
_tab completion:_ If you begin typing an id or repository name, etc, and hit tab then git will fill in the full id/name _(to highlight how powerful this is, if you begin all of your branch names with `feature` and one of the branches is called `feature_hotfix`, after a branch command, if you start to type `hot` it will search through all branch names and fill in `feature_hotfix`)_**</span>


### Git settings

```
git config --list
```

will show you your current settings.

**All** of the settings can be changed by using

```
git config <config item> [your new value]
```

where the `--global` has to be used to change a system wide configuration. _(That is: `git config --global <config item> [your new value]`)_. It is important to set up the global settings to the ones that you will use most often.

_(in the remainder of this guide `< >` will represent an option for the git command (that is required) and `[ ]` will represent a value that you are setting/using)_

## Your first git repository

```
git init
```

will set up git in the current folder _(the folder that the command line is pointing to)_ 

<div style='background-color:#d2d2d2;padding: 30px;'>  
    
_On a mac, `command` + `shift` + `.` will reveal hidden/invisible files/directorys (which begin with `.`), you will see that a `.git` folder is created._

</div>

```
git init [folder name]
```

will create the folder `[folder name]` & set up git in that folder.

- You can set up as many independant local repositories as you want.
- Each will track the contents of each of the folders _(or at least the committed files)_ independently.

---

<div style='background-color:rgb(255,255,255);padding: 30px;'>       

    
### First Task: Create a repository, perform your first commit

- _On the command line_, go to a location that you want to track with git.  
- `git init git` will create a new folder, `git`, and begin to track that folder.    
  - However, you will now need to tell the command line to `cd` _(change directory)_ into that folder: `cd git` to move to that newly created folder.

---

<div style='background-color:#d2d2d2;padding: 30px;'>      
    
_Some details:_  
- By default, this _repository_ contains a _single branch_  
- By default, the name of this branch is `master`  
  _(as this is the default name used for all repositories (for the main/original branch), when you are interacting with other repositories this can be confusing, so you can change this original branch to something else, convention states that `main` is used.)_  
- `git branch -M main` renames the original branch from `master` to `main`   
  - `git status` will show you information about this new repository.  
  - `git log` will show you the history of commits. 

</div>

---

- _On the command line_, `touch file1.txt` will create an empty text file. _Create the files `file1.txt` and `file2.txt`_

---

<div style='background-color:#d2d2d2;padding: 30px;'>      

_Commit details_  
- The first commit will always involve **two** commands _(after which, you can use a single command)_: an `add` and a `commit` command
  - `git add .` will add **all** files to a _staging_ area
  - `git commit -m "your message"` will commit all files in the _staging_ area with a reminder message _(that will show up when you use `git log`)_
- After the first commit, `git commit -a -m "your message` can be used to _add/stage_ and _commit_ the files in one step.

</div>


---

- Open one of the files in a text editor. _(In most text editors, you will see the name of the repository, `main`, somewhere in one of the toolbars - for VSCode it is on the bottom left of the status bar)_.
- _On the command line_, perform your first commit _(of all files)_.
- Go back to the text editor.  Edit the file, adding any text. _(`main`, in the status bar, will change to `main*` show that there is an uncommited change)_
- _On the command line_, type `git status`. _(This will show you if any file has change since the last commit)_.
- _On the command line_, type `git diff`. _(This will show you the file changes since the last commit)_.

<span style='color: rgb(0,0,128);'>**Congrats ... you are now a git user!!**</span>

---

### Second Task: Roll back a commit

- Go back to the text editor.  Edit a file, adding any text.
- _On the command line_, commit all files again.
- _On the command line_, type `git log`
  - **This is important because this is where your find the "commit ids" _(aka hashs, or SHAs)_ - the number after the word `commit`**
- Look through the `log` information and find the first few characters of the **first** commit you performed _(because you want to go back to that)_
- _On the command line_, type `git checkout <SHA>`
  - **Important:** This is where _tab completion_ is a god send, for the `SHA` just type in the first few numbers and hit tab.
  - This is just an example, as explained clearly in this [stackoverflow post](https://stackoverflow.com/questions/4114095/how-do-i-revert-a-git-repository-to-a-previous-commit) _(scroll down to `First of all what is HEAD?`)_ this leaves you in a _'headless'_ state
- Go back to the text editor. The previously committed changes have disappeared.
- _On the command line_, type `git checkout <SHA>` where `SHA` is the hash for the most recent commit.
- Go back to the text editor. The last committed changes have reappeared.

_(As will be explained later, you need to then use `git checkout main` to ensure that the HEAD is on the `main` branch)_

</div>



```python
!jupyter nbconvert --to html --TagRemovePreprocessor.remove_cell_tags='{"hide_code"}' git.ipynb
```

    [NbConvertApp] Converting notebook git.ipynb to html
    [NbConvertApp] Writing 278025 bytes to git.html



```python

```
