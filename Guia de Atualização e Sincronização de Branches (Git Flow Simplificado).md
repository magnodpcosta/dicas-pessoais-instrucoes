# 🔄 Guia de Atualização e Sincronização de Branches (Git Flow Simplificado)

Este guia mostra como **manter suas branches sincronizadas com a `main`**, como **trazer atualizações**, **fazer merge ou rebase**, e como **manter um fluxo limpo** entre repositórios locais e remotos no GitHub.

---


## 📂 **1. Estrutura recomendada**

| Tipo de Branch   | Finalidade                          | Exemplo               |
|------------------|--------------------------------------|-----------------------|
| `main`           | Código de produção (estável)         | `main`                |
| `feature/...`    | Desenvolvimento de uma nova funcionalidade | `feature/sinaenco`    |
| `fix/...`        | Correção de bug                     | `fix/tabela-sinaenco` |

💡 **Dica:**
Você pode manter um padrão simples se preferir, como sempre trabalhar em uma branch chamada `sinaenco`.
Mas, ao criar novas features, o ideal é nomear cada branch conforme o contexto.

---

## 🧱 **2. Criar uma nova branch a partir da `main`**

Antes de começar qualquer ajuste, **garanta que a `main` local está atualizada**:

```bash
# Estar na main local
git checkout main

# Atualizar com a main remota
git pull origin main
```

Agora, crie sua nova branch de trabalho baseada na `main` atualizada:

```bash
git checkout -b sinaenco
```

💡 Isso cria uma cópia exata da `main` e muda o `HEAD` para a nova branch. Ou seja: agora você trabalha isoladamente, sem afetar a `main`.

---

## 🛠️ **3. Trabalhar e enviar para o GitHub**

Durante o desenvolvimento:

```bash
git add .
git commit -m "feat: ajuste na tabela sinaenco"
git push -u origin sinaenco
```

🧠 O `-u` vincula sua branch local à remota (`origin/sinaenco`), facilitando futuros `git push` e `git pull`.

---

## 🔁 **4. Trazer atualizações da `main` para sua branch**

Imagine que outros desenvolvedores já atualizaram a `main`, e você precisa sincronizar.

### 🟢 **Opção 1 — Usar Merge (mais seguro e comum em times)**

```bash
git checkout sinaenco
git fetch origin
git merge origin/main
```

📘 Isso cria um commit de merge (histórico preservado). Ideal em times grandes ou quando você quer manter a história real dos commits.

### 🟣 **Opção 2 — Usar Rebase (histórico linear e limpo)**

```bash
git checkout sinaenco
git fetch origin
git rebase origin/main
```

💡 Rebase reorganiza seus commits para que pareçam ter sido criados a partir da versão mais recente da `main`.

🧩 **Dica de ouro (como pensar):**
🔸 **Merge** = “quero unir duas histórias.”
🔸 **Rebase** = “quero fingir que comecei do ponto mais recente.”

---

## ⚔️ **5. Lidando com conflitos**

Se houver conflitos durante `merge` ou `rebase`:

1. O Git pausará o processo e mostrará os arquivos com conflito.
2. Corrija os arquivos manualmente.
3. Depois use:

```bash
git add .
git merge --continue   # se estiver em merge
# ou
git rebase --continue  # se estiver em rebase
```

---

## 🚀 **6. Enviar a atualização sincronizada**

Após o `merge` ou `rebase` bem-sucedido:

```bash
git push
```

Se você fez `rebase` e o `push` falhar, use:

```bash
git push --force-with-lease
```

⚠️ Nunca use `--force` puro — o `--force-with-lease` é mais seguro, pois evita sobrescrever commits alheios.

---

## 🧹 **7. Criar Pull Request (PR)**

Quando a branch estiver pronta:

1. Acesse o GitHub → Repositório → Aba **Pull requests** → **New Pull Request**.
2. Compare:
   - **base:** `main`
   - **compare:** `sinaenco`
3. Descreva claramente suas mudanças.
4. Aguarde aprovação e merge.

---

## 🧩 **8. Após o PR ser aprovado e integrado à `main`**

Para manter seu ambiente limpo e atualizado:

