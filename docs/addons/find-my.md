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

| Name | Required | Default | Description |
|----------------------------------|-------------|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| persons | no | undefined | Set the persons you want to show in find_my |
| devices | no | undefined | Set the devices you want to show in find_my |
| vehicles | no | undefined | Set the vehicles you want to show in find_my |

#### 查找我的额外选项
您可以将以下任何选项传递给您的实体以自定义外观。 如果您没有设置 icon 或 picture_entity ，它将尝试从 customize.yaml 中获取它们。

| Name | Required | Default | Description |
|----------------------------------|-------------|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| name | no | global_name | Set a name for this entity |
| entity | yes | undefined | Set the entity used, these work best with either `person` or `device_tracker` entities |
| icon | no | global_icon | Specify a custom icon for your entity |
| entity_picture | no | global_entity_picture | Specify a custom entity_picture for your entity |
| battery_entity | no | undefined | If this entity has a separate battery entity you can enter it here, else no battery is shown |
| geocoded_location_entity | no | undefined | If this entity has a separate geocoded location entity you can enter it here, else not geocoded location is shown |

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
      - name: Jimmy
        entity: person.jimmy
        battery_entity: sensor.sm_n976b_battery_level
        geocoded_location_entity: sensor.sm_n976b_geocoded_location
      - name: Stephanie
        entity: person.stephanie
        battery_entity: sensor.sm_n986b_batterijniveau
        geocoded_location_entity: sensor.sm_n986b_gegeocodeerde_locatie
    devices:
      - name: Tile Pro
        entity: device_tracker.dog
      - name: Note 10+ 5G
        entity: device_tracker.sm_n976b
        geocoded_location_entity: sensor.sm_n976b_geocoded_location
        battery_entity: sensor.sm_n976b_battery_level
```

#### Entity Picture Tips
You can use entity pictures so that your view will look like the ones from the screenshots. It is recommended that you create the entity pictures yourself and not just enter pictures you find on the internet.

The best settings will be to open paint/photoshop. Create a square of 130x130 pixels and put your entity picture in the middle of it (resize the photo at will).

NOTE: The default theme uses a white button, if you want to use another color I recommend you to change the background color of the images you are going to use as well!

#### Bonus Entity Picture Tips
- If you have iCloud you can get beautiful ready to go images from the icloud website by logging in view icloud and then saving the images to your desktop.
- If you use the Unifi Controller you can get some nice images as well by clicking any device and then click on report wrong icon (this will open up a search menu in which you can right-click to save, note that Apple users will want to try Chrome or Firefox since Safari doesn't support this).

### 图片:

![Homekit Infused](../images/hki-find-my.png)
