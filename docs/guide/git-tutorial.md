Here we give some tips and tricks when you work in a team to manage git project.

### 1. Keep your branch with latest code.
**Tips:** please do always rebase your current active branch with master. 
Why? By rebase your branch will sync your code always update with changed or merged master.

**Tricks:** on your current working branch do this step

```bash
   git fetch
```
then rebase from master
```bash
   git rebase origin/master
```




