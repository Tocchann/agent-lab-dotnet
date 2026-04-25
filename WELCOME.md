# 🎮 Welcome to Soc Ops - Social Bingo Lab!

Your development environment is **ready to go!** 🚀

---

## ✅ Environment Setup Complete

Your local development environment has been successfully configured:

- ✅ **.NET 10.0.202 SDK** installed and verified
- ✅ **Build task** tested and functional  
- ✅ **Dev server** running on `http://localhost:5166`
- ✅ **Browser preview** opened and ready

---

## 🎯 What is This Project?

**Soc Ops** is an interactive Social Bingo game designed to help you practice **GitHub Copilot Agent Mode** for software development. 

### Game Overview
- Find people who match the bingo questions
- Get 5 in a row (horizontally, vertically, or diagonally) to win
- Perfect icebreaker for technical mixers and community events

### Tech Stack
- **Language:** C#
- **Framework:** .NET 10 with Blazor WebAssembly
- **Architecture:** Component-based Razor components
- **Services:** Game logic, state management, and bingo calculations

---

## 🚀 Quick Start

### 1. **Explore the Live App**
The development server is running! Open your browser to see the game in action:
- **URL:** http://localhost:5166
- **Play** the bingo game to understand how it works

### 2. **Review the Project Structure**
```
SocOps/
├── Components/          # Razor UI components
│   ├── BingoBoard
│   ├── GameScreen
│   └── StartScreen
├── Services/            # Business logic
│   ├── BingoGameService
│   └── BingoLogicService
├── Models/              # Data structures
├── Data/                # Questions and content
└── Pages/               # Page routes
```

### 3. **Review the Code**
- **Home.razor** - Main game entry point
- **BingoGameService.cs** - Core game state management
- **Questions.cs** - Game questions data

---

## 📚 Workshop Guide

This project is a structured learning experience with 4 parts. Access the guides offline in the `workshop/` folder:

| Part | Title | Duration | Topics |
|------|-------|----------|--------|
| **[01-setup.md](workshop/01-setup.md)** | Setup & Context Engineering | 15 min | Project setup, teaching AI about your codebase |
| **[02-design.md](workshop/02-design.md)** | Design-First Frontend | 15 min | Redesign UI with creative themes using GitHub Copilot |
| **[03-quiz-master.md](workshop/03-quiz-master.md)** | Custom Quiz Master | 10 min | Create custom quiz themes with AI assistance |
| **[04-multi-agent.md](workshop/04-multi-agent.md)** | Multi-Agent Development | 20 min | Build features with TDD and design agents |

---

## 🎓 GitHub Copilot Agent Mode Features

You'll learn to use:

1. **Context Engineering** - Teach AI about your codebase with custom instructions
2. **Background Agents** - Run long-lived AI workers in the background
3. **Cloud Agents** - Offload complex tasks to cloud-powered AI
4. **Design-First Development** - Let AI iterate on UI while you guide vision
5. **Test-Driven Development** - Use TDD agents for reliable feature development

---

## 💡 Important Files

| File/Folder | Purpose |
|-------------|---------|
| [SocOps/Program.cs](SocOps/Program.cs) | App configuration and dependency injection |
| [SocOps/Components/](SocOps/Components/) | Reusable UI components |
| [SocOps/Services/](SocOps/Services/) | Business logic and game services |
| [SocOps/Data/Questions.cs](SocOps/Data/Questions.cs) | Customizable game questions |
| [workshop/](workshop/) | Complete learning materials |

---

## 🛠️ Useful Commands

```bash
# Build the project
dotnet build SocOps/SocOps.csproj

# Run development server
dotnet run --project SocOps/SocOps.csproj

# The server runs on: http://localhost:5166
```

---

## 📖 Next Steps

### Option A: Jump Into Workshop
1. Open [01-setup.md](workshop/01-setup.md)
2. Follow the Context Engineering guide
3. Progress through each workshop part

### Option B: Play First, Learn Later
1. Visit http://localhost:5166 and play the game
2. Explore the codebase to understand how it works
3. Start with [02-design.md](workshop/02-design.md) to modify the UI

### Option C: Hands-On Learning
1. Open GitHub Copilot Chat in VS Code
2. Ask it to explain how [SocOps/Services/BingoGameService.cs](SocOps/Services/BingoGameService.cs) works
3. Suggest improvements or features
4. Use Agent Mode to implement them

---

## 🔗 Resources

- 🎮 **Play Online:** https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/
- 📚 **Official Lab Guide:** https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/docs/
- 🛠️ **.NET 10 Documentation:** https://learn.microsoft.com/dotnet/
- 🤖 **GitHub Copilot Docs:** https://docs.github.com/en/copilot

---

## 🎯 Learning Objectives

By the end of this workshop, you'll be able to:

✨ Teach GitHub Copilot about complex codebases  
✨ Use AI agents for background processing  
✨ Design UIs iteratively with AI assistance  
✨ Build features test-first with AI support  
✨ Understand multi-agent workflows  

---

## ❓ Troubleshooting

**Server won't start?**
- Verify .NET 10 SDK: `dotnet --version`
- Kill existing process: `lsof -i :5166` then `kill -9 <PID>`
- Rebuild: `dotnet build SocOps/SocOps.csproj`

**Browser shows blank page?**
- Wait 10-15 seconds for Blazor to initialize
- Check browser console (F12) for errors
- Refresh the page (Ctrl+R or Cmd+R)

**Build fails?**
- Clean: `dotnet clean SocOps/SocOps.csproj`
- Restore: `dotnet restore SocOps/SocOps.csproj`
- Rebuild: `dotnet build SocOps/SocOps.csproj`

---

## 🎉 You're All Set!

Your environment is ready. The development server is running, and you're ready to start learning with GitHub Copilot Agent Mode.

**Happy coding!** 🚀

---

*Last Setup: April 25, 2026 | .NET 10.0.202 | SocOps Ready*
