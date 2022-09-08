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

## Alarm警报

您可以在此处设置警报，包括标题徽章和/或弹出窗口。 此页面上的设置必须在 `/hki-user/config/config.yaml` 中配置！

| Name | Required | Default | Description |
|----------------------------------|-------------|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| entity | yes | alarm_control_panel.home_alarm | Sets the alarm entity used |
| show_badge | no | true | Choose whether to show or hide the alarm badge in the header |
| icon | no | predefined | Set your own alarm icon, this accepts [JS templates](https://github.com/custom-cards/button-card#javascript-templates) |
| icon_color | no | predefined | Set your own icon color, this accepts [JS templates](https://github.com/custom-cards/button-card#javascript-templates) |
| [tap_action](https://github.com/custom-cards/button-card#Action) | no | predefined | Set a custom tap_action, see [actions](https://github.com/custom-cards/button-card#Action) for more information, if you set a tap_action the default popup will no longer work and be replaced by this action instead |
| [hold_action](https://github.com/custom-cards/button-card#Action) | no | none | Set a custom hold_action, see [actions](https://github.com/custom-cards/button-card#Action) |
| [double_tap_action](https://github.com/custom-cards/button-card#Action) | no | none | Set a custom double_tap_action, see [actions](https://github.com/custom-cards/button-card#Action) |
| popup | no | keypad | Design your own popup when clicking this badge (*Note: Will not work if tap_action is defined!*), this must be a list of cards! If ommitted it will show a keypad instead |

```yaml
# config.yaml (默认设置)
  alarm:
    entity: alarm_control_panel.home_alarm
    show_badge: true
```
```yaml
# config.yaml (示例自定义卡片)
  alarm:
    entity: alarm_control_panel.home_alarm
    show_badge: true
    popup:
      - type: markdown
        content: 我的警报面板
      - type: alarm-panel
        entity: alarm_control_panel.home_alarm
```

### 图片:

![Homekit Infused](../images/hki-alarm-2.png)
![Homekit Infused](../images/hki-alarm-1.png)
