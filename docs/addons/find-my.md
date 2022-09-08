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

## Addons > Find My

这个插件是一个完整而漂亮的 Find My 插件，灵感来自 Apple 自己的 Find My 应用程序（还有一点来自@LRvdLinden）。

您可以在配置文件菜单中找到 find_my 快捷方式。 你必须在 `/hki-user/config/config.yaml` 中设置 find_my ！

您可以使用以下任何选项来修改您的插件。 至少选择一个类别才能正常运行！

| 名称 | 必须 | 默认 | 说明 |
|----------------------------------|-------------|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| persons | 否 | 未定义 | 在 find_my 中置要显示的人 |
| devices | 否 | 未定义 | 在 find_my 中设置要显示的设备 |
| vehicles | 否 | 未定义 | 在 find_my 中设置要显示的车辆 |

#### 查找我的额外选项
您可以将以下任何选项传递给您的实体以自定义外观。 如果您没有设置 icon 或 picture_entity ，它将尝试从 customize.yaml 中获取它们。

| 名称 | 必须 | 默认 | 说明 |
|----------------------------------|-------------|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| name | 否 | global_name | 为该实体设置名称。默认：全局名称 |
| entity | 是 | 未定义 | 设置使用的实体，这些最适用于 `person` 或 `device_tracker` 实体 |
| icon | 否 | global_icon | 为您的实体指定自定义图标 |
| entity_picture | 否 | global_entity_picture | 为您的实体指定自定义 entity_picture |
| battery_entity | 否 | 未定义 | 如果该实体有单独的电池实体，您可以在此处输入，否则不显示电池 |
| geocoded_location_entity | 否 | 未定义 | 如果该实体有单独的地理编码位置实体，您可以在此处输入，否则将显示没有地理编码的位置 |

例子:

```yaml
# config.yaml (例子 个人)
  find_my:
    persons:
      - name: jimmy             # 吉米
        entity: person.jimmy
        battery_entity: sensor.sm_n976b_battery_level
        geocoded_location_entity: sensor.sm_n976b_geocoded_location
      - name: Stephanie         # 斯蒂芬妮
        entity: person.stephanie
        battery_entity: sensor.sm_n986b_batterijniveau
        geocoded_location_entity: sensor.sm_n986b_gegeocodeerde_locatie
```
```yaml
# config.yaml (示例人员和设备)
  find_my:
    persons:
      - name: Jimmy             # 吉米
        entity: person.jimmy
        battery_entity: sensor.sm_n976b_battery_level
        geocoded_location_entity: sensor.sm_n976b_geocoded_location
      - name: Stephanie         # 斯蒂芬妮
        entity: person.stephanie
        battery_entity: sensor.sm_n986b_batterijniveau
        geocoded_location_entity: sensor.sm_n986b_gegeocodeerde_locatie
    devices:
      - name: Tile Pro          # Tile Pro 
        entity: device_tracker.dog
      - name: Note 10+ 5G
        entity: device_tracker.sm_n976b
        geocoded_location_entity: sensor.sm_n976b_geocoded_location
        battery_entity: sensor.sm_n976b_battery_level
```

#### 实体图片提示
您可以使用实体图片，以便您的视图看起来像屏幕截图中的视图。 建议您自己创建实体图片，而不仅仅是输入您在互联网上找到的图片。

最好的设置是打开 paint/photoshop 。 创建一个 130x130 像素的正方形，将你的实体图片放在它的中间（随意调整照片大小）。

注意：默认主题使用白色按钮，如果您想使用其他颜色，我建议您更改要使用的图像的背景颜色！

#### 额外实体图片提示
- 如果您有 iCloud，您可以通过登录 view icloud，然后将图像保存到您的桌面，从 icloud 网站准备好漂亮的图像。
- 如果您使用 Unifi 控制器，您也可以通过单击任何设备然后单击报告错误图标来获得一些漂亮的图像（这将打开一个搜索菜单，您可以在其中右键单击保存，注意 Apple 用户会需要 Chrome 或 Firefox，因为 Safari 不支持此功能）。

### 图片:

![Homekit Infused](../images/hki-find-my.png)
