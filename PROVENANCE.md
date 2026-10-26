# 素材来源与许可范围（PROVENANCE）

本仓库的**代码**按 MIT 许可（见 [`LICENSE`](LICENSE)）。`assets/` 目录下的**美术素材**（图片 / 动图 / 音效）**不在 MIT 覆盖范围内**，按下面的说明「原样提供」。

## 一、许可范围

| 范围 | 许可 |
|---|---|
| `lib/`、`cordis.patch.yml`、`package.json`、文档与维护脚本 | **MIT**（见 `LICENSE`） |
| `icon.png`（插件列表图标） | **不适用 MIT**：与 `assets/` 下的美术素材同属"原样提供"，仅用于标识本插件；不授予再许可，也不声明为原创作品。 |
| `assets/**`（图片 / 动图 / 音效） | **不适用 MIT**：由维护者提供或使用 AI 工具生成，按 **as-is** 随插件分发，仅用于运行本插件；不授予再许可，也不声明为原创作品。 |

这样划分的原因：代码可以明确授权，而美术素材的来源与权利状态往往无法百分之百举证 —— 与其给一个站不住的授权，不如如实标注范围，并承诺收到权利主张就处理（见第四节）。

## 二、逐项来源

| 文件 | 来源 / 说明 |
|---|---|
| `DSniang1.png`（鲸鱼本体，气泡由代码绘制） | **AI 工具生成**的图像，经人工挑选与裁切。生成工具与原始出处**已不可考**（文件内元数据已被剥离，见第三节）。 |
| `icon.png`（插件列表图标，256×256 PNG 含透明） | 由现有素材裁切 / 缩放而来（源头同 `DSniang1.png` 系列，AI 工具生成、出处不可考）。已剥离全部内嵌元数据，块序列仅 `IHDR / IDAT / IEND`。 |
| `DSniang02.png` | 同上（备用整图，兼容旧版手动安装路径）。 |
| `DSH2.png`（README 顶部展示图） | 由维护者自行设计与排版（使用在线设计工具），2026-09 替换为清理版（已剥离全部内嵌元数据）。 |
| `rua.gif`、`bubble-petpet.gif` | 内置动图素材。 |
| `bubble-money1.gif` | 内置泡泡图（余额预警默认内容的配图）。 |
| `Ya1.mp3` / `Ya2.mp3`、`D1.mp3` / `D2.mp3` | 内置音效（按压 / 松开）。 |
| `minecraft-exp-orb.wav`、`task-end-a.wav` | 内置任务结束音（Minecraft·经验球 / 预设 A）。 |

## 三、元数据清理

图片素材曾内嵌过设计工具的 XMP 归属信息（工具名、模板名、账号 id，甚至第三方品牌名）。自 **0.3.1** 起，随包 PNG **一律剥离** `eXIf` / `iTXt` / `tEXt` / `zTXt` 元数据块，只保留渲染必需的 `IHDR` / `sRGB` / `gAMA` / `pHYs` / `IDAT` / `IEND`。

- 复核：解析每个 PNG 的块序列，确认不再有文本 / EXIF 块；
- 剥离：逐块重写，不触碰像素数据（IHDR/IDAT/IEND 原样保留），因此画面完全不变。

## 四、权利主张 / Takedown

如果你认为 `assets/` 中有素材侵犯了你的权利，请在本仓库开一条 issue，说明**文件名**与**依据**，我们会在核实后**立即替换或移除**，不附加其它条件。我们也欢迎直接提供可自由再分发的替代素材。

---

# fork 增补：dsh-whale-pig-widget

本仓库是 [`dsh-whale-widget`](https://github.com/MeteorNOX/DeepSeek-Balance-Whale-Widget) `0.4.2` 的 fork，
**上游 `assets/` 全部原样保留**（来源与许可范围同上文第一～四节，未作任何改动）。

新增内容只有以下四项，均由 fork 作者提供：

| 文件 | 说明 | 许可 |
|---|---|---|
| `assets/builtin/pig.gif` | 小猪·待机（三态之一，256×256 / 128 色 / 51 帧） | 同 `assets/` 规则：as-is 随插件分发，不授予再许可 |
| `assets/builtin/pig-busy.gif` | 小猪·干活（吃饲料，18 帧） | 同上 |
| `assets/builtin/pig-sleep.gif` | 小猪·打盹（趴着睡，20 帧） | 同上 |
| `assets/builtin/pig-oink.wav` | 猪叫一声（点击音效） | 同上 |

这些文件由 fork 作者自备素材经缩放与调色板压缩而来（512×512 → 256×256，无外部素材、无第三方字体或图库）。
如需替换为自己的宠物，覆盖同名文件即可。

`lib/index.js` 中 fork 新增的代码（`ensureBuiltinPig()` 及其播种逻辑、`/dsh-whale/running.json` 路由、
三态变体识别）按 MIT 授权，© 2026 KIM。
