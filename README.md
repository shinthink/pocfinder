# PoCFinder

![Version](https://img.shields.io/badge/version-2.9-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Platform](https://img.shields.io/badge/platform-Linux%20%7C%20macOS-lightgrey)

**PoCFinder** is a fast and interactive terminal tool to search for Proof of Concept (PoC) repositories on GitHub.

It provides a clean interface with rich preview, automatic caching, and the ability to quickly open or clone repositories.

---

## ✨ Features

- 🔍 Search PoCs using keywords or CVE IDs
- ⚡ **Automatic caching** system (10 minutes TTL)
- 🖥️ Rich live preview on the right panel (Description, Language, Forks, Open Issues, README Preview)
- 🎨 Modern terminal UI inspired by popular security tools
- 🚀 Built on top of GitHub CLI (`gh`) for fast and reliable results
- 📋 Quick actions: Open in browser or clone repository directly

---

## 📦 Requirements

Before using PoCFinder, make sure you have the following installed:

| Tool           | Purpose                        | Installation Command                  |
|----------------|--------------------------------|---------------------------------------|
| `gh`           | GitHub Command Line Interface  | `brew install gh` or `apt install gh` |
| `fzf`          | Interactive fuzzy finder       | `brew install fzf`                    |
| `jq`           | JSON processor                 | `brew install jq`                     |

You also need to set your GitHub Personal Access Token:

```bash
export GH_TOKEN=ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

> **Tip**: Add the token to your shell configuration file (`.zshrc`, `.bashrc`, etc.) so it loads automatically.

---

## 🚀 Installation

```bash
# Clone the repository
git clone https://github.com/shinthink/pocfinder.git
cd pocfinder

# Make the script executable
chmod +x pocfinder

# Run PoCFinder
./pocfinder
```

---

## 📖 Usage

### Basic Usage

```bash
# Run in interactive mode
./pocfinder

# Search directly using a keyword or CVE
./pocf CVE-2024
./pocf sqlmap
./pocf "remote code execution"
```

### Available Commands

| Command                    | Description                                      |
|---------------------------|--------------------------------------------------|
| `./pocfinder`                  | Run interactive mode                             |
| `./pocfinder <keyword>`        | Search directly with keyword or CVE              |
| `./pocfinder refresh`          | Clear cache and fetch fresh data                 |
| `./pocfinder refresh <keyword>`| Refresh cache for specific keyword               |

### How to Use (Step by Step)

1. **Run the tool**
   ```bash
   ./pocfinder
   ```

2. **Enter a keyword or CVE ID** when prompted (or pass it directly as argument).

3. **Browse results**
   - Use `↑` and `↓` arrow keys to navigate.
   - On the **right panel**, you will see:
     - Repository name and stars
     - Language, Forks, and Open Issues
     - Description
     - Updated date and URL
     - README Preview (first 20 lines)

4. **Select a repository**
   - Press `Enter` to open the detail view.

5. **Choose an action**
   - `[1]` Open in Browser
   - `[2]` Clone the repository
   - `[q]` Exit

### Example

```bash
./pocfinder CVE-2024
```

This will search for repositories related to CVE-2024 and display them with rich information on the right side.

---

## 🗂️ Project Structure

```
pocfinder/
├── pocfinder              # Main executable script
├── README.md
└── LICENSE
```

---

## ⚙️ How It Works

- Uses `gh search repos` to query GitHub repositories
- Results are cached locally in `~/.pocfinder/` directory
- Cache is valid for **10 minutes** by default
- Uses `fzf` to provide an interactive and fast selection experience
- README preview is limited to the first 20 lines for performance

---

## 📌 Notes

- The tool works best when you have a valid `GH_TOKEN` set.
- Cache helps speed up repeated searches for the same keyword.
- You can force refresh data using the `refresh` command.

---

## 🤝 Contributing

Contributions are welcome!  
Feel free to open issues or submit pull requests to improve the tool.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

## 👤 Author

**shinthink**

---

> PoCFinder was built to help security researchers and bug bounty hunters find relevant PoCs faster and more efficiently.
