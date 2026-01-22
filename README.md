# 🔧 Git Crash Course

## Vad är Git?

Git är ett versionhanteringssystem som spårar ändringar i din kod. Tänk på det som "spara-funktion på steroider" – du kan gå tillbaka till vilken version som helst.

---

## Grundläggande begrepp

| Begrepp | Förklaring |
|---------|------------|
| **Repository (repo)** | Projektmappen som Git spårar |
| **Commit** | En sparad "snapshot" av dina ändringar |
| **Branch** | En parallell version av koden |
| **Remote** | En kopia av repot på en server (t.ex. GitHub) |
| **Clone** | Ladda ner ett repo från GitHub |
| **Push** | Ladda upp dina commits till GitHub |
| **Pull** | Hämta senaste ändringar från GitHub |

---

## Komma igång

### 1. Konfigurera Git (gör en gång)

```bash
git config --global user.name "Ditt Namn"
git config --global user.email "din.email@example.com"
```

### 2. Skapa ett nytt repo

```bash
# Gå till din projektmapp
cd mitt-projekt

# Initiera Git
git init

# Lägg till alla filer
git add .

# Gör första commit
git commit -m "Initial commit"
```

### 3. Koppla till GitHub

```bash
# Skapa först ett tomt repo på GitHub, sedan:
git remote add origin https://github.com/dittnamn/repo-namn.git

# Pusha till GitHub
git push -u origin main
```

---

## Dagligt arbetsflöde

```bash
# 1. Se status (vilka filer har ändrats?)
git status

# 2. Lägg till ändringar
git add .                    # Lägg till alla ändringar
git add filnamn.py           # Lägg till specifik fil

# 3. Commita med meddelande
git commit -m "Add ETL pipeline for orders"

# 4. Pusha till GitHub
git push
```

---

## Vanliga kommandon

### Se vad som händer

```bash
git status           # Visa ändrade filer
git log              # Visa commit-historik
git log --oneline    # Kortare format
git diff             # Visa ändringar i filer
```

### Ångra ändringar

```bash
git checkout -- filnamn.py    # Ångra ändringar i en fil
git reset HEAD filnamn.py     # Ta bort fil från staging
git revert HEAD               # Ångra senaste commit
```

### Hämta från GitHub

```bash
git pull             # Hämta och mergea ändringar
git fetch            # Bara hämta (mergea inte)
```

---

## .gitignore

Skapa en fil som heter `.gitignore` i rotmappen. Filer som listas här spåras INTE av Git.

```gitignore
# Python
__pycache__/
*.pyc
.venv/
venv/

# Environment
.env

# Jupyter
.ipynb_checkpoints/

# IDE
.vscode/
.idea/

# Data (om stora filer)
*.csv
*.db

# OS
.DS_Store
Thumbs.db
```

**VIKTIGT:** Lägg alltid `.env` i `.gitignore`! API-nycklar ska ALDRIG pushas till GitHub.

---

## Exempel: Pusha dagens övningar

```bash
# 1. Navigera till projektmappen
cd repetitionsdag-nordkaffe

# 2. Initiera Git (om inte redan gjort)
git init

# 3. Skapa .gitignore
echo ".env" >> .gitignore
echo "__pycache__/" >> .gitignore
echo ".ipynb_checkpoints/" >> .gitignore

# 4. Lägg till alla filer
git add .

# 5. Gör commit
git commit -m "Add repetition exercises: Pandas, ETL, NLP, GenAI"

# 6. Koppla till GitHub (ersätt URL med din)
git remote add origin https://github.com/dittnamn/repetitionsdag.git

# 7. Pusha
git push -u origin main
```

---

## Bra commit-meddelanden

**Dåligt:**
- "fix"
- "update"
- "asdf"

**Bra:**
- "Add ETL pipeline for order data"
- "Fix date parsing in clean_dates function"
- "Add sentiment analysis to reviews"

---

## Om något går fel

### "Your branch is behind"
```bash
git pull --rebase origin main
```

### "Merge conflict"
1. Öppna filen och leta efter `<<<<<<` markeringar
2. Redigera manuellt för att lösa konflikten
3. `git add .` och `git commit`

### Vill börja om helt
```bash
rm -rf .git          # Ta bort Git-historiken
git init             # Börja om
```

---

## Resurser

- [Git dokumentation](https://git-scm.com/doc)
- [GitHub Guides](https://guides.github.com/)
- [Oh Shit, Git!?!](https://ohshitgit.com/) – när det går fel

---

## Cheatsheet

```bash
# Setup
git config --global user.name "Namn"
git config --global user.email "email"

# Skapa/klona
git init                          # Nytt repo
git clone <url>                   # Klona repo

# Dagligt
git status                        # Se ändringar
git add .                         # Stage alla ändringar
git commit -m "meddelande"        # Commita
git push                          # Pusha till remote
git pull                          # Hämta från remote

# Historik
git log --oneline                 # Se historik
git diff                          # Se ändringar

# Branches
git branch                        # Lista branches
git checkout -b ny-branch         # Skapa och byt
git checkout main                 # Byt till main
git merge ny-branch               # Mergea branch
```

---

**Lycka till med Git! 🚀**
