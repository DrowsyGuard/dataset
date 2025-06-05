# Python Development Environment Setup

This guide will help you set up a Python development environment on macOS using Homebrew and pyenv.

## Prerequisites

- macOS system
- Terminal access
- Internet connection

## Step 1: Install Homebrew

Homebrew is a package manager for macOS that makes it easy to install development tools.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

After installation, add Homebrew to your PATH:

```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

## Step 2: Install and Configure pyenv

pyenv allows you to easily install and manage multiple Python versions.

### Install pyenv
```bash
brew install pyenv
```

### Add pyenv to your PATH
Add the following lines to your shell configuration file (`~/.zprofile` for zsh):

```bash
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init --path)"
eval "$(pyenv init -)"
```

Reload your shell configuration:
```bash
source ~/.zprofile
```

## Step 3: Install Python Dependencies

Install the necessary libraries for building Python from source:

```bash
brew install xz zlib readline openssl sqlite3
```

Set up compiler flags for proper linking:

```bash
export CPPFLAGS="-I$(brew --prefix xz)/include"
export LDFLAGS="-L$(brew --prefix xz)/lib"
```

## Step 4: Install Python 3.11.9

If you have a previous installation of Python 3.11.9, remove it first:

```bash
pyenv uninstall 3.11.9
```

Install Python 3.11.9:

```bash
pyenv install 3.11.9
```

Set Python 3.11.9 as the global default version:

```bash
pyenv global 3.11.9
```

## Verification

Verify your installation by checking the Python version:

```bash
python --version
```

You should see `Python 3.11.9`.

## Troubleshooting

- If you encounter build errors during Python installation, ensure all dependencies are installed and compiler flags are set correctly
- If `pyenv` commands are not found, make sure you've added pyenv to your PATH and reloaded your shell configuration
- For M1/M2 Macs, Homebrew installs to `/opt/homebrew/` by default

## Next Steps

With your Python environment set up, you can now:
- Install packages using `pip`
- Create virtual environments with `python -m venv`
- Use pyenv to install additional Python versions as needed
