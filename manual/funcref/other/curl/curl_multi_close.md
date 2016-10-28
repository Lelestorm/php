
## curl_multi_close()
(PHP 5, PHP 7)  
curl_multi_close — 关闭一组cURL句柄

#### 说明  
```php
void curl_multi_close ( resource $mh )
```

关闭一组cURL句柄。  

#### 参数   
$mh  
&nbsp;&nbsp;&nbsp;&nbsp;由 curl_multi_init() 返回的 cURL 多个句柄。  

#### 返回值
没有返回值   

#### 范例   
---  
Example #1 curl_multi_close() example  
这个范例将会创建2个cURL句柄，把它们加到批处理句柄，然后并行地运行它们。  

```php
<?php
// 创建一对cURL资源
$ch1 = curl_init();
$ch2 = curl_init();

// 设置URL和相应的选项
curl_setopt($ch1, CURLOPT_URL, "http://www.example.com/");
curl_setopt($ch1, CURLOPT_HEADER, 0);
curl_setopt($ch2, CURLOPT_URL, "http://www.php.net/");
curl_setopt($ch2, CURLOPT_HEADER, 0);

// 创建批处理cURL句柄
$mh = curl_multi_init();

// 增加2个句柄
curl_multi_add_handle($mh,$ch1);
curl_multi_add_handle($mh,$ch2);

$running=null;
// 执行批处理句柄
do {
    curl_multi_exec($mh,$running);
} while ($running > 0);

// 关闭全部句柄
curl_multi_remove_handle($mh, $ch1);
curl_multi_remove_handle($mh, $ch2);
curl_multi_close($mh);
?>
```

## 链接

- [curl函数](directory.md)
- 上一节：[curl_multi_add_handle](curl_multi_add_handle.md)
- 下一节：[curl_multi_exec](curl_multi_exec.md)
