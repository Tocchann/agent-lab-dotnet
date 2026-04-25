---
name: Soc Ops Agent Lab
description: "Workspace instructions for the Soc Ops GitHub Copilot Agent Lab project. Covers C# / .NET 10 / Blazor WebAssembly development, project structure, build/run commands, and code conventions."
---

# Soc Ops - GitHub Copilot Agent Lab

**Soc Ops** is an educational workshop project demonstrating GitHub Copilot Agent Mode capabilities using a Social Bingo game for in-person mixers.

- 🎮 **App**: Interactive bingo game where players find people matching questions and get 5 in a row to win
- 📚 **Workshop**: 4-part guided lab teaching AI-assisted development patterns
- 🤖 **Lab Focus**: Context engineering, agentic primitives, design-first development, TDD workflows

---

## Project Structure

```
SocOps/                          # Main Blazor WebAssembly app (.NET 10)
├── Program.cs                   # App config, dependency injection, services
├── App.razor                     # Root component
├── _Imports.razor               # Global usings
├── SocOps.csproj                # Project manifest
├── Components/                  # Reusable Razor components
│   ├── BingoBoard.razor         # 5x5 grid layout
│   ├── BingoSquare.razor        # Individual cell with toggle state
│   ├── GameScreen.razor         # Main gameplay UI
│   ├── StartScreen.razor        # Welcome/intro
│   └── BingoModal.razor         # Victory/bingo notification
├── Pages/                       # Route-based pages (@page)
│   ├── Home.razor               # Main game entry (/)
│   └── [Other demo pages]
├── Services/                    # Business logic & state
│   ├── BingoGameService.cs      # Main game orchestrator, persistence
│   └── BingoLogicService.cs     # Pure bingo logic (board gen, win checks)
├── Models/                      # Data structures
│   ├── GameState.cs             # Enum: Start, Playing, Bingo
│   ├── BingoSquareData.cs       # Cell data (id, text, marked)
│   └── BingoLine.cs             # Winning line metadata
├── Data/                        # Static content
│   └── Questions.cs             # Customizable bingo prompts
├── Layout/                      # Shared layouts
│   ├── MainLayout.razor
│   └── NavMenu.razor
└── wwwroot/                     # Static assets
    └── css/
        └── app.css              # Custom utility classes (flex, grid, colors, etc)

workshop/                        # Guided learning materials (offline)
├── 00-overview.md               # Goals and checklist
├── 01-setup.md                  # Dev environment + context engineering intro
├── 02-design.md                 # Design-first UI redesign with Copilot
├── 03-quiz-master.md            # Custom quiz themes with agents
└── 04-multi-agent.md            # TDD workflows + multi-stage development

.github/                         # Copilot customizations
├── copilot-instructions.md      # This file
├── instructions/                # File-scoped instructions
│   ├── css-utilities.instructions.md       # Styling practices & utility reference
│   └── frontend-design.instructions.md    # Design principles, avoiding "AI slop"
├── agents/                      # Specialized workflow agents
│   ├── tdd.agent.md             # Orchestrates full TDD cycle
│   ├── tdd-red.agent.md         # Writes failing tests
│   ├── tdd-green.agent.md       # Writes minimal implementation
│   ├── tdd-refactor.agent.md    # Improves code quality
│   ├── quiz-master.agent.md     # Curates icebreaker questions
│   ├── ui-review.agent.md       # Reviews component design
│   └── pixel-jam.agent.md       # Creative UI design challenges
└── prompts/                     # Focused single-task prompts
    ├── setup.prompt.md          # Initial dev environment setup
    └── cloud-explore.prompt.md  # Cloud hosting exploration
```

---

## Build & Run Commands

### Development

```bash
# From repo root, navigate to app directory
cd SocOps

# Restore dependencies (includes NuGet packages)
dotnet restore

# Build the project
dotnet build

# Run with hot reload (dev server on http://localhost:5166)
dotnet run

# Access the app
# → http://localhost:5166
```

### Production

```bash
# Publish as static WebAssembly (GitHub Pages deployment)
dotnet publish -c Release

# Output: SocOps/bin/Release/net10.0/publish/wwwroot/
```

---

## Code Conventions

### C# / .NET Standards

- **File-scoped namespaces**: `namespace SocOps.Services;` (no braces)
- **Nullable reference types**: Enabled (`<Nullable>enable</Nullable>`)
- **Implicit usings**: Enabled (`<ImplicitUsings>enable</ImplicitUsings>`)
- **Naming**: PascalCase for classes/methods, camelCase for private fields, `_prefixForFields`
- **Constants**: `private const string STORAGE_KEY` (UPPER_SNAKE_CASE)
- **Services**: Injected via constructor, cached in private read-only fields

### Razor Components

