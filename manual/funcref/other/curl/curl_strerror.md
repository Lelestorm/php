
## curl_strerror()
(PHP 5 >= 5.5.0, PHP 7)  
curl_strerror — 返回给定错误码的错误描述

#### 说明  
```php
string curl_strerror ( int $errornum )
```

返回给定错误代码的错误消息文本描述。

#### 参数   
$errornum  
&nbsp;&nbsp;&nbsp;&nbsp; 一个 [» cURL 错误码](https://curl.haxx.se/libcurl/c/libcurl-errors.html) 常量。  

#### 返回值
返回一个错误描述，无效错误码返回NULL。

#### 范例   
---  
Example #1 curl_strerror() example  

```php
<?php
// 创建一个带URL协议的cURL资源句柄
$ch = curl_init("htp://example.com/");

// 执行cURL会话
curl_exec($ch);

// 检测错误并获取错误描述
if($errno = curl_errno($ch)) {
    $error_message = curl_strerror($errno);
    echo "cURL error ({$errno}):\n {$error_message}";
}

// 关闭句柄
curl_close($ch);

// 以上例程会输出：
cURL error (1):

Unsupported protocol
?>
```

## 链接

- [curl函数](directory.md)
- 上一节：[curl_share_setopt](curl_share_setopt.md)
- 下一节：[curl_unescape](curl_unescape.md)
