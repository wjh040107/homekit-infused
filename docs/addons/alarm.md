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

| 名称 | 必须 | 默认 | 说明 |
|----------------------------------|-------------|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| entity | 是 | alarm_control_panel.home_alarm | 设置使用的报警实体 |
| show_badge | 否 | true | 选择是否在标题中显示或隐藏警报徽章 |
| icon | no | 预定义 | 设置自己的报警图标，这个接受 [JS模板](https://github.com/custom-cards/button-card#javascript-templates) |
| icon_color | no | 预定义 | 设置自己的图标颜色，这接受 [JS模板](https://github.com/custom-cards/button-card#javascript-templates) |
| [tap_action](https://github.com/custom-cards/button-card#Action) | 否 | 预定义 | 设置一个自定义的 tap_action, 查看 [actions](https://github.com/custom-cards/button-card#Action) 获取更多信息，如果你设置了一个 tap_action，默认的弹出窗口将不再起作用并被这个动作取代 |
| [hold_action](https://github.com/custom-cards/button-card#Action) | no | none | 设置自定义 hold_action, 查看 [actions](https://github.com/custom-cards/button-card#Action) |
| [double_tap_action](https://github.com/custom-cards/button-card#Action) | no | 无 | 设置自定义 double_tap_action, 查看 [actions](https://github.com/custom-cards/button-card#Action) |
| popup | no | keypad | 单击此徽章时设计自己的弹出窗口（*注意：如果定义了 tap_action 将不起作用！*），这必须是卡片列表！如果省略，它将显示一个小键盘 |

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
