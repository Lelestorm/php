
## curl_pause()
(PHP 5 >= 5.5.0, PHP 7)  
curl_multi_exec — 暂停和恢复运行 cURL 句柄的连接

#### 说明  
```php
int curl_pause ( resource $ch , int $bitmask )
```

处理在栈中的每一个句柄。无论该句柄需要读取或写入数据都可调用此方法。  

#### 参数   
$ch  
&nbsp;&nbsp;&nbsp;&nbsp;由 curl_init() 返回的 cURL 句柄。  

$bitmask  
&nbsp;&nbsp;&nbsp;&nbsp;一个 CURLPAUSE_* 常量.

#### 返回值
返回错误号 ，（CURLE_OK 没有错误）。

## 链接

- [curl函数](directory.md)
- 上一节：[curl_multi_strerror](curl_multi_strerror.md)
- 下一节：[curl_reset](curl_reset.md)
