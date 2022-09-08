# Homekit Infused 5

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
# views.yaml (示例最小配置)
  living_room:
    icon: mdi:floor-lamp
```
```yaml
# views.yaml (带有自定义标签的示例)
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

| 名称 | 必需 | 默认 | 说明 |
|----------------------------------|-------------|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 'object' | yes | none | 设置视图的名称、路径和标题，这不是实际属性，而是视图的第一行，*注意：这不能包含特殊字符，只能使用小写字符！* |
| title | no | view_name | 设置视图的标题，如果未定义，则将使用视图的名称，不能使用模板作为标题 |
| subtitle | no | undefined | 设置字幕文本，这接受 [JS 模板](https://github.com/custom-cards/button-card#javascript-templates)，如果不设置字幕，它将显示默认通知 |
| icon | no | mdi:home | 设置导航栏、快捷按钮和字幕的图标，这也接受FA图标，您可以使用 [JS 模板](https://github.com/custom-cards/button-card#javascript-templates)，只要您不将此图标设置为显示在导航栏中 |
| show_header | no | subtitle | 设置为 true 以在此视图上完全隐藏标题 |
| show_in_favorites | no | false | 如果希望此视图自动包含在收藏夹插件中，请将其设置为 `true` |
| show_in_menu | no | undefined | 这将强制在菜单插件中显示视图，这在使用 `menu:` 或 `view_selector:` addon 时非常有用 |
| button_label | no | no label | 设置按钮标签文本，这接受 [JS 模板](https://github.com/custom-cards/button-card#javascript-templates) |
| button_badge | no | undefined | 这将为菜单和收藏夹按钮设置一个bagde，它将始终显示输入实体的状态，您可以使用任何实体_id (例如. `sensor.current_temperature`) |
| show_in_navbar | no | false | “设置为true”如果您希望此视图在导航栏中可见，这与菜单不同 |
| visible | no | undefined | 这将仅为某些用户显示导航栏图标，这仅反映 `show_in_navbar` 为 `true` 时，这必须定义为列表！查看[官方文件](https://www.home-assistant.io/lovelace/views/#visible)更多信息。注意：任何用户仍然可以访问URL |
| [addons](addons.md) | no | undefined | 若要在视图中添加一个插件，请参阅[Addons](addons.md)部分以获取文档 |
| [layout](addons/layout.md) | no | undefined | 更改视图布局，请参阅[Layout](addons/layout.md)部分的文档 |
| [view_selector](addons/view-selector.md) | no | undefined | 将view_selector添加到视图顶部，请参阅[View Selector](addons/view-selector.md)以获取文档 |
| [custom_legacy](addons/custom-legacy.md) | no | undefined | 禁用所有插件并在视图上使用完整的YAML样式，有关文档，请参阅[Custom Legacy](addons/custom-legacy.md)部分 |

```yaml
# views.yaml (例子)
  kitchen:
    subtitle: 我的厨房
    button_badge: sensor.kitchen_temp
    icon: mdi:fridge
    show_in_navbar: true
    show_in_favorites: true
```

# 通用配置

以下项目可以在 `/hki-user/config/config.yaml` 中找到。 默认情况下，这些设置是为您预定义的，但其中一些可以根据您自己的喜好进行编辑。 这不是运行 HKI 的必需步骤，但您将来需要编辑其中的一些。

| 名称 | 说明 |
|--------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [alarm警报](addons/alarm.md) | 更改标题中警报徽章的行为/弹出 |
| [header页眉](addons/header.md) | 更改页眉徽章和/或是否全局显示通知 |
| [popups弹出窗口](addons/popups.md) | 更改弹出窗口中关闭按钮的位置并更改 RGB 灯光弹出窗口中的颜色 |
| [profile人员资料](addons/profile.md) | 更改配置文件菜单的内容，您可以根据每个用户设置配置文件菜单 |

# Other Config

| 名称 | 说明 |
|--------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Device Counters设备计数器](addons/device-counters.md) | 为您设置计算设备的实体，这是推荐的步骤 |
| [Find My查找我的](addons/find-my.md) | 按照此部分设置您的 find_my 页面 |
| [Notifications通知](addons/notifications.md) | 设置通知以显示在标题的副标题中 |
| [Splitting the config拆分配置](splitting-the-config.md) | 这将向您展示如何将 views.yaml 文件拆分为多个单独的文件，并向您展示如何组织代码 |
| [Theming主题](addons/themes.md) | 如何像绝地大师一样编辑HKI的外观？ |

＃ 提示与技巧

HKI 加载后的性能非常快，应该非常稳定。然而，使用大量插件的大型设置会对启动时间产生巨大影响。这仅适用于启动 Home Assistant。大型设置最多可能需要 3 分钟才能重新启动。
Lovelace 重新加载时间取决于设置大小，对于大型设置，将在 5 到 40 秒之间变化。

如前所述，这只会影响启动时间，不会影响 Home Assistant 的任何其他功能，也不会在加载后减慢您的界面。

显然，如果您每次都必须编辑设置并重新启动，这会让您发疯。要解决这个问题，您应该一个一个地编辑/创建视图！注释掉您完成的视图（除了主页视图，这很重要！）并重新启动。您会发现重新启动只需几秒钟，这使您可以超级快速地编辑仪表板。一旦您的视图完成并经过测试，您可以将其注释掉并创建下一个视图。完成所有视图后，只需取消注释您创建的视图并重新启动。

### 更多示例
我可以永远继续使用示例，但最好只查看我在 [在这里](https://github.com/jimz011/homekit-infused/tree/5.x.x-personal) 上的示例配置
