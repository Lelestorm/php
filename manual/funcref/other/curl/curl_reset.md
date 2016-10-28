
## curl_reset()
(PHP 5 >= 5.5.0, PHP 7)  
curl_reset — 重置一个 libcurl 会话句柄的所有的选项

#### 说明  
```php
void curl_reset ( resource $ch )
```

该函数将给定的 cURL 句柄所有选项重新设置为默认值。  

#### 参数   
$ch  
&nbsp;&nbsp;&nbsp;&nbsp;由 curl_init() 返回的 cURL 句柄。  

#### 返回值
没有返回值。

#### Note:   
curl_reset()也将重置curl_init()的URL参数。  
  
---  
```php
<?php
//Hack for php < 5.5 : 
function curl_reset(&$ch){
  $ch = curl_init();
}
?>
```

#### 参见  
- [curl_setopt()](curl_setopt.md) - 设置一个cURL传输选项

## 链接

- [curl函数](directory.md)
- 上一节：[curl_pause](curl_pause.md)
- 下一节：[curl_setopt_array](curl_setopt_array.md)
