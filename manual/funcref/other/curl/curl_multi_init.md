
## curl_multi_init()
(PHP 5, PHP 7)  
curl_multi_init — 返回一个新cURL批处理句柄

#### 说明  
```php
resource curl_multi_init ( void )
```

允许并行地处理批处理cURL句柄。

#### 参数   
此函数没有参数。

#### 返回值
成功时返回一个cURL批处理句柄，失败时返回FALSE。

#### 范例   
---  
Example #1 curl_multi_init() example  
这个范例将会创建 2 个 cURL 句柄，把它们加到批处理句柄，然后并行地运行它们。 

```php
<?php
// 创建一对cURL资源
$ch1 = curl_init();
$ch2 = curl_init();

// 设置URL和相应的选项
curl_setopt($ch1, CURLOPT_URL, "http://www.example.com/");
curl_setopt($ch1, CURLOPT_HEADER, 0);
curl_setopt($ch2, CURLOPT_URL, "http://www.php.net/");
curl_setopt($ch2, CURLOPT_HEADER, 0);

// 创建批处理cURL句柄
$mh = curl_multi_init();

// 增加2个句柄
curl_multi_add_handle($mh,$ch1);
curl_multi_add_handle($mh,$ch2);

$running=null;
// 执行批处理句柄
do {
    usleep(10000);
    curl_multi_exec($mh,$running);
} while ($running > 0);

// 关闭全部句柄
curl_multi_remove_handle($mh, $ch1);
curl_multi_remove_handle($mh, $ch2);
curl_multi_close($mh);
?>
```

## 链接

- [curl函数](directory.md)
- 上一节：[curl_multi_info_read](curl_multi_info_read.md)
- 下一节：[curl_multi_remove_handle](curl_multi_remove_handle.md)
