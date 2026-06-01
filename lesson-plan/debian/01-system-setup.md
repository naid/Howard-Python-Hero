# Debian 01 — System setup

**Time:** 2–3 hours  
**Prerequisite:** None  
**Tested on:** Debian 12 (Bookworm). Ubuntu users can use the same commands with `sudo` where noted.

## Goals

- Use the terminal on Debian
- Update the system and install build tools
- Create a workspace for this course

## 1. Open terminal

- **Desktop:** Applications → Terminal, or `Ctrl+Alt+T`
- **SSH:** `ssh user@your-server-ip`

Prompt example: `user@debian:~$`

## 2. Update package lists

```bash
sudo apt update
sudo apt upgrade -y
```

Enter your password when prompted. Reboot if the kernel was upgraded:

```bash
sudo reboot
```

## 3. Essential packages

```bash
sudo apt install -y \
  build-essential \
  git \
  curl \
  wget \
  htop \
  tree \
  vim \
  nano \
  ca-certificates \
  software-properties-common
```

| Package | Purpose |
|---------|---------|
| `build-essential` | gcc, make — compile Python C extensions |
| `git` | Version control |
| `curl` / `wget` | Downloads |
| `htop` | Monitor CPU/RAM/GPU processes |

Verify:

```bash
git --version
gcc --version
```

## 4. Create workspace

```bash
mkdir -p ~/python-hero/projects
cd ~/python-hero
```

## 5. Install a code editor (optional)

**VS Code:**

```bash
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
sudo install -o root -g root -m 644 packages.microsoft.gpg /etc/apt/trusted.gpg.d/
sudo sh -c 'echo "deb [arch=amd64,arm64,armhf signed-by=/etc/apt/trusted.gpg.d/packages.microsoft.gpg] https://packages.microsoft.com/repos/code stable main" > /etc/apt/sources.list.d/vscode.list'
sudo apt update
sudo apt install -y code
```

Or use `vim` / `nano` only — sufficient for the course.

## 6. Terminal basics (practice)

| Command | What it does |
|---------|----------------|
| `pwd` | Current directory |
| `ls -la` | List files with details |
| `cd ~/python-hero` | Change directory |
| `mkdir notes` | New folder |
| `nano notes/day1.txt` | Edit file in terminal |
| `cat notes/day1.txt` | Display file |
| `man ls` | Manual for `ls` (press `q` to quit) |

**Exercise:** Write your learning goal in `~/python-hero/notes/day1.txt`.

## 7. Shell aliases (optional)

Add to `~/.bashrc`:

```bash
cat >> ~/.bashrc << 'EOF'

# Python Hero aliases
alias ll='ls -lah'
alias ..='cd ..'
EOF

source ~/.bashrc
```

## 8. Check for NVIDIA GPU (optional)

```bash
lspci | grep -i nvidia
```

If you see an NVIDIA device, you will set up CUDA in [03-gpu-and-accelerators](03-gpu-and-accelerators.md).

## Checklist

- [ ] `sudo apt update` succeeds
- [ ] `git` and `gcc` installed
- [ ] `~/python-hero` exists

**Next:** [02-python-environment](02-python-environment.md)
