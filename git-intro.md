### Core Git Commands for Everyday Use

Here's a walk-through of the most common Git commands using a simple story project as an example. Imagine you have a folder named `my-story` containing a file `story.txt`.

**1. `git init`**

- **Function:** Initializes a new Git repository. This creates a hidden `.git` directory in your project folder to track all your changes. It's the first step for any new project.
- **Example:**

    ```bash
    # Navigate into your project folder
    cd my-story

    # Initialize it as a Git repository
    git init
    # Output: Initialized empty Git repository in /path/to/my-story/.git/
    ```

**2. `git status`**

- **Function:** Shows the current state of your project. It tells you which files have been modified, which are new (untracked), and which are staged for the next commit.
- **Example:** Let's create `story.txt` and add a line.

    ```bash
    echo "Once upon a time..." > story.txt

    # Now check the status
    git status
    # Output:
    # On branch master
    # No commits yet
    # Untracked files:
    #   (use "git add <file>..." to include in what will be committed)
    #         story.txt
    ```

    _What happened:_ Git sees a new file (`story.txt`) but isn't tracking it yet.

**3. `git add`**

- **Function:** Adds your changes from the working directory to the "staging area." The staging area is like a draft of your next commit. You can add one or all files.
- **Example:**

    ```bash
    # Add story.txt to the staging area
    git add story.txt

    # You can also add all modified/new files in the current directory with:
    # git add .
    ```

    _What happened:_ `story.txt` is now staged, ready to be saved in the project's history.

**4. `git commit`**

- **Function:** Saves the staged changes permanently to the repository's history. Each commit is a "snapshot" of your project at a point in time, identified by a unique ID and a descriptive message.
- **Example:**
    ```bash
    git commit -m "Start writing the story"
    # Output:
    # [master (root-commit) 1a2b3c4] Start writing the story
    #  1 file changed, 1 insertion(+)
    #  create mode 100644 story.txt
    ```
    _What happened:_ The initial version of `story.txt` is now saved in Git's history.

**5. `git branch`**

- **Function:** Manages branches. A branch is an independent line of development. You can create a new branch to work on a feature without affecting the main codebase (`main` or `master`).
- **Example:** Let's create a new branch to add a character.

    ```bash
    # Create a new branch called 'add-character'
    git branch add-character

    # List all branches. The asterisk (*) shows your current branch.
    git branch
    # Output:
    # * master
    #   add-character
    ```

    _What happened:_ A new branch `add-character` was created, identical to `master` at this point.

**6. `git checkout`**

- **Function:** Switches between branches.
- **Example:**
    ```bash
    # Switch to the new branch to work on it
    git checkout add-character
    # Output: Switched to branch 'add-character'
    ```
    _What happened:_ You are now working on the `add-character` branch. Any commits you make will be on this branch only.

**7. `git merge`**

- **Function:** Combines the changes from one branch into your current branch.
- **Example:** On the `add-character` branch, let's modify the story.

    ```bash
    echo "A brave knight appeared." >> story.txt
    git add story.txt
    git commit -m "Feat: Add knight character"

    # Now, let's go back to the main branch
    git checkout master

    # And merge the changes from our feature branch into master
    git merge add-character
    # Output:
    # Updating 1a2b3c4..5d6e7f8
    # Fast-forward
    #  story.txt | 1 +
    #  1 file changed, 1 insertion(+)
    ```

    _What happened:_ The commit from the `add-character` branch is now part of the `master` branch history. The `story.txt` file on `master` is now updated.

**8. `git remote add` & `git push`**

- **Function:** `git remote add` connects your local repository to a remote one (e.g., on GitHub). `git push` sends your committed changes to that remote repository.
- **Example:**

    ```bash
    # First, connect to a remote repository (you only do this once)
    git remote add origin https://github.com/your-username/my-story.git

    # Then, push your master branch to the remote named 'origin'
    git push -u origin master
    ```

    _What happened:_ Your entire commit history is now safely backed up on GitHub.

**9. `git pull`**

- **Function:** Fetches changes from a remote repository and merges them into your current local branch. This is how you get updates made by others.
- **Example:**
    ```bash
    # If a collaborator pushed a change, you would run this to get it
    git pull origin master
    ```
    _What happened:_ Your local `master` branch is now synchronized with the remote `master` branch.

**10. `git clone`**

- **Function:** Creates a local copy of a remote repository that already exists on a server like GitHub.
- **Example:**
    ```bash
    # Clone a project from GitHub to your computer
    git clone https://github.com/some-repo/cool-project.git
    ```
    _What happened:_ A new folder named `cool-project` is created on your machine, containing the entire project and its Git history.
