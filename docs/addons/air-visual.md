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
| title | no | undefined | 设置栈的标题，省略此行或设置 `title: hide` 将隐藏标题 |
| [view_layout](layout.md#view-layout) | no | undefined | 这最好与 [layout](layout.md#view-layout) 插件一起使用，但也可以用于控制是否在不同的屏幕尺寸上显示此堆栈 |
| weather | no | unknown | 设置天气实体以在此卡片中显示天气 |
| hide_header | no | true | 是否显示/隐藏此卡片的标题标题（这与上面定义的标题不同） |
| air_pollution_level | yes | sensor.u_s_air_pollution_level | 设置空气污染传感器实体 |
| air_quality_index | yes | sensor.u_s_air_quality_index | 设置空气质量指数传感器实体 |
| main_pollutant | yes | sensor.u_s_main_pollutant | 设置主要污染物传感器实体 |
| city_name | yes | unknown | 设置您的城市名称 |
| type | no | undefined | 设置类型可以使堆栈有条件，此选项将只接受 `conditional` |
| conditions | no | undefined | 添加实体和条件，这将确定何时显示此插件，例如 例如如果实体 x 已打开 `on`, 则显示此插件 (参见 [addons](../addons.md) 示例 |


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
