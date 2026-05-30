# Codex 额度重置工具

查询 ChatGPT Codex 邀请资格和 rate limit reset credits，一键重置额度。

## 使用方法

```bash
pip3 install flask curl_cffi
python3 app.py
```

浏览器访问 http://localhost:8080 ，粘贴从 `https://chatgpt.com/api/auth/session` 获取的 session JSON。

## 如何获取 Session JSON

1. 浏览器登录 [chatgpt.com](https://chatgpt.com)
2. F12 打开 DevTools → Network 标签
3. 访问 `https://chatgpt.com/api/auth/session`
4. 复制 Response 的完整 JSON 内容
5. 粘贴到网页输入框，点击「查询资格」

## 技术方案

- **前端**: 纯 HTML/CSS/JS，暗色主题，中文界面
- **后端**: Flask + curl_cffi（模拟 Chrome TLS 指纹绕过 Cloudflare）
- **代理**: 自动检测 macOS 系统代理（ClashX/V2Ray 等）

## API 端点

| 功能 | ChatGPT API |
|------|------------|
| 查询邀请资格 | `GET /backend-api/referrals/invite/eligibility` |
| 查询 reset credits | `GET /backend-api/wham/rate-limit-reset-credits` |
| 消耗 reset credit | `POST /backend-api/wham/rate-limit-reset-credits/consume` |
| 查询使用状态 | `GET /backend-api/wham/usage` |
