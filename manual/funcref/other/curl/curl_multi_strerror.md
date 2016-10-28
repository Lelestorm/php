
## curl_multi_strerror()
(PHP 5 >= 5.5.0, PHP 7)  
curl_multi_strerror — 返回错误码的描述

#### 说明  
```php
string curl_multi_strerror ( int $errornum )
```

返回一个 URLM 错误码的文本描述。

#### 参数   
$errornum  
&nbsp;&nbsp;&nbsp;&nbsp; [» CURLM 错误码](https://curl.haxx.se/libcurl/c/libcurl-errors.html) 常量.  

#### 返回值
返回一个有效的错误码描述，失败返回NULL。  

#### 范例   
---  
Example #1 curl_multi_strerror() example  
这个范例将会创建 2 个 cURL 句柄，把它们加到批处理句柄，然后并行地运行它们。 

```php
<?php
// 创建一对cURL资源
$ch1 = curl_init("http://example.com"/);
$ch2 = curl_init("http://php.net/");

// 创建一个cURL批处理句柄
$mh = curl_multi_init();

// 增加2个批处理句柄
curl_multi_add_handle($mh, $ch1);
curl_multi_add_handle($mh, $ch2);

// 执行批处理句柄
do {
    $status = curl_multi_exec($mh, $active);
    // 检测错误
    if($status > 0) {
        // 显示错误信息
        echo "ERROR!\n " . curl_multi_strerror($status);
    }
} while ($status === CURLM_CALL_MULTI_PERFORM || $active);
?>
```

## 链接

- [curl函数](directory.md)
- 上一节：[curl_multi_setopt ](curl_multi_setopt.md)
- 下一节：[curl_pause](curl_pause.md)
