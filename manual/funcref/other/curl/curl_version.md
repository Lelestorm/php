
## curl_version()
(PHP 5 >= 5.5.0, PHP 7)  
curl_version — 获取cURL版本信息

#### 说明  
```php
array curl_version ([ int $age = CURLVERSION_NOW ] )
```

返回关于cURL的版本信息。

#### 参数   
$age  

#### 返回值
返回一个相关的数组包含如下元素：
```php
[
    'version_number' => 'cURL 24位版本号',
    'version' => 'cURL 版本号，字符串形式',
    'ssl_version_number' => 'OpenSSL 24 位版本号',
    'ssl_version' => 'OpenSSL 版本号，字符串形式',
    'libz_version'  => 'zlib 版本号，字符串形式',
    'host' => '关于编译cURL主机的信息',
    'age' => '',
    'features' => '一个CURL_VERSION_XXX常量的位掩码',
    'protocols' => '一个cURL支持的协议名字的数组'
]
```

#### 范例   
---  
Example #1 curl_version() example  

这个范例将会检查当前cURL版本使用curl_version()返回的'features'位掩码中哪些特性是可用的。

```php
<?php
// 获取cURL版本数组
$version = curl_version();

// 在cURL编译版本中使用位域来检查某些特性
$bitfields = Array(
        'CURL_VERSION_IPV6', 
        'CURL_VERSION_KERBEROS4', 
        'CURL_VERSION_SSL', 
        'CURL_VERSION_LIBZ'
    );

foreach($bitfields as $feature)
{
    echo $feature . ($version['features'] & constant($feature) ? ' matches' : ' does not match');
    echo PHP_EOL;
}
?>
```

## 链接

- [curl函数](directory.md)
- 上一节：[curl_unescape](curl_unescape.md)
- 下一节：[]()
