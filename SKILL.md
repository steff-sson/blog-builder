---
name: blog-builder
description: Schreibt Blog-Posts + LinkedIn-Drafts aus Vault-Projektnotizen. Wählt Format je nach User-Wunsch: Portal (~300 Wörter) oder Tutorial (~1500-2000 Wörter). IMMER draft: true. User reviewed vor Live.
license: MIT
compatibility: opencode
---

## Was ich tue
- Erkennt am Prompt des Users das Format: "Kurz-Post"/"Case Study" → Portal. "Tutorial"/"Anleitung" → Tutorial.
- Fragt nach wenn nicht klar.

## Format: Portal (Kurz-Post, ~300 Wörter)
- Struktur: Lead → Problem → Lösung → Ergebnis → Lesson
- Ich-Perspektive
- KEINE Code-Blöcke
- Keine MCP-Erklärungen
- Keine Schritt-für-Schritt
- Max 300 Wörter

### Phase 1: Projekt verstehen (Portal)

1. Frage nach Projektnamen falls nicht genannt
2. Lese `projekte/<projekt>.md` und ggf. `services/<projekt>.md`
3. Extrahiere: Problem · Lösung · Ergebnis · Tech-Stack · Dauer · Zahlen
4. Frage nach bei Unklarheiten

### Phase 2: Post schreiben (Portal)

**Datei:** `[BLOG-REPO]/content/blog/<slug>.md`

**Frontmatter:**
```yaml
---
title: "Aussagekräftiger Titel"
date: YYYY-MM-DD
draft: true
description: "Ein Satz, der neugierig macht — Problem und Ergebnis in einem."
---
```

**Struktur:**
1. **Lead** — Konkrete Szene oder Frage. Keine abstrakte Einleitung. "Letzten Dienstag...", "Kennst du das, wenn..."
2. **Problem** — Was war los? In einem Absatz. Für wen war es ein Problem? Warum hat es gestört?
3. **Lösung** — Nicht der Code, sondern der Weg. Welche Entscheidungen? Was wurde verworfen? Wie lang?
4. **Ergebnis** — Konkret. Zahlen wenn möglich. Was ist anders als vorher?
5. **Lesson** — Eine Erkenntnis. Keine Zusammenfassung. Ein Satz der hängen bleibt.

**Tone-Regeln Portal:**
- Ich-Perspektive ("Ich habe", "Mir war klar")
- Kurze Sätze (max 20 Wörter)
- Keine Buzzwords (Revolution, Game-Changer, 10x)
- Konkret statt abstrakt
- Kein Code im Fließtext
- Schreibe wie du einem Kollegen in der Küche was erzählst

## Format: Tutorial (Lang-Post, ~1500-2000 Wörter)
- Struktur: Hook → OpenCode-Kontext → Skills → Warum-X → MCPs mit Erklär-Ebenen → Retro → Schritt-für-Schritt (5 Steps) → Zukunft → Repo-Links
- Neutrale Perspektive ("Der Mensch", "Der Skill")
- 1-3 Code-Blöcke, jeder mit Vorher-Erklärung und Nachher-Kontext
- 5 Steps: ① Installieren ② Projekt anlegen ③ Skill starten ④ Output prüfen ⑤ Veröffentlichen

### Erklär-Ebenen (nur Tutorial)
Jeder Fachbegriff (MCP, Skill, Subagent, Agent):
- 1 Satz Tech-Erklärung
- 1 Satz Nicht-Tech-Erklärung
- Optional: "Für Nicht-Techies"-Callout

### Warum-X-Regel (nur Tutorial)
Jedes Tool beim ersten Auftauchen: 2 Sätze "Warum [Tool]?"

### CI/CD-Trenn-Regel (hart)
Deployment/Webhook/CI/CD/GitHub Actions NIEMALS im gleichen Post. Verweis auf separaten Post reicht.

### Phase 1: Projekt verstehen (Tutorial)

1. Frage nach Projektnamen falls nicht genannt
2. Lese `projekte/<projekt>.md` und ggf. `services/<projekt>.md`
3. Extrahiere: Problem · Lösung · Ergebnis · Tech-Stack · Dauer · Zahlen · Lessons Learned
4. Lese ggf. `brain/`-Notizen für Domain-Kontext

### Phase 2: Post schreiben (Tutorial)

