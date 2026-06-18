# OmniConsole Translations

> 🌐 **English** | [繁體中文](README.zh-TW.md)

Community translations for [**OmniConsole**](https://github.com/8bit2qubit/OmniConsole) and its **OmniCharm** widget. Help bring OmniConsole to your language!

<p align="center">
<a href="https://github.com/8bit2qubit/OmniConsole"><img src="https://img.shields.io/badge/main%20repo-OmniConsole-blue?style=flat" alt="Main Repo"></a>
<a href="LICENSE"><img src="https://img.shields.io/badge/license-CC%20BY--NC%204.0-lightgrey?style=flat" alt="License"></a>
</p>

## 💡 How it works

OmniConsole reads community translations directly from this repository. Once your translation is merged here, it appears in the in-app **Community Languages** manager (Settings → ☰ → Advanced → Community Languages → **Manage**) for everyone to download — and stays up to date automatically as OmniConsole and its translations evolve.

Translations are plain `.resw` (XML) files — just edit text and open a pull request.

---

## 📁 Repository structure

Translations are organized by OmniConsole version, then by project, then by language:

```
<version>/
├── OmniConsole/                   ← the main app
│   ├── en-US/Resources.resw       ← English baseline (reference — do not translate)
│   └── <lang>/Resources.resw      ← a translation (e.g., ja-JP, es-ES)
└── OmniConsole.PhantomLink/       ← the OmniCharm widget
    ├── en-US/Resources.resw       ← English baseline (reference — do not translate)
    └── <lang>/Resources.resw      ← a translation
```

- `<version>` matches an OmniConsole release (e.g., `3.1.0.0`). The app downloads the folder matching its own version.
- `<lang>` is a BCP-47 language code (e.g., `ja-JP`, `es-ES`, `fr-FR`, `de-DE`, `ko-KR`).
- Each language is **a full set of two files**: one for the main app, one for the OmniCharm widget.
- The `en-US/Resources.resw` in each project is the **English baseline** — use it as your reference; do not translate it.

---

## 🌐 How to contribute a translation

### Add a new language (e.g., fr-FR)

1. **Fork** this repository.
2. Pick the **latest version folder** (e.g., `3.1.0.0/`).
3. For each project (`OmniConsole` and `OmniConsole.PhantomLink`), copy its `en-US/Resources.resw` into a new folder named after your language code, e.g., `3.1.0.0/OmniConsole/fr-FR/Resources.resw`.
4. Translate the **`<value>`** of each `<data>` entry (see rules below). Leave everything else as-is.
5. Open a **pull request**.

Both the main app (`OmniConsole`) and the OmniCharm widget (`OmniConsole.PhantomLink`) matter — please be sure to translate both for a complete experience.

### Update / fix an existing translation

Edit the `<value>` you want to change, remove its `untranslated:*` comment if present (see below), and open a pull request.

---

## ✏️ Translation rules

A `.resw` file is standard XML. You mainly edit the text inside `<value>`:

```xml
<data name="SettingsTitle.Text" xml:space="preserve">
  <value>{OmniConsole} Settings</value>
</data>
```

- **Keep the brand placeholder `{OmniConsole}` exactly as-is** — do not translate or alter it. (Industry "Do Not Translate" convention.)
- **`{0}` `{1}` etc. are parameter placeholders** — keep them; their position can move to fit your language, but do not change or remove them.
- **`AUTHENTICITY.md` filename**: a few strings (e.g., the certificate-details text) reference the `AUTHENTICITY.md` file on the main repo. Only **Traditional Chinese (`zh-TW`)** and **Simplified Chinese (`zh-CN`)** have a localized `AUTHENTICITY.zh-TW.md`; **all other languages should reference the English `AUTHENTICITY.md`**. So keep `AUTHENTICITY.md` as-is in your translation (unless you are translating into Chinese, where it is `AUTHENTICITY.zh-TW.md`).
- **`untranslated:new` / `untranslated:changed` comments** mark entries that still need translating. These only appear when updating an existing translation; a brand-new language (copied from `en-US`) will not have them.
  - `untranslated:new` — a brand-new string in this version.
  - `untranslated:changed` — the English changed since the last version; the old translation may no longer fit, so review it.
  - The `<value>` of these falls back to English until you translate it. **After translating, change the `<value>` and delete the whole `<comment>` line.**
- Only the **`<value>`** and the `untranslated:*` comment matter. Do not add other comments or restructure the file.

---

## ✍️ index.json — language list & translator credits

OmniConsole shows a translator credit next to each community language. Credits live in `index.json`, keyed by version — but **contributors do not edit it**; it is maintained when a pull request is merged, using the contributor's GitHub username:

```json
{
  "versions": {
    "3.1.0.0": [
      {
        "code": "zh-TW",
        "translators": ["8bit2qubit"],
        "revision": 1
      }
    ]
  }
}
```

- `code` — the BCP-47 language code (must match your folder name).
- `translators` — the contributor's GitHub username; shown in-app as the translator credit. Multiple contributors: `["name1", "name2"]`.
- `revision` — bumped by 1 when a fix to an existing translation is published, so installed copies know to refresh. New languages start at `1`.

---

## ✅ Before you open a pull request

- The two folders use your exact language code (e.g., `fr-FR`, not `fr` or `FR-fr`).
- `{OmniConsole}` placeholders and `{0}`/`{1}` parameters are intact.
- Translated entries have their `untranslated:*` comments removed.

Thank you for helping more people enjoy OmniConsole in their own language! 💜

---

## 📄 License

Translations in this repository are licensed under [**Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)**](LICENSE).

You are free to share and adapt these translations for noncommercial use, with attribution to the translators. By contributing, you agree your translation is provided under this license.
