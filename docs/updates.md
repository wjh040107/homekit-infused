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

## 更新
### 如何将 HKI 5 更新到更新版本？
要将 Homekit Infused 更新到更新版本，您只需下载最新版本并替换以下 2 个文件夹：
- /hki-base/
- /packages/

请务必阅读任何重大更改。

### 升级程序到 HKI 4 （最新版本 v2022.02.0）
简单地说……没有！ 有太多的整体变化，以至于解释如何转换您的设置需要花费与编写整个项目一样多的时间。

不过也没有那么糟糕，HKI 4 的用户会发现很多东西几乎相同，只是略有不同。 在大多数情况下，您可以简单地重新使用您已经拥有的配置并进行一些调整。 尽管如此，您不应该复制您拥有的整个设置，慢慢进行并逐个查看。

尽管我将在这里提到两个非常显着的变化：
- 通知的模板名称已更改。
- `/hki-user/views` 不再是 custom_cards 的默认文件夹，该文件夹已重命名为 `custom_legacy`! 可以在[这里](splitting-the-config.md) 找到为什么进行此更改

幸运的是，您不必重做所有通知，只需确保将所有包含 `'../hki-base/templates/header/notification-template.yaml'` 的行更改为 `'../hki-base/templates/header/subtitle-notification-template.yaml'`.

## 版本（这些始终是最新的，并用作家庭助理中的传感器）
[当前 HKI 版本](version.html)

[最新兼容 HA 版本](version_compatible.html)
