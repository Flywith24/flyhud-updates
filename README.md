# FlyHUD Updates

FlyHUD 公开版本清单，由 GitHub Pages 提供 HTTPS 静态托管。

固定地址：https://flywith24.github.io/flyhud-updates/ios-updates.json

当前 `channels` 为空：服务已部署，但不公告任何新版本。初始空清单有效期为一年；启用真实公告时，将清单有效期收紧到不超过 7 天，后续发布或延期时维护该日期。

## 发布新版本公告

1. 确认 App Store 已开放，或 TestFlight 目标测试组均可安装该 build。
2. 修改 `ios-updates.json`，保留 schemaVersion、platform、bundleID。
3. 在 channels 中添加 `appStore` / `testFlight`，包含 version、build、minimumOS、enabled、publishedAt、expiresAt、url、highlights。日期为 UTC ISO 8601，版本和 build 为字符串。
4. App Store 链接使用 https://apps.apple.com/app/id6787705132；TestFlight 链接须用测试账号实际验证，不能以网站首页代替安装入口。
5. 在 FlyHUD 源码仓库运行 `python3 script/validate_ios_releases.py --manifest <清单路径>`。
6. 提交到 Pages 发布分支，等待部署完成，匿名请求固定 URL 确认返回新 JSON。

TestFlight 公告到期时间不得超过实际 build 到期时间。撤回公告时删除对应渠道或设置 enabled 为 false，并保持顶层 expiresAt 有效。清单中不要放凭据、账号或用户数据。
