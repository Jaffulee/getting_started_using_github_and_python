### Visit my website: https://jaffulee.github.io/Jaffulee/

# Getting Started with Python Development

This guide provides step-by-step instructions to set up your development environment for Python projects, including installing essential tools like Python, VS Code, Git, and GitHub Desktop, and configuring your first project with a virtual environment and Git repository.

## 1. Install Essential Tools

### 1.1. Python

Python is the programming language we'll be using.

1.  **Download Python:** Go to the official Python website: [https://www.python.org/downloads/](https://www.python.org/downloads/)
2.  **Install:** Run the installer.
    *   **Crucial Step:** During installation, ensure you tick the checkbox for **"Add Python to PATH"**. This allows you to run Python commands from any terminal.

### 1.2. VS Code (Visual Studio Code)

VS Code is a popular and powerful code editor.

1.  **Download VS Code:** Go to the official VS Code website: [https://code.visualstudio.com/](https://code.visualstudio.com/)
2.  **Install:** Follow the installation prompts.
3.  **Install Python Extension:**
    *   Open VS Code.
    *   Go to the Extensions view (Ctrl+Shift+X or Cmd+Shift+X).
    *   Search for "Python" by Microsoft and install it. This extension provides rich support for Python development.

### 1.3. Git

Git is a version control system for tracking changes in your code.

1.  **Download Git:** Go to the official Git website: [https://git-scm.com/downloads](https://git-scm.com/downloads)
2.  **Install:** Run the installer.
    *   **Important Note:** When prompted to select your default editor, it's generally recommended to choose something other than Vim if you're not familiar with it (e.g., VS Code or Notepad++).

### 1.4. GitHub Desktop

GitHub Desktop provides a graphical interface for interacting with Git and GitHub.

1.  **Download GitHub Desktop:** Go to the official GitHub Desktop website: [https://desktop.github.com/download/](https://desktop.github.com/download/)
2.  **Install:** Follow the installation prompts.

## 2. Set Up a GitHub Repository

You'll create a repository on GitHub and then clone it to your local machine using GitHub Desktop.

### 2.1. Create a New Repository on GitHub
1.  Go to [https://github.com/](https://github.com/) and log in (or create an account).
2.  Click the `+` icon in the top right corner and select `New repository`.
    - To create a repository based on an existing project, you can navigate to the desired repository and click `fork`, or click `Import Repository` instead.
3.  Give your repository a meaningful name (e.g., `my-python-project`).
4.  Choose whether it's public or private.
5.  (Optional) Add a README file, `.gitignore` (select `Python` template), and license. These can also be added later.
6.  Click `Create repository`.

### 2.2. Clone the Repository Using GitHub Desktop

1.  Navigate to your newly created repository on GitHub (e.g., `github.com/YourUsername/my-python-project`).
2.  Click the green `Code` button.
3.  Select `Open with GitHub Desktop`.
4.  GitHub Desktop will open, prompting you to choose a local path to clone the repository. Select a suitable folder on your computer.
5.  Click `Clone`.

### 2.3. Open the Project in VS Code

1.  Once the repository is cloned in GitHub Desktop, click on `Repository` in the top menu.
2.  Select `Open in Visual Studio Code`. This will open your project folder in VS Code.

## 3. Configure Your Python Project in VS Code

It's best practice to use a Python virtual environment for each project. This isolates project dependencies.

### 3.1. Create a Python Virtual Environment

1.  In VS Code, open a new terminal (`Terminal > New Terminal`).
2.  Run the following command to create a virtual environment named `.venv` in your project folder:
    ```bash
    python -m venv .venv
    ```
3.  Activate the virtual environment:
    *   **On Windows:**
        ```bash
        .venv\Scripts\activate
        ```
        If you get a security error when running `activate`, you may need to change your machine's execution policy. Run Windows PowerShell **as administrator** and execute:
        ```powershell
        Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine
        ```
    *   **On macOS / Linux:**
        ```bash
        source .venv/bin/activate
        ```
4.  Verify that your terminal prompt now has a green `(.venv)` on the left, indicating the virtual environment is active.
5. Install your desired dependencies by running `pip install` in your virtual environment terminal, e.g.:
    ```bash
    pip install pandas
    ```
6.  Save Dependencies to `requirements.txt`:
    - Run: `pip freeze > requirements.txt`
    - _(To install packages from this file later, you would run `pip install -r requirements.txt`)_

### 3.2. Select Python Interpreter

VS Code needs to know which Python interpreter (specifically, the one in your virtual environment) to use for your project.

1.  Press `Ctrl+Shift+P` (or `Cmd+Shift+P` on Mac) to open the Command Palette.
2.  Type and select `Python: Select Interpreter`.
3.  Choose the Python interpreter associated with your `.venv` (it will typically appear as `Python x.xx.x (.venv)`).
4.  (Optional) To ensure VS Code always activates the virtual environment in new terminals:
    *   Navigate to `File > Preferences > Settings` (or `Code > Settings` on macOS).
    *   Search for `python terminal` and ensure `Activate Terminal` and `Execute in File Directory` are enabled.

## 4. Git Workflow and `.gitignore`

### 4.1. Creating a `.gitignore` File

A `.gitignore` file tells Git which files or folders to intentionally ignore from your repository. This is crucial for:
*   **Virtual Environments:** You don't want to commit the entire `.venv` folder, as it can be large and system-specific.
*   **Sensitive Information:** Files like `.env` (which might contain API keys or passwords) should never be committed to a public repository.
*   **Build Artifacts/Caches:** Files like `__pycache__` are generated and don't need to be tracked.

1.  In the root of your project folder in VS Code, create a new file named `.gitignore`. If you already have one, verify that the next step contains everything mentioned.
2.  Add the following lines to your `.gitignore` file:

    ```
    .venv/
    .env
    __pycache__/
    *.pyc
    ```

### 4.2. Pushing Changes to GitHub

Once you've made changes (like creating `.gitignore` or new Python files), you'll want to save them to your GitHub repository.

1.  In your VS Code terminal (with the virtual environment activated), stage your changes:
    ```bash
    git add .
    ```
    (This stages all new and modified files in the current directory and subdirectories.)
2.  Commit your changes with a descriptive message:
    ```bash
    git commit -m "Initial project setup with virtual environment and gitignore"
    ```
3.  Push your committed changes to GitHub:
    ```bash
    git push origin main
    ```
    (If your default branch is named `master` instead of `main` (one of the Git installation settings), use `git push origin master`.)
4.  Verify on GitHub that your `.gitignore` (and any other files you added) are now visible in your repository.

You are now set up to begin developing your Python project!

### 5. Working With Branches

Working directly on your `main` or `master` branch for development is generally not recommended. A common and safer workflow involves creating a new branch for your specific task or feature, making all your changes there, pushing those changes to that dedicated branch, and then merging it back into the main branch once the work is complete and reviewed.

1.  **Create a New Branch:**
    *   In your VS Code terminal, create a new branch and switch to it using the command:
        ```bash
        git switch -c feature/my-new-feature
        ```
        (Replace `feature/my-new-feature` with a descriptive name for your branch, e.g., `bugfix/fix-login-error` or `feature/add-user-profile`.)
2.  **Make Changes and Commit:**
    *   Do your development work on this new branch, creating new files or modifying existing ones.
    *   Commit your changes identically to before:
        ```bash
        git add .
        git commit -m "Add new feature: my new feature"
        ```
3.  **Push Changes to Your Branch:**
    *   Push your committed changes to the new branch on GitHub:
        ```bash
        git push origin feature/my-new-feature
        ```
        (The first time you push a new branch, Git might prompt you to set an upstream branch, e.g., `git push --set-upstream origin feature/my-new-feature`).
4.  **Create a Pull Request and Merge:**
    *   On your GitHub repository website, after pushing your branch, you will typically see a banner or button appear at the top (e.g., "Compare & pull request") to initiate a Pull Request.
    *   Click this button, review your changes, and create the Pull Request.
    *   Once you are happy with your changes and any code reviews are complete, you can merge the Pull Request into your `main` (or `master`) branch.

