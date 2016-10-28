
## curl_multi_getcontent()
(PHP 5, PHP 7)  
curl_multi_getcontent — 如果设置了CURLOPT_RETURNTRANSFER，则返回获取的输出的文本流

#### 说明  
```php
string curl_multi_getcontent ( resource $ch )
```

如果CURLOPT_RETURNTRANSFER作为一个选项被设置到一个具体的句柄，那么这个函数将会以字符串的形式返回那个cURL句柄获取的内容。

#### 参数   
$ch  
&nbsp;&nbsp;&nbsp;&nbsp;由 curl_init() 返回的 cURL 句柄  

#### 返回值
如果设置了CURLOPT_RETURNTRANSFER，则返回获取的输出的文本流。  

#### 参见  
- [curl_multi_init()](curl_multi_init.md) - 返回一个新cURL批处理句柄

## 链接

- [curl函数](directory.md)
- 上一节：[curl_multi_exec](curl_multi_exec.md)
- 下一节：[curl_multi_info_read](curl_multi_info_read.md)
