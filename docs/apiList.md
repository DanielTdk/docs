首页幻灯片是调用博客最新的三篇文章，图片来自于文章的缩略图。

文章缩略图的显示顺序为：

顺序是：thumb（自定义字段）--> 第一个图片附件--> 文章第一张图片 --> 随机图片输出


随机图片存储在主题根目录的<em>img/random</em>下面。

修改图片请按照`数字.jpg`命名，并同步修改主题根目录下的function.php的
```php
$rand = rand(1,3);
```

把数字3修改为缩略图的数目总数。

![random_pics](https://cdn.ihewro.com/img/randomNums.png)
