# blog-builder

OpenCode Skill: Aus einer Vault-Projektnotiz einen Blog-Post + LinkedIn-Draft erstellen.

Immer `draft: true`. User reviewed vor Live.

## Installation

```bash
# 1. Skill kopieren
mkdir -p ~/.config/opencode/skills/blog-builder
cp SKILL.md ~/.config/opencode/skills/blog-builder/

# 2. Pfade anpassen
# In ~/.config/opencode/skills/blog-builder/SKILL.md:
# [BLOG-REPO] → absoluter Pfad zu deinem Hugo-Blog
# [VAULT-PFAD] → absoluter Pfad zu deinem Obsidian-Vault
# [DEINE-DOMAIN] → deine Blog-Domain

# 3. OpenCode starten — Skill wird automatisch erkannt
opencode
```

## Nutzung

```
"Schreib einen Blog-Post über [Projektname]"

→ Skill liest Vault-Notiz
→ Schreibt Blog-Post (draft: true) + LinkedIn-Draft
→ Legt vor → User reviewt → Freigabe oder Änderung
```

## Lizenz

MIT
