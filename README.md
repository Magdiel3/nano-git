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

