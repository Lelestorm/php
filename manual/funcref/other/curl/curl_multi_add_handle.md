
## curl_multi_add_handle()
(PHP 5, PHP 7)  
curl_multi_add_handle — 向curl批处理会话中添加单独的curl句柄

#### 说明  
```php
int curl_multi_add_handle ( resource $mh , resource $ch )
```

增加 $ch 句柄到批处理会话 $mh

#### 参数   
$mh  
&nbsp;&nbsp;&nbsp;&nbsp;由 curl_multi_init() 返回的 cURL 多个句柄。  

$ch  
&nbsp;&nbsp;&nbsp;&nbsp;由 curl_init() 返回的 cURL 句柄。  

#### 返回值
成功时返回0，失败时返回CURLM_XXX之一的错误码。

#### 范例   
---  
Example #1 curl_multi_add_handle() example  
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
} while($running > 0);

// 关闭全部句柄
curl_multi_remove_handle($mh, $ch1);
curl_multi_remove_handle($mh, $ch2);
curl_multi_close($mh);
?>
```

#### 参见
- [curl_multi_init()](curl_multi_init.md) - 返回一个新cURL批处理句柄
- [curl_multi_remove_handle()](curl_multi_remove_handle.md) - 移除curl批处理句柄资源中的某个句柄资源

## 链接

- [curl函数](directory.md)
- 上一节：[curl_init](curl_init.md)
- 下一节：[curl_multi_close](curl_multi_close.md)
