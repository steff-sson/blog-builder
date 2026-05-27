---
name: blog-builder
description: Schreibt Blog-Posts + LinkedIn-Drafts aus Vault-Projektnotizen. IMMER draft: true. User reviewed vor Live.
license: MIT
compatibility: opencode
---

## Was ich tue

Wenn der User sagt "Veröffentliche Projekt X", "Schreib einen Blog-Post über X" oder ähnlich:

### Phase 1: Projekt verstehen

1. Frage nach dem Projektnamen, falls nicht genannt
2. Lese die Vault-Notiz: `projekte/<projekt>.md` und ggf. `services/<projekt>.md`
3. Extrahiere: Problem · Lösung · Ergebnis · Tech-Stack · Dauer · Zahlen
4. Frage nach wenn etwas unklar ist

### Phase 2: Blog-Post schreiben

**Datei:** `[BLOG-REPO]/content/blog/<slug>.md`

**Frontmatter:**
```yaml
---
title: "Aussagekräftiger Titel"
date: YYYY-MM-DD
draft: true
description: "Ein Satz, der neugierig macht — das Problem und das Ergebnis in einem."
---
```

**Struktur (max 300 Wörter):**

1. **Lead** — Konkrete Szene oder Frage. Keine abstrakte Einleitung. "Letzten Dienstag...", "Kennst du das, wenn...", "Ich dachte, ich hätte alles im Griff. Bis..."
2. **Das Problem** — Was war los? In einem Absatz. Für wen war es ein Problem? Warum hat es gestört?
3. **Der Lösungsweg** — Nicht der Code, sondern der Weg. Welche Entscheidungen wurden getroffen? Was wurde verworfen? Wie lang hat's gedauert?
4. **Das Ergebnis** — Konkret. Zahlen wenn möglich. Was ist anders als vorher?
5. **Was ich gelernt habe** — Eine Erkenntnis. Keine Zusammenfassung. Ein Satz der hängen bleibt.

**Tone-Regeln:**
- Ich-Perspektive ("Ich habe", "Mir war klar")
- Kurze Sätze (max 20 Wörter)
- Keine Buzzwords (Revolution, Game-Changer, 10x)
- Konkret statt abstrakt ("Das hab ich heute hingekriegt" statt "KI ist die Zukunft")
- Kein Code-Blöcke im Fließtext
- Schreibe wie du einem Kollegen in der Küche was erzählst

### Phase 3: LinkedIn-Draft ableiten

3 Absätze aus dem Blog-Post:

1. **Hook** — Das Problem in einem Satz. Mit Wiedererkennungswert.
2. **Brücke** — Was ich gemacht habe. Kurz. Ohne Technik-Jargon.
3. **Ergebnis + Frage** — Was rauskam. Ende mit einer Frage ans Netzwerk.

Kein Link zum Blog-Post (LinkedIn priorisiert External-Links nicht). Keine Hashtags.

### Phase 4: Vorlegen

Zeige beides im Chat:

```
📝 Blog-Post (Draft) → content/blog/<slug>.md
📱 LinkedIn-Draft:

[Hook]
[Brücke]
[Ergebnis + Frage]

— draft: true, unsichtbar bis Freigabe
— Sag "Passt", "Ändere X" oder "Veröffentlichen"
```

### Phase 5: Freigabe (nur auf Befehl)

Wenn User "Veröffentlichen" oder "Live" sagt:
1. Setze `draft: true` → `draft: false`
2. `git add` + `git commit -m "blog: <titel>"`
3. `git push` (triggered Webhook → Hugo build auf Server)
4. Bestätigung: "Online unter https://blog.weitzelnet.com/blog/<slug>/"

Wenn User "Ändere X" sagt:
1. Änderung umsetzen
2. Erneut vorlegen (Phase 4)

Wenn User gar nichts sagt: Es bleibt Draft. Kein automatisches Veröffentlichen.

### Review-Checkliste (vor Vorlage anwenden)

- [ ] **Wo ist die konkrete Szene?** — Jeder Post beginnt mit einem Moment, nicht einer These
- [ ] **Welches Detail ist überflüssig?** — Streichen. Kürzen bis es wehtut
- [ ] **Wo schreibe ich für Fachleute statt für Menschen?** — Umschreiben. Der Leser kennt den Kontext nicht
- [ ] **Wo fehlt das "Ich"?** — Persönliche Haltung einweben. Nicht neutral berichten

### Pfade

```
Blog-Repo:      [BLOG-REPO]
Blog-Posts:     [BLOG-REPO]/content/blog/
Logo:           [BLOG-REPO]/static/img/logo.svg
Vault Projekte: [VAULT-PFAD]/projekte/
Vault Services: [VAULT-PFAD]/services/
```
