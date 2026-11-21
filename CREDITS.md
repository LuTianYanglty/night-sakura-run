# 署名与许可

## 角色立绘
- **FALLiNG_AiR** —— “character”套组（5 名角色、多表情），**CC0 1.0**（公有领域）。
  来源：https://opengameart.org/node/126911
  本项目把原图裁切并缩小到 1280 px 高后放在 `assets/characters/`，未做其他修改。
  CC0 不要求署名，这里仍然注明以示感谢。

## 车辆模型
- `assets/brz.glb` 由你电脑 `Downloads/Subaru BRZ 2022②` 里的模型减面转换而来（转换脚本在 HTML 版工程的 `tools/convert_brz.py`）。
  这个模型的授权取决于你当初下载它的来源——**在确认授权之前，请只在本地原型里使用，不要公开分发这个文件。**
  “Subaru”“BRZ”是 SUBARU CORPORATION 的商标，本原型与其无关。

- `assets/su7.glb` —— **“2025 Xiaomi SU7 Ultra”，作者 Ddiaz Design**（https://sketchfab.com/ddiaz-design），
  来源 https://sketchfab.com/3d-models/2025-xiaomi-su7-ultra-5fd4113db0a846a4884f575de60b298e ，
  许可 **CC BY-NC-SA 4.0**（署名 · 非商业 · 相同方式共享，http://creativecommons.org/licenses/by-nc-sa/4.0/）。
  本项目做了改动：按材质合并、减面（约 69 万面 → 21 万面）、只保留一只车轮并移到轮心、车灯按前后拆开、
  车漆 / 玻璃 / 饰件换成本项目的材质、内饰贴图转成 JPEG（脚本：`_model_src/su7/s2_process.py`）。
  改动后的 `su7.glb` 同样以 CC BY-NC-SA 4.0 提供；因此带着它的构建**只能非商业使用**。
  “Xiaomi”“SU7”是小米的商标，本原型与其无关。

### Roma（`assets/roma.glb`，只在本机，不随网页版发布）
由用户自己提供的 `2020 Ferrari Roma.blend` 转换（`tools/convert_roma.py`）。文件里没有署名和许可信息；从网格和贴图的命名看，
它是别人从一款商业赛车游戏里转出来的模型，版权属于原游戏的权利方。因此它只留在这台机器上做学校实验用：
不提交到公开仓库，不打进网页版。

## 引擎声（`assets/audio/sr3/`）
- **Stunt Rally 3** 的水平对置四缸采样 `su-ss-1…8.wav`、`su-oe-1…8.wav`，作者 **CryHam**，许可 **CC BY 4.0**
  （http://creativecommons.org/licenses/by/4.0/）。用 engine-sim 在每 1000 rpm 稳态录制后在 Audacity 里剪辑、均衡。
  来源：https://github.com/stuntrally/stuntrally3 （`data/sounds/engines`，说明见同目录的 `_sounds.txt`，已一并放入）。
  文件未改动；游戏里按转速交叉淡化并变调。
- 同一来源、同一许可的另外三套（已放入 `assets/audio/sr3/`，`scripts/sfx.gd` 里登记为 i6 / v8 / v12，目前还没有车在用）：
  直列六缸 `b-i6r-1…8.wav`、V8 `v8f-1…10.wav`、V12 `v12d-1…10.wav`。
- 电机声（`ev_lo/mid/hi.wav`）和电车的“运动声浪”两层（`ev_growl.wav` 低频咕噜声、`ev_space.wav` 和声嗡鸣）由
  `tools/gen_audio.py` 合成。

## 其余全部内容
城市、套件与轮毂网格、贴图、拉花、室内背景、其余音效与两段音乐、物理、界面、剧本，
均为本原型程序生成或专门编写，不包含第三方素材。

## 引擎与字体
- Godot Engine 4.6（MIT）。
- 界面文字使用系统字体（macOS 上为苹方 PingFang SC），工程里不包含字体文件。

## 参考
- 手感与改装结构参考了《Need for Speed》(2015) 的公开资料（官方 Handling 101、零件列表），未使用其任何素材。

## Fonts (bundled for the web build, `assets/fonts/`)

- `cjk_m.otf`, `cjk_b.otf`: Noto Sans CJK SC (Medium / Bold), cut down to the characters the game prints with
  `tools/subset_font.py`. © Adobe / Google, SIL Open Font License 1.1.
- `num.ttf`: Roboto Condensed Bold (static instance of the Roboto variable font). © Google, SIL Open Font License 1.1.

- `pad.ttf`: controller button icons, drawn by `tools/gen_padfont.py` for this project; the letters inside the
  icons are outlines of Inter ExtraBold (© The Inter Project Authors, SIL Open Font License 1.1).
- `gauge_brz.ttf`: built from Michroma Regular (© The Michroma Project Authors, SIL Open Font License 1.1) by
  `tools/subset_font.py`: Latin only, narrowed to 68 %, figures centred in one cell width, renamed "NSR Gauge BRZ"
  as a modified version; still under the OFL. Original in `tools/Michroma-Regular.ttf`; licence text in
  `gauge_brz_OFL.txt`. Source: https://github.com/google/fonts/tree/main/ofl/michroma — the BRZ cluster's numerals.
- `gauge_su7.otf`: Inter Display Medium, cut down to Latin and figures (© The Inter Project Authors, SIL Open Font
  License 1.1) — the SU7 cluster's numerals, standing in for Xiaomi's MiSans, which is not openly licensed.

