
## curl_multi_setopt()
(PHP 5 >= 5.5.0, PHP 7)  
curl_multi_setopt — 为 cURL 并行处理设置一个选项

#### 说明  
```php
bool curl_multi_setopt ( resource $mh , int $option , mixed $value )
```

#### 参数   
$mh  
&nbsp;&nbsp;&nbsp;&nbsp;由 curl_multi_init() 返回的 cURL 多个句柄。  

$value  
&nbsp;&nbsp;&nbsp;&nbsp;将要设置给 option 的值。  
&nbsp;&nbsp;&nbsp;&nbsp;在 option 参数为下列值时 value 需要为 int 类型：
<table>
    <thead><tr><td>Option 的值</td><td>value </td></tr></thead>
    <tbody>
        <tr>
            <td>CURLMOPT_PIPELINING</td>
            <td>传入 1 来启用或 0 来禁用。 在并行处理时启用管道模式 将会尽可能地使用管线化的 HTTP （译注：HTTP长连接）来 传输，这意味着如果你提交第二个请求，这个请求将会使用 已经存在的链接，第二个请求将会被送入同一个链接的“管 道”中。</td>
        </tr>
        <tr>
            <td>CURLMOPT_MAXCONNECTS</td>
            <td>传入一个数字来指定 libcurl 可以同时缓存的活跃链接的数量。默认值为 10。当缓存写满时， lincurl 将关闭较早创建的链接来创建新的链接。</td>
        </tr>
    </tbody>
</table>

#### 返回值
成功时返回 TRUE， 或者在失败时返回 FALSE。  

## 链接

- [curl函数](directory.md)
- 上一节：[curl_multi_select](curl_multi_select.md)
- 下一节：[curl_multi_strerror](curl_multi_strerror.md)
