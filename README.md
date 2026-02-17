# Automate Project Initialization

![Author - Rehan Khan](https://img.shields.io/badge/Author-Rehan%20Khan-blue)

A Python tool that automates the repetitive process of project initialization — creates a local folder, initializes a Git repository, creates a remote GitHub repo, and pushes the initial commit, all with a single terminal command.

[Demo Video](https://drive.google.com/file/d/1fxOUDBTTRx7c5eJ0y71_0DURdgcm6gq-/view?usp=sharing)

## What It Does

```
create my-new-project
```

This single command:
1. Creates a new folder locally
2. Initializes a Git repository
3. Creates a new repository on GitHub
4. Sets the remote origin
5. Pushes the initial commit

## Two Approaches

| Approach | How It Works | Extra Setup |
|----------|-------------|-------------|
| **GitHub API** (`withGithubAPI/`) | Uses PyGithub to create the remote repo via API | None |
| **Selenium** (`withSelenium/`) | Automates browser to create repo on GitHub | Requires [ChromeDriver](https://chromedriver.chromium.org/) |

## Project Structure

```
Automation_projectInitialization/
├── withGithubAPI/
│   ├── create.py           # Creates repo via GitHub API
│   └── requirements.txt    # PyGithub
├── withSelenium/
│   ├── create.py           # Creates repo via browser automation
│   └── requirements.txt    # selenium
└── .my_custom_commands.sh  # Custom terminal command setup
```

## Installation

1. Clone the repository into your home directory

   ```sh
   git clone https://github.com/khan-rehan/Automation_projectInitialization.git
   ```

2. Choose an approach and install dependencies

   ```sh
   cd Automation_projectInitialization/withGithubAPI  # or withSelenium
   pip install -r requirements.txt
   ```

3. Edit `create.py` and set your GitHub username and password/token

4. Edit `.my_custom_commands.sh` — update line 8 with your GitHub remote URL:

   - HTTPS: `git remote add origin https://github.com/USERNAME/$1.git`
   - SSH: `git remote add origin git@github.com:USERNAME/$1.git`

5. Update all directory paths in the scripts to match your system

6. Source the shell script

   ```sh
   source ~/.my_custom_commands.sh
   ```

## Usage

```sh
create <project-name>
```

To make the command permanent, add `source ~/.my_custom_commands.sh` to your shell profile (`~/.bashrc` or `~/.zshrc`).
