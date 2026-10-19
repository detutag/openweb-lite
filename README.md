---
title: OpenWebUI Lite
emoji: 🤖
colorFrom: purple
colorTo: blue
sdk: static
sdk_version: "1"
app_file: dist/index.html
pinned: false
short_description: 純前端聊天 UI，支援任何 OpenAI 相容 API
---

# OpenWebUI Lite

一個可直接部署到 Hugging Face **Static Space** 的純前端聊天 UI。支援任何 OpenAI 相容 API，所有請求由瀏覽器直接發出，API Key 僅保存在您瀏覽器的 `localStorage`。

## 快速部署

本 repo 已包含預先構建的 `dist/` 目錄。建立 Hugging Face Space 時：

1. 選擇 **Static** 型別。
2. 上傳本 repo 的 `README.md` 和 `dist/`。
3. Space 會依照此 `README.md` 的 `app_file: dist/index.html` 啟動頁面。

> 💡 **請只上傳 `dist/` 和 `README.md`。** 其他來源碼和依賴文件無需部署。

需要重新構建：

```bash
npm install
npm run build
```

## 使用方式

1. 點擊頂部「設定」。
2. 填入 API Key、Base URL、Endpoint 與 Model ID。
3. 開始對話。

### 常用供應商設定

| 供應商      | Base URL                         | Endpoint             | Model ID 範例                |
| :---------- | :------------------------------- | :------------------- | :-------------------------- |
| OpenAI      | `https://api.openai.com/v1`      | `/chat/completions`   | `gpt-4o`                    |
| Anthropic   | `https://api.anthropic.com`      | `/chat/completions`   | `claude-3-5-sonnet-20241022`|
| Groq        | `https://api.groq.com/openai/v1` | `/chat/completions`   | `llama-3.1-70b-versatile`   |
| OpenRouter  | `https://openrouter.ai/api/v1`   | `/chat/completions`   | `meta/llama-3.1-8b`         |

## 本地測試

```bash
npm install
npm run dev
```

開發伺服器預設監聽 `http://localhost:7860`。

## 技術選型

- Vite + React 18
- Tailwind CSS
- React Markdown
- 原生 Fetch / ReadableStream 處理 SSE

## 限制與注意

- HuggingFace Static Space 不會執行 `npm run build`，因此部署必須包含 `dist/`。
- 瀏覽器直連第三方 API 時，供應商的 CORS 政策會影響可用性。
- API Key 僅保存在瀏覽器，不適合多人共用相同資料。

## 授權

MIT License.
