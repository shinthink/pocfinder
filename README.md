# PoCFinder

![Version](https://img.shields.io/badge/version-2.9-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Platform](https://img.shields.io/badge/platform-Linux%20%7C%20macOS-lightgrey)

**PoCFinder** is a fast and interactive terminal tool to search for Proof of Concept (PoC) repositories on GitHub.

It provides a clean `fzf`-based interface with rich preview, automatic caching, and quick actions to open or clone repositories directly from the terminal.

---

## ✨ Features

- 🔍 Search PoCs by keyword or CVE ID
- ⚡ **Automatic caching** system (results are saved for 10 minutes)
- 🖥️ Rich live preview panel (Description, Language, Forks, Open Issues, README Preview)
- 🎨 Modern terminal UI inspired by popular security tools
- 🚀 Built on top of GitHub CLI (`gh`) for fast and reliable results
- 📋 Quick actions to open repository in browser or clone it

---

## 📦 Requirements

Before using PoCFinder, install the following dependencies:

### Required Tools

| Tool | Purpose                          | Ubuntu / Debian          | Fedora / RHEL            | macOS (Homebrew)      |
|------|----------------------------------|--------------------------|--------------------------|-----------------------|
| `gh` | GitHub Command Line Interface    | `apt install gh`         | `dnf install gh`         | `brew install gh`     |
| `fzf`| Interactive fuzzy finder         | `apt install fzf`        | `dnf install fzf`        | `brew install fzf`    |
| `jq` | JSON processor                   | `apt install jq`         | `dnf install jq`         | `brew install jq`     |

> **Note**: `brew` (Homebrew) is popular on **macOS**. On Linux, it is recommended to use your distribution’s package manager (`apt`, `dnf`, `pacman`, etc.).

### GitHub Personal Access Token

PoCFinder requires a GitHub token to avoid rate limiting.

```bash
export GH_TOKEN=ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

**Recommended**: Add this line to your shell configuration file:

```bash
# Bash
echo 'export GH_TOKEN=ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxx' >> ~/.bashrc

# Zsh
echo 'export GH_TOKEN=ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxx' >> ~/.zshrc
```

---

## 🚀 Installation

```bash
# Clone the repository
git clone https://github.com/shinthink/pocfinder.git
cd pocfinder

# Make the script executable
chmod +x pocf

# Run PoCFinder
./pocf
```

---

## 📖 Usage

### Basic Commands

```bash
# Run in interactive mode
./pocf

# Search directly with keyword or CVE
./pocf CVE-2024
./pocf sqlmap
./pocf "remote code execution"
```

### Available Commands

| Command                        | Description                              |
|--------------------------------|------------------------------------------|
| `./pocf`                       | Run interactive mode                     |
| `./pocf <keyword>`             | Search directly                          |
| `./pocf refresh`               | Clear cache and fetch fresh data         |
| `./pocf refresh <keyword>`     | Refresh cache for specific keyword       |

### How to Use

1. Run `./pocf`
2. Enter a keyword or CVE ID
3. Use arrow keys (`↑` `↓`) to browse results
4. View detailed information and README preview on the **right panel**
5. Press `Enter` to select a result
6. Choose an action:
   - `[1]` Open in Browser
   - `[2]` Clone Repository
   - `[q]` Exit

---

## 🗂️ Project Structure

```
pocfinder/
├── pocf          # Main script
├── README.md
├── LICENSE
└── .gitattributes
```

---

## ⚙️ How It Works

- Uses `gh search repos` to find relevant repositories
- Results are cached locally in `~/.pocfinder/`
- Uses `fzf` for fast interactive selection
- Displays rich information and a short README preview without leaving the terminal

---

## 📌 Notes

- A valid `GH_TOKEN` is required for the best experience
- Cached results are valid for 10 minutes
- Use `./pocf refresh` to force update the cache

---

## 🤝 Contributing

Contributions are welcome! Feel free to open issues or submit pull requests.

---

## 📄 License

This project is licensed under the MIT License.

---

## 👤 Author

**shinthink**

---

> Built to help security researchers and bug bounty hunters find relevant PoCs more efficiently.
