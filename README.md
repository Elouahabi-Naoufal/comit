# Comit - Git Shortcut Utility

A professional Git shortcut utility that replaces complex multi-step Git workflows with simple, memorable commands. Instead of typing multiple Git commands, you can accomplish common tasks with a single `comit` command.

## What This Does

If you're tired of typing the same Git commands over and over, this tool is for you. Instead of:

```bash
git add .
git commit -m "Fix authentication bug"
git push origin main
```

You just type:

```bash
comit "Fix authentication bug"
```

That's it. The tool handles over 40 different Git workflows, from basic commits to advanced operations like interactive rebasing and hotfix management.

## Installation

### Linux & macOS

#### Quick Install (Recommended)

1. Download the `comit` file from this repository
2. Make it executable and move it to your system path:

```bash
chmod +x comit
sudo mv comit /usr/local/bin/
```

3. Run the setup wizard:

```bash
comit --setup
```

#### Manual Install (No sudo required)

1. Create a local bin directory:

```bash
mkdir -p ~/.local/bin
```

2. Copy and make executable:

```bash
cp comit ~/.local/bin/
chmod +x ~/.local/bin/comit
```

3. Add to PATH in your shell profile:

**For Bash** (`~/.bashrc` or `~/.bash_profile`):
```bash
export PATH="$HOME/.local/bin:$PATH"
```

**For Zsh** (`~/.zshrc`):
```bash
export PATH="$HOME/.local/bin:$PATH"
```

4. Restart your terminal or run `source ~/.bashrc` (or `source ~/.zshrc`)

### Windows

#### Using WSL (Windows Subsystem for Linux) - Recommended

1. Install WSL2 with Ubuntu from Microsoft Store
2. Open Ubuntu terminal and follow the Linux installation steps above
3. Use `comit` from within the WSL environment

#### Using Git Bash

1. Install Git for Windows (includes Git Bash)
2. Download the `comit` file to a folder like `C:\tools\`
3. Open Git Bash and navigate to the folder:

```bash
cd /c/tools/
chmod +x comit
```

4. Add to PATH by creating an alias in `~/.bashrc`:

```bash
echo 'alias comit="/c/tools/comit"' >> ~/.bashrc
source ~/.bashrc
```

#### Using PowerShell (Advanced)

1. Install Git for Windows
2. Create a PowerShell wrapper script `comit.ps1`:

```powershell
#!/usr/bin/env pwsh
bash C:\tools\comit $args
```

3. Add the script location to your PowerShell PATH

## First Time Setup

After installation, run the setup wizard to configure Git and optionally save your GitHub token:

```bash
comit --setup
```

This will configure your Git username, email, default branch settings, and optionally save a GitHub token for private repository operations.

## Basic Usage

### Simple Commits
```bash
comit "Your commit message"           # Add, commit, and push
comit -n "Work in progress"           # Commit without pushing
comit --wip "Still working on this"   # Quick work-in-progress commit
```

### Branch Operations
```bash
comit -b feature/login "Start login"  # Create new branch and commit
comit -c main                         # Switch to main branch
comit --merge feature/login           # Merge branch into current
```

### Quick Info
```bash
comit -s                              # Quick status
comit -l                              # Recent commit log
comit --tree                          # Visual commit tree
```

## All Available Commands

Run `comit --help` to see the complete list of available commands. The help is organized into categories:

- **Setup & Configuration**: First-time setup, token management, SSH keys
- **Basic Commits**: Standard commit workflows with various options
- **Branch Operations**: Create, switch, merge, and delete branches
- **Workflow Shortcuts**: Pull, sync, stash operations
- **Advanced Operations**: Squashing, resetting, hotfixes, releases
- **Information & Status**: Various ways to check repository status

## Common Workflows

### Daily Development
```bash
comit -p                              # Pull latest changes
comit "Fix user authentication"       # Make changes and commit
comit --sync                          # Sync with remote
```

### Feature Development
```bash
comit -b feature/new-ui "Start UI"    # Create feature branch
comit "Add login form"                # Work on feature
comit "Style login page"              # More commits
comit -c main                         # Switch back to main
comit --merge feature/new-ui          # Merge when ready
```

### Emergency Fixes
```bash
comit --hotfix "Fix critical bug"     # Creates timestamped hotfix branch
comit --release v1.2.1               # Tag and push release
```

## GitHub Integration

The tool supports GitHub token integration for private repositories and enhanced features:

```bash
comit --save-token                    # Save your GitHub token
comit --token                         # Initialize new repo with GitHub
comit --ssh                           # Setup SSH keys for GitHub
```

## Advanced Features

### Interactive Operations
- `comit --squash 3` - Interactively squash last 3 commits
- `comit --clean` - Clean workspace (with confirmation)
- `comit --hard-reset main` - Hard reset to main branch

### Repository Management
- `comit --clone https://github.com/user/repo` - Clone and setup
- `comit --sync-fork` - Sync forked repository with upstream
- `comit --new-feature name` - Create feature branch with upstream

## Safety Features

The tool includes several safety measures:

- Confirmation prompts for destructive operations
- Automatic checks for Git repository presence
- Clear error messages and colored output
- Ability to undo last commit with `comit --oops`

## Documentation

Install the man page for offline documentation:

```bash
comit --install-man
man comit
```

## Requirements

### All Platforms
- Git installed and configured
- Optional: GitHub account for token features

### Platform-Specific
- **Linux/macOS**: Bash shell (pre-installed)
- **Windows**: WSL2, Git Bash, or PowerShell with Git for Windows

## Troubleshooting

### Command Not Found

**Linux/macOS:**
- Check if file is executable: `chmod +x /usr/local/bin/comit`
- Verify PATH includes the directory: `echo $PATH`

**Windows (Git Bash):**
- Ensure the alias is set: `alias comit`
- Check if Git Bash can find the file: `which comit`

**Windows (WSL):**
- Follow the Linux troubleshooting steps above

### Permission Denied

**Linux/macOS:**
- Use the manual install method to install in your home directory
- Or use `sudo` if you have administrator access

**Windows:**
- Run Git Bash or PowerShell as Administrator
- Or place the file in a user-writable directory

### Git Errors
Run `comit --config` to check your Git configuration. Make sure your username and email are set:

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

## Why Use This

This tool was created because developers spend too much time typing repetitive Git commands. Whether you're a beginner who finds Git intimidating or an experienced developer who wants to work faster, this utility streamlines your workflow.

Instead of memorizing dozens of Git command combinations, you learn one simple command with intuitive options. The tool handles the complexity while you focus on your code.

## Contributing

Feel free to suggest improvements or report issues. The tool is designed to be simple and reliable, covering the most common Git workflows that developers use daily.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.