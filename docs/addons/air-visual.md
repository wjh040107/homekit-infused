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

## Addons > Air Visual

一张不错的空气质量卡，供您欣赏。

### HACS 要求

| 名称 | 类型  | 说明 |
|----------------------------------|-------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Air Visual Card](https://github.com/dnguyen800/air-visual-card) | 前端 | 一张显示空气质量的卡片 |

您必须在 Home Assistant 中设置 Air Visual 集成（您可以在 Home Assistant 的集成部分中执行此操作）

您可以使用以下任何选项来修改您的插件。

### 堆栈和插件配置

| 名称 | 必需 | 默认 | 说明 |
|----------------------------------|-------------|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| title | no | undefined | Set the title of the stack, ommitting this line will or setting `title: hide` will hide the title |
| [view_layout](layout.md#view-layout) | no | undefined | This is best used in conjunction with the [layout](layout.md#view-layout) addon, but can also be used to control whether to show this stack on different screen sizes. |
| weather | no | unknown | Setup a weather entity to show the weather in this card |
| hide_header | no | true | Whether to show/hide the header title of this card (this is NOT the same as the title defined above) |
| air_pollution_level | yes | sensor.u_s_air_pollution_level | Set the air pollution sensor entity |
| air_quality_index | yes | sensor.u_s_air_quality_index | Set the air quality index sensor entity |
| main_pollutant | yes | sensor.u_s_main_pollutant | Set the main pollutant sensor entity |
| city_name | yes | unknown | Set your city name |
| type | no | undefined | Setting a type can make the stack condtional, this option will ONLY accept `conditional` |
| conditions | no | undefined | Add entities and conditions, this will determine when this addon will be shown, e.g. if entity x is turned `on`, then show this addon (see [addons](../addons.md) for examples |


```yaml
# views.yaml (例子)
  my_view:
    addons:
      air_visual:
        - air_pollution_level: sensor.u_s_air_pollution_level
          air_quality_index: sensor.u_s_air_quality_index
          main_pollutant: sensor.u_s_main_pollutant
          weather: weather.eindhoven
          city_name: Eindhoven
```

### 图片:

![Homekit Infused](../images/hki-air-visual.png)
