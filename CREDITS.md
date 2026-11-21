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

## 引擎声（`assets/audio/sr3/`）
- **Stunt Rally 3** 的水平对置四缸采样 `su-ss-1…8.wav`、`su-oe-1…8.wav`，作者 **CryHam**，许可 **CC BY 4.0**
  （http://creativecommons.org/licenses/by/4.0/）。用 engine-sim 在每 1000 rpm 稳态录制后在 Audacity 里剪辑、均衡。
  来源：https://github.com/stuntrally/stuntrally3 （`data/sounds/engines`，说明见同目录的 `_sounds.txt`，已一并放入）。
  文件未改动；游戏里按转速交叉淡化并变调。
- 电机声（`ev_lo/mid/hi.wav`）由 `tools/gen_audio.py` 合成。

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

## Map data being evaluated: PLATEAU Fukuoka

`_map_src/plateau/` (not in the build yet) holds eight CityGML files of central Fukuoka — buildings and roads of the
standard meshes 50303302 / 50303303 / 50303312 / 50303313 (Tenjin, Nakasu, Hakata) — taken from
"3D都市モデル（Project PLATEAU）福岡市（2024年度）", Ministry of Land, Infrastructure, Transport and Tourism of
Japan, https://www.geospatial.jp/ckan/dataset/plateau-40130-fukuoka-shi-2024 . Open data under the PLATEAU site
policy (CC BY 4.0-compatible terms; attribution: 国土交通省 Project PLATEAU). Only these files were fetched from the
993 MB archive (by byte range, 5.9 MB).

## Not used: `bst_fukuoka`

The Assetto Corsa track pack Berry supplied was inspected with `tools/kn5.py` and not converted: its textures and part
of its vertex data are encrypted for Custom Shaders Patch (the author's protection), and its material and texture
names indicate it is a port of a commercial game's city. Nothing from it is in this project.
