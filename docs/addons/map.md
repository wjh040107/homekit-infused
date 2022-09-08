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

| Name | Required | Default | Description |
|----------------------------------|-------------|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| title | no | undefined | Set the title of the stack, ommitting this line will or setting `title: hide` will hide the title |
| default_zoom | no | default | Sets the default zoom, around 15 is probably what you will want for your setup |
| aspect_ratio | no | none | Sets an aspect ratio for your map |
| [view_layout](layout.md#view-layout) | no | undefined | This is best used in conjunction with the [layout](layout.md#view-layout) addon, but can also be used to control whether to show this stack on different screen sizes. |
| dark_mode | no | false | Whether to use a dark or light map |
| type | no | undefined | Setting a type can make the stack condtional, this option will ONLY accept `conditional` |
| conditions | no | undefined | Add entities and conditions, this will determine when this addon will be shown, e.g. if entity x is turned `on`, then show this addon (see [addons](../addons.md) for examples |
| entities | yes | array | Add the entities you want in your stack, entities must be listed as an array |

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
