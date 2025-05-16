```python
import warnings
warnings.filterwarnings('ignore')

from formatting_width import formatting_width
formatting_width(width=80)
```

# Git II: Branching (Local)

The **version control** features in _git_, on their own, are useful. However, in combination with **branching** they are very powerful.

By adding **Branching**, _git_ becomes a **“Distributed Version Control System**

However, to introduce **Branching**, I will continue, as before, working from a _Local Repository_.

<span style='color: rgb(0,0,128);'>**Important: The main difficulty with using _git_ is when there are conflicts between branches. This _only_ occurs when _both_ branches have been edited independently (so that git does not know which changes in which branch to preserve)**. In other words, if you branch and only make changes on one single branch and then merge those changes, **there will never be conflicts**</span>

---

## Your first branch

<span style='color: rgb(0,0,128);'>As with `commit`s, there is a two step version and a one step version of creating and accessing branches. However, either can be used _at any time_ and _the one step version is the most commonly used_</span>

_Two step approach, create a branch, then 'check it out'_
```
git branch [branch name]
git checkout [branch name]
```

_One step approach, create a branch and 'check it out' (where the `-b` flag is used to create the branch (and is thus not required the next time that the branch is check out)_

```
git checkout -b [branch name]
```


---

<div style='background-color:rgb(255,255,255);padding: 30px;'>       

    
### First Task: Create a branch

- _On the command line_, create and checkout a new branch: `git checkout -b [branch name]`
  - Until there is a commit on either branches, the information in each will remain the same.
- Go to the text editor _(note that `main`, in the status bar, will have changed to the new branch name)_, edit one of the files.
- _On the command line_, commit the changes _(`git commit -a -m ["commit message"]`)_
- _On the command line_, change branches back to `main` _(`git checkout main`)_
- In the text editor, the repository name will be `main` again, and the last modifications to the file will disappear.
  - You can switch between the two branches to see that the changes will reappear when you _'checkout'_ the branch.

---

<div style='background-color:#d2d2d2;padding: 30px;'>      
    
_Some details:_  
- `git diff main first_branch` will show you the differences between the two branches _(assuming that the new branch is called `first_branch`)_
- If there are _no new commits_ there will be _no difference_
- `git log` will show the complete history of commits _**for all branches**_

</div>

---

### Second Task: Merge Branches

- _On the command line_, **ensure that you have `main` checked out**, `git merge main [branch name]` will merge the new branch into `main` _(Note: `[branch name]` is the single word name that  you have used for the new branch)_
  - **Important:** If you have the new branch checked out,  `git merge [branch name] main `, will **try** merge changes to main into the new branch _(given that there are none, you will be told `Already up to date` .. so doing this will not cause an issue, but may be confusing)._ If you are editing multiple branches, there is a subtle difference in the direction of the merge. This is [explained in the checked answer (scroll down the page) here](https://stackoverflow.com/questions/49715421/does-the-order-of-git-merging-matter).
  - Also, the command is slightly confusing, the second _branch_ is merged into the first _branch_
  - As long as you edit the new branch and merge it into the `main` branch, there will never be conflicts _(it is only if you edit both, in different ways, that conflicts arise)_
  - Typically, once merged, you will delete the new branch. _However,_ if you have performed extensive work on that branch, there may be value, at some point in the future, in the commits in that branch.
  - `git branch -d [branch name]` will delete the branch

---

<div style='background-color:#d2d2d2;padding: 30px;'>      
    
_Some details:_  
- If after some extended period of time, you realize that you want to go back to one of the commits on the _new branch_ (or you want information from that commit), you would need a ph.d. in _git_ to determine which _direct_ approach to take. _(stackoverflow if full of disagreements about which way is the best way to recover information from commits and merge them into `main`. [This thread is a good example](https://stackoverflow.com/questions/4114095/how-do-i-revert-a-git-repository-to-a-previous-commit))_.
- By far the simplest way to approach this is to make a **third branch** directly from **the commit that you want information from**
  - `git log` will give you the commits and their `SHA`s - copy and paste the commit `SHA` that you need
  - `git checkout -b [3rd branch name] [SHA]`
  - By doing this, you have checkout that particulare commit (`SHA`) into a new branch, so that **the files** visible to you _(in your text editor, etc)_ will be for the commit that you want the information from.
  - This allows you to copy and paste that information _(into a file not within the repository that you are working in)_, and then, once complete you can checkout `main` (or another branch) again, delete the 3rd branch (it will not delete any information from other branches).
  - How you reincorporate the information is up to you, the main thing is that you have that old information. 
  

</div>


</div>



```python
!jupyter nbconvert --to html --TagRemovePreprocessor.remove_cell_tags='{"hide_code"}' git_branch.ipynb
```

    [NbConvertApp] Converting notebook git_branch.ipynb to html
    [NbConvertApp] Writing 276165 bytes to git_branch.html



```python

```
