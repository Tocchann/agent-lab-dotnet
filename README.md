🌐 [Português (BR)](README.pt_BR.md) | [Español](README.es.md)

# 🎯 Soc Ops — Social Bingo

> **Break the ice, make connections, win at networking!**

Soc Ops is an interactive social bingo game designed for in-person mixers, team events, and conferences. Find people who match the prompts, mark your card, and race to get 5 in a row!

<p align="center">
  <img src="https://github.com/user-attachments/assets/2c6d0c33-72ec-47e8-b6bc-20837e7d830b" alt="Start Screen" width="300" />
  <img src="https://github.com/user-attachments/assets/4785afd4-c22a-4b1c-9b78-64d426c599e9" alt="Game Board" width="300" />
</p>

<p align="center">
  🎮 <strong><a href="https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/">Play the Game</a></strong> &nbsp;•&nbsp; 📚 <strong><a href="https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/docs/">View Lab Guide</a></strong>
</p>

---

## ✨ Features

- 🎲 **Randomized boards** — Every player gets a unique arrangement
- 💾 **Auto-save progress** — Pick up where you left off
- 🏆 **Bingo detection** — Automatic win detection for rows, columns, and diagonals
- 🎉 **Celebration modal** — Confetti-worthy victory screen
- 📱 **Mobile-first** — Works great on phones at events

---

## 📚 Lab Guide

This repo is the starting point for a hands-on workshop building with GitHub Copilot agents in VS Code.

| Part | Title |
|------|-------|
| [**00**](https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/docs/step.html?step=00-overview) | Overview & Checklist |
| [**01**](https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/docs/step.html?step=01-setup) | Setup & Context Engineering |
| [**02**](https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/docs/step.html?step=02-design) | Design-First Frontend |
| [**03**](https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/docs/step.html?step=03-quiz-master) | Custom Quiz Master |
| [**04**](https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/docs/step.html?step=04-multi-agent) | Multi-Agent Development |

> 📝 Lab guides are also available in the [`workshop/`](workshop/) folder for offline reading.

---

## 🚀 Quick Start

### Prerequisites
- [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) or higher

### Run Locally
```bash
cd SocOps
dotnet run
# Open http://localhost:5166
```

### Build
```bash
cd SocOps
dotnet build
```

### Open in GitHub Codespaces

After creating your own repo from this template:

1. Open your repo on GitHub
2. Click **Code** → **Codespaces** → **Create codespace on main**
3. Wait for the devcontainer to finish setup
4. From the repository root, run:
   ```bash
   cd SocOps
   dotnet run
   ```

---

## 🎨 Customize Your Game

### Change Questions
Edit `SocOps/Data/Questions.cs` to add your own icebreaker prompts:
```csharp
public static readonly List<string> QuestionsList = new()
{
    "has a pet",
    "speaks more than 2 languages",
    "your custom question here",
    // ... 24+ questions for a full board
};
```

---

## 🛠️ Tech Stack

- **Framework**: Blazor WebAssembly (.NET 10)
- **Styling**: Custom CSS utilities (Tailwind-inspired)
- **State**: Scoped services with localStorage persistence
- **Deployment**: GitHub Pages via Actions

## 📁 Project Structure

```
SocOps/
├── Components/     # BingoBoard, BingoSquare, Modals
├── Models/         # Game state & data models
├── Services/       # Game logic & state management
├── Data/           # Question bank
└── wwwroot/        # Static assets
```

## 🚢 Deployment

Automatically deploys to GitHub Pages on push to `main`:
- Your game: `https://{username}.github.io/{repo-name}`

## 📝 License

MIT — use it for your next event!
