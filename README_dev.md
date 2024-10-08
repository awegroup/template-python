## Introduction

Hi! Welcome to this Python Template, this `README_dev.md` contains instructions on the intended usage of this python template.

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

# Setting up your project
1. Move to the [template](https://github.com/awegroup/template-python)
2. Find the green button on the top-right that says "Use this template," and create a new repository with your `<repository-name>`.
3. Navigate to the green "<> Code" button and copy the SSH link. Tip: SSH keys are a way of authenticating, which alleviates the need to enter your GitHub password on each commit; see this [tutorial](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) to generate an SSH key and establish this connection. 
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
     
   ```bash
     # linux
     source venv/bin/activate
     ```
     ```bash
     # Windows (Command Prompt)
     venv\Scripts\activate
     ```
     ```bash
     # Windows (PowerShell)
     .\venv\Scripts\Activate
   ```

   
12. Open this folder with your favorite code editor (IDE, for example VSCode) and start coding!
13. Once you are finished you can deactivate the venv
    ```bash
    deactivate
    ```

# Workflow for implementing new features
1. First navigate to repository locally and activate virtual environment
   ```bash
     # linux
     source venv/bin/activate
     ```
     ```bash
     # Windows (Command Prompt)
     venv\Scripts\activate
     ```
     ```bash
     # Windows (PowerShell)
     .\venv\Scripts\Activate
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
  git commit -m "#<issue-number> <commit-message>"
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


# Packaging through the .toml file
###  Setting up the .toml file
1. Ensure all your package code is inside the folder `src/<package-name> and contains `__init__.py` files in all its sub directories
2. Go to the `pyproject.toml` file and enter your package-name to the 3rd line:
  ```bash
    name = "<package-name>"
  ```
4. For proper documentation: change the fields; version, description, requires-python, license, keywords, authors, maintainers and classifiers.
5. Add the dependencies that you need to the dependency list, example:
    ```bash
    dependencies = [
    "numpy", 
    "pandas>=1.5.3", 
    "matplotlib>=3.7.1"
     ]
    ```
5. Add developer dependencies if you like, example:
    ```bash
      [project.optional-dependencies]
      dev = [
        "pytest",
        "pytest-cov",
        "black",
        ]
    ```
7. Change the "source" URL
    ```bash
     "Source" = "<enter_your_repository_URL>"
    ```
8. Optional, if you would like your users to ONLY install `.py` files within the `src/<package-name>` directory and not the other files, you can remove the following lines:
    ```bash
      # To grab all the files from the src folders of installed packages, not only the .py files
      [tool.setuptools.packages.find]
      where = ["src"]
    ``` 

### Using your package locally
1. Navigate to the root-directory of your repository and create a virtual environment
   ```bash
     # linux
     source venv/bin/activate
     ```
     ```bash
     # Windows (Command Prompt)
     venv\Scripts\activate
     ```
     ```bash
     # Windows (PowerShell)
     .\venv\Scripts\Activate
   ```
2. Install your local package using, where the `[dev]` is optional, to include the developer specified dependencies
   ```bash
     pip install -e .[dev]
   ```
3. When writing code, e.g. inside the `scripts/` folders, you can now access the package using
   ```bash
     # To import the package
     import <package-name>
     # for a specific file within the package
     from <package-name> import <file-name>
     # for a specific function, within a file, within the package
     from <package-name>.<file-name> import <function-name>
   ```
   
