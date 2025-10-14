## ✨ **Exemplo Completo (Resumo Rápido)**
```bash
# Iniciar projeto
git init
git add .
git commit -m "feat: primeira versão do projeto"

# Conectar e enviar para GitHub
git remote add origin https://github.com/SEU_USUARIO/NOME_DO_REPOSITORIO.git
git branch -M main
git push -u origin main
```

# 🚀 Guia Completo: Criar e Subir um Projeto para o GitHub
Este guia ensina como **criar um repositório local**, **conectar ao GitHub** e **enviar seu projeto**, além de resolver erros comuns como `fetch first`.

---

## 📌 **1. Inicializar o Repositório Local**
No terminal, dentro da pasta do seu projeto:
```bash
git init
git add .
git commit -m "feat: primeira versão do projeto"
```
💡 **Dica:** `git init` cria a pasta `.git`, que permite o controle de versões.

---

## 🌍 **2. Criar o Repositório no GitHub**
1. Acesse [github.com/new](https://github.com/new).
2. Dê um nome profissional (exemplo: `firstweb-api-app`).
3. **Não marque** as opções de criar README, `.gitignore` ou LICENSE (para evitar conflitos).
4. Clique em **Create repository**.

---

## 🔗 **3. Conectar o Repositório Remoto**
Copie a URL gerada pelo GitHub e execute:
```bash
git remote add origin https://github.com/SEU_USUARIO/NOME_DO_REPOSITORIO.git
git branch -M main
git push -u origin main
```
🧠 **Dica:** `-u` define o branch remoto padrão, simplificando futuros `git push` e `git pull`.

---

## 🧱 **4. Criar um Arquivo `.gitignore` (Essencial)**
Crie um arquivo `.gitignore` na raiz do projeto com o seguinte conteúdo (exemplo para projetos .NET):
```shell
## Build results
bin/
obj/
out/
Debug/
Release/

## User-specific files
*.user
*.suo
*.userosscache
*.sln.docstates

## Visual Studio Code
.vscode/
.history/
*.code-workspace

## Visual Studio
.vs/
*.ncb
*.opendb
*.VC.db
*.VC.VC.opendb

## Environment files
.env
*.log

## OS generated files
.DS_Store
Thumbs.db

## NuGet
*.nupkg
packages/

## Temporary files
~\$*
*.tmp
*.temp

```

Salve e envie:
```bash
git add .gitignore
git commit -m "chore: adicionar .gitignore padrão"
git push
```

---

## 🔁 **5. Atualizar o Repositório (Rotina Diária)**
Sempre que fizer alterações:
```bash
git add .
git commit -m "feat: descrição da mudança"
git push
```

---

## ⚠️ **6. Erro Comum: “fetch first”**
### ❌ Mensagem de erro:
```plaintext
! [rejected] main -> main (fetch first)
error: failed to push some refs to 'https://github.com/SEU_USUARIO/REPO.git'
hint: Updates were rejected because the remote contains work that you do not have locally.
```

### ✅ **Soluções:**
#### **Opção 1** — Mesclar com o que está no GitHub (recomendado se há arquivos lá):
```bash
git pull origin main --rebase
git push -u origin main
```

#### **Opção 2** — Sobrescrever tudo com o código local (use com cautela!):
```bash
git push -u origin main --force
```
💡 **Dica:** Esse erro geralmente ocorre se você deixou marcada a opção de criar README ou `.gitignore` ao criar o repositório no GitHub.

---

## 🧠 **7. Comandos Úteis**

| Comando | Função |
|---------|--------|
| `git status` | Mostra o status dos arquivos (alterados, adicionados, etc.) |
| `git remote -v` | Lista os repositórios remotos configurados |
| `git branch` | Mostra o branch atual |
| `git log` | Exibe o histórico de commits |
| `git remote remove origin` | Remove o remoto atual (para reconfigurar) |
| `git remote add origin <URL>` | Adiciona o repositório remoto novamente |

---

## 🧹 **8. Recomendações Finais**
✅ Sempre faça commits com mensagens claras (use `feat`, `fix`, `refactor`, `chore`, etc.).
✅ Nunca edite diretamente no GitHub se estiver trabalhando localmente.
✅ Use o `.gitignore` para manter seu repositório limpo.
✅ Evite o `--force` a menos que tenha certeza do que está fazendo.

---

🧩 **Pronto!** Seu projeto agora está versionado e publicado no GitHub com segurança. 🚀
