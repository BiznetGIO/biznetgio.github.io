# Guidelines

---

## Project organization

- We only use one branch for the project: `master` branch.
- Tag will be created to mark stable release.
- Bug fix or Hot fix branches should be created for fixing bugs and merged into
  `master` when ready.

!!! info

    we don't use `master` - `development` branch for monorepo. Instead we use
    `<servicename>/<workitem>` such as `api/add-health-endpoint`, and those
    branches will be merged into master eventually.

## Project name in repositories 

We define project name with prefix svc/fe in repositories.

1.  **svc-**`<yourawesomeproject-api>` 
	If your project contain backend APi such a microservice.
2.  **fe-**`<yourawesomeproject-frontend>` 
	If a frontend project.
3.  `<yourawesomeproject>` 
	Left blank if doesn't contain frontend or backend. 		


## Opening a new issue

1. Look through existing issues to see if your issue already
   exists. **So we don't have duplicate issue**.
2. If your issue already exists, comment on its thread with any
   information you have. Even if this is simply to note that you are having the same problem, it is still helpful!
3. Always *be as descriptive as you can*.
4. What is the expected behavior? What is the actual behavior? What are the steps to reproduce?
5. Attach screenshots, videos, GIFs if possible.
6. **Include `<project>` version or branch experiencing the issue.**
7. **Include OS version experiencing the issue.**


## Submitting a pull request

1. Find an issue to work on, or create a new one. *Avoid duplicates, please check existing issues!*
2. Fork the repo, or make sure you are synced with the latest changes on `master`.
3. Create a new branch with a sweet name: `git checkout -b issue_<##>_<description>`.
4. Do code.
 - Plese follow [PEP8](https://pep8.org/)
 - Please watch your [line length](https://baymard.com/blog/line-length-readability). It's
   advised to limit under 80 char.
5. Write unit tests when applicable.
6. Don't break unit tests or functionality.
7. Update the documentation header comments if needed.
8. **Rebase on `master` branch and resolve any conflicts _before submitting a pull request!_**
9. Submit a pull request to the `master` branch. Make sure to add yourself to
   AUTHORS file.

!!! info

     Start the title with `WIP:` to prevent a Work In Progress merge request from being merged before it's ready. 

## Close issue

Tag an issue start with `close #<issue_number>` on your pull request description.
Issue will close automatically when pull request merged succesfully. 
 

## Restricted Rule
1. Dont create new branch except from master.
2. Dont create pull request except to master.
3. Define prefix `WIP:` to avoid project owner merge your code if you not done yet.
4. Perhaps if you still change your code and unmerge pull request, 
   edit your pull request title with prefix `WIP:`   
5. You should not commit and push your code to others existing pull request. 
Do it for your pull request only!  

!!! important  
    Creating new branch without rebasing from master will miss some latest code. 
    Before continue on your working branch, always fetch first and rebase with master.
    Still confuse with this? Check git tips and ticks [here](git-tutorial.md). 



### First time setup

Please refer to instalation guide and running test suitein each project.