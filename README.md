# The Human Pattern Lab — Content Repository

This repository is the **canonical source of truth** for all long-form written content used across **The Human Pattern Lab** ecosystem.

It contains **only content** — no application code, no build tooling, no rendering logic.

If it’s Markdown and it represents an idea, concept, note, or document that should exist *independently of any UI*, it lives here.

---

## 📦 What This Repository Is

* A **content ledger** for the Lab
* The upstream source for:

    * Lab Notes (blog / essays)
    * Multi-language content
    * Docs and standards
* Designed to be **consumed**, not executed

Other systems (API, website, docs site) **pull from this repo** and decide how content is indexed, rendered, published, or archived.

---

## 🚫 What This Repository Is Not

* ❌ Not a React / frontend project
* ❌ Not an API
* ❌ Not a database
* ❌ Not environment-specific

No build steps. No frameworks. No magic.

---

## 🗂️ Repository Structure

```txt
labnotes/
  en/
    pinned-thread.md
    context-switching-gremlin.md
  ko/
    pinned-thread.md

docs/
  standards/
    carmel-judgment-protocol.md
  philosophy/
    meaning-lives-in-use.md
```

### Folder meanings

* **`labnotes/`**

    * Long-form essays, memos, reflections
    * Synced into the Lab database via a guarded importer
    * Locale folders (`en`, `ko`, etc.) are **first-class**

* **`docs/`**

    * Standards, protocols, reference documents
    * May be rendered directly by a docs site or API

---

## 🌍 Localization Model

Localization is directory-based:

```txt
labnotes/en/example.md
labnotes/ko/example.md
```

* Filenames (slugs) should match across locales
* Each locale file is treated as its own content source
* Translation status is handled downstream (not here)

---

## 🧠 Frontmatter Philosophy

Markdown files may include frontmatter to describe metadata such as:

* `title`
* `slug` / `id`
* `category` / `type`
* `status` (draft / published)
* `published_at`
* conceptual metadata (e.g. `safer_landing`, `shadow_density`)

This repo **does not enforce schema rules**.

Validation, normalization, and defaults are applied by downstream consumers (API, sync tools, etc.).

---

## 🔄 How Content Is Used

Typical flow:

1. Markdown lives here (source of truth)
2. An external system syncs content into a database
3. The database becomes the runtime index
4. UIs render **only from the database**

This prevents:

* Multiple competing sources
* UI-only content
* Silent divergence between environments

---

## 🧪 Development & Integration

This repo is commonly included as:

* a **git submodule**
* or a **read-only dependency**

Example usage (API sync):

```env
LABNOTES_DIR=external/content/labnotes
```

The consuming system is responsible for:

* discovering files
* parsing frontmatter
* managing publish state
* rendering Markdown to HTML

---

## ✨ Guiding Principle

> **Markdown is the ledger.**
> **Databases are indexes.**
> **UIs are views.**

This repository exists to keep that boundary clean.

---

## 🦊 Maintained By

**The Human Pattern Lab**
Concepts, systems, and quiet revolutions.

If something feels like it belongs here — it probably does.
