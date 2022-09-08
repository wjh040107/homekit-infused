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

## Addons > Map

此插件为您的视图提供了一个地图，您可以将其与您自己定义的实体一起使用。

您可以使用以下任何选项来修改您的插件。

### 视图和插件配置

| 名称 | 必须 | 默认 | 说明 |
|----------------------------------|-------------|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| title | no | undefined | 设置视图的标题，省略此行或设置 `title: hide` 将隐藏标题 |
| default_zoom | no | default | 设置默认缩放，大约 15 可能是您设置所需的 |
| aspect_ratio | no | none | 为您的地图设置纵横比 |
| [view_layout](layout.md#view-layout) | no | undefined | 这最好与 [layout](layout.md#view-layout) 插件一起使用，但也可以用于控制是否在不同的屏幕尺寸上显示此视图。 |
| dark_mode | no | false | 是否使用深色或浅色地图 |
| type | no | undefined | 设置类型可以使视图有条件，此选项将只接受 `conditional` |
| conditions | no | undefined | 添加实体和条件，这将确定何时显示此插件，例如如果实体 x 已打开 `on` ，则显示此插件参见 [addons](../addons.md) 示例 |
|实体 |是的 |数组 |在视图中添加您想要的实体，实体必须作为数组列出 |
| entities | yes | array | 在视图中添加您想要的实体，实体必须作为数组列出 |

```yaml
# views.yaml (例子)
  my_view:
    addons:
      map:
        - title: Location Stephanie    # 位置斯蒂芬妮
          default_zoom: 15
          aspect_ratio: 16x10
          entities:
            - person.stephanie
```              
```yaml
# views.yaml (具有多个地图的示例)
  my_view:
    addons:
      map:
        - title: Location Stephanie    # 位置斯蒂芬妮
          entities:
            - person.stephanie
        - title: Location Jimmy    # 位置吉米
          entities:
            - person.jimmy
```  
```yaml
# views.yaml (单个地图上有多个实体的示例)
  my_view:
    addons:
      map:
        - title: Location    # 地点
          entities:
            - person.stephanie
            - person.jimmy
            - person.tala
```  

### 图片:

![Homekit Infused](../images/hki-map.png)