- **File naming**: PascalCase (e.g., `BingoBoard.razor`)
- **Parameters**: Public properties with `[Parameter]` attribute
- **Events**: EventCallback pattern (e.g., `[Parameter] EventCallback<int> OnSquareClick`)
- **Styling**: CSS utility classes from `wwwroot/css/app.css` (no scoped CSS by default)
- **State management**: Lifted to parent (single source of truth in BingoGameService)
- **Child → Parent**: Callbacks; Parent → Child: Parameters

### Styling (CSS Utilities)

Use custom utility classes defined in `wwwroot/css/app.css`:

```html
<!-- Flex layout -->
<div class="flex items-center justify-center gap-2">

<!-- Grid (5 columns for bingo) -->
<div class="grid grid-cols-5 gap-1 w-full aspect-square">

<!-- Spacing: margin bottom -->
<div class="mb-2">

<!-- Colors: accent (blue), marked (green), text grays -->
<div class="bg-accent text-white">
```

See [.github/instructions/css-utilities.instructions.md](.github/instructions/css-utilities.instructions.md) for complete reference.

### File Organization

- One component per `.razor` file (except `_Imports.razor`)
- One service per `.cs` file (unless tightly coupled)
- Models in `Models/` folder
- Keep components pure (no side effects in render)
- Service methods: Clear, single responsibility

---

## Workflow Patterns

### 1. Component Development (Design-First)

**Use prompt**: `/setup` or ask directly in Chat
- AI generates creative, distinctive designs (see [frontend-design.instructions.md](.github/instructions/frontend-design.instructions.md))
- Avoid generic layouts; commit to a cohesive aesthetic
- Use CSS variables for theme consistency
- Add animations for high-impact moments (page load, wins)

### 2. Custom Quiz Themes

**Use agent**: Press `@` → Select `Quiz Master`
- Provide theme (e.g., "Tech Culture", "Startup Life", "Open Source")
- Agent curates balanced, inclusive icebreaker questions
- Update `Data/Questions.cs` with results
- Test in running app (hot reload)

### 3. Feature Development (TDD)

**Use agent**: Press `@` → Select `TDD Supervisor`
- Describe feature/bug in natural language
- Agent orchestrates:
  1. Write failing tests (TDD Red)
  2. Write minimal implementation (TDD Green)
  3. Run tests to verify
  4. Optionally refactor (TDD Refactor)
- Output ready for commit

### 4. UI Polish & Review

**Use agent**: Press `@` → Select `UI Review`
- Submit component code or screenshot
- Agent reviews for accessibility, responsiveness, design coherence
- Suggests pixel-level improvements

---

## Teaching Copilot About This Project

### Context Engineering (Setup Part 1)

1. Share codebase overview:
   ```
   This is a Blazor WebAssembly app using .NET 10, custom CSS utilities, 
   and a service-based architecture for game logic. The main service is 
   BingoGameService; UI components are in Components/ folder.
   ```

2. Link key files in chat:
   - [SocOps/Program.cs](SocOps/Program.cs) — DI setup
   - [SocOps/Services/BingoGameService.cs](SocOps/Services/BingoGameService.cs) — Main orchestrator
   - [SocOps/Components/](SocOps/Components/) — Example components
   - [SocOps/Data/Questions.cs](SocOps/Data/Questions.cs) — Data to customize

3. Mention constraints:
   - "Use file-scoped namespaces"
   - "Keep components pure; lift state to services"
   - "Use CSS utility classes from app.css, not inline styles"

### Using Specialized Agents

Each agent is pre-trained for a specific task:

| Agent | When to Use | Example |
|-------|-------------|---------|
| **TDD Supervisor** | Build features test-first | "Add a daily challenge mode with reset at midnight" |
| **Quiz Master** | Customize questions | "Create questions for a gaming community event" |
| **UI Review** | Polish designs | "Review this component for accessibility" |
| **Frontend Design** | Redesign with flair | "Redesign the bingo board with a cyberpunk aesthetic" |
| **Pixel Jam** | Creative UI challenges | "Make a brutalist design for the start screen" |

---

## Workshop Learning Path

This codebase is designed as a guided 4-part workshop:

| Part | File | Duration | What You'll Learn |
|------|------|----------|-------------------|
| **00** | [00-overview.md](workshop/00-overview.md) | 5 min | Lab goals, prerequisites, checklist |
| **01** | [01-setup.md](workshop/01-setup.md) | 15 min | Dev environment, context engineering, teaching AI about the project |
| **02** | [02-design.md](workshop/02-design.md) | 15 min | Design-first development, creative UI, GitHub Copilot design iteration |
| **03** | [03-quiz-master.md](workshop/03-quiz-master.md) | 10 min | Custom quiz themes with agents, data generation |
| **04** | [04-multi-agent.md](workshop/04-multi-agent.md) | 20 min | TDD workflows, multi-agent orchestration, feature development |

Each section includes hands-on tasks and builds on prior knowledge.

---

## Common Development Tasks

### Add Custom Bingo Questions

1. Open [SocOps/Data/Questions.cs](SocOps/Data/Questions.cs)
2. Edit or replace the list of `BingoPrompt` objects
3. Save; app hot-reloads on next game start

