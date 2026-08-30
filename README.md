# Side-B

纯文字论坛调查游戏。

当前发布：**RC1.8**

此版本加入自动更新机制：
- `version.json` 每次以 `no-store` 获取；
- JS/CSS 使用版本参数加载；
- Service Worker 更新时不使用旧缓存；
- 游戏进度继续使用原来的 localStorage key，不会因为网页升级自动清档。

> 从 RC1.8 开始，后续更新只需修改 `version.json` 的 `build` 值并上传新文件。
