## HidenCloud自动续期 

## 配置

在仓库 `Settings → Secrets and variables → Actions` 中添加以下 Secrets：

| Secret 名称 | 必填 | 说明 | 示例 |
|---|---|---|---|
| `COOKIE_VALUE`  | ✅必填 | Remenber_web cookie | Remenber_web cookie的值 |
| `EMAIL`         | ✅必填 | HidenCloud 邮箱 | xxx@gmail.com |
| `PASSWORD`      | ✅必填 | HidenCloud 密码 | xxxxxxxx      |
| `NODE_LINK`     | ❌可选 | 代理节点地址，支持多种协议 | vless:// vmess:// trojan:// hysteria2:// anytls:// tuic:// |
| `TG_BOT_TOKEN`  | ❌可选 | Telegram Bot Token | `123456:ABC-DEF12l-zyx57W2v1u` |
| `TG_CHAT_ID`    | ❌可选 | Telegram Chat ID | `123456789` |


### 代理格式（确认在v2rayN里使用正常的节点）`最好用注册号的代理`

`NODE_LINK` 支持以下任意一种代理协议的完整分享链接（不配置则直连）：

- **VLESS**：`vless://uuid@server:port?security=reality&sni=...&type=ws&...`
- **VMess**：`vmess://base64encoded`
- **Trojan**：`trojan://password@server:port?sni=...&type=ws&...`
- **Shadowsocks**：`ss://base64@server:port`
- **SOCKS5**：`socks5://user:pass@server:port` 或 `socks5://server:port`

## 使用

### GitHub Actions 运行步骤

1. Fork 本仓库  
2. 在仓库 Secrets 中配置必填的环境变量,（可选）配置 `TG_BOT_TOKEN`、`TG_CHAT_ID`、`NODE_LINK`  
3. Actions菜单里手动触发 `workflow_dispatch`  
4. 根据服务到期时间来修改cron运行时间,比如你的服务是25号到期,计算后是星期二,则设置cron为每周一运行


---

**⚠️ 免责声明**：本脚本仅供学习交流使用，使用者需遵守 [HidenCloud](https://hidencloud.com) 的服务条款。因使用本脚本造成的任何问题，作者不承担任何责任。
