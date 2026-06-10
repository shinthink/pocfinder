# PoCFinder

![Version](https://img.shields.io/badge/version-2.9-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Platform](https://img.shields.io/badge/platform-Linux%20%7C%20macOS-lightgrey)

**PoCFinder** is a fast and interactive terminal tool to search for Proof of Concept (PoC) repositories on GitHub.

It provides a clean `fzf`-based interface with rich preview, automatic caching, and quick actions to open or clone repositories directly from the terminal.

---

## ✨ Features

- 🔍 Search PoCs by keyword or CVE ID
- ⚡ **Automatic caching** system (results saved for 10 minutes)
- 🖥️ Rich live preview panel (Description, Language, Forks, Open Issues, README Preview)
- 🎨 Modern terminal UI inspired by popular security tools
- 🚀 Built on top of GitHub CLI (`gh`) for fast and reliable results
- 📋 Quick actions: Open in browser or clone repository

---

## 📦 Requirements

### Required Tools

| Tool | Purpose                              | Minimum Version     | Installation |
|------|--------------------------------------|---------------------|--------------|
| `gh` | GitHub Command Line Interface        | **2.20.0 or higher** | See below    |
| `fzf`| Interactive fuzzy finder             | Any                 | See below    |
| `jq` | JSON processor                       | Any                 | See below    |

> **Important**: `gh` version **2.20.0 or newer** is required because PoCFinder uses the `gh search repos` command.

### How to Install Dependencies

#### Ubuntu / Debian (Recommended)

```bash
# Add GitHub CLI official repository
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null

sudo apt update
sudo apt install gh fzf jq -y
```

#### Fedora / Rocky Linux / AlmaLinux

```bash
sudo dnf install gh fzf jq -y
```

#### Arch Linux / Manjaro

```bash
sudo pacman -S github-cli fzf jq
```

#### macOS (using Homebrew)

```bash
brew install gh fzf jq
```

### GitHub Personal Access Token

You need to set a GitHub Personal Access Token:

```bash
export GH_TOKEN=ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

Add it to your shell configuration file:

```bash
# For Bash
echo 'export GH_TOKEN=ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxx' >> ~/.bashrc

# For Zsh
echo 'export GH_TOKEN=ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxx' >> ~/.zshrc
```

---

## 🚀 Installation

```bash
git clone https://github.com/shinthink/pocfinder.git
cd pocfinder
chmod +x pocfinder
./pocfinder
```

---

## 📖 Usage

```bash
# Interactive mode
./pocfinder

# Search directly
./pocfinder CVE-2024
./pocfinder sqlmap
./pocfinder "remote code execution"

# Refresh cache
./pocfinder refresh
./pocfinder refresh CVE-2025
```

### How to Use

1. Run `./pocfinder`
2. Enter a keyword or CVE ID
3. Use arrow keys to browse results
4. View detailed information and README preview on the **right panel**
5. Press `Enter` to select a repository
6. Choose an action (`[1]` Open in Browser, `[2]` Clone, or `[q]` Exit)

---

## 🗂️ Project Structure

```
pocfinder/
├── pocfinder
├── README.md
├── LICENSE
└── .gitattributes
```

---

## ⚙️ How It Works

- Uses `gh search repos` to find relevant repositories
- Results are cached locally in `~/.pocfinder/`
- Uses `fzf` for fast interactive selection
- Displays repository details and a short README preview

---

## 📌 Notes

- `gh` version **2.20.0 or higher** is required
- A valid `GH_TOKEN` is needed for the best experience
- Use `./pocfinder refresh` to force update the cache

---

## 🤝 Contributing

Contributions are welcome!

---

## 📄 License

This project is licensed under the MIT License.

---

## 👤 Author

**shinthink**

---

> Built to help security researchers and bug bounty hunters find relevant PoCs more efficiently.
