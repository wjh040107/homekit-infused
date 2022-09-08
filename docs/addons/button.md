# Homekit Infused 5

## 内容
- [简介](index.md)
- [安装](installation.md)
- [配置](configuration.md)
- [插件](addons.md)
- [更新](updates.md)
- [问题和疑问](issues.md)
- [关于我](about.md)
- [谢谢](thanks.md)

## Addons > Button

这个插件可以让你用非常强大的按钮来填充你的视图！

### HACS 要求

| 名称 | 类型  | 说明 |
|----------------------------------|-------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Light Popup Card灯光弹出卡](https://github.com/DBuit/light-popup-card) | 前端 | 这是按住/双击按钮时打开的弹出窗口，您需要在 HACS | 中手动添加此存储库 |
| [More Info Card更多信息卡](https://github.com/thomasloven/lovelace-more-info-card) | 前端 | 这是一张显示标准 HA 风格色轮和灯光弹出卡的卡片 |
| [Mini Graph Card迷你图卡](https://github.com/kalkih/mini-graph-card) | 前端 | 迷你图形卡提供了创建更高级图形的可能性！ |

**注意：** 这个插件只是一个预配置的 [custom:button-card](https://github.com/custom-cards/button-card) 模板。 您可以使用该卡中 99.9% 的可用选项，但是 HKI 有一些在该卡中找不到的额外选项/配置。

您可以使用以下任何选项来修改您的插件。

### 视图配置

| 名称 | 必须 | 默认 | 说明 |
|----------------------------------|-------------|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| title | 否 | 未定义 | 设置视图的标题，省略此行或设置 `title: hide` 将隐藏标题 |
| columns | 否 | 3 | 定义此视图将使用的列数 |
| square | 否 | true | 设置按钮是否应该是方形的，这仅在您在下面的配置中设置单个 aspect_ratios 时有用 |
| lock | 否 | false | 这会锁定整个视图，现在需要两次点击来打开/关闭，第一次点击解锁，第二次切换 |
| aspect_ratio | 否 | 1/1 | 一次设置此视图中所有按钮的纵横比 |
| [view_layout](layout.md#view-layout) | 否 | 未定义 | 这最好与 [layout](layout.md#view-layout) 插件一起使用，但也可以用于控制是否在不同的屏幕尺寸上显示此视图。 |
| type | 否 | 未定义 | 设置类型可以使堆栈有条件，此选项将只接受 `conditional` |
| conditions | 否 | 未定义 | 添加实体和条件，这将确定何时显示此插件，例如如果实体 x 已打开 `on` ，则显示此插件（参见 [addons](../addons.md) 示例 |
| entities | 是 | 实体清单 | 列出您想在此处显示的所有实体 |

### 按钮选项

默认情况下，您必须输入如下示例中的实体数组，这不需要额外的选项，只会获取全局 name/icon 。
您必须将其定义为对象才能使用以下选项。

| 名称 | 必须 | 默认 | 说明 |
|----------------------------------|-------------|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| entity | 是 | 未定义 | 设置使用的实体 |
| type | 否 | auto | 这会强制 HKI 将按钮视为特定类型，从而改变外观。在 `rgb`, `color-temp`, `switch` 或 `graph` 或 `fan` 之间进行选择。默认情况下，HKI 会尝试自行判断按钮的类型，但如果它弄错了，则通过设置 type类型强制它 |
| name | 否 | global_name | 为这个按钮设置一个名字，它接受 [JS 模板](https://github.com/custom-cards/button-card#javascript-templates) |
| label | 否 | 无 | 为这个按钮设置一个标签，它接受 [JS 模板](https://github.com/custom-cards/button-card#javascript-templates) |
| icon | 否 | global_icon | 为这个按钮设置一个图标，这个接受 [JS 模板](https://github.com/custom-cards/button-card#javascript-templates) |
| [state_display](https://github.com/custom-cards/button-card#javascript-templates) | 否 | 未定义 | 覆盖状态显示的方式，这接受 [JS 模板](https://github.com/custom-cards/button-card#javascript-templates) |
| entity_picture | 否 | global_entity_picture | 为该按钮设置实体图片，注意当在 customize.yaml 或此处设置实体图片时，它将优先于图标，除非您设置 `show_entity_picture: false` ，否则接受 [JS 模板](https://github.com/custom-cards/button-card#javascript-templates) |
| background_image | 否 | 未定义 | 将 URL 或 `/local/*` 设置为图像以显示为背景 |
| lock | 否 | false | 这将锁定此按钮，现在需要点击两次才能 on/off ，第一次点击解锁，第二次切换 |
| aspect_ratio | 否 | 1/1 | 为这个按钮设置一个自定义的 aspect_ratio，请注意，当设置 1/1 以外的任何内容时，您需要在堆栈配置中设置 `square: false` |
| size | 否 | 25% | 设置图标大小，请注意，由于使用了网格，此设置并不总是按预期工作，请尝试一下 |
| units | 否 | 未定义 | 覆盖或定义要在实体状态之后显示的单位。如果省略，则使用实体的单位 |
| button_badge | 否 | 未定义 | 在您的按钮中使用 HKI 预定义的徽章，您必须定义一个要使用的实体，您只能使用它的状态！ |
| icon_color_active | 否 | 未定义 | 当实体处于活动状态时，使用它来覆盖图标颜色，它接受 [JS 模板](https://github.com/custom-cards/button-card#javascript-templates) |
| icon_color_inactive | 否 | 未定义 | 使用它来覆盖默认图标颜色，它接受 [JS 模板](https://github.com/custom-cards/button-card#javascript-templates) |
| show_name | 否 | true | 选择显示/隐藏名称，设置为 `false` 隐藏它 |
| show_label | 否 | true | 选择显示/隐藏标签，设置为 `false` 隐藏它 |
| show_icon | 否 | true | 选择显示/隐藏图标，设置为 `false` 隐藏它 |
| show_state | 否 | true | 选择显示/隐藏状态，设置为 `false` 隐藏它 |
| show_last_changed | 否 | false | 选择显示/隐藏 last_changed 状态，设置为 `true` 以显示它，注意这将替换标签！ |
| show_live_stream | 否 | false | 如果设置了相机实体，则显示实时流而不是静止图像 |
| show_units | 否 | true | 选择显示/隐藏单位，设置为 `false` 隐藏它 |
| show_entity_picture | 否 | true | 选择显示/隐藏 entity_picture，设置为 `false` 隐藏它 |
| [confirmation](https://github.com/custom-cards/button-card#confirmation) | 否 | 未定义 | 显示确认弹出窗口。更多信息见 [官方文档](https://github.com/custom-cards/button-card#confirmation) 了解更多信息 |
| template | 否 | 未定义 | 默认情况下，此按钮将采用 HKI 默认样式，您可以设置 `template: empty` 将其清除并使用自己的样式 |
| [layout](https://github.com/custom-cards/button-card#Layout) | 否 | 未定义 | 可以使用此选项修改按钮的布局，您必须设置 `template: empty` 才能正常工作。更多信息见 [官方文档](https://github.com/custom-cards/button-card#Layout) 了解更多信息 |
| [triggers_update](https://github.com/custom-cards/button-card#triggers_update) | 否 | 未定义 | 将触发卡片更新的 entity_id 列表。更多信息见 [官方文档](https://github.com/custom-cards/button-card#triggers_update) 了解更多信息 |
| [group_expand](https://github.com/custom-cards/button-card#triggers_update) | 否 | false | 如果触发卡片更新的任何实体是组，它将自动扩展组，并且卡片将在任何子实体状态更改时更新。这也适用于嵌套组。见 [官方文档](https://github.com/custom-cards/button-card#triggers_update) 了解更多信息 |
| spin | 否 | false | 如果您希望图标在状态为 `on` 时旋转，请将其设置为 `true` |
| [styles](https://github.com/custom-cards/button-card#styles) | 否 | 预设 | 为按钮设置自己的样式，最好与 `template: empty` 一起使用。更多信息见 [官方文档](https://github.com/custom-cards/button-card#styles) 了解更多信息 |
| [extra_styles](https://github.com/custom-cards/button-card#injecting-css-with-extra_styles) | 否 | 未定义 | 设置额外的样式。更多信息见 [官方文档](https://github.com/custom-cards/button-card#injecting-css-with-extra_styles) 了解更多信息 | 
| [state](https://github.com/custom-cards/button-card#State) | 否 | 预设 | 为每个状态设置自定义样式，必须是对象列表！更多信息见 [官方文档](https://github.com/custom-cards/button-card#State) 了解更多信息 |
| [custom_fields](https://github.com/custom-cards/button-card#Custom-Fields) | 否 | 预设 | 使用您的自定义样式设置自定义字段。更多信息见 [官方文档](https://github.com/custom-cards/button-card#Custom-Fields) 了解更多信息 |
| [tap_action](https://github.com/custom-cards/button-card#Action) | 否 | 预设 | 为您的按钮设置自定义的 tap_action，默认情况下 HKI 根据实体域自动使用不同的操作。更多信息见 [官方文档](https://github.com/custom-cards/button-card#Action) 了解更多信息 |
| [hold_action](https://github.com/custom-cards/button-card#Action) | 否 | 预设 | 为您的按钮设置自定义 hold_action，默认情况下 HKI 根据实体域自动使用不同的操作。更多信息见 [官方文档](https://github.com/custom-cards/button-card#Action) 了解更多信息 |
| [double_tap_action](https://github.com/custom-cards/button-card#Action) | 否 | 预设 | 为您的按钮设置自定义 double_tap_action，默认情况下 HKI 根据实体域自动使用不同的操作。更多信息见 [官方文档](https://github.com/custom-cards/button-card#Action) 了解更多信息 |

```yaml
# views.yaml (示例简单，没有额外的选项)
  living_room:
    addons:
      button:
        - title: 客厅
          columns: 3
          entities:
            - switch.receiver
            - switch.samsung_tv
            - switch.xbox_one
```
```yaml
# views.yaml (示例简单，多个视图)
  living_room:
    addons:
      button:
        - title: 客厅
          square: false
          entities:
            - switch.receiver
            - switch.samsung_tv
            - switch.xbox_one
        - title: 卧室
          columns: 3
          entities:
            - switch.receiver
            - switch.samsung_tv
            - switch.xbox_one
```
```yaml
# views.yaml (带有额外选项的示例)
  living_room:
    addons:
      button:
        - title: 客厅
          entities:
            - entity: switch.receiver
              icon: mdi:speakers
              label: 我的扬声器
            - entity: switch.samsung_tv
              name: TV
            - entity: switch.xbox_one
              lock: true
            - entity: sensor.livingroom_temperature
              type: graph
```
#### HKI 特定按钮类型额外选项

如果您设置  `type: graph`, `type: switch`, `type: rgb` 和 `type: color-temp` ，一些按钮会获得一些额外的选项。

| 名称 | 必须 | 默认 | 说明 |
|----------------------------------|-------------|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| popup_style弹出式风格 | 否 | auto | 当具有 `type: switch` 、`type: rgb` 或 `type: color-temp` 时，您可以强制弹出窗口为 `switch` 或 `slider` |
||||
| line_color线条颜色 | 否 | red | 当有 `type: graph` 时，您可以设置 line_color，这可以是 css 名称或十六进制值 (例如 Red 或 '#FF22FF') |
| graph_type图类型 | 否 | line | 当有 `type: graph` 时，您可以在 `bar` 或 `line` 之间更改 graph_type |

#### Tips
默认情况下，标签要么是灯的亮度，要么是空的，但是使用按钮卡 JS 模板，您可以拥有像这样的酷标签

![Homekit Infused](../images/hki-button-3.png)

```yaml
# views.yaml (带有自定义标签的示例)
  my_view:
    addons:
      button:
        - title: 洗衣房
          entities:
            - entity: switch.washing_machine
              lock: true
              label: "[[[ return `${states['sensor.washing_machine_power'].state} W`; ]]]"
```

图标也是如此，您可以将每个状态的图标模板化为不同：

```yaml
# views.yaml (带有自定义图标的示例)
  my_view:
    addons:
      button:
        - title: 洗衣房
          entities:
            - entity: switch.washing_machine
              icon: "[[[ if (entity.state == 'on') return `mdi:lamp`; else return `mdi:floor-lamp` ]]]"
```

### 图片:

![Homekit Infused](../images/hki-button-1.png)

![Homekit Infused](../images/hki-button-2.png)

![Homekit Infused](../images/hki-button-4.png)

![Homekit Infused](../images/hki-button-5.png)

![Homekit Infused](../images/hki-button-6.png)
