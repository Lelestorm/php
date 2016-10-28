
## curl_setopt_array()
(PHP 5 >= 5.1.3, PHP 7)  
url_setopt_array — 为cURL传输会话批量设置选项

#### 说明  
```php
bool curl_setopt_array ( resource $ch , array $options )
```

为cURL传输会话批量设置选项。这个函数对于需要设置大量的cURL选项是非常有用的，不需要重复地调用curl_setopt()。

#### 参数   
$ch  
&nbsp;&nbsp;&nbsp;&nbsp;由 curl_init() 返回的 cURL 句柄。  

$options  
&nbsp;&nbsp;&nbsp;&nbsp;一个数组（array）用来确定将被设置的选项及其值。数组的键值必须是一个有效的curl_setopt()常量或者是它们对等的整数值。

#### 返回值
如果全部的选项都被成功设置，返回TRUE。如果一个选项不能被成功设置，马上返回FALSE，忽略其后的任何在options数组中的选项。

#### 范例   
---  
Example #1 初始化一个新的cURL会话并抓取一个web页面

```php
<?php
// 创建一个新cURL资源
$ch = curl_init();

// 设置URL和相应的选项
$options = array(
            CURLOPT_URL => 'http://www.example.com/',
            CURLOPT_HEADER => false
        );

curl_setopt_array($ch, $options);

// 抓取URL并把它传递给浏览器
curl_exec($ch);

// 关闭cURL资源，并且释放系统资源
curl_close($ch);
?>
```

早于PHP 5.1.3这个函数可以做如下模拟：  

```php
<?php
// 对curl_setopt_array()的等价实现
if (!function_exists('curl_setopt_array')) {
   function curl_setopt_array(&$ch, $curl_options)
   {
       foreach ($curl_options as $option => $value) {
           if (!curl_setopt($ch, $option, $value)) {
               return false;
           } 
       }
       return true;
   }
}
?>
```

#### Note:  
就curl_setopt()来说，传递一个数组到CURLOPT_POST将会把数据以multipart/form-data的方式编码，然而传递一个URL-encoded字符串将会以application/x-www-form-urlencoded的方式对数据进行编码。

## 链接

- [curl函数](directory.md)
- 上一节：[curl_reset](curl_reset.md)
- 下一节：[curl_setopt](curl_setopt.md)
