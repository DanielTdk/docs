【注意：】活动预约功能必须先在后台创建分类`分类预约`，缩略名称为`reservation`。见下图：

![reservation](https://cdn.ihewro.com/img/reservationCategory.png)

在该分类发布的文章，文章下面会有活动预约的功能，游客可以输入手机号和姓名以及留言，直接发送至目标邮箱。


打开主题根目录下面的report.php文件。

见下截图，修改以下三个部分：

![eamilsetting](https://cdn.ihewro.com/img/emailsetting.png)

1. 邮箱服务商的stmp地址：如果你的邮箱是163邮箱则不用修改，是QQ邮箱则修改为stmp.qq.com

2. 用户账号密码： QQ邮箱和163邮箱填写的密码均为授权码，而不是登录密码！

3. 发件人收件人回复人邮箱地址：均一致且均为上面账号密码的邮箱。
