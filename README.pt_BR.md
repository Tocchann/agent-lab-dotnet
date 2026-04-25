<!-- l10n-sync: source-file="README.md" -->
# 🎯 Soc Ops — Social Bingo

> **Quebre o gelo, faça conexões, vença no networking!**

Soc Ops é um jogo interativo de Social Bingo projetado para encontros presenciais, eventos de equipe e conferências. Encontre pessoas que correspondam às perguntas, marque seu cartão e corra para conseguir 5 em fila!

🎮 **[Jogar](https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/)** • 📚 **[Ver Guia do Lab](https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/docs/)**

<p align="center">
  <img src="https://github.com/user-attachments/assets/2c6d0c33-72ec-47e8-b6bc-20837e7d830b" alt="Tela Inicial" width="300" />
  <img src="https://github.com/user-attachments/assets/4785afd4-c22a-4b1c-9b78-64d426c599e9" alt="Tabuleiro do Jogo" width="300" />
</p>

---

## ✨ Funcionalidades

- 🎲 **Tabuleiros aleatórios** — Cada jogador recebe uma disposição única
- 💾 **Salvamento automático** — Continue de onde parou
- 🏆 **Detecção de bingo** — Detecção automática de vitória em linhas, colunas e diagonais
- 🎉 **Modal de celebração** — Tela de vitória com confete
- 📱 **Mobile-first** — Funciona muito bem em celulares nos eventos

---

## 🚀 Início Rápido

### Pré-requisitos
- [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) ou superior

### Executar Localmente
```bash
cd SocOps
dotnet run
# Abrir http://localhost:5166
```

### Compilar
```bash
cd SocOps
dotnet build
```

### Abrir no GitHub Codespaces (opcional)

Após criar seu próprio repositório a partir deste template:

1. Abra seu repositório no GitHub
2. Clique em **Code** → **Codespaces** → **Create codespace on main**
3. Aguarde a configuração do devcontainer ser concluída
4. A partir da raiz do repositório, execute:
   ```bash
   cd SocOps
   dotnet run
   ```

---

## 🎨 Personalize Seu Jogo

### Alterar Perguntas
Edite `SocOps/Data/Questions.cs` para adicionar suas próprias perguntas:
```csharp
public static readonly List<string> QuestionsList = new()
{
    "tem um animal de estimação",
    "fala mais de 2 idiomas",
    "sua pergunta personalizada aqui",
    // ... 24+ perguntas para um tabuleiro completo
};
```

---

## 🛠️ Stack Tecnológica

- **Framework**: Blazor WebAssembly (.NET 10)
- **Estilização**: Utilitários CSS personalizados (inspirados no Tailwind)
- **Estado**: Serviços com persistência no localStorage
- **Deploy**: GitHub Pages via Actions

---

## 📁 Estrutura do Projeto

```
SocOps/
├── Components/     # BingoBoard, BingoSquare, Modais
├── Models/         # Estado do jogo e modelos de dados
├── Services/       # Lógica do jogo e gerenciamento de estado
├── Data/           # Banco de perguntas
└── wwwroot/        # Recursos estáticos
```

---

## 📚 Guia do Lab

| Parte | Título |
|-------|--------|
| [**00**](https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/docs/step.html?step=00-overview) | Visão Geral & Lista Rápida |
| [**01**](https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/docs/step.html?step=01-setup) | Configuração & Engenharia de Contexto |
| [**02**](https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/docs/step.html?step=02-design) | Frontend Design-First |
| [**03**](https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/docs/step.html?step=03-quiz-master) | Quiz Master Personalizado |
| [**04**](https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/docs/step.html?step=04-multi-agent) | Desenvolvimento Multi-Agent |

> 📝 Os guias do lab também estão disponíveis na pasta [`workshop/pt_BR/`](workshop/pt_BR/) para leitura offline.

---

## 🚢 Deploy

O deploy é feito automaticamente no GitHub Pages ao fazer push para `main`:
- Seu jogo: `https://{usuario}.github.io/{nome-repo}`

---

## 📝 Licença

MIT — use nos seus próximos eventos!
