# Nano Git

Trying to explain git to somebody (small)

### What is git?

Git is a **distributed version control system** designed to handle everything from small to very large projects with speed and efficiency. It allows multiple people to work on a project simultaneously without interfering with each other's work. Git keeps track of changes made to files, so you can revert to previous versions if needed, and it helps in managing and merging changes from different contributors.

Git is a version control system **created by Linus Torvalds in 2005**. It is used to track changes, collaborate with others, and maintain a project's history. Git is known for its speed, efficiency, and ability to handle large projects.

### What is GitHub?

GitHub is a web-based platform that uses Git for version control and collaboration. It provides a user-friendly interface for managing Git repositories, making it easier for developers to share their code and collaborate on projects. GitHub offers features such as issue tracking, project management, and continuous integration, which help streamline the development process.

GitHub also hosts open-source projects, allowing developers to contribute to and benefit from a vast ecosystem of shared code. With GitHub, you can fork repositories, submit pull requests, and review code changes, making it an essential tool for modern software development.

## First example

> **Note:** Before starting, ensure that Git is installed on your system. You can download and install Git from the official [Git website](https://git-scm.com/). For detailed installation instructions, refer to the [Git installation guide](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

1. **Create a repo locally**

    Open your terminal and navigate to the directory where you want to create your local repository. Then, run the following commands:

    ```sh
    mkdir my-project
    cd my-project
    git init
    ```

    This will create a new directory called `my-project` and initialize an empty Git repository in it.

2. **Create a repo in GitHub**

    Go to [GitHub](https://github.com/) and log in to your account. Click on the `+` icon in the top right corner and select `New repository`. Fill in the repository name, description (optional), and choose whether it should be public or private. Click on `Create repository`.

3. **Upload local repo to GitHub**

    First, add your GitHub repository as a remote to your local repository. Replace `USERNAME` with your GitHub username and `REPO_NAME` with the name of your GitHub repository:

    ```sh
    git remote add origin git@github.com:USERNAME/REPO_NAME.git
    ```

    If you haven't set up SSH keys yet, follow the instructions in the [GitHub Docs](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/about-ssh) to generate and add an SSH key to your GitHub account.

    Next, add your files to the repository, commit the changes, and push them to GitHub:

    ```sh
    echo "# Nano Git" >> README.md
    git add README.md
    git commit -m "Initial commit"
    git push -u origin master
    ```

    This will upload your local repository to GitHub and set the `origin` remote as the default for future pushes.

For more detailed information, refer to the [GitHub Docs](https://docs.github.com/en/get-started/quickstart/create-a-repo) on creating a repository.

## Explanation of first example

This code interacts with a Git repository. Below are the key concepts used in this context:
- **Commit**: A commit in Git is a snapshot of your repository at a specific point in time. It records changes to the files and directories in the repository. Each commit has a unique identifier (SHA) and includes metadata such as the author, date, and commit message.
> NOTE: A SHA (Secure Hash Algorithm) is a cryptographic hash function that generates a unique identifier for each commit. For more information, refer to the [SHA Wikipedia page](https://en.wikipedia.org/wiki/Secure_Hash_Algorithms).
- **Origin**: Origin is the default name given to the remote repository from which a local repository was cloned. It serves as a reference to the original repository URL, allowing you to fetch and push changes to and from the remote repository.
- **Staging**: Staging is the process of preparing changes to be committed. When you stage changes, you add them to the staging area (also known as the index). This allows you to review and modify the changes before committing them to the repository.
- **Push**: Push is the process of sending committed changes from your local repository to a remote repository. This updates the remote repository with your latest commits, making them available to other collaborators.
- **Fetch**: Fetch is the process of downloading changes from a remote repository to your local repository. It updates your local copy of the remote branches, allowing you to see the latest changes made by others without merging them into your local branches.

# Second example
1. **Generate files to be ignored**

    In your project directory, create 10 files named `ignore_file_0.txt` to `ignore_file_9.txt`:

    ```sh
    for i in {0..9}; do touch "ignore_file_$i.txt"; done
    ```

    This will create 10 empty files that match the pattern `ignore_file_*.txt`.

2. **Create a `.gitignore` file**

    In your project directory, create a file named `.gitignore` and add the following line to it:

    ```sh
    echo "ignore_file_*.txt" >> .gitignore
    ```

    This will ensure that any files matching the pattern `ignore_file_*.txt` are ignored by Git and not tracked in the repository.

3. **Add and commit the `.gitignore` file**

    Add the `.gitignore` file to the staging area, commit the changes, and push them to GitHub:

    ```sh
    git add .gitignore
    git commit -m "Add .gitignore to ignore files matching ignore_file_*.txt"
    git push
    ```

    This will create a new commit with the `.gitignore` file and push it to the remote repository on GitHub.

# Third example

1. **Create a branch from master**

    First, ensure you are on the `master` branch and create a new branch named `add_third_example`:

    > NOTE: First command could be skipped as we were alreay on master branch.
 
    > **IMPORTANT:** Always perform a `git pull` when creating a branch from master to avoid merging errors or diverging paths.

    ```sh
    git checkout master
    git branch add_third_example
    ```

    This will create a new branch called `add_third_example` based on the `master` branch.

2. **Switch to the new branch**

    Switch to the `add_third_example` branch:

    ```sh
    git checkout add_third_example
    ```

    This will switch your working directory to the `add_third_example` branch.

3. **Make changes and commit**

    Create a new file named `third_example.txt` and add some content to it:

    ```sh
    echo "This is the third example." >> third_example.txt
    git add third_example.txt
    git commit -m "Add third_example.txt with initial content"
    ```

    Modify the `third_example.txt` file:

    ```sh
    echo "Adding more content to the third example." >> third_example.txt
    git add third_example.txt
    git commit -m "Update third_example.txt with additional content"
    ```

    This will create two commits in the `add_third_example` branch.

    > NOTE: All the `>>` steps could be thought of manually opening and editing a text file in a regular text editor, such as TextEditor or VSCode.

4. **Merge changes to master**

    Switch back to the `master` branch and merge the changes from `add_third_example`:

    ```sh
    git checkout master
    git merge add_third_example
    ```

    This will merge the changes from the `add_third_example` branch into the `master` branch.

## Notes on merge strategies

- **Squash and merge**: This strategy combines all the commits from a feature branch into a single commit before merging it into the target branch. It is useful for keeping the commit history clean and concise. To perform a squash and merge, you can use the following command:

    ```sh
    git checkout master
    git merge --squash add_third_example
    git commit -m "Add third example"
    ```

- **Normal merge**: This strategy merges all the commits from the feature branch into the target branch, preserving the commit history. It is useful for maintaining a detailed history of changes. The command for a normal merge is:

    ```sh
        git checkout master
        git merge add_third_example
    ```

This will merge the feature branch into the target branch without squashing the commits.

## Notes on `--no-ff` flag

The `--no-ff` flag ensures that a merge commit is always created, even if a fast-forward merge is possible. This helps preserve the history of feature branches.

By default, Git performs a fast-forward merge if possible, which moves the branch pointer forward to the latest commit, resulting in a linear history.

To set `--no-ff` as the default for all merges, use the following command:

```sh
git config --global merge.ff false
```

In summary:
- `--no-ff`: Creates a merge commit, preserving branch history.
- Default (without `--no-ff`): Performs a fast-forward merge if possible, resulting in a linear history.

# Fourth example

1. **Create a new branch**

    Use steps from [previous example](#third-example) or you could do branch creation and switch in a single command as follows:
    ```sh
    git checkout -b fourth_example_prs
    ```

3. **Create a new dummy file and commit**

    Create a new file named `dummy_file.txt` and add some content to it:

    ```sh
    echo "This is a dummy file for the PR example." >> dummy_file.txt
    git add dummy_file.txt
    git commit -m "Add dummy_file.txt for PR example"
    ```

    This will create a commit in the `create_pr_example` branch.

4. **Push the branch to GitHub**

    Push the `create_pr_example` branch to the remote repository:

    ```sh
    git push -u origin create_pr_example
    ```

    This will push the branch to GitHub and set the `origin` remote as the default for future pushes.

5. **Open a Pull Request (PR)**

    Go to your repository on GitHub. You should see a prompt to compare and create a pull request for the recently pushed branch. Click on `Compare & pull request`.

    Fill in the PR title and description, then click on `Create pull request`.

    For more detailed information, refer to the [GitHub Docs](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) on creating a pull request.

## Notes on Pull Requests

- **Review process**: PRs allow team members to review code changes before merging them into the main branch. This helps ensure code quality and catch potential issues early.
- **Discussion and feedback**: PRs provide a platform for discussing changes, suggesting improvements, and providing feedback. This fosters collaboration and knowledge sharing within the team.
- **Automated checks**: PRs can be integrated with continuous integration (CI) tools to run automated tests and checks. This helps ensure that changes do not introduce new issues or break existing functionality.
- **Merge options**: When merging a PR, you can choose from different merge options such as `Merge`, `Squash and merge`, or `Rebase and merge`. Each option has its own benefits and use cases, as discussed in the previous examples.

By following these steps and considerations, you can effectively create and manage pull requests in GitHub, facilitating collaboration and maintaining code quality in your projects.