
## curl_escape()
(PHP 5 >= 5.5.0, PHP 7)  
curl_escape — 使用 URL 编码给定的字符串

#### 说明  
```php
string curl_escape ( resource $ch , string $str )
```

该函数使用 URL 根据» RFC 3986编码给定的字符串。  

#### 参数   
$ch  
&nbsp;&nbsp;&nbsp;&nbsp;由 curl_init() 返回的 cURL 句柄。  

$str   
&nbsp;&nbsp;&nbsp;&nbsp;需要编码的字符串

#### 返回值
没有返回值   

#### 范例   
---  
Example #1 初始化一个cURL会话来获取一个网页
```php
<?php
// 创建一个 curl 句柄
$ch = curl_init();

// 把编码后的字符串当做一个 GET 参数
$location = curl_escape($ch, 'Hofbräuhaus / München');
// 结果： Hofbr%C3%A4uhaus%20%2F%20M%C3%BCnchen

// 用编码好的字符串组装一个 URL
$url = "http://example.com/add_location.php?location={$location}";
// 结果： http://example.com/add_location.php?location=Hofbr%C3%A4uhaus%20%2F%20M%C3%BCnchen

// 发送 HTTP 请求并关闭句柄
curl_setopt($ch, CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_exec($ch);
curl_close($ch);
?>
```

#### 参见
* [curl_unescape()](curl_unescape.md) - 解码给定的 URL 编码的字符串
* [urlencode() ](javascript:;) - 编码 URL 字符串
* [rawurlencode()](javascript:;) - 按照 RFC 3986 对 URL 进行编码
* [» RFC 3986](http://www.faqs.org/rfcs/rfc3986)

## 链接

- [curl函数](directory.md)
- 上一节：[curl_error](curl_error.md)
- 下一节：[curl_exec](curl_exec.md)