### Create a New Component

1. Add `.razor` file to `SocOps/Components/`
2. Use existing components as templates (BingoSquare, GameScreen)
3. Define `[Parameter]` properties for inputs
4. Define `EventCallback<T>` properties for outputs
5. Use CSS utility classes for styling
6. Reference in parent via `<ComponentName ... />`

### Modify Game Logic

1. Edit [SocOps/Services/BingoLogicService.cs](SocOps/Services/BingoLogicService.cs) for pure functions (generation, checking)
2. Edit [SocOps/Services/BingoGameService.cs](SocOps/Services/BingoGameService.cs) for state management or persistence
3. Implement in components via event callbacks
4. Test with running app (Ctrl+F5 to hard-refresh)

### Style Changes

1. Edit [SocOps/wwwroot/css/app.css](SocOps/wwwroot/css/app.css) or component stylesheet
2. Hot reload works automatically
3. See [css-utilities.instructions.md](.github/instructions/css-utilities.instructions.md) for available utilities

---

## Pre-built Custom Agents & Why They Exist

### TDD Agents (`tdd*.agent.md`)

The TDD suite demonstrates multi-stage agent orchestration:
- **TDD Supervisor** (parent) → orchestrates the full cycle
- **TDD Red** → writes tests first (fail by design)
- **TDD Green** → minimalist implementation to pass tests
- **TDD Refactor** → improves design without changing behavior

**Use case**: Teaching test-driven development with AI; ensures tests exist before code.

### Quiz Master (`quiz-master.agent.md`)

Curates icebreaker questions for different themes:
- Balanced difficulty (easy, medium, bold)
- Category variety (personal, work, fun/random)
- Inclusive & safe topics
- Conversation-starter framing

**Use case**: Customizing the game for events, communities, or audiences.

### UI Review (`ui-review.agent.md`)

Provides structured design feedback:
- Accessibility (WCAG, contrast, semantics)
- Responsiveness (mobile-first, scaling)
- Coherence (theme, spacing, typography)
- Suggestions for per-pixel improvements

**Use case**: Polishing components before merge; learning design best practices.

### Frontend Design & Pixel Jam

See [.github/instructions/frontend-design.instructions.md](.github/instructions/frontend-design.instructions.md).

These instructions teach Copilot to avoid generic AI aesthetics and produce distinctive, thoughtful designs by:
- Committing to cohesive aesthetics (not scattered styles)
- Choosing distinctive typography and color
- Orchestrating animations for impact
- Matching complexity to vision (elaborate code for maximalist, precise for minimalist)

---

## GitHub Pages Deployment

The app deploys automatically to GitHub Pages on push to `main`:

1. **Prerequisite**: Enable GitHub Pages in Settings → Pages → Source: GitHub Actions
2. **Workflow**: [.github/workflows/](.github/workflows/) contains deployment automation
3. **Result**: App accessible at `https://{username}.github.io/{repo-name}/`

---

## Troubleshooting & Tips

### Server won't start

```bash
# 1. Verify .NET SDK (should be 10.0+)
dotnet --version

# 2. Kill any lingering process on port 5166
lsof -i :5166      # Find PID
kill -9 <PID>      # Kill it

# 3. Clean and rebuild
dotnet clean SocOps/
dotnet build SocOps/
```

### Blazor WebAssembly slow to load

- Wait 10–15 seconds for runtime to initialize
- Check browser console (F12) for errors
- Try Ctrl+F5 (hard refresh) to bypass cache

### Hot reload not working

- Ensure you're running `dotnet run` (not `dotnet build`)
- Save the file; changes usually reflect within 1–2 seconds
- If stuck, stop the server and run again

### Build fails with NuGet errors

```bash
dotnet clean SocOps/SocOps.csproj
dotnet restore SocOps/SocOps.csproj
dotnet build SocOps/SocOps.csproj
```

---

## Resources & Links

- 🎮 **Live Demo**: https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/
- 📚 **Lab Guide (Online)**: https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/docs/
- 🛠️ **.NET 10 Docs**: https://learn.microsoft.com/en-us/dotnet/
- 🤖 **GitHub Copilot Docs**: https://docs.github.com/en/copilot
- 🔗 **Blazor Docs**: https://learn.microsoft.com/en-us/aspnet/core/blazor
- 📝 **Workshop Materials**: [workshop/](workshop/) folder (offline-readable)

---

## Questions? Next Steps

1. **First time?** Start with [workshop/01-setup.md](workshop/01-setup.md)
2. **Want to design?** Use `/setup` or ask Copilot directly; read [frontend-design.instructions.md](.github/instructions/frontend-design.instructions.md)
3. **Ready for TDD?** Press `@` and select the `TDD Supervisor` agent
4. **Customizing questions?** Use the `@Quiz Master` agent

---

**Last Updated**: April 2026 | .NET 10 | Blazor WebAssembly