**Datei:** `[BLOG-REPO]/content/blog/<slug>.md`

**Frontmatter:**
```yaml
---
title: "Aussagekräftiger Titel"
date: YYYY-MM-DD
draft: true
description: "Ein Satz, der neugierig macht."
tags:
  - tutorial
---
```

**Struktur (1500-2000 Wörter):**

1. **Hook** — Konkrete Ausgangssituation. "Wer schon immer X wollte, aber Y im Weg hatte..."

2. **OpenCode-Kontext** — Was ist OpenCode? 2-3 Sätze. Link zu opencode.ai

3. **Skills** — Was sind Skills in OpenCode? Wie hängen sie mit diesem Post zusammen?

4. **Warum-X** — Warum dieses Tool/diesen Skill? 2 Sätze.

5. **MCPs mit Erklär-Ebenen** — Welche MCPs kamen zum Einsatz? Jeden mit Tech- + Nicht-Tech-Erklärung.

6. **Retro** — Was war überraschend? Was hat gefehlt? Was würde ich anders machen?

7. **Schritt-für-Schritt (5 Steps):**
   ① Installieren — Was wird gebraucht? Voraussetzungen?
   ② Projekt anlegen — Ordner, Dateien, Konfiguration
   ③ Skill starten — Befehl ausführen, was passiert
   ④ Output prüfen — Woran erkennt man Erfolg?
   ⑤ Veröffentlichen — Draft → Live (Hinweis: Deployment in separatem Post)

8. **Zukunft** — Was kommt als nächstes? Ausblick auf verwandte Themen.

9. **Repo-Links + Lizenz-Tabelle** — Siehe unten.

**Tone-Regeln Tutorial:**
- Neutrale Perspektive ("Der Mensch", "Der Skill", "es wird")
- Satzlänge max 22 Wörter
- 1-3 Code-Blöcke, jeder mit Vorher-Erklärung und Nachher-Kontext
- Kein CI/CD/Webhook im Post

### Lizenz-Tabelle (Tutorial)

```
| Skill | Zweck | Lizenz |
|-------|-------|--------|
| [Name] | [Kurzbeschreibung] | MIT |
```

Repo-Link: `https://github.com/weitzelnet/[repo]`

## Phase 3: LinkedIn-Draft (beide Formate)

3 Absätze:
1. **Hook** — Das Problem in einem Satz. Mit Wiedererkennungswert.
2. **Brücke** — Was ich gemacht habe. Kurz. Ohne Technik-Jargon.
3. **Ergebnis** — Was rauskam.

Kein Link zum Post, keine Hashtags.

## Phase 4: Vorlegen

Zeige beides im Chat:

```
📝 Blog-Post (Draft) → content/blog/<slug>.md
📱 LinkedIn-Draft:

[Hook]
[Brücke]
[Ergebnis]

— draft: true, unsichtbar bis Freigabe
— Sag "Passt", "Ändere X" oder "Veröffentlichen"
```

## Phase 5: Freigabe (nur auf Befehl)

Bei "Veröffentlichen" oder "Live":
1. Setze `draft: true` → `draft: false`
2. `git add` + `git commit -m "blog: <titel>"`
3. `git push`
4. Bestätigung: "Online unter https://blog.weitzelnet.com/blog/<slug>/"

Bei "Ändere X":
1. Änderung umsetzen
2. Erneut vorlegen (Phase 4)

Sonst: Es bleibt Draft. Kein automatisches Veröffentlichen.

## Review-Checkliste Portal
- Konkrete Szene im Lead?
- Max 300 Wörter?
- Ich-Perspektive?
- Keine Code-Blöcke?
- Keine MCP-Erklärungen?
- Keine Schritt-für-Schritt?
- Satzlänge max 20 Wörter?

## Review-Checkliste Tutorial
- Satzlänge max 22 Wörter?
- Jeder Code-Block hat Vorher-Erklärung + Nachher-Kontext?
- 3 Erklär-Ebenen pro Fachbegriff?
- CI/CD/Webhook nicht im Post?
- Lizenz-Tabelle am Ende?
- 5 Steps vollständig?
- Neutrale Perspektive durchgehalten?
- Warum-X-Regel eingehalten?
- 1500-2000 Wörter?

### Pfade

```
BLOG-REPO  = [BLOG-REPO]
VAULT-PFAD = [VAULT-PFAD]
```
