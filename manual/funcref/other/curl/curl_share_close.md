
## curl_share_close()
(PHP 5 >= 5.5.0, PHP 7)  
curl_share_close — 关闭一个 cURL 共享句柄

#### 说明  
```php
void curl_share_close ( resource $sh )
```

关闭一个 cURL 共享句柄并释放所有资源。

#### 参数   
$sh  
&nbsp;&nbsp;&nbsp;&nbsp;由 curl_share_init() 返回的 cURL 共享句柄。  

#### 返回值
没有返回值。  

#### 范例   
---  
Example #1 curl_share_close() example  
This example will create a cURL share handle, add two cURL handles to it, and then run them with cookie data sharing.

```php
<?php
// Create cURL share handle and set it to share cookie data
$sh = curl_share_init();
curl_share_setopt($sh, CURLSHOPT_SHARE, CURL_LOCK_DATA_COOKIE);

// Initialize the first cURL handle and assign the share handle to it
$ch1 = curl_init("http://example.com/");
curl_setopt($ch1, CURLOPT_SHARE, $sh);

// Execute the first cURL handle
curl_exec($ch1);

// Initialize the second cURL handle and assign the share handle to it
$ch2 = curl_init("http://php.net/");
curl_setopt($ch2, CURLOPT_SHARE, $sh);

// Execute the second cURL handle
//  all cookies from $ch1 handle are shared with $ch2 handle
curl_exec($ch2);

// Close the cURL share handle
curl_share_close($sh);

// Close the cURL handles
curl_close($ch1);
curl_close($ch2);
?>
```

## 链接

- [curl函数](directory.md)
- 上一节：[curl_setopt](curl_setopt.md)
- 下一节：[curl_share_init](curl_share_init.md)
