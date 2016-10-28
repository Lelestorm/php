
## curl_exec()
(PHP 4 >= 4.0.2, PHP 5, PHP 7)  
curl_exec — 执行一个cURL会话

#### 说明  
```php
mixed curl_exec ( resource $ch )
```

执行给定的cURL会话。  

这个函数应该在初始化一个cURL会话并且全部的选项都被设置后被调用。 

#### 参数   
$ch  
&nbsp;&nbsp;&nbsp;&nbsp;由 curl_init() 返回的 cURL 句柄。  

#### 返回值
成功时返回 TRUE， 或者在失败时返回 FALSE。 然而，如果 CURLOPT_RETURNTRANSFER选项被设置，函数执行成功时会返回执行的结果，失败时返回 FALSE 。   

#### 范例   
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

#### 参见
* [curl_multi_exec()](curl_multi_exec.md) - 运行当前 cURL 句柄的子连接

## 链接

- [curl函数](directory.md)
- 上一节：[curl_escape](curl_getinfo.md)
- 下一节：[curl_file_create](curl_file_create.md)
