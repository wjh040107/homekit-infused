这将修复弹出窗口不适用于按钮卡。

由于某种原因，您不能再通过 HACS 下载此版本。 首先通过 HACS 下载按钮卡。 完成后，转到您的 /www/community/button-card/ 文件夹并将那里的两个文件替换为来自此 repo 的两个文件。

您可能需要更改对此文件夹的权限才能在其中写入。

对于 Unraid 用户，您可以执行以下操作（更改路径以匹配您自己的路径）

chmod 777 -R /mnt/user/appdata/Home-Assistant/www/community/button-card

