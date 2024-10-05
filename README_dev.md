# Introduction

Hi! Welcome to this Python Template, this `README_dev.md` contains instructions on the intended usage of this python template.

## Getting-Started
1. Move to the [template](https://github.com/awegroup/template-python)
2. Find the green button on the top-right that says "Use this template," and create a new repository with your `<repository-name>`.
3. Clone the repository using the green "<> Code" button, copy the SSH link
4. Locally, on your PC, navigate to the folder in which you want the repository to be placed using `cd`. (tip: one can use Tab for auto-completion and double Tab to list all options)
5. Clone the repository. (tip: copy-pasting in terminal can be done using: cntrl-shift-v)
   ```bash
   git clone <copy-paste the SSH link> 
   ```
6. Navigate into the cloned repository (
   ```bash
   cd <repository-name>\
   ```
7. Time to create our first commit using git, first one should add all the changes. It is important to always do this from the root folder of your repository, to check what will be tracked you can use `git status`.
   ```bash
   git add .
   ```
8. Once the changes are staged, they should be committed with a commit message, e.g. "initial commit". (The `-m` is called a flag, indicating that the commit message will follow. For this message, the arrows `< >` are not required but added here as they are a standard notation form to indicate that there one should enter text)
   ```bash
   git commit -m "<type your message here>"
   ```
9. The commited changes are now saved on locally, and should be pushed to the remote (to Github). You can verify this worked, by checking the GitHub repository online.
   ```bash
   git push
   ```
10. Create a virtual environment (this is a folder in your project, in which all the required external packages ('dependencies') are stored)
    ```bash
    python -m venv venv
    ```
11. Activate the virtual environment, this should result in a (venv) in your terminal, indicating the virtual-environment is active. 
    ```bash
    source venv/bin/activate
    ```
12. you can now open this folder with your favorite code editor (IDE, e.g. VSCode) and start coding!
13. Once you are finished you can deactivate the venv using, don't forget next-time you start coding to activate the venv once more
    ```bash
    deactivate
    ```

## Setting-Up the Project
- [ ] Update 

## Proposed-Workflow

### Generic
- Work with a main, develop and feature branches
- Write user settings in a `.yaml` file
- Don't use any hardcode inside your source folder
- Write scripts that should be run inside notebooks
- The other folders should only contain functions or data


### Steps for implementing a new feature
1. Create an issue on GitHub
2. Create a branch from this issue and change the branch source to `develop`
3. Use provided cmds to checkout this branch locally
4. --- Implement your new feature---
5. Verify nothing broke using pytest
```
  pytest
```
7. git add, git commit (with # to current Issue number), git push
```
  git add .
  git commit -m "#<number> <message>"
  git push
```
7. Create a pull-request, with `base:develop`, to merge this feature branch and close this issue
9. Update branch information locally using `git fetch --prune`, pull in new info `git pull origin develop` and delete branch locally using `git branch -d <enter branch name>`
```
  git fetch --prune
  git pull --all
  git checkout develop
  git pull
```
9. Once merged on the remote and locally, delete this feature branch on the remote (see pull-request) and locally using 
```
  git branch -d <branch name>
```
10. Close issue


## Explanation of folders/files
- `.gitkeep` is placed such that the empty folder show on GitHub, without this file would be automatically ignored and the project structure would not be clear. Once other files are present inside this folder, this file can be deleted.
- The folders `data/`, `processed_data/`, and `results/` have been added to the `.gitignore` file, as they are expected to contain 
  - large files that should not be uploaded to GitHub
  - confidential data that should not be uploaded to GitHub
  - generated data that can be recreated
  - generated results that can be recreated
