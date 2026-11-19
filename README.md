# 宵行 · Nightrun

> 肃肃宵征，夙夜在公。——《诗经·召南·小星》
> 宵行即夜行：夜里赶路的人。

末世后一条荒废高速的穿山隧道，少年踩滑板巡线，无限循环。
**宵行** 是一张 [Lively Wallpaper](https://github.com/rocksdanister/lively) 动态壁纸：
Three.js 实时渲染、完全离线、零网络请求；桌面单击蹬地、双击压弯、鼠标横向移动即车道内侧移与侧倾。

在线试玩与下载：<https://nightrun.fxdgrld.top>（部署后生效）

## 仓库结构

```
nightrun/
├─ index.html              # 落地页（宵行主标题 + 隧道尽头灯）
├─ lab/
│  ├─ index.html           # 实景工作台：在线调参、页内导出自己的 zip
│  └─ assets/props/racer.js# 弃车道具（第三方开源跑车建模，12k 面）
├─ assets/                 # 落地页真渲染帧（hero.webp / scene.webp）
├─ docs/
│  ├─ world-bible.md       # 世界观设定
│  ├─ blueprint.html       # 工程蓝图 v1.1
│  └─ character.html       # 人物建模方案 v2
├─ dist/                   # 不进 Git（.gitignore）；zip 走 Release 附件
├─ DESIGN.md               # 落地页 direction brief
├─ .nojekyll               # GitHub Pages 必需
├─ CNAME                   # nightrun.fxdgrld.top
├─ README.md
└─ LICENSE                 # CC-BY-NC-4.0
```

## 安装（Lively）

1. 从 [Releases](https://github.com/zhui-ying-by-G/nightrun/releases) 下载 `nightrun-lively.zip`（约 461 KB）。
2. 把 zip **拖进 Lively 库**（web 工程不能由命令行导入）。
3. 更新后按 **「恢复默认」**：存档在 `SaveData/wpdata` 按目录指针保存，不按这一步新默认值不生效。

解压后的文件夹不要放 Downloads 等临时位置——Lively 存的是指针，移动/改名会丢 origin 与存档。
需要 WebGL2；不可用时回落 2D 近似，不会黑矩形。无音频。

## 公开版口径

只含**程序化少年**（21 骨刚性蒙皮）与**跑车道具**。开发全量版中的其他人物档、
伴生机制与第三方/同人资产均未打包；旧存档若指向被裁掉的档，会自动回落少年，不黑屏。

## 部署（GitHub Pages + 子域名）

本仓库按 GitHub Pages 纯静态站部署，域名 `nightrun.fxdgrld.top`：

1. 仓库根已含 `CNAME`（`nightrun.fxdgrld.top`）与 `.nojekyll`。
2. GitHub → Settings → Pages → Source: *Deploy from a branch* → `main` + `/ (root)`。
3. 域名注册商 DNS 加一条 CNAME：`nightrun` → `zhui-ying-by-G.github.io`。
4. DNS 生效后回 Pages 页勾 **Enforce HTTPS**。
5. 把 `dist/nightrun-lively.zip` 作为 **Release 附件**上传（tag 建议 `v1.0`）；
   落地页下载按钮指向 `releases/latest/download/nightrun-lively.zip`。
   zip 不进 Git：仓库只放站点文件。

## 构建与验收

构建器与验收闸在主工程 `D:\wallpaper by FX\standalone\infinite-tunnel\tools\`：

```
node tools/build-nightrun.mjs     # 从 src/ 重新生成 lab/ 与 dist/nightrun-lively.zip（锚点断言，失败不落盘）
node tools/verify-nightrun.mjs    # NIGHTRUN-GATE：渲染 / 旧存档回放 / 导出 manifest / 静态 IP 闸
```

Lively 配置校验：`python <lively-skill>/scripts/validate.py _nightrun/lively`。

## 许可与第三方

- 本仓库原创代码、文档与程序化资产：**CC-BY-NC-4.0**（见 `LICENSE`）。署名、非商业性使用。
- **跑车道具除外**：`lab/assets/props/racer.js` 为第三方开源建模的减面烘焙件，
  出处与许可信息由作者另行声明（待补），不在本许可授权范围内。
- [Three.js](https://github.com/mrdoob/three.js) r169：MIT License，Copyright © 2010-2024 three.js authors。
- 字体使用系统自带字体栈，无外部字体请求。

## 已知限制

- 帧率实测 56 fps @2560×1600（RTX 4060 Laptop，无头 Edge）；核显请在设置降画质档。
- 鼠标穿透取决于 Lively 的「桌面交互」设置；关掉即完全不响应点击。
- 微事件层每 2–7 分钟一出；8 小时尺度天光极慢偏色。

---

(c) 2026 FX · <https://fxdgrld.top>