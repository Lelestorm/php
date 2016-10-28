
## curl_error()
(PHP 4 >= 4.0.3, PHP 5, PHP 7)  
curl_error — 返回一个保护当前会话最近一次错误的字符串

#### 说明  
```php
string curl_error ( resource $ch )
```

返回一条最近一次cURL操作明确的文本的错误信息。  

#### 参数   
$ch  
&nbsp;&nbsp;&nbsp;&nbsp;由 curl_init() 返回的 cURL 句柄。  

#### 返回值
返回错误信息或 '' (空字符串) 如果没有任何错误发生。

#### 范例   
---  
Example #1 curl_error() example
```php
<?php
// 创建一个指向一个不存在的位置的cURL句柄
$ch = curl_init('http://404.php.net/');
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);

if(curl_exec($ch) === false){
    echo 'Curl error: ' . curl_error($ch);
}else{
    echo '操作完成没有任何错误';
}

// 关闭句柄
curl_close($ch);
?>
```

#### 参见
* [Curl error codes](http://curl.haxx.se/libcurl/c/libcurl-errors.html)

## 链接

- [curl函数](directory.md)
- 上一节：[curl_errno](curl_errno.md)
- 下一节：[curl_escape](curl_escape.md)
