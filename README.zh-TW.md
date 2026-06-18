# OmniConsole 社群翻譯

> 🌐 [English](README.md) | **繁體中文**

[**OmniConsole**](https://github.com/8bit2qubit/OmniConsole) 與其 **OmniCharm** 小工具的社群翻譯。一起讓 OmniConsole 說你的語言吧！

<p align="center">
<a href="https://github.com/8bit2qubit/OmniConsole"><img src="https://img.shields.io/badge/main%20repo-OmniConsole-blue?style=flat" alt="主程式儲存庫"></a>
<a href="LICENSE"><img src="https://img.shields.io/badge/license-CC%20BY--NC%204.0-lightgrey?style=flat" alt="授權"></a>
</p>

## 💡 運作方式

OmniConsole 會直接從這個儲存庫讀取社群翻譯。你的翻譯一旦合併進來，就會出現在 App 內的**社群語言**管理介面（設定 → ☰ → 進階 → 社群語言的「管理」）供大家下載，並隨著 OmniConsole 與翻譯的演進自動保持最新。

翻譯就是純文字的 `.resw`（XML）檔案，只要編輯文字、發出 Pull Request 即可。

---

## 📁 儲存庫結構

翻譯依 OmniConsole 版本、再依專案、再依語言分層：

```
<版本>/
├── OmniConsole/                   ← 主程式
│   ├── en-US/Resources.resw       ← 英文基準（參考用，請勿翻譯）
│   └── <語言>/Resources.resw      ← 翻譯（如 ja-JP、es-ES）
└── OmniConsole.PhantomLink/       ← OmniCharm 小工具
    ├── en-US/Resources.resw       ← 英文基準（參考用，請勿翻譯）
    └── <語言>/Resources.resw      ← 翻譯
```

- `<版本>` 對應某個 OmniConsole 發行版本（如 `3.1.0.0`）。App 會下載與自己版本相符的資料夾。
- `<語言>` 是 BCP-47 語言碼（如 `ja-JP`、`es-ES`、`fr-FR`、`de-DE`、`ko-KR`）。
- 每個語言都是**兩個檔案的整套**：一個給主程式、一個給 OmniCharm 小工具。
- 每個專案的 `en-US/Resources.resw` 是**英文基準**，請當參考來源用，不要翻譯它。

---

## 🌐 如何貢獻翻譯

### 新增一個語言（以 fr-FR 為例）

1. **Fork** 這個儲存庫。
2. 選擇**最新的版本資料夾**（如 `3.1.0.0/`）。
3. 在每個專案（`OmniConsole` 與 `OmniConsole.PhantomLink`）底下，把它的 `en-US/Resources.resw` 複製到一個以你的語言碼命名的新資料夾，例如 `3.1.0.0/OmniConsole/fr-FR/Resources.resw`。
4. 翻譯每個 `<data>` 項目的 **`<value>`**（規則見下方），其餘保持原樣。
5. 發出 **Pull Request**。

主程式（`OmniConsole`）與 OmniCharm 小工具（`OmniConsole.PhantomLink`）兩個都很重要，請務必一起翻譯，帶來完整的體驗。

### 更新／修正既有翻譯

編輯你想修改的 `<value>`，若有 `untranslated:*` 註解請一併移除（見下方），然後發出 Pull Request。

---

## ✏️ 翻譯規則

`.resw` 是標準 XML，你主要編輯 `<value>` 裡的文字：

```xml
<data name="SettingsTitle.Text" xml:space="preserve">
  <value>{OmniConsole} Settings</value>
</data>
```

- **品牌佔位符 `{OmniConsole}` 請原樣保留**，不要翻譯或更動（業界的「請勿翻譯」慣例）。
- **`{0}` `{1}` 等是參數佔位符**，請保留；位置可依你的語言調整，但不要更動或移除。
- **`AUTHENTICITY.md` 檔名**：少數字串（如憑證詳細資訊）會提到主程式儲存庫的 `AUTHENTICITY.md` 檔。只有 **繁體中文（`zh-TW`）** 與 **簡體中文（`zh-CN`）** 有在地化的 `AUTHENTICITY.zh-TW.md`；**其他所有語言一律指向英文版 `AUTHENTICITY.md`**。因此你的翻譯中請保留 `AUTHENTICITY.md` 原樣（除非你翻的是中文，則為 `AUTHENTICITY.zh-TW.md`）。
- **`untranslated:new` / `untranslated:changed` 註解**標記仍待翻譯的項目。這些註解只在更新既有翻譯時才會出現；全新語言（從 `en-US` 複製）不會有。
  - `untranslated:new`：本版全新的字串。
  - `untranslated:changed`：英文自上一版以來有變動，舊譯文可能已不合適，請重新檢視。
  - 這些項目的 `<value>` 在你翻譯前會先顯示英文。**翻完後請更改 `<value>`，並刪除整行 `<comment>`。**
- 只有 **`<value>`** 與 `untranslated:*` 註解需要處理。請勿新增其他註解或更動檔案結構。

---

## ✍️ index.json：語言清單與譯者署名

OmniConsole 會在每個社群語言旁顯示譯者署名。署名記在 `index.json` 裡、依版本分類，而**貢獻者不需要編輯它**；它會在 Pull Request 合併時維護，使用貢獻者的 GitHub 帳號名稱：

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

- `code`：BCP-47 語言碼（必須與你的資料夾名稱相符）。
- `translators`：貢獻者的 GitHub 帳號名稱，會在 App 內顯示為譯者署名。多位貢獻者：`["name1", "name2"]`。
- `revision`：為既有翻譯發布修正時將它加 1，已安裝的副本便會知道要更新。新語言從 `1` 開始。

---

## ✅ 發出 Pull Request 前

- 兩個資料夾都使用你正確的語言碼（如 `fr-FR`，而非 `fr` 或 `FR-fr`）。
- `{OmniConsole}` 佔位符與 `{0}`／`{1}` 參數都完好無缺。
- 已翻譯的項目都已移除 `untranslated:*` 註解。

感謝你讓更多人能以自己的語言享受 OmniConsole！💜

---

## 📄 授權

本儲存庫的翻譯採用 [**創用 CC 姓名標示-非商業性 4.0 國際 (CC BY-NC 4.0)**](LICENSE) 授權。

在非商業用途下，你可以自由分享與修改這些翻譯，並須標示譯者。提交貢獻即表示你同意你的翻譯以此授權提供。
