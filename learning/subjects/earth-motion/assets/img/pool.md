# 地球运动 图片库索引

> 本文件是课件挑图的**唯一检索入口**：`lesson-design` 与课件只读这里，不翻目录。
> `来源 URL` 写图片所在**页面**的地址，`许可` 抄页面标注（页面没写填「未标注」）——课件 `figcaption` 的来源与许可由渲染器按本表自动补。
> 图片库目录（本文件的兄弟）：`assets/img/pool/`。

| 文件 | 主题标签 | 一句话说明 | 来源 URL | 许可 | 尺寸 | 抓取日期 |
|---|---|---|---|---|---|---|

## Gaps

### 已确认的解法：PDF 渲染管线（总控负责，采图角色不必再试）

网页上取不到的四类图（黄赤交角与直射点回归运动、晨昏线（圈）与昼夜长短、正午太阳高度与竿影、太阳视运动与日出日落方位/天球与地平坐标），**官方图其实都在 PDF 里，且已实测可渲染**：

- 引擎自带 `dsoffice render`（LibreOffice + PDFium）可把 PDF 渲染成 PNG：`ELECTRON_RUN_AS_NODE=1` + `node.cmd 'F:\deepseek\DSH Desktop\resources\office-cli.mjs' render --input <pdf> --output-dir <dir>`（默认 144 dpi，可用 `--max-image-resolution` 调低）。
- 实测样例：香港天文台《太陽周年路徑圖（簡略版）》（`2026simp-paths-sun.pdf`）→ 1191×1684 PNG，内容为夏至/春秋分/冬至三条日弧、北南东西方位、日出日落点与香港位置，正是「太阳视运动与日出日落方位」节点的官方配图。144 dpi 输出 600 KB（超本库 500 KB 上限），入库前需按更低 dpi 重渲。
- 后续需要官方图时由总控渲染并登记入本索引，**不再派采图角色重复尝试网页抓取**。

### 后续进展：讲解角色已自产内联示意图（2026-10-05 记录，第 2 课）

上一条 Gaps 点名的四类图，**第 2 课（`motion.basics`）已用内联 `::: svg` 自行画出其中两类，均不落库**（内联图随课件出厂，不进 `pool/`，索引无需登记）：

- 自转决定昼夜交替与地方时（北极上空俯视图：地轴、赤道、平行阳光、晨昏圈、昼夜半球、自转方向）——见 `lessons/0002-motion.basics.md`。
- 公转与地轴指向不变（椭圆轨道俯视图：太阳、二至二分四个位置、四个位置互相平行的地轴、黄道面、公转方向）——见同文件。

因此这两类图**不必再走 PDF 渲染或网页采集**。仍未覆盖的两类是：**正午太阳高度与竿影**（第 6 课用）、**太阳视运动轨迹与日出日落方位／天球与地平坐标**（第 10—11 课用）；届时要现成官方图，仍按上面的 `dsoffice render` 链路从 HKO 年曆 PDF 渲出并登记本索引。

### 本轮未入库的原因（逐条）

本轮**一张图都没能入库**（图片库为空，索引只有表头）。逐条记原因：

