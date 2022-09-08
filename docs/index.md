# Homekit Infused 5

## 内容
- [简介](index.md)
- [安装](installation.md)
- [配置](configuration.md)
- [插件](addons.md)
- [更新](updates.md)
- [问题和问题](issues.md)
- [关于我](about.md)
- [谢谢](thanks.md)

# 介绍
这是 Homekit Infused 5，一个完整的用于 Home Assistant 的 lovelace 仪表板解决方案。
简而言之，Homekit Infused 会将您的 Home Assistant 仪表板变成带有漂亮标题的 Homekit 样式变体，从而为您的仪表板提供更多平板电脑/手机应用程序样式。

注意：Homekit Infused 是一个 YAML 风格的仪表板，这意味着建议您对 YAML 有一个基本的了解。但是，如果您遵循文档/视频教程，您仍然应该能够创建仪表板。您应该能够毫不费力地创建一个漂亮的仪表板！

Homekit Infused 不会替换您现有的任何仪表板，因此您可以放心，安装 HKI 不会破坏您现有的任何仪表板。您可以将 Homekit Infused 与其他仪表板结合使用。

简而言之，Homekit Infused 5 包含以下所有内容以及更多内容！
- 难以说服您的伴侣使用 HA？ HKI有一个非常棒的WAF！
- 带有通知的漂亮标题，可按视图自定义，并自动为您添加到每个视图中。
- 一个可自定义的导航栏，也可以设置在屏幕底部。
- 一个自动创建的菜单。
- 只需定义视图名称、标题和图标，即可超级快速地创建新视图。只是这些行将创建一个新视图、一个菜单条目、一个导航栏按钮和图标以及一个标题，很酷吧？
- 2两个完全可定制的主题，您可以在其中实时更改 Homekit Infused 的整体外观！
- 通过创建脚本与 HKI 社区分享您自己创建的主题，最好的主题将添加到未来的 HKI 版本中！
- 许多预配置的插件，您可以添加到您的任何视图中，默认情况下，所有插件都经过预配置以快速创建仪表板。
- 自定义插件，允许您使用任何可用的核心或社区创建卡的家庭助理卡。
- 一个完全可定制的每个用户配置文件菜单。
- 一个完全可定制的警报面板。
- 众所周知，HKI 5 是记录最好的仪表板之一，也没有什么不同，甚至更好！
- 有经验的用户可以在每个视图的基础上完全自定义 YAML（这对于想要迁移的 HKI 3 和 4 用户特别有用）
- 轻松更新，每次更新复制/替换 2 个文件夹！
- 超快的前端，即使是大型设置（观看我的视频以查看它的实际效果）。
- 与 HKI 4 相比，超过 200 种新设置！
- 还有很多我的意思是更多！

### 在 YouTube 上关注我
[单击此处查看所有最新更新/视频](https://www.youtube.com/jimz011)

# 免责声明
警告：
- 对于因用户错误导致的任何数据丢失或缺陷，我概不负责。
- 此项目中使用的任何自定义卡片/组件都不是我制作的，所有学分都应归原作者所有。
- 此项目中使用的任何自定义卡/组件都有指向其原始存储库和创建者的链接。

# 我个人用于此设置的硬件
#### 计算机

- Intel i7 4790K
- 32GB DDR3 1600MHz RAM
- 9x HDD (6x 3TB, 2x 2TB, 1x 1TB)
- 2x SSD (1x 120GB, 1x 480GB)
- 使用的管理程序: Unraid
- Docker: 是
- VM's: 1 (Ubuntu)
- Docker 容器: 70+
- Home Assistant: Home Assistant Core 在Unraid的docker上运行

#### 手机和可穿戴设备
- Note 20 Ultra
- Z Fold 3 5G
- iPhone 5S
- Galaxy Watch 4 Classic x2

#### 其他
- Xbox One (2013)
- Playstation 2

#### 智能设备
- 6x Philips Hue dimmers (deCONZ controlled)
- 3x IKEA Tradfri remotes (deCONZ controlled)
- 1x Koogeek kh01cn hardware switch (connected through HA with Homekit Controller)
- 11x LED strips (around 70 meters in total) with MagicHome controllers (Flashed with ESPHome, varying from RGB to RGBWC)
- 14x Ikea Tradfri smart switches  (deCONZ controlled)
- 2x Ikea Tradfri bulbs (ranging from normals to color temperature ones)  (deCONZ controlled)
- 13x Philips Hue lights (ranging from filament to color temperature ones)  (deCONZ controlled)
- 3x Sonoff POW R2 (to monitor the washingmachine, dryer and dishwasher)
- 7x Sonoff Basic used as light or device switches (Flashed with ESPHome)
- 2x Sonoffs TH-16 (used to monitor temperature and humidity, but also doubles as a switch)  (Flashed with ESPHome)
- 1x TP-Link HS110 Energy Reading smart switch (to monitor the refrigerator)
- 4x Blitwolf SHP13 Energy Reading smart switch (to monitor the freezer and unraid server)
- 1x Honeywell smoke detector by Xiaomi  (deCONZ controlled)
- 6x Aqara door/window sensors by Xiaomi (3 used on doors, 3 on windows)  (deCONZ controlled)
- 3x Aqara temperature/humidity sensors by Xiaomi  (deCONZ controlled)
- 1x Xiaomi Roborock S55 (Rooted and flashed with Valetudo RE)
- 1x Apple TV 4K
- 1x Nvidia Shield TV Pro (2019)
- 2x Samsung smart TV
- 2x Google Nest mini's
- 1x Google Home mini
- 1x Google Home
- 4x Google Nest Hub
- 2x Aqara motion sensor by Xiaomi (deCONZ controlled)
- 3x IKEA Tradfri Motion sensors (deCONZ controlled)
- 1x Xiaofang Camera (rooted and flashed with Dafang Hacks)
- 1x Simple webcam (via motioneye)
- 1x deCONZ stick by Dresden Elektronic
- 1x Xiaomi Mija Gateway (Lumigateway version 3) (I only ever use this as speaker/light, no other devices are attached to this and it is cut off from the internet)
- 1x Xiaomi Aqara Airconditioning Companion (version 3) (I don't have a compatible airconditioner yet, though it does work as a switch and energy reader, not yet in my HA)
- 1x Xiaomi Aqara Cube (this device is actually better than I thought it would be, but because of the way our house is programmed it is just a fun object)
- 1x Unifi Dream Machine Pro
- 2x Unifi AP AC-Lite WiFI Access Points
- 2x Unifi Flex G3 Camera
- 2x Unifi Flex-Mini Switches
- 1x TP-Link Switch
- 1x Raspberry Pi B (running a failover AdGuard Server)
- A bunch of NFC stickers around the house

可能还有更多，但我现在想不起来  
