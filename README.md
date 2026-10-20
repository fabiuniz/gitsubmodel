# 📦 Guia Didático: Gerenciamento de Projetos com Submódulos Git

Este documento explica como gerenciar dependências externas isoladas utilizando **Submódulos Git** e como automatizar o processo.

---

## 🧐 O que é um Submódulo Git?

Um submódulo permite que você mantenha um repositório Git dentro de outro repositório Git como uma subpasta. Isso é extremamente útil quando:
- Você deseja reutilizar código em múltiplos projetos.
- Quer manter equipes ou históricos de commits separados, mas centralizar a execução.

---

## 🛠️ Guia Passo a Passo

### Passo 1: Clonar o projeto principal junto com os submódulos
Ao clonar o repositório principal (`gitsubmodel`) pela primeira vez, você deve usar a flag `--recurse-submodules` para garantir que os submódulos venham juntos:

```bash
git clone --recurse-submodules https://github.com/fabiuniz/gitsubmodel.git
```

> **Caso já tenha clonado sem a flag**, execute o comando abaixo para baixar os submódulos:
> ```bash
> git submodule update --init --recursive
> ```

---

### Passo 2: Adicionar um novo Submódulo
Para adicionar o repositório `game_javascript` como um submódulo dentro da pasta `games/` do projeto principal, utilize o comando:

```bash
git submodule add https://github.com/fabiuniz/game_javascript.git games/game_javascript
```

---

### Passo 3: Salvar as alterações
Após configurar os submódulos, registre as mudanças no Git do projeto principal:

```bash
git add .
git commit -m "📦 Adiciona game_javascript como submodule em games/"
git push
```

---

### Passo 4: Como remover um Submódulo
Se precisar remover completamente um submódulo do projeto, execute os comandos abaixo:

1. **Desvincular e remover a pasta do submódulo:**
   ```bash
      git push --set-upstream origin main
      git rm -f games/game_javascript
   ```

2. **Limpar o cache do Git:**
   ```bash
      rm -rf .git/modules/games/game_javascript
   ```

3. **Registrar a remoção:**
   ```bash
      git add .
      git commit -m "🗑️ Remove submódulo do projeto"
   ```