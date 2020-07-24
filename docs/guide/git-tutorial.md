Here we give some tips and tricks when you work in a team to manage git project.

### 1. Always create branch from master.
**Tips:** Do as always before you create new branch. Untracking file without sync from master probably raise conflicts. 

**Tricks:** checkout to master first
```bash
   git checkout master
```
pull from upstream to update all content and informations into your local repo

```bash
   git pull
```
you can create branch then checkout to new branch
```bash
   git checkout -b <your-new-feature-branch>
```


### 2. Keep your branch with latest code.
**Tips:** please do always rebase your current active branch with master. 
Why you should do this? with rebase your branch will always sync with master if any changed or merged.

**Tricks:** on your current working branch do this step

```bash
   git fetch
```
then rebase from master
```bash
   git rebase origin/master
```
do pull to ensure your code sync with master
```bash
   git pull
```