- **缺：全部来自 Wikimedia Commons 的候选图——站点连不上。** Commons 是总控指定的首选图源（`Category:Earth's orbit`、`Category:Celestial spheres`、`Category:Sun paths`、`Category:Analemma`、`Category:Sundials` 等分类页与站内搜索），但本轮 4 次探测全部失败：`commons.wikimedia.org` HTTPS 握手超时 / 远程主机强迫关闭连接，HTTP 同样握手超时，`commons.m.wikimedia.org` 连接超时，`upload.wikimedia.org`（Commons 的图片文件服务器）握手超时。**不是图的问题，是整站不可达**——换分类、换下钻层级都无意义。连不上的还有 `zh.wikipedia.org`（连接超时，与总控上次结论一致，已按要求只试一次）。
- **缺：香港天文台官方太阳路径图与年历插图——页面无静态位图。** 点名的 `my.weather.gov.hk/.../SunPathDay3_ue.htm`（互动版太阳路径图）、`www.hko.gov.hk/.../Sun_Transit.htm`（日上中天）、`sun_ra_dec.htm`（太阳视赤经与视赤纬）三页均**返回 200 但页内 `<img>` 数为 0**：路径图是脚本动态渲染的 SVG，数据靠 AJAX 取，属规格第 2 条"不抓动态加载"。点名的一整组 HKO 官方图（年曆 2026 全文、太阳周年路径图简略版、二十四节气表）都是 `application/pdf`（200 可下载，但**抓 PDF 不在本角色范围内**，规格第 2 条明令不抓）。
- **缺：MIT 12.540 Lecture 4 讲义里的球面三角与坐标类型插图——图在 PDF 里。** PDF 本体可达（200，1.7 MB），但讲义插图只能靠 PDF 渲染或 OCR 才拿得到，抓 PDF/OCR 都不是本角色的活；OCW 课程页与 Lecture Notes 页只有站徽、社交图标与一张卫星轨道示意图（与本科目学习主题无关），无可用内容图。
- **缺：Wolfram MathWorld 的球面三角形示意图——只有矢量原图，格式不在图片库允许清单内。** 点名的 `SphericalTrigonometry.html` 与站内下钻到的 `SphericalTriangle.html`、`Sphere.html` 三页，「有意义的插图」各只有 1 张，**全部是内联 SVG**（页面其余 `<img>` 是页头菜单、内联公式与 logo，均已过滤）。已下载并核过：

  | 原图 | 自然尺寸 | 体积 | 说明 |
  |---|---|---|---|
  | `mathworld.wolfram.com/images/eps-svg/SphericalTriangle.svg` | 196.75×200.06 pt | 177 KB | 球面三角形：三个顶点、三条大圆弧边与三个球面角 |
  | `mathworld.wolfram.com/images/eps-svg/sphere.svg` | 188.1×187.34 pt | 224 KB | 球面与截面圆（讲「大圆与球面距离」可用） |
  | `mathworld.wolfram.com/images/eps-svg/SphericalTrig.svg` | 86.65×83.97 pt | 15 KB | 太窄，本就不过 400 px 门槛 |

  两条硬约束把它们挡在库外：**① `scripts/check_pool.py` 的允许扩展名只有 png/jpg/jpeg/webp/gif，`.svg` 一律判"文件名不合规"**（本机无 LibreOffice/PDFium/ImageMagick/Inkscape，转格式要装工具，越界）；**② 自然宽度 189–197 pt（约 250–262 px）不到 400 px 门槛**，而"不缩放、不合成"是硬边界。三张原图已留在科目 `.stage/image-scout/`（`mw-triangle.svg` 177174 B、`mw-sphere.svg` 224305 B、`mw-sphericaltrig.svg` 15579 B；SHA-256 前缀依次 `27a845c9…`、`1cddb9c7…`、`af03269e…`），总控若要，可让讲解角色按「配图」规格自行产图。
- **缺：NOAA 页面的可用插图。** `gml.noaa.gov` 点名的 `calcdetails.html` 与站内下钻的 `solcalc/`、`solcalc/sunrise.html` 三页里 `<img>` 只有美国国旗、gov 徽标、NOAA 徽标与三个**蒙气差公式小图**（`ar_eq1–3.gif`，宽约 100–200 px，不到门槛，且属公式截图不是示意图），无内容示意图。
- **缺：人教社官方插图——站点维护中。** `www.pep.com.cn/gzdl/` 返回 200，但正文是一张"系统升级维护公告"占位页（5 秒后跳首页），无教材插图可取，与资源清单里记的状态一致。
- **缺（下游用图建议）**：本科目最需要的四类图——黄赤交角与直射点回归运动、晨昏线（圈）与昼夜长短、正午太阳高度与竿影、太阳视运动轨迹与日出日落方位／天球与地平坐标——本轮**一张都没有**落到库里。课件若要配图，只能走讲解角色的「配图」路线自行产图；若要补抓现成图，前提是先解决 Commons（首选图源）的可达性，或让总控确认 PDF 渲染链路（HKO 年曆的太阳周年路径图详略两版、MIT 讲义插图都在 PDF 里，渲染出来即是官方图）。
- **未覆盖的入口**：本轮未碰任何清单外站点与站内搜索页；Commons 因整站不可达，其分类页与站内搜索一页都没取到。
