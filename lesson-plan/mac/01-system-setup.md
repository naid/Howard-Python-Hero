# Mac 01 — System setup

**Time:** 2–3 hours  
**Prerequisite:** None

## Goals

- Open and use Terminal confidently
- Install developer tools and Homebrew
- Create a workspace folder for this course

## 1. Open Terminal

1. Press `Cmd + Space`, type **Terminal**, press Enter.
2. You should see a prompt like `yourname@MacBook ~ %`.

Terminal is how you run commands. You will use it constantly in ML work.

## 2. Install Xcode Command Line Tools

Apple’s compiler toolchain is required for many Python packages.

```bash
xcode-select --install
```

A dialog appears — click **Install** and wait (10–20 minutes).

Verify:

```bash
git --version
clang --version
```

Both should print version numbers, not “command not found”.

## 3. Install Homebrew

[Homebrew](https://brew.sh/) installs developer software on Mac.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Follow on-screen instructions. On Apple Silicon, Homebrew often installs to `/opt/homebrew`.

Add Homebrew to your PATH (Apple Silicon — adjust if the installer tells you otherwise):

```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

Verify:

```bash
brew --version
```

## 4. Useful Homebrew packages

```bash
brew install git wget curl htop tree
```

| Tool | Purpose |
|------|---------|
| `git` | Version control (Lesson 3) |
| `wget` / `curl` | Download datasets |
| `htop` | Monitor CPU/RAM |
| `tree` | Visualize project folders |

## 5. Create your course workspace

```bash
mkdir -p ~/python-hero/projects
cd ~/python-hero
```

Optional: open in a code editor.

```bash
brew install --cask visual-studio-code
code ~/python-hero
```

Alternatives: Cursor, PyCharm Community (free).

## 6. Terminal basics (practice)

| Command | What it does |
|---------|----------------|
| `pwd` | Print current directory |
| `ls` | List files |
| `ls -la` | List with details |
| `cd ~/python-hero` | Change directory |
| `mkdir notes` | Create folder |
| `touch hello.txt` | Create empty file |
| `cat hello.txt` | Show file contents |
| `clear` | Clear screen |

**Exercise:** Create `~/python-hero/notes/day1.txt` and write one sentence about your goal for this course.

## 7. Shell configuration (optional but recommended)

Add aliases to `~/.zshrc`:

```bash
cat >> ~/.zshrc << 'EOF'

# Python Hero aliases
alias ll='ls -lah'
alias ..='cd ..'
EOF

source ~/.zshrc
```

## Checklist

- [ ] Terminal opens and `pwd` works
- [ ] `git --version` works after Xcode CLI tools
- [ ] `brew --version` works
- [ ] `~/python-hero` folder exists

**Next:** [02-python-environment](02-python-environment.md)
