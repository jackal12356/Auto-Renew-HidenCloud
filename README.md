# HidenCloud 自动续期

## 配置

在仓库 `Settings → Secrets and variables → Actions` 中添加以下 Secrets：

| Secret 名称 | 必填 | 说明 | 示例 |
|---|---|---|---|
| `COOKIE_VALUE`  | ✅必填 | Remenber_web cookie | Remenber_web cookie的值 |
| `EMAIL`         | ✅必填 | HidenCloud 邮箱 | xxx@gmail.com |
| `PASSWORD`      | ✅必填 | HidenCloud 密码 | xxxxx |
| `NODE_LINK`     | ❌可选 | 代理节点地址，支持多种协议 | vless:// vmess:// trojan:// |
| `TG_BOT_TOKEN`  | ❌可选 | Telegram Bot Token | `123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11` |
| `TG_CHAT_ID`    | ❌可选 | Telegram Chat ID | `123456789` |



### ⚙️ REPO_TOKEN 权限要求


### HIDENCLOUD 格式

邮箱和密码用 `-----` 分隔（目前仅支持单账号）：

```
myaccount@mail.com-----MyStr0ngP@ssw0rd
```

### 代理格式（最好本地浏览器试试能不能登陆再用）`最好用注册号的代理`

`NODE_LINK` 支持以下任意一种代理协议的完整分享链接（不配置则直连）：

- **VLESS**：`vless://uuid@server:port?security=reality&sni=...&type=ws&...`
- **VMess**：`vmess://base64encoded`
- **Trojan**：`trojan://password@server:port?sni=...&type=ws&...`
- **Shadowsocks**：`ss://base64@server:port`
- **SOCKS5**：`socks5://user:pass@server:port` 或 `socks5://server:port`

## 使用

### GitHub Actions（推荐）

1. Fork 本仓库  
2. 在仓库 Secrets 中配置 `HIDENCLOUD` 和 `REPO_TOKEN`（注意 PAT 权限）  
3. （可选）配置 `TG_BOT_TOKEN`、`TG_CHAT_ID`、`PROXY_NODE`  
4. 工作流会按初始 Cron 计划运行，首次成功后会自动计算并更新为最优的后续执行时间  
5. 你也可以随时在 Actions 页面手动触发 `workflow_dispatch`  

## 注意事项

- Cloudflare Turnstile 验证有一定失败概率，脚本已内置等待与重试机制  
- 工作流会自动修改 `.github/workflows/HidenCloud_Renew.yml` 中的 Cron 表达式，请确保 Actions 有写入权限  
- 浏览器状态缓存在 GitHub Actions Cache 中，可加速后续运行，每次执行后会自动清理旧缓存  
- 日志和 Telegram 通知中的敏感信息（邮箱、服务器 ID 等）均已脱敏处理  
- 代理为可选项，若在国内环境运行，建议配置代理以提高稳定性  

---

**⚠️ 免责声明**：本脚本仅供学习交流使用，使用者需遵守 [HidenCloud](https://hidencloud.com) 的服务条款。因使用本脚本造成的任何问题，作者不承担任何责任。
