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

## 插件
插件是内置的预配置卡片，您可以在任何视图上打开/关闭。您可以通过将密钥添加到视图配置来添加插件（在 /hki-user/config/views.yaml 中完成）。所有插件都预先配置了垂直堆栈和标题，在定义插件时必须牢记这一点。每个插件都有一些额外的堆栈选项，因此每个插件文档的第一部分都会向您展示这些额外的选项。

您可以通过使用 [layout](addons/layout.md) 插件和/或更改定义插件的顺序来控制插件的放置。首先定义的插件将首先呈现。如何准确配置插件取决于插件，您应该在将插件添加到配置之前阅读插件特定文档。

```yaml
# views.yaml (示例如何添加插件)
  my_view:                                  # 我的视图
    subtitle: 概述                          # 副标题
    icon: mdi:thermostat                    # 图标
    addons:                                 # 插件
      thermostat:                           # 恒温器
        - title: 我的恒温器                 # 标题
          entities:                         # 实体
            - # 恒温器插件配置在这里！

  my_second_view:                           # 我的第二个视图
    subtitle: 概述                          # 副标题
    icon: mdi:vacuum-clean                  # 图标
    addons:                                 # 插件
      button:                               # 按钮
        - title: 我的灯                     # 标题
          entities:                         # 实体
            - # 按钮插件配置在这里！
```
# Addons插件

| 姓名 | 说明 |
|--------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [air_visual空气质量](addons/air-visual.md) | 一张好看的空气质量卡 |
| [areas区域](addons/areas.md) | 一张显示您房间信息的卡片 *即将推出* |
| [battery电池电量](addons/battery.md) | 为您提供电池电量概览的插件 |
| [button按钮](addons/button.md) | 功能强大的按钮卡，可能是您唯一需要的插件 |
| [calendar日历](addons/calendar.md) | 默认日历卡 |
| [camera摄像头](addons/camera.md) | 将您的摄像头添加到视图中的插件 |
| [custom习惯](addons/custom.md) | 允许任何卡片或多张卡片的终极插件！ |
| [energy能源](addons/energy.md) | 在仪表盘中重新创建 HA 能源仪表板 |
| [entities实体卡](addons/entities.md) | 一张好用的实体卡 |
| [favorites收藏](addons/favorites.md) | 示带有您收藏视图的快捷方式的视图 |
| [gauge仪表](addons/gauge.md) | 为您的实体显示简单的仪表 |
| [glance预览](addons/glance.md) | 一张好用的预览卡 |
| [google TTS](addons/google.md) | Google Home TTS 卡 |
| [iframe框架](addons/iframe.md) | 方便的框架卡，可用于视图 |
| [history历史](addons/history.md) | 这是核心 HA 图形卡，您可以将其用作 HKI 中图形插件的替代品 |
| [logbook日志记录](addons/logbook.md) | 使用日志记录您的实体 |
| [map地图](addons/map.md) | 跟踪您的实体的地图 |
| [media_player媒体播放器](addons/media-player.md) | 媒体播放器插件 |
| [menu菜单](addons/menu.md) | 在...菜单以外的其他视图上显示菜单！ |
| [meteoalarm气象](addons/meteoalarm.md) | 一张向您展示天气警报的好卡片 |
| [picture_elements图片元素卡](addons/picture-elements.md) | HKI的核心图片元素卡 |
| [plant_status监控植物](addons/plant-status.md) | 监控您的植物 |
| [plex插件](addons/plex.md) | 一个非常漂亮的Plex插件 |
| [remote_control遥控器](addons/remote-control.md) | 一个漂亮的 Nvidia Shield TV/Apple TV 遥控器 |
| [sensor传感器](addons/sensor.md) | 核心传感器卡 |
| [statistics统计](addons/statistics.md) | 创建漂亮的统计图表 |
| [upcoming_media媒体预告](addons/upcoming-media.md) | 显示来自您的sonarr/radarr的即将到来和最近添加的媒体 |
| [thermostat恒温器](addons/thermostat.md) | 恒温器按钮供您查看 |
| [weather天气](addons/weather.md) | HKI的天气插件，选择核心或简单天气 |
| [xbox控制器卡](addons/xbox.md) | Xbox 控制器卡 |

＃＃＃ 高级用法

插件可以定义多次，这在您想要一个顶部有按钮堆栈的视图、中间有一个地图、底部有另一个按钮堆栈的视图时特别有用。

要在单个视图中定义相同类型的额外插件，您必须在插件名称中添加后缀，后缀名称无关紧要，只要您使用一个即可。 `addon_whatever：`

```yaml
# views.yaml (定义多个相同类型的插件的示例)
  my_view:
    title: Location
    addons:
      button:
        - title: 我的快速切换
          entities:
            - switch.phone
      button_2:
        - title: 我的第二个快速切换
          entities:
            - switch.iphone
      button_whatever:
        - title: 另一个按钮插件
          entities:
            - switch.galaxy
```

插件也可以是有条件的，具体取决于实体的状态！

```yaml
# views.yaml (定义多个相同类型的插件的示例)
  my_view:
    title: 地点
    type: conditional
    addons:
      button:
        - title: 这只会在吉米在家时显示
          conditions:
            - entity: person.jimmy
              state: "home"
          entities:
            - switch.phone
      button_2:
        - title: 这只会在 Jimmy 和 Stephanie 在家时显示
          conditions:
            - entity: person.jimmy
              state: "home"
            - entity: person.stephanie
              state: "home"
          entities:
            - switch.iphone
      button_3:
        - title: 这只会在 Jimmy 不在家且 Stephanie 在家时显示
          conditions:
            - entity: person.jimmy
              state_not: "home"
            - entity: person.stephanie
              state: "home"
          entities:
            - switch.iphone
```

### 额外的信息

发现了 `simple_weather`, `devices`, `rooms`, `sun_card`, `find_my`, `layout`, `columns`, `mini-media-player`, `search` `vacuum` and `graph` 这些插件存在于 HKI 4吗？

那么推理可以在下面找到：
- `sun_card`、`mini-media-player` 和 `graph` 是对模板来说太大或不需要添加的插件，您仍然可以将它们与 `custom:` 插件一起使用，这允许它们的所有选项 被解锁并提供更多的自定义。
- `find_my` 和 `layout` 没有被删除，而是将其文档移至配置页面。
- `columns` 是多余的而且相当混乱。 现在只是为每个插件设置列。
- `devices` 已合并到新的 `button:` 插件中。
- `房间`已被重新设计，现在称为`区域：`。
- `simple_weather` 已与 `weather:` 插件合并，可以在那里找到。
- `search` 现在已集成到配置文件菜单中。
- `vacuum` 模板太难了，虽然已经有很多很棒的选项可用。 我建议使用带有漂亮真空卡的自定义插件（如小米真空卡或小米真空地图卡）
