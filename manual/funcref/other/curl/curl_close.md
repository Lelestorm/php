[目录](directory.md)  
## curl_close()
(PHP 4 >= 4.0.2, PHP 5, PHP 7)  
curl_close — 关闭一个cURL会话  

###### 说明  
```php
void curl_close ( resource $ch )
```

关闭一个cURL会话并且释放所有资源。cURL句柄ch 也会被释放。  

###### 参数   
$ch  
&nbsp;&nbsp;&nbsp;&nbsp;由 curl_init() 返回的 cURL 句柄。

###### 返回值
没有返回值。

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
- 下一节：[curl_copy_handle](curl_copy_handle.md)
