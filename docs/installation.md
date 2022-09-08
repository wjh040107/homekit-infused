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
| Name | Type  | Description |
|----------------------------------|-------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Auto Entities](https://github.com/thomasloven/lovelace-auto-entities) | Frontend | This card is handy to fill certain domains/entities very quickly |
| [Card Mod](https://github.com/thomasloven/lovelace-card-mod) | Frontend | This mod allows for custom css on any card and even stacks |
| [Button Card](https://github.com/custom-cards/button-card) | Frontend | This is the button used throughout the entire setup, **WARNING: MAKE SURE YOU SELECT, `Show Beta Versions` AND SELECT THE LATEST VERSION!** |
| [State Switch](https://github.com/thomasloven/lovelace-state-switch) | Frontend | This is used to make cards appear based on certain conditions, like a conditional-card but better |
| [Card Tools](https://github.com/thomasloven/lovelace-card-tools) | Frontend | This is needed for various custom cards to run |
| [Search Card](https://github.com/postlund/search-card) | Frontend | An easy to use search card |
| [Swipe Card](https://github.com/bramkragten/swipe-card) | Frontend | This card is mainly used for the scrolling notifications |
| [Config Template Card](https://github.com/iantrich/config-template-card) | Frontend | Allows for some specific templating, it is required for the profile button |
| [Fold Entity Row](https://github.com/thomasloven/lovelace-fold-entity-row) | Frontend | Allows entities cards to have a row that can be folded/collapsed |
| [Text Input Row](https://github.com/gadgetchnnel/lovelace-text-input-row/) | Frontend | Allows text input rows to be much wider |
| [Layout Card](https://github.com/thomasloven/lovelace-layout-card) | Frontend | This card is needed for the layout, IMPORTANT: Read the note below |
| [Browser Mod](https://github.com/thomasloven/hass-browser_mod) | Integration | Browser-mod makes the browser more useful and gives us the opportunity to show/create custom popups and many more! |
| [Lovelace Gen](https://github.com/thomasloven/hass-lovelace_gen) | Integration | This is the MOST important piece of the setup, without this HKI will not work! Don't add this to your `configuration.yaml` file as the included package already does so for you, if you already have `lovelace_gen:` in your `configuration.yaml` please remove or comment that line! |

### Adding Resources
Resources are added automatically when the card gets installed within HACS, but to be sure check them through `Sidebar > Lovelace Dashboards > Resources`. If there are no resources listed, make sure you either add them manually or reinstall them through HACS (you can find the url to add if you click on `redownload`, you do not need to redownload them, but you can use the URL's to add the resources manually if needed).

If you can't see the resources tab, set your profile to `advanced mode` in `Sidebar > Profile`!

### Installation
Download the project, you can grab the latest release from [here](https://github.com/jimz011/homekit-infused/releases).
Copy the following files/folders to the root of your Home Assistant installation

- Copy the `/hki-base/` folder to the root of your setup
- Copy the `/hki-user/` folder to the root of your setup
- Copy the `/packages/` folder to the root of your setup
- Add the following lines to your `configuration.yaml` file

```yaml
homeassistant:
  packages: !include_dir_named packages/
```

Optionally you can add the images folder to your setup (it has some useful images that you might want to use):
- Copy the `/www/` folder to the root of your setup

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

Restart Home Assistant after you have done this change!
