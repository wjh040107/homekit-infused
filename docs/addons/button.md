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

| Name | Required | Default | Description |
|----------------------------------|-------------|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| title | no | undefined | Set the title of the stack, ommitting this line will or setting `title: hide` will hide the title |
| columns | no | 3 | Define the number of columns this stack will use |
| square | no | true | Set if the buttons should be square or not, this is only useful when you set individual aspect_ratios in the config below |
| lock | no | false | this locks the entire stack and will now need two taps to turn on/off, the first tap unlocks, the second toggles |
| [view_layout](layout.md#view-layout) | no | undefined | This is best used in conjunction with the [layout](layout.md#view-layout) addon, but can also be used to control whether to show this stack on different screen sizes. |
| type | no | undefined | Setting a type can make the stack condtional, this option will ONLY accept `conditional` |
| conditions | no | undefined | Add entities and conditions, this will determine when this addon will be shown, e.g. if entity x is turned `on`, then show this addon (see [addons](../addons.md) for examples |
| entities | yes | list of entities | List all your entities you want to show up here |

### 按钮选项

默认情况下，您必须输入如下示例中的实体数组，这不需要额外的选项，只会获取全局 name/icon 。
您必须将其定义为对象才能使用以下选项。

| Name | Required | Default | Description |
|----------------------------------|-------------|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| entity | yes | undefined | Set the entity used |
| type | no | auto | This forces a button to be seen by HKI as a specific type, which alters the appearance. Choose between `rgb`, `color-temp`, `switch`, or `graph` or `fan`. By default HKI tries to figure out itself what kind of type the button is, but if it gets it wrong force it by setting the type |
| name | no | global_name | Set a name for this button, this accepts [JS templates](https://github.com/custom-cards/button-card#javascript-templates) |
| label | no | none | Set a label for this button, this accepts [JS templates](https://github.com/custom-cards/button-card#javascript-templates) |
| icon | no | global_icon | Set an icon for this button, this accepts [JS templates](https://github.com/custom-cards/button-card#javascript-templates) |
| [state_display](https://github.com/custom-cards/button-card#javascript-templates) | no | undefined | Override the way the state is displayed, this accepts [JS templates](https://github.com/custom-cards/button-card#javascript-templates) |
| entity_picture | no | global_entity_picture | Set an entity picture for this button, note that when an entity_picture is set in either customize.yaml or here, that it will take priority over an icon, unless you set `show_entity_picture: false`, this accepts [JS templates](https://github.com/custom-cards/button-card#javascript-templates) |
| background_image | no | undefined | Set an URL or a `/local/*` to an image to show as background |
| lock | no | false | this locks this button and will now need two taps to turn on/off, the first tap unlocks, the second toggles |
| aspect_ratio | no | 1/1 | Set a custom aspect_ratio for this button, note that you will want to set `square: false` in the stacks configuration when setting anything other than 1/1 |
| size | no | 25% | Set the icon size, note that this setting is not always working as expected due to the grid used, play around with it |
| units | no | undefined | Override or define the units to display after the state of the entity. If omitted, it's using the entity's units |
| button_badge | no | undefined | Use the HKI predefined badge in your button, you MUST define an entity to use, you can only use it's state! |
| icon_color_active | no | undefined | Use this to override the icon color when the entity is active, this accepts [JS templates](https://github.com/custom-cards/button-card#javascript-templates) |
| icon_color_inactive | no | undefined | Use this to override the default icon color, this accepts [JS templates](https://github.com/custom-cards/button-card#javascript-templates) |
| show_name | no | true | Choose to show/hide the name, set to `false` to hide it |
| show_label | no | true | Choose to show/hide the label, set to `false` to hide it |
| show_icon | no | true | Choose to show/hide the icon, set to `false` to hide it |
| show_state | no | true | Choose to show/hide the state, set to `false` to hide it |
| show_last_changed | no | false | Choose to show/hide the last_changed state, set to `true` to show it, note that this will replace the label! |
| show_live_stream | no | false | If a camera entity is set, show a live stream instead of still images |
| show_units | no | true | Choose to show/hide the units, set to `false` to hide it |
| show_entity_picture | no | true | Choose to show/hide the entity_picture, set to `false` to hide it |
| [confirmation](https://github.com/custom-cards/button-card#confirmation) | no | undefined | Display a confirmation popup. See [official documentation](https://github.com/custom-cards/button-card#confirmation) for more information |
| template | no | undefined | By default this button will take on the HKI default style, you can set `template: empty` to clear it and use your own styles |
| [layout](https://github.com/custom-cards/button-card#Layout) | no | undefined | The layout of the button can be modified using this option, you MUST set `template: empty` for this to work properly. See [official documentation](https://github.com/custom-cards/button-card#Layout) for more information |
| [triggers_update](https://github.com/custom-cards/button-card#triggers_update) | no | undefined | entity_id list that would trigger a card update. See [official documentation](https://github.com/custom-cards/button-card#triggers_update) for more information |
| [group_expand](https://github.com/custom-cards/button-card#triggers_update) | no | false | if any of the entities triggering a card update is a group, it will auto-expand the group and the card will update on any child entity state change. This works with nested groups too. See [official documentation](https://github.com/custom-cards/button-card#triggers_update) for more information |
| spin | no | false | Set this to `true` if you want the icon to spin when the state is `on` |
| [styles](https://github.com/custom-cards/button-card#styles) | no | predefined | Set your own styles to the button, this is best used with `template: empty`. See [official documentation](https://github.com/custom-cards/button-card#styles) for more information |
| [extra_styles](https://github.com/custom-cards/button-card#injecting-css-with-extra_styles) | no | undefined | Set extra styles. See [official documentation](https://github.com/custom-cards/button-card#injecting-css-with-extra_styles) for more information | 
| [state](https://github.com/custom-cards/button-card#State) | no | predefined | Set custom styles per state, must be an object list! See [official documentation](https://github.com/custom-cards/button-card#State) for more information |
| [custom_fields](https://github.com/custom-cards/button-card#Custom-Fields) | no | predefined | Set custom fields with your custom styles. See [official documentation](https://github.com/custom-cards/button-card#Custom-Fields) for more information |
| [tap_action](https://github.com/custom-cards/button-card#Action) | no | predefined | Set a custom tap_action for your button, by default HKI uses a different action automatically depending on the entity domain. See [official documentation](https://github.com/custom-cards/button-card#Action) for more information |
| [hold_action](https://github.com/custom-cards/button-card#Action) | no | predefined | Set a custom hold_action for your button, by default HKI uses a different action automatically depending on the entity domain. See [official documentation](https://github.com/custom-cards/button-card#Action) for more information |
| [double_tap_action](https://github.com/custom-cards/button-card#Action) | no | predefined | Set a custom double_tap_action for your button, by default HKI uses a different action automatically depending on the entity domain. See [official documentation](https://github.com/custom-cards/button-card#Action) for more information |

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
| popup_style | 否 | 汽车 | 当具有 `type: switch` 、`type: rgb` 或 `type: color-temp` 时，您可以强制弹出窗口为 `switch` 或 `slider` |
||||
| line_color | 否 | red | 当有 `type: graph` 时，您可以设置 line_color，这可以是 css 名称或十六进制值 (例如 Red 或 '#FF22FF') |
| graph_type | 否 | line | 当有 `type: graph` 时，您可以在 `bar` 或 `line` 之间更改 graph_type |

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
