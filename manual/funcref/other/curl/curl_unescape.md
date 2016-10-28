
## curl_unescape()
(PHP 5 >= 5.5.0, PHP 7)  
curl_unescape — 解码给定的 URL 编码的字符串

#### 说明  
```php
string curl_unescape ( resource $ch , string $str )
```

该函数解码给定的 URL 编码的字符串。

#### 参数   
$ch  
&nbsp;&nbsp;&nbsp;&nbsp;由 curl_init() 返回的 cURL 句柄。  

$str  
&nbsp;&nbsp;&nbsp;&nbsp;需要解码的 URL 编码字符串

#### 返回值
返回解码后的字符串 或者在失败时返回 FALSE。

#### 范例   
---  
Example #1 curl_escape() example  

这个范例将会检查当前cURL版本使用curl_version()返回的'features'位掩码中哪些特性是可用的。

```php
<?php
// 创建一个 curl 句柄
$ch = curl_init('http://example.com/redirect.php');

// 发送 HTTP 请求并且遵循重定向
curl_setopt($ch, CURLOPT_FOLLOWLOCATION, 1);
curl_exec($ch);

// 获取最后的有效 URL
$effective_url = curl_getinfo($ch, CURLINFO_EFFECTIVE_URL);
// 结果： "http://example.com/show_location.php?loc=M%C3%BCnchen"

// 解码这个 URL
$effective_url_decoded = curl_unescape($ch, $effective_url);
// "http://example.com/show_location.php?loc=München"

// 关闭句柄
curl_close($ch);
?>
```

#### Notes:  
curl_unescape() 不会将加号 (+) 解码成空格。而 urldecode() 会。  

## 链接

- [curl函数](directory.md)
- 上一节：[curl_strerror](curl_strerror.md)
- 下一节：[curl_version](curl_version.md)
