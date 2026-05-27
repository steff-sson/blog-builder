# blog-builder

Blog-Publish-Workflow für blog.weitzelnet.com.

**Regel:** Blog-Posts IMMER als `draft: true` anlegen. Der User reviewed und gibt frei.

**Projekt-Verknüpfung:** Projekte liegen im Vault unter `projekte/` oder `services/`. Der Skill liest die Notiz und schreibt den Post.

**Blog-Repo:** `~/github/blog.weitzelnet.com/`
**Hugo:** content/blog/ — `draft: true` im Frontmatter bedeutet unsichtbar
**Build:** Hugo mit `--buildFuture` (für Preview zukünftiger Beiträge)
**Deployment:** git push → Webhook → Hugo build auf Server
