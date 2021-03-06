
## curl_multi_info_read()
(PHP 5, PHP 7)  
curl_multi_info_read — 获取当前解析的cURL的相关传输信息

#### 说明  
```php
array curl_multi_info_read ( resource $mh [, int &$msgs_in_queue = NULL ] )
```

查询批处理句柄是否单独的传输线程中有消息或信息返回。消息可能包含诸如从单独的传输线程返回的错误码或者只是传输线程有没有完成之类的报告。  
  
重复调用这个函数，它每次都会返回一个新的结果，直到这时没有更多信息返回时，FALSE 被当作一个信号返回。通过msgs_in_queue返回的整数指出将会包含当这次函数被调用后，还剩余的消息数。  

```
Waring: 返回的资源指向的数据调用curl_multi_remove_handle()后将不会存在。
```

#### 参数   
$mh  
&nbsp;&nbsp;&nbsp;&nbsp;由 curl_multi_init() 返回的 cURL 多个句柄。  

$msgs_in_queue  
&nbsp;&nbsp;&nbsp;&nbsp;仍在队列中的消息数量。

#### 返回值
成功时返回相关信息的数组，失败时返回FALSE。  
```php
// 返回数组的内容
[
    'msg' => 'CURLMSG_DONE常量。其他返回值当前不可用。',
    'result' => 'CURLE_*常量之一。如果一切操作没有问题，将会返回CURLE_OK常量。',
    'handle' => 'cURL资源类型表明它有关的句柄。'
]
```

#### 范例   
---  
Example #1 curl_multi_info_read() example  
这个范例将会创建 2 个 cURL 句柄，把它们加到批处理句柄，然后并行地运行它们。 

```php
<?php
// 创建一对cURL资源
$urls = array(
   "http://www.cnn.com/",
   "http://www.bbc.co.uk/",
   "http://www.yahoo.com/"
);

$mh = curl_multi_init();

foreach ($urls as $i => $url) {
    $conn[$i] = curl_init($url);
    curl_setopt($conn[$i], CURLOPT_RETURNTRANSFER, 1);
    curl_multi_add_handle($mh, $conn[$i]);
}

do {
    $status = curl_multi_exec($mh, $active);
    $info = curl_multi_info_read($mh);
    if (false !== $info) {
        var_dump($info);
    }
} while ($status === CURLM_CALL_MULTI_PERFORM || $active);

foreach ($urls as $i => $url) {
    $res[$i] = curl_multi_getcontent($conn[$i]);
    curl_close($conn[$i]);
}

var_dump(curl_multi_info_read($mh));
?>
```

以上例程的输出类似于：

```php
<?php
    array(3) {
      ["msg"]=>
      int(1)
      ["result"]=>
      int(0)
      ["handle"]=>
      resource(5) of type (curl)
    }
    array(3) {
      ["msg"]=>
      int(1)
      ["result"]=>
      int(0)
      ["handle"]=>
      resource(7) of type (curl)
    }
    array(3) {
      ["msg"]=>
      int(1)
      ["result"]=>
      int(0)
      ["handle"]=>
      resource(6) of type (curl)
    }
    bool(false)
?>
```

## 链接

- [curl函数](directory.md)
- 上一节：[curl_multi_getcontent](curl_multi_getcontent.md)
- 下一节：[curl_multi_init](curl_multi_init.md)
