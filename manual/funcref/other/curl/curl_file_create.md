
## curl_exec()
(PHP 5 >= 5.5.0, PHP 7)  
curl_file_create — 创建一个 CURLFile 对象

#### 说明  

此函数是该函数的别名： CURLFile::__construct()

#### 范例   
```php
For PHP < 5.5:

<?php

if (!function_exists('curl_file_create')) {
    function curl_file_create($filename, $mimetype = '', $postname = '') {
        return "@$filename;filename="
            . ($postname ?: basename($filename))
            . ($mimetype ? ";type=$mimetype" : '');
    }
}

?>
```

#### 参见
* [CURLFile::__construct()]() - 

## 链接

- [curl函数](directory.md)
- 上一节：[curl_exec](curl_exec.md)
- 下一节：[curl_getinfo](curl_getinfo.md)
