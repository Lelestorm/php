
## curl_multi_select()
(PHP 5, PHP 7)  
curl_multi_select — 等待所有cURL批处理中的活动连接

#### 说明  
```php
int curl_multi_select ( resource $mh [, float $timeout = 1.0 ] )
```

阻塞直到cURL批处理连接中有活动连接。  

#### 参数   
$mh  
&nbsp;&nbsp;&nbsp;&nbsp;由 curl_multi_init() 返回的 cURL 多个句柄。  

$timeout  
&nbsp;&nbsp;&nbsp;&nbsp;以秒为单位，等待响应的时间。

#### 返回值
成功时返回描述符集合中描述符的数量。失败时，select失败时返回-1，否则返回超时(从底层的select系统调用).

## 链接

- [curl函数](directory.md)
- 上一节：[curl_multi_remove_handle](curl_multi_remove_handle.md)
- 下一节：[curl_multi_setopt](curl_multi_setopt.md)
