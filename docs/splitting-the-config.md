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

## 拆分配置
可以拆分配置，以便更好地组织视图并使代码更具可读性。

由于重写整个文档是没有用的，这里是 [官方文档](https://www.home-assistant.io/docs/configuration/splitting_configuration/).

我提到这一点，因为我相信这是新用户在他们已经投入大量时间在他们的仪表板/配置上之前看不到的少数东西之一。您可以为您的配置、lovelace、自动化等执行此操作。基本上家庭助理中的任何内容都可以使用此方法进行拆分。它最终将使您的代码更具可读性，最重要的是，您可能会更好地找到很久以前编写的代码。

这基本上允许您将配置拆分为多个文件。

#### 拆分views.yaml文件
如果您阅读过官方文档，您会发现您基本上可以将任何文件拆分到任何文件夹中，只要您从主文件中引用它即可。 views.yaml 文件也可以这样做，在本例中，我们将使用一个简单的示例来说明如何将视图拆分为多个文件。对于此示例，您必须在 `/hki-user/` 中创建一个名为 `views` (完整路径如下所示 `/hki-user/views`).

```yaml
# views.yaml (例子)
views:
  !include_dir_named ../views
```

上面的文件不需要再被触及，因为所有的配置都来自我们刚刚创建的文件夹。
在 `/hki-user/views` 中创建一个具有对象名称的文件（文件名将是视图的对象和标题）

```yaml
# hki-user/views/livingroom.yaml
subtitle: 我的客厅 
addons:
  button:
    - title: 我的客厅灯
      entities:
        - light.lava_lamp
```

使用此方法时，您必须在单独的文件中定义每个视图。 您不能在同一个文件中有多个视图！
基本上，您所做的事情与在 views.yaml 文件中的操作完全相同，只是将它们拆分为多个文件。

还有另一种方式，用户可以拆分配置。
```yaml
# views.yaml (例子)
views:
  !include_dir_merge_named ../views
```

上面的文件不需要再被触及，因为所有的配置都来自我们刚刚创建的文件夹。
在 `/hki-user/views` 中创建一个具有对象名称的文件，在这种情况下，名称并不重要，因为我们需要定义对象 `object` 。

```yaml
# hki-user/views/livingroom.yaml
living_room:
  title: 客厅
  subtitle: 我的客厅 
  addons:
    button:
      - title: 我的客厅灯
        entities:
          - light.lava_lamp
```

使用此方法允许您在同一个文件中添加多个视图以及拥有多个文件，但您必须为每个视图定义对象。

无论您选择哪种方法并不重要，这完全取决于个人喜好，它们只是组织代码的方法。 如果您不喜欢这样做，只需使用 `views.yaml` 文件。
