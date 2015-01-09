AliyunOSS
====================

```
    ___     __    _                                    ____    _____   _____
   /   |   / /   (_)   __  __  __  __   ____          / __ \  / ___/  / ___/
  / /| |  / /   / /   / / / / / / / /  / __ \        / / / /  \__ \   \__ \
 / ___ | / /   / /   / /_/ / / /_/ /  / / / /       / /_/ /  ___/ /  ___/ /
/_/  |_|/_/   /_/    \__, /  \__,_/  /_/ /_/        \____/  /____/  /____/
                    /____/
```

阿里云 OSS 官方 SDK 的 Composer 封装，支持任何 PHP 项目，包括 Laravel、Symfony、TinyLara 等等。

###更新记录

* 2015-01-09 `Release v1.0`

###安装

将以下内容增加到 composer.json：

```json
require: {
    "johnlui/aliyun-oss": "1.0"
}
```

然后运行 `composer dump-autoload`。

###使用

```php
use JohnLui\AliyunOSS\AliyunOSS;


// 构建 OSSClient 对象
// 三个参数：服务器地址、阿里云提供的AccessKeyId、AccessKeySecret
$oss = AliyunOSS::boot('http://oss-cn-qingdao.aliyuncs.com',  $AccessKeyId, $AccessKeySecret);

// 新增 Bucket
$oss->createBucket($bucketName);

// 获取某个 Bucket 中所有文件的 key 值
// 返回：Array
$keysArray = $oss->getAllObjectKey($bucketName);
var_dump($keysArray);

// 设置 Bucket
$ossWithBucket = $oss->setBucket($bucketName);

// 上传一个文件（示例文件为 public 目录下的 robots.txt）
// 两个参数：资源名称、文件路径
$ossWithBucket->uploadFile('robots.txt', public_path('robots.txt'));

// 从服务器获取这个资源的 URL 并打印
// 两个参数：资源名称、过期时间。返回：String
$url = $ossWithBucket->getUrl('robots.txt', new DateTime("+1 day"));
echo $url;
```

###捐献Star

> ###别忘了点击上面右侧的 Star 哦，变成 Unstar 就可以了！ :stuck_out_tongue_winking_eye:

###License

除 “版权所有 （C）阿里云计算有限公司” 的代码文件外，遵循 [MIT license](http://opensource.org/licenses/MIT) 开源。