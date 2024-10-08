# Introduction

Hi! Welcome to this Python Template, this `README_dev.md` contains instructions on the intended usage of this python template.

## Setting Up the Project
1. Move to the [template](https://github.com/awegroup/template-python)
2. Find the green button on the top-right that says "Use this template," and create a new repository with your `<repository-name>`.
3. Clone the repository using the green "<> Code" button and copy the SSH link. Tip: SSH keys are a way of authenticating, which alleviates the need to enter your GitHub password on each commit; see this [tutorial](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) to generate an SSH key and establish this connection. 
4. Locally, on your PC, navigate to the folder in which you want the repository to be placed using `cd`. (tip: one can use Tab for auto-completion and double Tab to list all options)
5. Clone the repository. Tip 1: copy-pasting in terminal can be done using: cntrl-shift-v. Tip 2: the arrows `< >` are not required but added here as they are a standard notation form to indicate that there one should enter text)
   ```bash
   git clone <copy-paste the SSH link> 
   ```
6. Navigate into the cloned repository 
   ```bash
   cd <repository-name>
   ```
7. It's time to create our first commit using git; this starts with adding (or staging) the changes. It is important always to do this from the root folder of your repository, to check what will be tracked you can use `git status`.
   ```bash
   git add .
   ```
8. Once the changes are staged, they should be committed with a commit message, e.g. "initial commit". The `-m` is called a flag, indicating that the commit message will follow.
   ```bash
   git commit -m "<type your message here>"
   ```
9. The committed changes are now saved locally and should be pushed to the remote (to Github). You can verify this worked by checking the GitHub repository online.
   ```bash
   git push
   ```
10. Create a virtual environment. The venv is a folder in your project in which all the required external packages ('dependencies') are stored)
    ```bash
    python -m venv venv
    ```
11. Activate the virtual environment; this should result in a (venv) in your terminal, indicating the virtual environment is active. Tip: for proper dependency management, one should **always activate the venv before coding**.
     
   - Linux / macOS
   ```bash
   source venv/bin/activate
   ```
   
   - Windows (Command Prompt)
   ```bash
   venv\Scripts\activate
   ```

   - Windows (PowerShell)
   ```bash
   .\venv\Scripts\Activate
   ```

   
12. Open this folder with your favorite code editor (IDE, for example VSCode) and start coding!
13. Once you are finished you can deactivate the venv
    ```bash
    deactivate
    ```

## Proposed-Workflow

### Generic
- Branch management: work with main branches that have stable releases and create feature branches for implementing new features and merge this once completed. 
- Write user settings in a `.yaml` file
- Store all essential code inside the `src/<package-name>/` folder, and install this package using `pip install -e .` to call these using `import <package-name>`
- All raw data should be in `data`, all processed in `processed_data`, all results in `results`, etc. 
- If results use specific settings, these should also be stored along with the results, such that the result can be reproduced at a later stage (reproducible science)
- - `.gitkeep` is placed such that the empty folder shows on GitHub; without this file, it would be automatically ignored, and the project structure would not be clear. Once other files are inside this folder, this file can be deleted.
- The folders `data/`, `processed_data/`, and `results/` have been added to the `.gitignore` file, as they are expected to contain 
  - large files that should not be uploaded to GitHub
  - confidential data that should not be uploaded to GitHub
  - generated data that can be recreated
  - generated results that can be recreated


### Steps for implementing a new feature
1. First navigate to repository locally and activate virtual environment
   ```bash
   source venv/bin/activate
   ```
2. Create an issue on GitHub
3. Create a branch from this issue and change the branch source to `develop`
4. Use the provided GitHub commands to checkout this branch locally
5. **--- Implement your new feature---**
6. Verify nothing broke using pytest
```
  pytest
```
7. git add, git commit (with # to current Issue number), git push
```
  git add .
  git commit -m "#<number> <message>"
  git push
```
8. Create a pull-request, with `base:develop`, to merge this feature branch and close this issue
9. Update branch information locally using `git fetch --prune`, pull in new info `git pull origin develop` and delete branch locally using `git branch -d <enter branch name>`
```
  git fetch --prune
  git pull --all
  git checkout develop
  git pull
```
10. Once merged on the remote and locally, delete this feature branch on the remote (see pull-request) and locally using 
```
  git branch -d <branch name>
```
11. Close issue