1️⃣ **Excluir branches:**

```bash
# Local
git branch -d sinaenco

# Remoto
git push origin --delete sinaenco
```

2️⃣ **Atualizar a `main`:**

```bash
git checkout main
git pull origin main
```

3️⃣ **Criar uma nova branch quando precisar:**

```bash
git checkout -b sinaenco
```

---

## 🧠 **9. Pensamento estratégico (Git Flow no dia a dia)**

| Situação                     | O que fazer                                                                 |
|------------------------------|------------------------------------------------------------------------------|
| Comecei algo novo            | Crie uma branch a partir da `main` atualizada                              |
| A `main` recebeu atualizações | Faça `merge` ou `rebase`                                                     |
| Quero enviar minhas mudanças | Faça `commit` + `push` + PR                                                  |
| PR foi aprovado              | Exclua branch local e remota e atualize a `main`                            |
| Preciso continuar o trabalho | Crie uma nova branch a partir da `main` atualizada                         |

---

## 🪄 **10. Dicas rápidas**

✅ Faça commits pequenos e descritivos.
✅ Evite trabalhar diretamente na `main`.
✅ Prefira `merge` se estiver colaborando com outras pessoas.
✅ Use `rebase` se quiser uma linha de commits limpa (sem merges).
✅ Sempre atualize sua `main` local antes de criar novas branches.
✅ Após o merge no PR, delete a branch antiga — não recicle branches.

---

## 💬 **11. Resumo visual**

```
(main atualizado)───●─────●─────●───────────────
                      \
                       \───●──●──●─── (sinaenco)
                             ↑
                             |__ Rebase → finge que partiu da main
                             |__ Merge → une as histórias
```

---

## 🧩 **12. Comandos essenciais do fluxo**

| Ação                                      | Comando                                                                 |
|-------------------------------------------|-------------------------------------------------------------------------|
| Atualizar `main`                          | `git checkout main && git pull origin main`                           |
| Criar nova branch                         | `git checkout -b nome-da-branch`                                        |
| Fazer commit                              | `git add . && git commit -m "mensagem"`                                 |
| Enviar branch                             | `git push -u origin nome-da-branch`                                    |
| Trazer updates da `main` (merge)          | `git fetch origin && git merge origin/main`                             |
| Trazer updates da `main` (rebase)         | `git fetch origin && git rebase origin/main`                            |
| Excluir branch local                      | `git branch -d nome-da-branch`                                           |
| Excluir branch remota                     | `git push origin --delete nome-da-branch`                               |
| Atualizar após PR                         | `git checkout main && git pull origin main`                            |

---

## ⚡ **13. Cheat Sheet (resumo rápido)**

| Ação                                      | Comando                                                                 |
|-------------------------------------------|-------------------------------------------------------------------------|
| Atualizar `main`                          | `git checkout main && git pull origin main`                           |
| Criar nova branch                         | `git checkout -b nome-da-branch`                                        |
| Fazer commit                              | `git add . && git commit -m "mensagem"`                                 |
| Enviar branch                             | `git push -u origin nome-da-branch`                                    |
| Trazer updates da `main` (merge)          | `git fetch origin && git merge origin/main`                             |
| Trazer updates da `main` (rebase)         | `git fetch origin && git rebase origin/main`                            |
| Excluir branch local                      | `git branch -d nome-da-branch`                                           |
| Excluir branch remota                     | `git push origin --delete nome-da-branch`                               |
| Atualizar após PR                         | `git checkout main && git pull origin main`                            |

---

## 🧩 **Conclusão**

Seguindo este guia:
- Sua `main` sempre refletirá o código de produção.
- Cada branch representará uma entrega isolada e controlada.
- O histórico ficará limpo, compreensível e seguro.

🧠 **Resumo mental final:**
🔸 **Merge** = une histórias.
🔸 **Rebase** = reescreve o passado pra parecer mais bonito.

📘 **Autor:** Guia prático baseado no fluxo Git usado em equipes profissionais e revisado para simplicidade e segurança.
💡 Ideal para quem trabalha com Visual Studio + GitHub no dia a dia.
