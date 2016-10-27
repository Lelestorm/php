[目录](directory.md)  
## curl_setopt()
(PHP 4 >= 4.0.2, PHP 5, PHP 7)  
curl_setopt — 设置一个cURL传输选项

#### 说明  
```php
bool curl_setopt ( resource $ch , int $option , mixed $value )
```

为 cURL 会话句柄设置选项。  

#### 参数   
<span style="color: #369;">$ch</span> 

&nbsp;&nbsp;&nbsp;&nbsp;由 curl_init() 返回的 cURL 句柄。   
<span style="color: #369;">$option</span> 

&nbsp;&nbsp;&nbsp;&nbsp;需要设置的CURLOPT_XXX选项。  
<span style="color: #369;">$value</span>   
&nbsp;&nbsp;&nbsp;&nbsp;将设置在option选项上的值。  

**<p style="color: #369;">以下 `option` 参数的 `value`应该被设置成 `bool` 类型：</p>**  

<table class="doctable informaltable">
    <thead>
        <tr>
            <th>选项</th>
            <th><code>value</code></th>
            <th>备注</th>
        </tr>
    </thead>

    <tbody class="tbody">
        <tr>
            <td><strong><code>CURLOPT_AUTOREFERER</code></strong></td>
            <td>
            <strong><code>TRUE</code></strong> 时将根据 <em>Location:</em> 重定向时，自动设置 header 中的<em>Referer:</em>信息。
            </td>
            <td></td>
        </tr>

          <tr>
           <td><strong><code>CURLOPT_BINARYTRANSFER</code></strong></td>
           <td>
            设为 <strong><code>TRUE</code></strong> ，将在启用 <strong><code>CURLOPT_RETURNTRANSFER</code></strong> 时，返回原生的（Raw）输出。
           </td>
           <td>
            从 PHP 5.1.3 开始，此选项不再有效果：使用
           <strong><code>CURLOPT_RETURNTRANSFER</code></strong> 后总是会返回原生的（Raw）内容。
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_COOKIESESSION</code></strong></td>
           <td>
            设为 <strong><code>TRUE</code></strong>  时将开启新的一次 cookie 会话。它将强制 libcurl 忽略之前会话时存的其他 cookie。
            libcurl 在默认状况下无论是否为会话，都会储存、加载所有 cookie。会话 cookie 是指没有过期时间，只存活在会话之中。
           </td>
           <td>
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_CERTINFO</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong> 将在安全传输时输出 SSL 证书信息到 <em>STDERR</em>。
           </td>
           <td>
            在 cURL 7.19.1 中添加。
            PHP 5.3.2 后有效。
            需要开启 <strong><code>CURLOPT_VERBOSE</code></strong> 才有效。
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_CONNECT_ONLY</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong> 将让库执行所有需要的代理、验证、连接过程，但不传输数据。此选项用于
            HTTP、SMTP 和 POP3。
           </td>
           <td>
            在 7.15.2 中添加。
            PHP 5.5.0 起有效。
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_CRLF</code></strong></td>
           <td>
            启用时将Unix的换行符转换成回车换行符。
           </td>
           <td>
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_DNS_USE_GLOBAL_CACHE</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong> 会启用一个全局的DNS缓存。此选项非线程安全的，默认已开启。
           </td>
           <td>
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_FAILONERROR</code></strong></td>
           <td>
           当 HTTP 状态码大于等于 400，<strong><code>TRUE</code></strong> 将将显示错误详情。 默认情况下将返回页面，忽略 HTTP 代码。
           </td>
           <td>
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_FILETIME</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong>  时，会尝试获取远程文档中的修改时间信息。
            信息可通过<span class="function"><a href="function.curl-getinfo.php" class="function">curl_getinfo()</a></span>函数的<code class="parameter">CURLINFO_FILETIME</code> 选项获取。
           </td>
           <td>
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_FOLLOWLOCATION</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong>  时将会根据服务器返回 HTTP 头中的 <em>"Location: "</em> 重定向。（注意：这是递归的，<em>"Location: "</em> 发送几次就重定向几次，除非设置了 <strong><code>CURLOPT_MAXREDIRS</code></strong>，限制最大重定向次数。）。
           </td>
           <td>
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_FORBID_REUSE</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong> 在完成交互以后强制明确的断开连接，不能在连接池中重用。
           </td>
           <td>
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_FRESH_CONNECT</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong> 强制获取一个新的连接，而不是缓存中的连接。
           </td>
           <td>
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_FTP_USE_EPRT</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong> 时，当 FTP 下载时，使用 EPRT (和 LPRT)命令。 设置为 <strong><code>FALSE</code></strong> 时禁用 EPRT 和 LPRT，仅仅使用PORT 命令。
           </td>
           <td>
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_FTP_USE_EPSV</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong> 时，在FTP传输过程中，回到 PASV 模式前，先尝试 EPSV 命令。设置为 <strong><code>FALSE</code></strong> 时禁用 EPSV。
           </td>
           <td>
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_FTP_CREATE_MISSING_DIRS</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong> 时，当 ftp 操作不存在的目录时将创建它。
           </td>
           <td>
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_FTPAPPEND</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong> 为追加写入文件，而不是覆盖。
           </td>
           <td>
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_TCP_NODELAY</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong> 时禁用 TCP 的 Nagle 算法，就是减少网络上的小包数量。
           </td>
           <td>
             PHP 5.2.1 有效，编译时需要 libcurl 7.11.2 及以上。
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_FTPASCII</code></strong></td>
           <td>
            <strong><code>CURLOPT_TRANSFERTEXT</code></strong> 的别名。
           </td>
           <td>
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_FTPLISTONLY</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong> 时只列出 FTP 目录的名字。
           </td>
           <td>
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_HEADER</code></strong></td>
           <td>
            启用时会将头文件的信息作为数据流输出。
           </td>
           <td>
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLINFO_HEADER_OUT</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong> 时追踪句柄的请求字符串。
           </td>
           <td>
            从 PHP 5.1.3 开始可用。<strong><code>CURLINFO_</code></strong> 的前缀是有意的(intentional)。
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_HTTPGET</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong>  时会设置 HTTP 的 method 为 GET，由于默认是 GET，所以只有 method 被修改时才需要这个选项。
           </td>
           <td>
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_HTTPPROXYTUNNEL</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong>  会通过指定的 HTTP 代理来传输。
           </td>
           <td>
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_MUTE</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong>  时将完全静默，无论是何 cURL 函数。
           </td>
           <td>
           在 cURL 7.15.5  中移出（可以使用 CURLOPT_RETURNTRANSFER 作为代替）
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_NETRC</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong>  时，在连接建立时，访问<var class="filename">~/.netrc</var>文件获取用户名和密码来连接远程站点。
           </td>
           <td>
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_NOBODY</code></strong></td>
           <td>
           <strong><code>TRUE</code></strong>  时将不输出 BODY 部分。同时 Mehtod 变成了 HEAD。修改为  <strong><code>FALSE</code></strong> 时不会变成 GET。
           </td>
           <td>
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_NOPROGRESS</code></strong></td>
           <td><p class="para">
            <strong><code>TRUE</code></strong> 时关闭 cURL 的传输进度。
            </p><blockquote class="note"><p><strong class="note">Note</strong>: 
             </p><p class="para">
              PHP 默认自动设置此选项为 <strong><code>TRUE</code></strong>，只有为了调试才需要改变设置。
             </p>
            </blockquote>
            </td>
           <td>
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_NOSIGNAL</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong> 时忽略所有的 cURL 传递给 PHP 进行的信号。在 SAPI 多线程传输时此项被默认启用，所以超时选项仍能使用。
           </td>
           <td>
            cURL 7.10时被加入。
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_POST</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong> 时会发送 POST 请求，类型为：<em>application/x-www-form-urlencoded</em>，是 HTML 表单提交时最常见的一种。
           </td>
           <td>
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_PUT</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong> 时允许 HTTP 发送文件。要被 PUT 的文件必须在 <strong><code>CURLOPT_INFILE</code></strong>和<strong><code>CURLOPT_INFILESIZE</code></strong> 中设置。
           </td>
           <td>
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_RETURNTRANSFER</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong>  将<span class="function"><a href="function.curl-exec.php" class="function">curl_exec()</a></span>获取的信息以字符串返回，而不是直接输出。
           </td>
           <td>
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_SAFE_UPLOAD</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong> 禁用 <em>@</em> 前缀在 <strong><code>CURLOPT_POSTFIELDS</code></strong> 中发送文件。
            
            意味着 <em>@</em> 可以在字段中安全得使用了。 
            可使用 <a href="class.curlfile.php" class="classname">CURLFile</a> 作为上传的代替。
           </td>
           
           
           
           
           <td>
            PHP 5.5.0 中添加，默认值 <strong><code>FALSE</code></strong>。
            PHP 5.6.0 改默认值为 <strong><code>TRUE</code></strong>。
           </td>
          </tr>

          
          
          
          
          
          
          
          
          
          
          
          
          
          
          
          
          
          
          
          
          
          
          
          
          
          
          
          
          
          
          
          
          <tr>
           <td><strong><code>CURLOPT_SSL_VERIFYPEER</code></strong></td>
           <td>
            <strong><code>FALSE</code></strong>  禁止 cURL 验证对等证书（peer's
            certificate）。要验证的交换证书可以在 <strong><code>CURLOPT_CAINFO</code></strong> 选项中设置，或在 <strong><code>CURLOPT_CAPATH</code></strong>中设置证书目录。
           </td>
           <td>
            自cURL 7.10开始默认为 <strong><code>TRUE</code></strong>。从 cURL 7.10开始默认绑定安装。
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_TRANSFERTEXT</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong>  对 FTP 传输使用 ASCII 模式。对于LDAP，它检索纯文本信息而非 HTML。在 Windows 系统上，系统不会把 <em>STDOUT</em> 设置成二进制 模式。
           </td>
           <td>
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_UNRESTRICTED_AUTH</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong> 在使用<strong><code>CURLOPT_FOLLOWLOCATION</code></strong>重定向 header 中的多个 location 时继续发送用户名和密码信息，哪怕主机名已改变。
           </td>
           <td>
           </td>
          </tr>

          <tr>
           <td><strong><code>CURLOPT_UPLOAD</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong>  准备上传。
           </td>
           <td>
           </td>
          </tr>

          
          
          
          
          
          <tr>
           <td><strong><code>CURLOPT_VERBOSE</code></strong></td>
           <td>
            <strong><code>TRUE</code></strong> 会输出所有的信息，写入到<em>STDERR</em>，或在<strong><code>CURLOPT_STDERR</code></strong>中指定的文件。
           </td>
           <td>
           </td>
          </tr>

         </tbody>
        
       </table>
###### 返回值
成功时返回 TRUE， 或者在失败时返回 FALSE。

###### Note:
传递一个数组到CURLOPT_POSTFIELDS，cURL会把数据编码成 multipart/form-data，而然传递一个URL-encoded字符串时，数据会被编码成 application/x-www-form-urlencoded。

## 链接

- [curl函数](directory.md)
- 上一节：[curl_init](curl_init.md)
- 下一节：[curl_setopt](curl_setopt.md)
