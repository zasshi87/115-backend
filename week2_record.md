# Week 2：完整 Tool-Use 對話紀錄

## 1. 兩次 API 呼叫重點觀察表

| 步驟         | 模型建議                                                                      | 程式實際執行                                                                                                                                                                   |
| :--------- | :------------------------------------------------------------------------ | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 第一次 API 回應 | `"name": "http_get"`,  `"arguments": "{\"url\":\"https://example.com\"}"` | 尚未執行；只收到建議（`"id": "call-3f6eda91-506f-40a2-9fb7-cff984a000c3"`）                                                                                                          |
| 工具執行       | 無                                                                         | `"status_code"`: ` 200`、`"body_summary"`: ` "<!doctype html><html lang=en><head><meta charset=utf-8><link rel=icon href=data:,><meta name=viewport content=\"width=dev"` |
| 第二次 API 請求 | 無                                                                         | `tool_call_id`: ` "call-3f6eda91-506f-40a2-9fb7-cff984a000c3"                                                                                                            |
| 第二次 API 回應 | 無                                                                         | `choices[0].message.content`: `抓取成功（HTTP 200），我看到的是 example.com 的標準示範頁面，包含一個標題為「Example Domain」的巨大標題和一段說明此頁面可供網頁設計使用的文字。`                                                |

## 2. 完整終端機輸出紀錄

```text
status: 200
tool_calls: [
  {
    "id": "call-3f6eda91-506f-40a2-9fb7-cff984a000c3",
    "type": "function",
    "function": {
      "name": "http_get",
      "arguments": "{\"url\":\"https://example.com\"}"
    }
  }
]
模型建議: {"url":"https://example.com"}
程式執行: {"status_code": 200, "body_summary": "<!doctype html><html lang=en><head><meta charset=utf-8><link rel=icon href=data:,><meta name=viewport content=\"width=dev"}
status: 200
reply: 抓取成功（HTTP 200），我看到的是 example.com 的標準示範頁面，包含一個標題為「Example Domain」的巨大標題和一段說明此頁面可供網頁設計使用的文字。