# Homekit 注入 5

＃＃ 内容
- [简介](index.md)
- [安装](installation.md)
- [配置](configuration.md)
- [插件](addons.md)
- [更新](updates.md)
- [问题和问题](issues.md)
- [关于我](about.md)
- [谢谢](thanks.md)

＃＃ 配置
在 Homekit Infused 中，为内置插件或自定义卡片设置和配置视图非常容易。不要忘记阅读本页末尾的提示和技巧部分！

*注意：要使以下配置中的任何更改生效，您必须重新启动 Home Assistant！

### 设置视图
Homekit Infused 是一个 YAML 风格的仪表板，因此您必须通过 YAML 文件对其进行配置。为了简单起见，Homekit Infused 主要通过单个文件 `/hki-user/config/views.yaml` 进行管理，您应该使用该文件来编辑 Homekit Infused。

开始打开上述文件。您会发现已经为您配置了 2 个视图，但任何新视图或对已包含视图的更改都应在此文件中完成。

要创建新视图，您必须设置一个对象（在本例中为房间名称）以启动新视图。这是你新观点的第一行。

```yaml
# views.yaml (example minimal configuration)
  living_room:
    icon: mdi:floor-lamp
```
```yaml
# views.yaml (example with custom subtitle)
  living_room:
    subtitle: Overview
    icon: mdi:floor-lamp
```

上面的示例将为您创建一个名为 客厅 的视图，并自动执行以下操作：
- 设置视图的标题（在本例中为客厅）
- 设置浏览器使用的视图路径（在本例中为 https://hassio.local/homekit-infused/living_room）
- 为导航栏、副标题和菜单/收藏夹按钮设置图标
- 在菜单中创建一个条目

这是为您提供全新视图的最低要求，但是如果没有任何其他代码，该视图将是空的。 Homekit Infused 能够为您填充视图、使用自定义用户代码或同时使用两者。 以下是您可以添加到视图中的所有视图选项，以完全根据您的喜好自定义每个视图。

| Name | Required | Default | Description |
|----------------------------------|-------------|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 'object' | yes | none | Sets the name, path and title of the view, this is not an actual property but the first line of your view, *NOTE: This can NOT contain special characters, use lowercase characters only!* |
| title | no | view_name | Set the title of the view, if undefined it will use the name of the view instead, you can NOT use templates for the title! |
| subtitle | no | undefined | Set the subtitle text, this accepts [JS templates](https://github.com/custom-cards/button-card#javascript-templates), if you don't set a subtitle it will show the default notifications instead |
| icon | no | mdi:home | Set the icon for the navigation_bar, shortcut buttons and subtitle, this also accepts FA icons, you can use [JS templates](https://github.com/custom-cards/button-card#javascript-templates) as long as you don't set this icon to show in the nav_bar |
| show_subtitle | no | subtitle | Set to show the header subtitle to true or false |
| show_in_favorites | no | false | Set to `true` if you want this view to be auto included in the favorites addon |
| show_in_menu | no | undefined | This forces a view to be shown in the menu addon, this is useful when using the `menu:` or `view_selector:` addon |
| button_label | no | no label | Set the button label text, this accepts [JS templates](https://github.com/custom-cards/button-card#javascript-templates) |
| button_badge | no | undefined | This will set a bagde for the menu and favorites button, it will always show the state of an entered entity, you can use any entity_id (e.g. `sensor.current_temperature`) |
| show_in_navbar | no | false | Set to `true` if you want this view to be visible in the navigation_bar, this is not the same as the menu! |
| visible | no | undefined | This will show the nav_bar icon only for certain users, this only reflects if `show_in_navbar` is `true`, this MUST be defined as a list! Check out the [Official Documentation](https://www.home-assistant.io/lovelace/views/#visible) for more information. NOTE: The URL will still be accessible for any user! |
| [addons](addons.md) | no | undefined | Add an addon to your view, refer to the [Addons](addons.md) section for documentation |
| [layout](addons/layout.md) | no | undefined | Change your views layout, refer to the [Layout](addons/layout.md) section for documentation |
| [view_selector](addons/view-selector.md) | no | undefined | Add a view_selector to the top of your view, refer to the [View Selector](addons/view-selector.md) section for documentation |
| [custom_legacy](addons/custom-legacy.md) | no | undefined | Disable all addons and go full YAML style on your views, refer to the [Custom Legacy](addons/custom-legacy.md) section for documentation |

```yaml
# views.yaml (example)
  kitchen:
    subtitle: My Kitchen
    button_badge: sensor.kitchen_temp
    icon: mdi:fridge
    show_in_navbar: true
    show_in_favorites: true
```

# 通用配置

以下项目可以在 `/hki-user/config/config.yaml` 中找到。 默认情况下，这些设置是为您预定义的，但其中一些可以根据您自己的喜好进行编辑。 这不是运行 HKI 的必需步骤，但您将来需要编辑其中的一些。

| Name | Description |
|--------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [alarm](addons/alarm.md) | Change the behaviour/popup of the alarm badge in the header |
| [header](addons/header.md) | Change the header badges and/or whether or not to show the subtitle globally |
| [popups](addons/popups.md) | Change the location of the close button in popups and change the colors in RGB light popups |
| [profile](addons/profile.md) | Change the contents of the profile menu, you can set the profile menu on a per user basis |

# Other Config

| Name | Description |
|--------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Device Counters](addons/device-counters.md) | Setup entities that count devices for you, this is a recommended step |
| [Find My](addons/find-my.md) | Setup your find_my page by following this section |
| [Notifications](addons/notifications.md) | Setup notifications to show in the subtitle of the header |
| [Splitting the config](splitting-the-config.md) | This will show you how to split up the views.yaml file into multiple separate files and show you how to organize code |
| [Theming](addons/themes.md) | How to edit the appearance of HKI like a Jedi Master? |

＃ 提示与技巧

HKI 加载后的性能非常快，应该非常稳定。然而，使用大量插件的大型设置会对启动时间产生巨大影响。这仅适用于启动 Home Assistant。大型设置最多可能需要 3 分钟才能重新启动。
Lovelace 重新加载时间取决于设置大小，对于大型设置，将在 5 到 40 秒之间变化。

如前所述，这只会影响启动时间，不会影响 Home Assistant 的任何其他功能，也不会在加载后减慢您的界面。

显然，如果您每次都必须编辑设置并重新启动，这会让您发疯。要解决这个问题，您应该一个一个地编辑/创建视图！注释掉您完成的视图（除了主页视图，这很重要！）并重新启动。您会发现重新启动只需几秒钟，这使您可以超级快速地编辑仪表板。一旦您的视图完成并经过测试，您可以将其注释掉并创建下一个视图。完成所有视图后，只需取消注释您创建的视图并重新启动。

### 更多示例
我可以永远继续使用示例，但最好只查看我在 [here](https://github.com/jimz011/homekit-infused/tree/5.x.x-personal) 上的示例配置
