
## curl_share_init()
(PHP 5 >= 5.5.0, PHP 7)  
curl_share_init — 初始化一个 cURL 共享句柄

#### 说明  
```php
resource curl_share_init ( void )
```

允许在 cURL 之间共享数据。

#### 参数   
此函数没有参数。  

#### 返回值
返回一个 cURL 共享句柄资源. 

#### 范例   
---  
Example #1 curl_share_init() example  

这个例子将会创建一个 cURL 共享句柄, 创建 2 个 cURL 句柄，把它们加到共享句柄, 并运行共享cookie数据。

```php
<?php
// 创建一个 cURL share 句柄，并设置共享cookie
$sh = curl_share_init();
curl_share_setopt($sh, CURLSHOPT_SHARE, CURL_LOCK_DATA_COOKIE);

// 初始化第一个 cURL 句柄，并分配共享句柄
$ch1 = curl_init("http://example.com/");
curl_setopt($ch1, CURLOPT_SHARE, $sh);

// 执行
curl_exec($ch1);

// 初始化第二个 cURL 句柄，并分配共享句柄
$ch2 = curl_init("http://php.net/");
curl_setopt($ch2, CURLOPT_SHARE, $sh);

// 执行
//  $ch1和$ch2共享所有cookie
curl_exec($ch2);

// 关闭 cURL share handle
curl_share_close($sh);

// 关闭 cURL handles
curl_close($ch1);
curl_close($ch2);
?>
```

## 链接

- [curl函数](directory.md)
- 上一节：[curl_share_close](curl_share_close.md)
- 下一节：[curl_share_setopt](curl_share_setopt.md)
