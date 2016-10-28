
## curl_share_setopt()
(PHP 5 >= 5.5.0,, PHP 7)  
curl_share_setopt — 设置一个cURL share handle 传输选项

#### 说明  
```php
bool curl_share_setopt ( resource $sh , int $option , string $value )
```

返回给定错误代码的错误消息文本描述。

#### 参数   
$sh  
&nbsp;&nbsp;&nbsp;&nbsp; 由 curl_share_init() 返回的 cURL 句柄。  

$option  
> - CURLSHOPT_SHARE ：指定共享数据类型。
> - CURLSHOPT_UNSHARE ：指定不共享的数据类型  

$value  
> - CURL_LOCK_DATA_COOKIE ：共享cookie数据。
> - CURL_LOCK_DATA_DNS ：共享DNS缓存。注意，使用 cURL multi（批处理）时，所有在相同批处理句柄中的子句柄默认共享DNS缓存
> - CURL_LOCK_DATA_SSL_SESSION ：链接同一服务器是，共享 SSL 会话（session） ID, 减少会话握手时间。注意：SSL session IDs 默认在同一句柄重复使用。

#### 返回值
成功时返回 TRUE， 或者在失败时返回 FALSE。

#### 范例   
---  
Example #1 curl_share_setopt() example  

This example will create a cURL share handle, add two cURL handles to it, and then run them with cookie data sharing.  

```php
<?php
// 创建一个共享cURL句柄，并设置共享cookie数据
$sh = curl_share_init();
curl_share_setopt($sh, CURLSHOPT_SHARE, CURL_LOCK_DATA_COOKIE);

// 初始第一个cURL句柄，并分配共享句柄。
$ch1 = curl_init("http://example.com/");
curl_setopt($ch1, CURLOPT_SHARE, $sh);

// 执行第一个句柄
curl_exec($ch1);

// 分配共享句柄给第二个初始化cURL，
$ch2 = curl_init("http://php.net/");
curl_setopt($ch2, CURLOPT_SHARE, $sh);

// 执行第二个句柄
//  $ch1和$ch2共享所有cookie
curl_exec($ch2);

// 关闭 cURL share handle
curl_share_close($sh);

// 关闭全部cURL资源
curl_close($ch1);
curl_close($ch2);
?>
```

## 链接

- [curl函数](directory.md)
- 上一节：[curl_share_init](curl_share_init.md)
- 下一节：[curl_strerror](curl_strerror.md)
