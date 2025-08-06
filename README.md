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

### Quick Install

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

### Manual Install

If you prefer to install it manually or don't have sudo access:

1. Create a local bin directory if it doesn't exist:

```bash
mkdir -p ~/.local/bin
```

2. Copy the comit file there:

```bash
cp comit ~/.local/bin/
chmod +x ~/.local/bin/comit
```

3. Add it to your PATH by adding this line to your `~/.bashrc` or `~/.zshrc`:

```bash
export PATH="$HOME/.local/bin:$PATH"
```

4. Restart your terminal or run `source ~/.bashrc`

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

- Bash shell (Linux, macOS, WSL on Windows)
- Git installed and configured
- Optional: GitHub account for token features

## Troubleshooting

### Command Not Found
If you get "command not found", make sure:
1. The file is executable: `chmod +x /usr/local/bin/comit`
2. The directory is in your PATH: `echo $PATH`

### Permission Denied
If you can't install to `/usr/local/bin`, use the manual install method to install in your home directory.

### Git Errors
Run `comit --config` to check your Git configuration. Make sure your username and email are set.

## Why Use This

This tool was created because developers spend too much time typing repetitive Git commands. Whether you're a beginner who finds Git intimidating or an experienced developer who wants to work faster, this utility streamlines your workflow.

Instead of memorizing dozens of Git command combinations, you learn one simple command with intuitive options. The tool handles the complexity while you focus on your code.

## Contributing

Feel free to suggest improvements or report issues. The tool is designed to be simple and reliable, covering the most common Git workflows that developers use daily.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.