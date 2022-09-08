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

### 安装
# 笔记
HKI 4 没有直接的升级路径，HKI 5 的编写方式非常相似，但偏差太大，无法进行体面的升级。 HKI 4 用户应该重新开始。如果您是新用户，这不适用于您，您可以继续进行文档的下一步。

还有一个可用的视频指南 [这里](https://www.youtube.com/playlist?list=PLezjWQmPsNpF9zNbWAXfm3mcnDwFYLdpT)，但始终建议您将文档放在手边，因为视频的老化速度很快！

# 建议
- 安装 Home Assistant 或创建当前设置的备份。我会建议您在干净的 Home Assistant 安装上安装它，尽管这不是必需的。
- 将所有已知设备添加到 Home Assistant（如果集成可用，首选方法是使用它而不是手动放入。
- 在 UI 中创建人员实体转到配置>人员并创建您家中的所有人员。通过下拉菜单将您拥有的 device_trackers 添加到人员实体。还将 entity_picture 添加到实体中，以便您的实体看起来更好，并且您将获得个性化的个人资料按钮。

# 要求
- 如果您还没有，请在 HA 安装的根目录中创建一个 secrets.yaml 文件。在该文件 `alarm_code: 123456` 中的任何行上添加以下行。您可以将代码更改为您想要的任何数字。不要跳过这部分，否则 HKI 将无法启动。
- 安装 HACS https://hacs.xyz/docs/installation/manual
- 安装下面的所有卡/组件。

### HACS
以下是运行 Homekit Infused 所需的所有插件的列表，您可以通过 HACS 安装所有插件。
| 名称 | 类型  | 说明 |
|----------------------------------|-------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Auto Entities](https://github.com/thomasloven/lovelace-auto-entities) | Frontend | 这张卡很方便快速填写某些域/实体 |
| [Card Mod](https://github.com/thomasloven/lovelace-card-mod) | Frontend | 这个mod允许在任何卡片甚至堆栈上自定义css |
| [Button Card](https://github.com/custom-cards/button-card) | Frontend | 这是整个设置过程中使用的按钮，**警告：请务必选择 `Show Beta Versions` 并选择最新版本！** |
| [State Switch](https://github.com/thomasloven/lovelace-state-switch) | Frontend | 这用于使卡片基于某些条件出现，如条件卡片但更好 |
| [Card Tools](https://github.com/thomasloven/lovelace-card-tools) | Frontend | 这是运行各种自定义卡所必需的 |
| [Search Card](https://github.com/postlund/search-card) | Frontend | 一个易于使用的搜索卡 |
| [Swipe Card](https://github.com/bramkragten/swipe-card) | Frontend | 此卡主要用于滚动通知 |
| [Config Template Card](https://github.com/iantrich/config-template-card) | Frontend | 允许一些特定的模板，它是配置文件按钮所必需的 |
| [Fold Entity Row](https://github.com/thomasloven/lovelace-fold-entity-row) | Frontend | 允许实体卡有一行可以折叠/折叠 |
| [Text Input Row](https://github.com/gadgetchnnel/lovelace-text-input-row/) | Frontend | 允许文本输入行更宽 |
| [Layout Card](https://github.com/thomasloven/lovelace-layout-card) | Frontend | 布局需要这张卡，重要提示：阅读下面的注释 |
| [Browser Mod](https://github.com/thomasloven/hass-browser_mod) | Integration | Browser-mod 使浏览器更有用，并让我们有机会显示/创建自定义弹出窗口等等 |
| [Lovelace Gen](https://github.com/thomasloven/hass-lovelace_gen) | Integration | 这是设置中最重要的部分，没有这个 HKI 将无法工作！不要将此添加到您的 `configuration.yaml` 文件中，因为包含的包已经为您这样做了，如果您的 `configuration.yaml` 中已经有 `lovelace_gen:`，请删除或注释该行！ |
### 添加资源
在 HACS 中安装卡时会自动添加资源，但请务必通过 侧边栏 > 仪表板 > 资源 进行检查。 如果没有列出资源，请确保您手动添加它们或通过 HACS 重新安装它们（如果单击“重新下载”，您可以找到要添加的url，您不需要重新下载它们，但您可以使用该URL手动添加资源）。

如果您看不到资源选项卡，请在 侧边栏 > 个人资料 中将您的个人资料设置为“高级模式”！

### 安装
下载项目，您可以从 [这里](https://github.com/jimz011/homekit-infused/releases) 获取最新版本。
将以下文件/文件夹复制到 Home Assistant 安装的根目录

- 将 `/hki-base/` 文件夹复制到安装程序的根目录
- 将 `/hki-user/` 文件夹复制到安装程序的根目录
- 将 `/packages/` 文件夹复制到设置的根目录
- 将以下行添加到您的 `configuration.yaml` 文件中

```yaml
homeassistant:
  packages: !include_dir_named packages/
```

或者，您可以将图像文件夹添加到您的设置中（它有一些您可能想要使用的有用图像）：
- 将 `/www/` 文件夹复制到设置的根目录

**注意：** packages 文件夹有 2 个额外的文件夹，名为 `homekit-infused-theme` 和 `homekit-infused-extra`，这两个软件包是可选的，如果您不想使用 HKI 中的高级主题选项或 HKI 可以为您创建的额外传感器。

## 这样！ 您已成功安装 Homekit Infused！ 现在继续配置它 :P

### 额外的信息
#### Dwains Dashboard！

如果你碰巧有 [Dwains Dashboard](https://github.com/dwainscheeren/dwains-lovelace-dashboard) 你必须在 Homekit Infused 配置文件中注释掉一行。

您必须继续进行以下更改，每次 HKI 更新时都必须重复此更改！ 您必须注释（或删除）以下行。
```yaml
# in /packages/homekit_infused/hki_configuration.yaml
lovelace_gen: !include_dir_merge_named ../../hki-user/config/
```

这是第 1 行，更改后应如下所示

```yaml
# lovelace_gen: !include_dir_merge_named ../../hki-user/config/
```

完成此更改后重新启动 Home Assistant！
