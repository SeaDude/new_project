# `new_project`

`new_project` is a Python-based CLI tool that automates the creation and scaffolding of Python projects. With a single command, it sets up a ready-to-use project directory, initializes Git, creates a private GitHub repository, and opens the project in VS Code with a pre-configured virtual environment.

## **Features**

- Automatically creates a project directory under `~/projects/<project-name>`.
- Adds essential starter files:
  - `.gitignore` (configured for Python virtual environments)
  - `README.md` with boilerplate sections
  - `requirements.txt`
- Sets up a Python virtual environment in `.venv`.
- Initializes Git, commits the starter files, and pushes to a new private GitHub repository.
- Opens the project in VS Code and activates the virtual environment in the integrated terminal.
- Dynamically determines your GitHub handle using:
  - The GitHub CLI (`gh`) if available, or
  - The `GITHUB_HANDLE` environment variable as a fallback.
- Displays the GitHub repository URL for quick access.

## **Installation**

### Prerequisites

- **Python 3.6+**
- **Git** (with GitHub authentication set up)
- **GitHub CLI (gh)**: Install and authenticate with:
```bash
gh auth login
```

    VS Code: Ensure the code command is available in your terminal:
        Open Command Palette in VS Code (Ctrl+Shift+P) and search for Shell Command: Install 'code' command in PATH.

### Install new_project

- Clone the repository:
```
git clone https://github.com/SeaDude/new_project.git
cd new_project
```

- Move the tool to your local bin directory:
```
chmod +x new_project.py
mv new_project.py ~/.local/bin/new_project
```

- Ensure `~/.local/bin` is in your PATH. Add this line to your `~/.bashrc` or `~/.zshrc`:

- `export PATH="$HOME/.local/bin:$PATH"`

- Reload your shell configuration:

- `source ~/.bashrc`  # or `source ~/.zshrc`

### Usage

To scaffold a new Python project, simply run:

`new_project <project-name>`

- For example:

`new_project my-awesome-app`

How the GitHub Handle is Determined

    The tool first attempts to fetch your GitHub handle using the GitHub CLI (gh).
    If the CLI is unavailable, it falls back to the GITHUB_HANDLE environment variable. To set this, run:

export GITHUB_HANDLE=<your-github-handle>

Add this to your shell configuration to persist it:

    echo "export GITHUB_HANDLE=<your-github-handle>" >> ~/.bashrc

### Example Output
```
Creating project directory at /home/user/projects/my-awesome-app...
Creating virtual environment...
Initializing git...
Creating remote GitHub repository using GitHub CLI...
Opening VS Code...
Project 'my-awesome-app' has been successfully scaffolded!
GitHub repository URL: https://github.com/SeaDude/my-awesome-app
```

### FAQs
- Will the projects directory be automatically created if it’s not present?

    - Yes, the projects directory will be automatically created under your home directory (~/projects) if it doesn’t already exist.
- Can I install this on Windows or macOS?

    - Yes:
        - macOS: Follow the same steps as Linux.
        - Windows: Save the script in a directory like C:\Scripts and add it to your PATH.