On the desktop the game still uses the system fonts (PingFang SC, DIN Alternate) for text; the bundled files are the
fallback, except the icon and gauge fonts, which are always the bundled ones.

## Garage (`assets/garage.glb`, `assets/garage_*.webp`)

Converted from the "地下车库停车场" Blender scene supplied by Berry (`_garage_src/underground/`), with
`_garage_src/g_export.py`: modifiers and geometry-node instances realised, pipes decimated, node materials flattened to
one base-colour image each, textures reduced, everything joined into one mesh. The scene and its textures
(textures.com and others) are third-party; their licence terms were not included in the archive.

## Shading reference

The car paint / glass / reflection set-up follows the SU7 showroom demo (`su7-replica`): a near-mirror coat lit mainly
by what it reflects, the car carrying its own environment, bloom over a filmic tone map.

## Sky and tone

- `shaders/sky.gdshader`: an analytic clear-sky model written for this project — exact single scattering in a
  plane-parallel Rayleigh + haze atmosphere with an ozone term, using the relative air-mass formula of Kasten & Young
  (1989) as it appears in the Preetham-style skies of three.js and Godot (both MIT). No code was copied from them.
- Tone mapping is Godot's built-in AgX.
- The night look (wet bodywork, haze around the lamps, split-tone grade) follows *Need for Speed* (2015) as a visual
  reference only; none of its assets are used.

## Controller

- `tools/ds5trig/ds5trig.swift`: written for this project. It talks to the DualSense through Apple's GameController
  framework and through the controller's HID output report; the report layout follows the Linux kernel's
  `hid-playstation` driver, the adaptive-trigger effect encodings follow the community documentation of the
  controller's modes 0x21 / 0x25 / 0x26. "DualSense" and "PlayStation" are trademarks of Sony Interactive
  Entertainment; this project is not affiliated with Sony.

## 福冈地图（`assets/maps/fukuoka/`，`assets/city/`）

- **街道与建筑轮廓**：「3D都市モデル（Project PLATEAU）福岡市（2024年度）」，国土交通省，
  https://www.geospatial.jp/ckan/dataset/plateau-40130-fukuoka-shi-2024 。PLATEAU 站点政策下的开放数据（与 CC BY 4.0
  兼容；署名：国土交通省 Project PLATEAU）。只取了标准网格 50303302 / 50303303 / 50303312 / 50303313（天神、中洲、
  博多）的建筑和道路共 8 个 CityGML 文件（从 993 MB 的压缩包里按字节范围取出 5.9 MB，放在 `_map_src/plateau/`）。
  `tools/plateau_convert.py` 把它转成游戏用的 `map.json` + `map.bin`：数据里只有道路用地的轮廓和建筑的底面、高度，
  车道线、人行横道、路缘、人行道、路灯、行道树、招牌和挑战的位置都是转换脚本推出来的，不是实测。
- **路面、人行道、墙面材质**：**ambientCG**（https://ambientcg.com ，**CC0**）的 Road012A、Road013A、Asphalt033、
  Concrete034、Concrete046、Concrete008、ManholeCover009，由 `tools/city_textures.py` 缩放并打包成
  `assets/city/ground_*.dat`、`walls_*.dat`、`manhole_*.dat`。（另外下载了 Facade007–020 和 PavingStones142/152，
  看过之后没有用：前者是整栋摩天楼的远景贴图，后者是欧洲石板路。原始文件都在 `_assets_src/acg/`。）
- **行道树**：**Poly Haven** 的 Jacaranda Tree（https://polyhaven.com/a/jacaranda_tree ，作者 Rico Cilliers 等，**CC0**）。
  原模型约 300 万面，`tools/bake_tree.py` 用 Blender 把它从三个方向烘成颜色 + 镂空 + 法线，`tools/pack_tree.py` 打包成
  `assets/city/tree_*.dat`，作远景树（三张交叉的面片）。近景树用 `tools/bake_tree_parts.py` 从同一棵树上取出树干
  （减到 2600 面）和 8 张单团枝叶的图，`tools/pack_tree_parts.py` 打包成 `tree_trunk.dat`、`tree_bark.dat`、
  `tree_clumps.dat`、`tree_parts.json`。一部分街道把叶色换成了樱花色。
- **招牌**（`assets/city/signs.dat`）：`tools/gen_signs.py` 用 Noto Sans CJK（SIL OFL 1.1）画的，文字都是通用的行业
  或菜名，没有真实的商号。
- 窗户里的房间、店面、卷帘门是着色器里按视线算出来的（interior mapping），没有用贴图。
- **行人**：**Quaternius** 的 Animated Human（https://opengameart.org/content/animated-human-low-poly ，**CC0**）。
  `tools/bake_people.py` 用 Blender 把它的走、跑两个循环（外加一套右手举起撑伞的走）烘成顶点动画贴图：
  `assets/city/people_pos.dat`、`people_nrm.dat`、`people.json`。原模型是赤脚、单色贴图：脚改成了鞋，衣服、头发、
  肤色在着色器里按人配色。原始文件在 `_assets_src/people/`。雨伞、垃圾桶、路灯杆是代码里拼的。
- 行车用的是游戏里已有的两个车模（见上面的“车辆模型”），只是换了车漆。

## Not used: `bst_fukuoka`

The Assetto Corsa track pack Berry supplied was inspected with `tools/kn5.py` and not converted: its textures and part
of its vertex data are encrypted for Custom Shaders Patch (the author's protection), and its material and texture
names indicate it is a port of a commercial game's city. Nothing from it is in this project.
