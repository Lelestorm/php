
## curl_multi_remove_handle()
(PHP 5, PHP 7)  
curl_multi_remove_handle — 移除curl批处理句柄资源中的某个句柄资源

#### 说明  
```php
int curl_multi_remove_handle ( resource $mh , resource $ch )
```

从给定的批处理句柄mh中移除ch句柄。当ch句柄被移除以后，仍然可以合法地用curl_exec()执行这个句柄。当正在移除的句柄正在被使用，在处理的过程中所有的传输任务会被终止。

#### 参数   
$mh  
&nbsp;&nbsp;&nbsp;&nbsp;由 curl_multi_init() 返回的 cURL 多个句柄。  

$ch  
&nbsp;&nbsp;&nbsp;&nbsp;由 curl_init() 返回的 cURL 句柄。

#### 返回值
成功时返回一个cURL句柄，失败时返回FALSE。

## 链接

- [curl函数](directory.md)
- 上一节：[curl_multi_init](curl_multi_init.md)
- 下一节：[curl_multi_select](curl_multi_select.md)
