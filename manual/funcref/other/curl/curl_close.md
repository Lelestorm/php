[目录](directory.md)  
## curl_close()
(PHP 4 >= 4.0.2, PHP 5, PHP 7)  
curl_close — 关闭一个cURL会话  

###### 说明  
```php
resource curl_init ([ string $url = NULL ] )
```

初始化一个新的会话，返回一个cURL句柄，供curl_setopt(), curl_exec()和curl_close() 函数使用。  

###### 参数   
$url  
&nbsp;&nbsp;&nbsp;&nbsp;如果提供了该参数，CURLOPT_URL 选项将会被设置成这个值。你也可以使用curl_setopt()函数手动地设置这个值。

###### 返回值
如果成功，返回一个cURL句柄，出错返回 FALSE。

###### 范例   
---  
Example #1 初始化一个cURL会话来获取一个网页
```php
<?php
// 创建一个新cURL资源
$ch = curl_init();

// 设置URL和相应的选项
curl_setopt($ch, CURLOPT_URL, "http://www.example.com/");
curl_setopt($ch, CURLOPT_HEADER, 0);

// 抓取URL并把它传递给浏览器
curl_exec($ch);

// 关闭cURL资源，并且释放系统资源
curl_close($ch);
?>
```

## 链接

- [curl函数](directory.md)
- 上一节：[#](#)
- 下一节：[curl_setopt](curl_setopt.md)
