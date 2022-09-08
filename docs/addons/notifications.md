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

## 通知

此卡片将在标题的副标题部分向您显示实时通知。 如果您有多个通知，它们会自动滑动并显示每个通知几秒钟。 您也可以浏览它们。

- 要创建通知，您必须打开以下文件 `/homekit-infused/user/notifications.yaml`
- 您首先需要创建一个条件卡，然后将通知卡放入其中。 定义条件的状态将决定是否显示通知。 请参阅下面的示例。

```yaml
# notifications.yaml (例子)
- type: conditional
  conditions:
    - entity: binary_sensor.smoke_sensor
      state: "on"
  card:
    !include
    - '../hki-base/templates/header/subtitle-notification-template.yaml'
    - icon: mdi:smoke-detector
      name: 厨房里有烟！！
      spin: true
```

### 通知额外选项

| 属性 | 必须 | 默认 | 说明 |
|----------------------------------|-------------|----------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| icon | yes | none | 设置一个图标来显示通知，这接受 [JS 模板](https://github.com/custom-cards/button-card#javascript-templates) |
| name | yes | none | 设置通知，接受 [JS 模板](https://github.com/custom-cards/button-card#javascript-templates) |
| spin | no | false | 设置显示通知时图标是否应该旋转 |
| [tap_action](https://github.com/custom-cards/button-card#Action) | no | undefined | 为此通知设置特定的 tap_action ，请参阅 [此处](https://github.com/custom-cards/button-card#Action) 了解可用选项 |
| [hold_action](https://github.com/custom-cards/button-card#Action) | no | undefined | 为此通知设置特定的 hold_action ，请参阅[此处](https://github.com/custom-cards/button-card#Action) 了解可用选项 |
| [double_tap_action](https://github.com/custom-cards/button-card#Action) | no | undefined | 为此通知设置特定的 double_tap_action ，请参阅 [此处](https://github.com/custom-cards/button-card#Action) 了解可用选项 |

```yaml
# notifications.yaml (多个通知示例)

# 烟雾探测器
- type: conditional        # 有条件的
  conditions:
    - entity: binary_sensor.smoke_sensor
      state: "on"
  card:
    !include
    - '../hki-base/templates/header/subtitle-notification-template.yaml'
    - icon: mdi:smoke-detector
      name: 厨房里有烟！！
      spin: true

# 前门
- type: conditional        # 有条件的
  conditions:
    - entity: binary_sensor.front_door
      state: "on"
  card:
    !include
    - '../hki-base/templates/header/subtitle-notification-template.yaml'
    - icon: mdi:door
      name: 前门打开了！！
```

```yaml
# 带有全部清晰通知的多个通知示例

# 一切正常
- type: conditional        # 有条件的
  conditions:
    - entity: binary_sensor.smoke_sensor
      state: "off"
    - entity: binary_sensor.smoke_sensor
      state: "off"
  card:
    !include
    - '../hki-base/templates/header/subtitle-notification-template.yaml'
    - icon: mdi:check-box-outline
      name: 一切正常，没有通知。
      
# 烟雾探测器
- type: conditional        # 有条件的
  conditions:
    - entity: binary_sensor.smoke_sensor
      state: "on"
  card:
    !include
    - '../hki-base/templates/header/subtitle-notification-template.yaml'
    - icon: mdi:smoke-detector
      name: 厨房里检测到烟雾！！
      spin: true

# Front Door
- type: conditional        # 有条件的
  conditions:
    - entity: binary_sensor.front_door
      state: "on"
  card:
    !include
    - '../hki-base/templates/header/subtitle-notification-template.yaml'
    - icon: mdi:door
      name: 前门是开着的！！
```

### 额外信息
有关更多示例，请查看我的 notifications.yaml 文件 [这里](https://github.com/jimz011/homekit-infused/blob/5.x.x-personal/hki-user/notifications.yaml)

### 图片:

![Homekit Infused](../images/hki-notifications.png)
