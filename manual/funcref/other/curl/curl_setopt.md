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
**$ch** 

&nbsp;&nbsp;&nbsp;&nbsp;由 curl_init() 返回的 cURL 句柄。   
**$option**

&nbsp;&nbsp;&nbsp;&nbsp;需要设置的CURLOPT_XXX选项。  
**$value**
&nbsp;&nbsp;&nbsp;&nbsp;将设置在option选项上的值。  

---

**以下 `option` 参数的 `value`应该被设置成 `bool` 类型：**  

<table>
    <thead>
        <tr>
            <th>选项</th>
            <th><code>value</code></th>
            <th>备注</th>
        </tr>
    </thead>

    <tbody>
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
            设为 <strong><code>TRUE</code></strong> ，将在启用 <strong><code>CURLOPT_RETURNTRANSFER</code></strong> 时，返回原生的（Raw）输出。</td>
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
            <td></td>
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
            <td>在 7.15.2 中添加。PHP 5.5.0 起有效。</td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_CRLF</code></strong></td>
            <td>启用时将Unix的换行符转换成回车换行符。</td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_DNS_USE_GLOBAL_CACHE</code></strong></td>
            <td>
            <strong><code>TRUE</code></strong> 会启用一个全局的DNS缓存。此选项非线程安全的，默认已开启。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_FAILONERROR</code></strong></td>
            <td>
            当 HTTP 状态码大于等于 400，<strong><code>TRUE</code></strong> 将将显示错误详情。 默认情况下将返回页面，忽略 HTTP 代码。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_FILETIME</code></strong></td>
            <td>
            <strong><code>TRUE</code></strong>  时，会尝试获取远程文档中的修改时间信息。
            信息可通过<span><a href="curl_getinfo.md">curl_getinfo()</a></span>函数的<code>CURLINFO_FILETIME</code> 选项获取。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_FOLLOWLOCATION</code></strong></td>
            <td>
            <strong><code>TRUE</code></strong>  时将会根据服务器返回 HTTP 头中的 <em>"Location: "</em> 重定向。（注意：这是递归的，<em>"Location: "</em> 发送几次就重定向几次，除非设置了 <strong><code>CURLOPT_MAXREDIRS</code></strong>，限制最大重定向次数。）。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_FORBID_REUSE</code></strong></td>
            <td>
            <strong><code>TRUE</code></strong> 在完成交互以后强制明确的断开连接，不能在连接池中重用。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_FRESH_CONNECT</code></strong></td>
            <td>
            <strong><code>TRUE</code></strong> 强制获取一个新的连接，而不是缓存中的连接。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_FTP_USE_EPRT</code></strong></td>
            <td>
            <strong><code>TRUE</code></strong> 时，当 FTP 下载时，使用 EPRT (和 LPRT)命令。 设置为 <strong><code>FALSE</code></strong> 时禁用 EPRT 和 LPRT，仅仅使用PORT 命令。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_FTP_USE_EPSV</code></strong></td>
            <td>
            <strong><code>TRUE</code></strong> 时，在FTP传输过程中，回到 PASV 模式前，先尝试 EPSV 命令。设置为 <strong><code>FALSE</code></strong> 时禁用 EPSV。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_FTP_CREATE_MISSING_DIRS</code></strong></td>
            <td>
            <strong><code>TRUE</code></strong> 时，当 ftp 操作不存在的目录时将创建它。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_FTPAPPEND</code></strong></td>
            <td>
            <strong><code>TRUE</code></strong> 为追加写入文件，而不是覆盖。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_TCP_NODELAY</code></strong></td>
            <td>
            <strong><code>TRUE</code></strong> 时禁用 TCP 的 Nagle 算法，就是减少网络上的小包数量。
            </td>
            <td>PHP 5.2.1 有效，编译时需要 libcurl 7.11.2 及以上。</td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_FTPASCII</code></strong></td>
            <td>
            <strong><code>CURLOPT_TRANSFERTEXT</code></strong> 的别名。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_FTPLISTONLY</code></strong></td>
            <td>
            <strong><code>TRUE</code></strong> 时只列出 FTP 目录的名字。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_HEADER</code></strong></td>
            <td>
            启用时会将头文件的信息作为数据流输出。
            </td>
            <td></td>
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
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_HTTPPROXYTUNNEL</code></strong></td>
            <td>
            <strong><code>TRUE</code></strong>  会通过指定的 HTTP 代理来传输。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_MUTE</code></strong></td>
            <td>
            <strong><code>TRUE</code></strong>  时将完全静默，无论是何 cURL 函数。
            </td>
            <td>在 cURL 7.15.5  中移出（可以使用 <code>CURLOPT_RETURNTRANSFER</code> 作为代替）</td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_NETRC</code></strong></td>
            <td>
            <strong><code>TRUE</code></strong>  时，在连接建立时，访问<var>~/.netrc</var>文件获取用户名和密码来连接远程站点。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_NOBODY</code></strong></td>
            <td>
            <strong><code>TRUE</code></strong>  时将不输出 BODY 部分。同时 Mehtod 变成了 HEAD。修改为  <strong><code>FALSE</code></strong> 时不会变成 GET。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_NOPROGRESS</code></strong></td>
            <td>
            <p><strong><code>TRUE</code></strong> 时关闭 cURL 的传输进度。</p>
            <blockquote>
            <p><strong>Note</strong>: </p>
            <p>PHP 默认自动设置此选项为 <strong><code>TRUE</code></strong>，只有为了调试才需要改变设置。</p>
            </blockquote>
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_NOSIGNAL</code></strong></td>
            <td>
            <strong><code>TRUE</code></strong> 时忽略所有的 cURL 传递给 PHP 进行的信号。在 SAPI 多线程传输时此项被默认启用，所以超时选项仍能使用。
            </td>
            <td>cURL 7.10时被加入。</td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_POST</code></strong></td>
            <td>
            <strong><code>TRUE</code></strong> 时会发送 POST 请求，类型为：<em>application/x-www-form-urlencoded</em>，是 HTML 表单提交时最常见的一种。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_PUT</code></strong></td>
            <td>
            <strong><code>TRUE</code></strong> 时允许 HTTP 发送文件。要被 PUT 的文件必须在 <strong><code>CURLOPT_INFILE</code></strong>和<strong><code>CURLOPT_INFILESIZE</code></strong> 中设置。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_RETURNTRANSFER</code></strong></td>
            <td>
            <strong><code>TRUE</code></strong>  将<span><a href="curl_exec.md">curl_exec()</a></span>获取的信息以字符串返回，而不是直接输出。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_SAFE_UPLOAD</code></strong></td>
            <td>
            <strong><code>TRUE</code></strong> 禁用 <em>@</em> 前缀在 <strong><code>CURLOPT_POSTFIELDS</code></strong> 中发送文件。意味着 <em>@</em> 可以在字段中安全得使用了。可使用 <a href="curlfile.md">CURLFile</a> 作为上传的代替。
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
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_UNRESTRICTED_AUTH</code></strong></td>
            <td>
            <strong><code>TRUE</code></strong> 在使用<strong><code>CURLOPT_FOLLOWLOCATION</code></strong>重定向 header 中的多个 location 时继续发送用户名和密码信息，哪怕主机名已改变。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_UPLOAD</code></strong></td>
            <td><strong><code>TRUE</code></strong>  准备上传。</td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_VERBOSE</code></strong></td>
            <td>
            <strong><code>TRUE</code></strong> 会输出所有的信息，写入到<em>STDERR</em>，或在<strong><code>CURLOPT_STDERR</code></strong>中指定的文件。
            </td>
            <td></td>
        </tr>
    </tbody>
</table>  

**以下 `option`的`value`应该被设置成 `integer`：**  

<table>
    <thead>
        <tr>
        <th>选项</th>
        <th><code>value</code></th>
        <th>备注</th>
        </tr>
    </thead>

    <tbody>
        <tr>
            <td><strong><code>CURLOPT_BUFFERSIZE</code></strong></td>
            <td>每次读入的缓冲的尺寸。当然不保证每次都会完全填满这个尺寸。</td>
            <td>在cURL 7.10中被加入。</td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_CLOSEPOLICY</code></strong></td>
            <td>此选项已被废弃，它不会被实现，永远不会有效果啦。</td>
            <td>PHP 5.6.0 中移除。</td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_CONNECTTIMEOUT</code></strong></td>
            <td>在尝试连接时等待的秒数。设置为0，则无限等待。</td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_CONNECTTIMEOUT_MS</code></strong></td>
            <td>
            尝试连接等待的时间，以毫秒为单位。设置为0，则无限等待。 
            如果 libcurl 编译时使用系统标准的名称解析器（ standard system name resolver），那部分的连接仍旧使用以秒计的超时解决方案，最小超时时间还是一秒钟。
            </td>
            <td>在 cURL 7.16.2 中被加入。从 PHP 5.2.3 开始可用。</td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_DNS_CACHE_TIMEOUT</code></strong></td>
            <td>设置在内存中缓存 DNS 的时间，默认为120秒（两分钟）。</td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_FTPSSLAUTH</code></strong></td>
            <td>
                FTP验证方式（启用的时候）：<br>
                <blockquote>
                <code>CURLFTPAUTH_SSL</code>：首先尝试SSL<br>
                <code>CURLFTPAUTH_TLS</code>：首先尝试TLS<br>
                <code>CURLFTPAUTH_DEFAULT</code>：cURL自己决定
                </blockquote>
            </td>
            <td>在 cURL 7.12.2 中被加入。</td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_HTTP_VERSION</code></strong></td>
            <td>
                <code>CURL_HTTP_VERSION_NONE</code>：默认值，cURL 自己判断使用哪个版本<br>
                <code>CURL_HTTP_VERSION_1_0</code>：强制使用 HTTP/1.0<br>
                <code>CURL_HTTP_VERSION_1_1</code>：强制使用 HTTP/1.1
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_HTTPAUTH</code></strong></td>
            <td>
                <p>
                    使用的 HTTP 验证方法。选项有：<br>
                    <code>CURLAUTH_BASIC</code><br>
                    <code>CURLAUTH_DIGEST</code><br>
                    <code>CURLAUTH_GSSNEGOTIATE</code><br>
                    <code>CURLAUTH_NTLM</code><br>
                    <code>CURLAUTH_ANY</code><br>
                    <code>CURLAUTH_ANYSAFE</code>。
                </p>
                <p>
                    可以使用 <em>|</em> 位域(OR)操作符结合多个值，cURL 会让服务器选择受支持的方法，并选择最好的那个。
                </p>
                <p>
                    <code>CURLAUTH_ANY</code>是 <code>CURLAUTH_BASIC | CURLAUTH_DIGEST | CURLAUTH_GSSNEGOTIATE | CURLAUTH_NTLM</code> 的别名。
                </p>
                <p>
                    <code>CURLAUTH_ANYSAFE</code> 是 <code>CURLAUTH_DIGEST | CURLAUTH_GSSNEGOTIATE | CURLAUTH_NTLM</code> 的别名。
                </p>
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_INFILESIZE</code></strong></td>
            <td>
            希望传给远程站点的文件尺寸，字节(byte)为单位。
            注意无法用这个选项阻止 libcurl 发送更多的数据，确切发送什么取决于 <strong><code>CURLOPT_READFUNCTION</code></strong>。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_LOW_SPEED_LIMIT</code></strong></td>
            <td>
            传输速度，每秒字节（bytes）数，根据<strong><code>CURLOPT_LOW_SPEED_TIME</code></strong>秒数统计是否因太慢而取消传输。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_LOW_SPEED_TIME</code></strong></td>
            <td>
            当传输速度小于<strong><code>CURLOPT_LOW_SPEED_LIMIT</code></strong>时(bytes/sec)，PHP会根据<strong><code>CURLOPT_LOW_SPEED_TIME</code></strong>来判断是否因太慢而取消传输。
            </td>
            <td></td>
        </tr>
          
        <tr>
            <td><strong><code>CURLOPT_MAXCONNECTS</code></strong></td>
            <td>
            允许的最大连接数量。达到限制时，会通过<strong><code>CURLOPT_CLOSEPOLICY</code></strong>决定应该关闭哪些连接。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_MAXREDIRS</code></strong></td>
            <td>
            指定最多的 HTTP 重定向次数，这个选项是和<strong><code>CURLOPT_FOLLOWLOCATION</code></strong>一起使用的。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_PORT</code></strong></td>
            <td>用来指定连接端口。</td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_POSTREDIR</code></strong></td>
            <td>
            位掩码<br>
            <blockquote>
            1 (301 永久重定向)<br>
            2 (302 Found)<br>
            4 (303 See Other)<br>
            </blockquote>
            设置 <strong><code>CURLOPT_FOLLOWLOCATION</code></strong> 时，什么情况下需要再次  HTTP POST 到重定向网址。
            </td>
            <td>cURL 7.19.1 中添加，PHP 5.3.2 开始可用。</td>
        </tr>
          
        <tr>
            <td><strong><code>CURLOPT_PROTOCOLS</code></strong></td>
            <td>
            <p>
            <strong><code>CURLPROTO_*</code></strong>的位掩码。启用时，会限制 libcurl 在传输过程中可使用哪些协议。这将允许你在编译libcurl时支持众多协议，但是限制只用允许的子集。默认 libcurl 将使用所有支持的协议。参见<strong><code>CURLOPT_REDIR_PROTOCOLS</code></strong>。
            </p>
            <p>
            可用的协议选项为：
            <blockquote>
            <code>CURLPROTO_HTTP</code><br>
            <code>CURLPROTO_HTTPS</code><br>
            <code>CURLPROTO_FTP</code><br>
            <code>CURLPROTO_FTPS</code><br>
            <code>CURLPROTO_SCP</code><br>
            <code>CURLPROTO_SFTP</code><br>
            <code>CURLPROTO_TELNET</code><br>
            <code>CURLPROTO_LDAP</code><br>
            <code>CURLPROTO_LDAPS</code><br>
            <code>CURLPROTO_DICT</code><br>
            <code>CURLPROTO_FILE</code><br>
            <code>CURLPROTO_TFTP</code><br>
            <code>CURLPROTO_ALL</code>
            </blockquote>
            </p>
            </td>
            <td>在 cURL 7.19.4 中被加入。</td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_PROXYAUTH</code></strong></td>
            <td>
            HTTP 代理连接的验证方式。使用在<strong><code>CURLOPT_HTTPAUTH</code></strong>中的位掩码。
            当前仅仅支持 <code>CURLAUTH_BASIC</code>和<code>CURLAUTH_NTLM</code>。
            </td>
            <td>在 cURL 7.10.7 中被加入。</td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_PROXYPORT</code></strong></td>
            <td>
            代理服务器的端口。端口也可以在<strong><code>CURLOPT_PROXY</code></strong>中设置。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_PROXYTYPE</code></strong></td>
            <td>
            可以是 <code>CURLPROXY_HTTP</code> (默认值) 
            <strong><code>CURLPROXY_SOCKS4</code></strong>、
            <strong><code>CURLPROXY_SOCKS5</code></strong>、
            <strong><code>CURLPROXY_SOCKS4A</code></strong> 或
            <strong><code>CURLPROXY_SOCKS5_HOSTNAME</code></strong>。
            </td>
            <td>在 cURL 7.10 中被加入。</td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_REDIR_PROTOCOLS</code></strong></td>
            <td>
            <strong><code>CURLPROTO_*</code></strong> 值的位掩码。如果被启用，位掩码会限制 libcurl 在 <strong><code>CURLOPT_FOLLOWLOCATION</code></strong>开启时，使用的协议。
            默认允许除 FILE 和 SCP 外所有协议。
            这和 7.19.4 前的版本无条件支持所有支持的协议不同。关于协议常量，请参照<strong><code>CURLOPT_PROTOCOLS</code></strong>。
            </td>
            <td>在 cURL 7.19.4 中被加入。</td>
        </tr>
          
        <tr>
            <td><strong><code>CURLOPT_RESUME_FROM</code></strong></td>
            <td>在恢复传输时，传递字节为单位的偏移量（用来断点续传）。</td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_SSL_VERIFYHOST</code></strong></td>
            <td>
            设置为 1 是检查服务器SSL证书中是否存在一个公用名(common name)。译者注：公用名(Common Name)一般来讲就是填写你将要申请SSL证书的域名 (domain)或子域名(sub domain)。
            设置成 2，会检查公用名是否存在，并且是否与提供的主机名匹配。
            在生产环境中，这个值应该是 2（默认值）。
            </td>
            <td>值 1 的支持在 cURL 7.28.1 中被删除了。</td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_SSLVERSION</code></strong></td>
            <td>
            <blockquote>
            <strong><code>CURL_SSLVERSION_DEFAULT</code></strong> (0)<br>
            <strong><code>CURL_SSLVERSION_TLSv1</code></strong> (1)<br>
            <strong><code>CURL_SSLVERSION_SSLv2</code></strong> (2)<br>
            <strong><code>CURL_SSLVERSION_SSLv3</code></strong> (3)<br>
            <strong><code>CURL_SSLVERSION_TLSv1_0</code></strong> (4)<br>
            <strong><code>CURL_SSLVERSION_TLSv1_1</code></strong> (5)<br>
            <strong><code>CURL_SSLVERSION_TLSv1_2</code></strong> (6)<br>
            <br>
            <p><strong>Note</strong>: </p>
            <p>你最好别设置这个值，让它使用默认值。设置为 2 或 3 比较危险，在 SSLv2 和 SSLv3 中有弱点存在。</p>
            </blockquote>
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_TIMECONDITION</code></strong></td>
            <td>
            设置如何对待 <strong><code>CURLOPT_TIMEVALUE</code></strong>。
            使用 <code>CURL_TIMECOND_IFMODSINCE</code>，仅在页面 <strong><code>CURLOPT_TIMEVALUE</code></strong> 之后修改，才返回页面。没有修改则返回 <em>"304 Not Modified"</em> 头，假设设置了 <strong><code>CURLOPT_HEADER</code></strong> 为  <strong><code>TRUE</code></strong>。<code>CURL_TIMECOND_IFUNMODSINCE</code>则起相反的效果。
            默认为 <code>CURL_TIMECOND_IFMODSINCE</code>。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_TIMEOUT</code></strong></td>
            <td>允许 cURL 函数执行的最长秒数。</td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_TIMEOUT_MS</code></strong></td>
            <td>
            设置cURL允许执行的最长毫秒数。
            如果 libcurl 编译时使用系统标准的名称解析器（ standard system name resolver），那部分的连接仍旧使用以秒计的超时解决方案，最小超时时间还是一秒钟。
            </td>
            <td>在 cURL 7.16.2 中被加入。从 PHP 5.2.3 起可使用。</td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_TIMEVALUE</code></strong></td>
            <td>
            秒数，从 1970年1月1日开始。这个时间会被 <strong><code>CURLOPT_TIMECONDITION</code></strong>使。默认使用<code>CURL_TIMECOND_IFMODSINCE</code>。
            </td>
            <td></td>
        </tr>
         
        <tr>
            <td><strong><code>CURLOPT_MAX_RECV_SPEED_LARGE</code></strong></td>
            <td>
                下载速度（每秒字节（bytes）数）超过在传输过程中的累积平均速度，传输将保持平均速率小于或等于参数值。默认为无限的速度。
            </td>
            <td>
                在 7.15.5 中被加入。 从 PHP 5.4.0 起可使用。
            </td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_MAX_SEND_SPEED_LARGE</code></strong></td>
            <td>
                上传速度（每秒字节（bytes）数）超过在传输过程中的累积平均速度，传输将保持平均速率小于或等于参数值。默认为无限的速度。
            </td>
            <td>
                在 7.15.5 中被加入。 从 PHP 5.4.0 起可使用。
            </td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_SSH_AUTH_TYPES</code></strong></td>
            <td>
                由一个或多个<br>
                <strong><code>CURLSSH_AUTH_PUBLICKEY</code></strong><br> 
                <strong><code>CURLSSH_AUTH_PASSWORD</code></strong><br>
                <strong><code>CURLSSH_AUTH_HOST</code></strong><br>
                <strong><code>CURLSSH_AUTH_KEYBOARD</code></strong><br>
                设置<strong><code>CURLSSH_AUTH_ANY</code></strong> 让 libcurl 自己决定
            </td>
            <td>
                在 7.16.1 中被加入。
            </td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_IPRESOLVE</code></strong></td>
            <td>
            允许应用程序选择在解析主机名时使用何种类型的IP地址。这是唯一有趣的，当使用多个版本的IP地址解析主机名称。可能的值是
            <strong><code>CURL_IPRESOLVE_WHATEVER</code></strong><br>
            <strong><code>CURL_IPRESOLVE_V4</code></strong><br>
            <strong><code>CURL_IPRESOLVE_V6</code></strong><br> 
            默认<strong><code>CURL_IPRESOLVE_WHATEVER</code></strong>
            </td>
            <td>
                在 7.10.8 中被加入。
            </td>
        </tr>
    </tbody>
</table>  

**对于下面的这些`option`，`value`应该被设置成 `string`：**  

<table>
    <thead>
        <tr>
            <th>选项</th>
            <th>设置的<code>value</code></th>
            <th>备注</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><strong><code>CURLOPT_CAINFO</code></strong></td>
            <td>
                一个保存着1个或多个用来让服务端验证的证书的文件名。这个参数仅仅在和<strong><code>CURLOPT_SSL_VERIFYPEER</code></strong>一起使用时才有意义。            .
            </td>
            <td>可能需要绝对路径。</td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_CAPATH</code></strong></td>
            <td>
            一个保存着多个CA证书的目录。这个选项是和<strong><code>CURLOPT_SSL_VERIFYPEER</code></strong>一起使用的。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_COOKIE</code></strong></td>
            <td>
            设定 HTTP 请求中<em>"Cookie: "</em>部分的内容。多个 cookie 用分号分隔，分号后带一个空格(例如， "<em>fruit=apple; colour=red</em>")。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_COOKIEFILE</code></strong></td>
            <td>
            包含 cookie 数据的文件名，cookie 文件的格式可以是 Netscape 格式，或者只是纯 HTTP 头部风格，存入文件。如果文件名是空的，不会加载 cookie，但 cookie 的处理仍旧启用。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_COOKIEJAR</code></strong></td>
            <td>
            连接结束后，比如，调用 curl_close 后，保存 cookie 信息的文件。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_CUSTOMREQUEST</code></strong></td>
            <td>
                <p>
                HTTP 请求时，使用自定义的 Method 来代替<em>"GET"</em>或<em>"HEAD"</em>。对 <em>"DELETE"</em> 或者其他更隐蔽的 HTTP 请求有用。
                有效值如 <em>"GET"</em>，<em>"POST"</em>，<em>"CONNECT"</em>等等；也就是说，不要在这里输入整行 HTTP 请求。例如输入<em>"GET /index.html HTTP/1.0\r\n\r\n"</em>是不正确的。
                </p>
                <blockquote>
                <p><strong>Note</strong>: </p>
                <p>不确定服务器支持这个自定义方法则不要使用它。</p>
                </blockquote>
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_EGDSOCKET</code></strong></td>
            <td>
            类似<strong><code>CURLOPT_RANDOM_FILE</code></strong>，除了一个Entropy Gathering Daemon套接字。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_ENCODING</code></strong></td>
            <td>
            HTTP请求头中<em>"Accept-Encoding: "</em>的值。
            这使得能够解码响应的内容。
            支持的编码有<em>"identity"</em>，<em>"deflate"</em>和<em>"gzip"</em>。如果为空字符串<em>""</em>，会发送所有支持的编码类型。
            </td>
            <td>在 cURL 7.10 中被加入。</td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_FTPPORT</code></strong></td>
            <td>
            这个值将被用来获取供FTP"PORT"指令所需要的IP地址。
            "PORT" 指令告诉远程服务器连接到我们指定的IP地址。这个字符串可以是纯文本的IP地址、主机名、一个网络接口名（UNIX下）或者只是一个'-'来使用默认的 IP 地址。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_INTERFACE</code></strong></td>
            <td>
            发送的网络接口（interface），可以是一个接口名、IP 地址或者是一个主机名。
            </td>
            <td></td>
        </tr>
          
        <tr>
            <td><strong><code>CURLOPT_KEYPASSWD</code></strong></td>
            <td>
            使用 <strong><code>CURLOPT_SSLKEY</code></strong> 
            或 <strong><code>CURLOPT_SSH_PRIVATE_KEYFILE</code></strong> 私钥时候的密码。
            </td>
            <td>在 cURL 7.16.1 中添加。</td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_KRB4LEVEL</code></strong></td>
            <td>
            KRB4 (Kerberos 4) 安全级别。下面的任何值都是有效的(从低到高的顺序)：<em>"clear"</em>、<em>"safe"</em>、<em>"confidential"</em>、<em>"private".</em>。如果字符串以上这些，将使用<em>"private"</em>。
            这个选项设置为 <strong><code>NULL</code></strong> 时将禁用 KRB4 安全认证。目前 KRB4 安全认证只能用于 FTP 传输。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_POSTFIELDS</code></strong></td>
            <td>
            <span>
            全部数据使用HTTP协议中的 "POST" 操作来发送。
            要发送文件，在文件名前面加上<em>@</em>前缀并使用完整路径。
            文件类型可在文件名后以 '<em>;type=mimetype</em>' 的格式指定。
            这个参数可以是 urlencoded 后的字符串，类似'<em>para1=val1&amp;para2=val2&amp;...</em>'，也可以使用一个以字段名为键值，字段数据为值的数组。
            如果<code>value</code>是一个数组，<em>Content-Type</em>头将会被设置成<em>multipart/form-data</em>。
            </span>
            <span>
             从 PHP 5.2.0 开始，使用 <em>@</em>  前缀传递文件时，<code>value</code> 必须是个数组。
            </span>
            <span>
             从 PHP 5.5.0 开始,  <em>@</em> 前缀已被废弃，文件可通过 CURLFile发送。
             设置 <strong><code>CURLOPT_SAFE_UPLOAD</code></strong> 为 <strong><code>TRUE</code></strong> 可禁用  <em>@</em>  前缀发送文件，以增加安全性。
            </span>
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_PRIVATE</code></strong></td>
            <td>
            cURL资源句柄相关的一些数据。<br>
            <small>该数据可以用 <a href="curl_getinfo.md">curl_getinfo()</a> 的<code>CURLINFO_PRIVATE</code>选项检索。
            cURL用这些数据不做任何事情。
            当使用一个多句柄的cURL时，这个私有数据通常是一个唯一的键，用来识别一个标准的cURL资源句柄。</small>
            </td>
            <td>在 cURL 7.10.3 中添加</td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_PROXY</code></strong></td>
            <td>HTTP 代理通道。</td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_PROXYUSERPWD</code></strong></td>
            <td>
            一个用来连接到代理的<em>"[username]:[password]"</em>格式的字符串。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_RANDOM_FILE</code></strong></td>
            <td>一个被用来生成 SSL 随机数种子的文件名。</td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_RANGE</code></strong></td>
            <td>
            以<em>"X-Y"</em>的形式，其中X和Y都是可选项获取数据的范围，以字节计。HTTP传输线程也支持几个这样的重复项中间用逗号分隔如<em>"X-Y,N-M"</em>。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_REFERER</code></strong></td>
            <td>在HTTP请求头中<em>"Referer: "</em>的内容。</td>
            <td></td>
        </tr>

        <tr>
            <td>
            <strong><code>CURLOPT_SSH_HOST_PUBLIC_KEY_MD5</code></strong></td>
            <td>
            包含 32 位长的 16 进制数值。这个字符串应该是远程主机公钥（public key） 的 MD5 校验值。在不匹配的时候 libcurl 会拒绝连接。
            此选项仅用于  SCP 和 SFTP 的传输。
            </td>
            <td>cURL 7.17.1 中添加。</td>
        </tr>
          
        <tr>
            <td><strong><code>CURLOPT_SSH_PUBLIC_KEYFILE</code></strong></td>
            <td>
            你的公钥（public key）文件名。<br>
            不使用的情况下：
            若设置了 HOME 环境变量，libcurl 默认为 $HOME/.ssh/id_dsa.pub；
            未设置 HOME 环境变量, 则为当前目录下"./id_dsa.pub"。
            </td>
            <td>cURL 7.16.1 中添加</td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_SSH_PRIVATE_KEYFILE</code></strong></td>
            <td>
            私有密钥（private key）文件名。<br>
            不使用的情况下：
            若设置了 HOME 环境变量，libcurl 默认为 $HOME/.ssh/id_dsa。
            未设置 HMOE 环境变量，默认为当前目录下"./id_dsa"。
            如果文件有密码保护，用<strong><code>CURLOPT_KEYPASSWD</code></strong>设置密码。
            </td>
            <td>cURL 7.16.1 中添加</td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_SSL_CIPHER_LIST</code></strong></td>
            <td>
            一个SSL的加密算法列表。例如<em>RC4-SHA</em>和<em>TLSv1</em>都是可用的加密列表。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_SSLCERT</code></strong></td>
            <td>一个包含 PEM 格式证书的文件名。</td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_SSLCERTPASSWD</code></strong></td>
            <td>
            使用<strong><code>CURLOPT_SSLCERT</code></strong>证书需要的密码。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_SSLCERTTYPE</code></strong></td>
            <td>
            证书的类型。支持的格式有<em>"PEM"</em> (默认值), <em>"DER"</em>和<em>"ENG"</em>。
            </td>
            <td>在 cURL 7.9.3中 被加入。</td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_SSLENGINE</code></strong></td>
            <td>
            用来在<strong><code>CURLOPT_SSLKEY</code></strong>中指定的SSL私钥的加密引擎变量。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_SSLENGINE_DEFAULT</code></strong></td>
            <td>用来做非对称加密操作的变量。</td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_SSLKEY</code></strong></td>
            <td>包含 SSL 私钥的文件名。</td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_SSLKEYPASSWD</code></strong></td>
            <td><p>
            在 <strong><code>CURLOPT_SSLKEY</code></strong>中指定了的SSL私钥的密码。
            </p><blockquote><p><strong>Note</strong>: 
             </p><p>
              由于这个选项包含了敏感的密码信息，记得保证这个PHP脚本的安全。
             </p>
            </blockquote>
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_SSLKEYTYPE</code></strong></td>
            <td>
            <strong><code>CURLOPT_SSLKEY</code></strong>中规定的私钥的加密类型，支持的密钥类型为<em>"PEM"</em>(默认值)、<em>"DER"</em>和<em>"ENG"</em>。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_URL</code></strong></td>
            <td>
            需要获取的 URL 地址，也可以在<span><a href="curl-init.md">curl_init()</a></span> 初始化会话的时候。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_USERAGENT</code></strong></td>
            <td>
            在HTTP请求中包含一个<em>"User-Agent: "</em>头的字符串。
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_USERPWD</code></strong></td>
            <td>
            传递一个连接中需要的用户名和密码，格式为：<em>"[username]:[password]"</em>。
            </td>
            <td></td>
        </tr>
    </tbody>
</table>   

**以下`option`，`value`应该被设置成数组：**  

<table>
    <thead>
        <tr>
            <th>选项</th>
            <th>可选<code>value</code>值</th>
            <th>备注</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><strong><code>CURLOPT_HTTP200ALIASES</code></strong></td>
            <td>HTTP 200 响应码数组，数组中的响应码被认为是正确的响应，而非错误。</td>
            <td>在 cURL 7.10.3 中被加入。</td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_HTTPHEADER</code></strong></td>
            <td>
            设置 HTTP 头字段的数组。格式：
            <code>
             array('Content-type: text/plain', 'Content-length: 100')
            </code>
            </td>
            <td></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_POSTQUOTE</code></strong></td>
            <td>
            在 FTP 请求执行完成后，在服务器上执行的一组array格式的 FTP 命令。
            </td>
            <td"></td>
        </tr>

        <tr>
            <td><strong><code>CURLOPT_QUOTE</code></strong></td>
            <td>一组先于 FTP 请求的在服务器上执行的FTP命令。 </td>
            <td></td>
        </tr>
    </tbody>
</table>  


**以下 `option`，`value`应该被设置成流资源 （例如使用`fopen()`）：**  

<table>
    <thead>
        <tr>
            <th>选项</th>
            <th>可选<code>value</code>值</th>
            <th>备注</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><strong><code>CURLOPT_FILE</code></strong></td>
            <td>设置输出文件，默认为<em>STDOUT</em> (浏览器)。</td>
            <td></td>
        </tr>
        <tr>
            <td><strong><code>CURLOPT_INFILE</code></strong></td>
            <td>上传文件时需要读取的文件。</td>
            <td></td>
        </tr>
        <tr>
            <td><strong><code>CURLOPT_STDERR</code></strong></td>
            <td>错误输出的地址，取代默认的<em>STDERR</em>。</td>
            <td></td>
        </tr>
        <tr>
            <td><strong><code>CURLOPT_WRITEHEADER</code></strong></td>
            <td>设置 header 部分内容的写入的文件地址。</td>
            <td></td>
        </tr>
    </tbody>
</table>  

** 以下`option` 的 `value`应该是有效的函数或者闭包：**  

<table>
    <thead>
        <tr>
            <th>选项</th>
            <th><code>value</code>值</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><strong><code>CURLOPT_HEADERFUNCTION</code></strong></td>
            <td>
            设置一个回调函数，这个函数有两个参数，第一个是cURL的资源句柄，第二个是输出的 header 数据。header数据的输出必须依赖这个函数，返回已写入的数据大小。
            </td>
        </tr>
        <tr>
            <td><strong><code>CURLOPT_PASSWDFUNCTION</code></strong></td>
            <td>
            设置一个回调函数，有三个参数，第一个是cURL的资源句柄，第二个是一个密码提示符，第三个参数是密码长度允许的最大值。返回密码的值。
            </td>
        </tr>
        <tr>
            <td><strong><code>CURLOPT_PROGRESSFUNCTION</code></strong></td>
            <td>
            <p>
            设置一个回调函数，有五个参数，第一个是cURL的资源句柄，第二个是预计要下载的总字节（bytes）数。第三个是目前下载的字节数，第四个是预计传输中总上传字节数，第五个是目前上传的字节数。
            </p>
            <blockquote class="note">
            <p><strong class="note">Note</strong>: </p>
            <p>
              只有设置 <strong><code>CURLOPT_NOPROGRESS</code></strong>
              选项为 <strong><code>FALSE</code></strong> 时才会调用这个回调函数。
            </p>
            </blockquote>
            <p>
            返回非零值将中断传输。
            传输将设置 <strong><code>CURLE_ABORTED_BY_CALLBACK</code></strong> 错误。
            </p>
            </td>
        </tr>
        <tr>
            <td><strong><code>CURLOPT_READFUNCTION</code></strong></td>
            <td>
            回调函数名。该函数应接受三个参数。第一个是 cURL resource；第二个是通过选项 
            <strong><code>CURLOPT_INFILE</code></strong> 传给 cURL 的 stream resource；第三个参数是最大可以读取的数据的数量。回
            调函数必须返回一个字符串，长度小于或等于请求的数据量（第三个参数）。一般从传入的 stream 
            resource 读取。返回空字符串作为 <em>EOF</em>（文件结束） 信号。
            </td>
        </tr>
          
        <tr>
            <td><strong><code>CURLOPT_WRITEFUNCTION</code></strong></td>
            <td>
            回调函数名。该函数应接受两个参数。第一个是 cURL resource；第二个是要写入的数据字符串。数据必须在函数中被保存。函数必须准确返回写入数据的字节数，否则传输会被一个错误所中断。
            </td>
        </tr>
    </tbody>
</table>

<table>
    <thead>
        <tr>
        <th>选项</th>
        <th><code>value</code>值</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><strong><code>CURLOPT_SHARE</code></strong></td>
            <td>
            [curl_share_init()](curl_share_init.md) 返回的结果。 使 cURL 可以处理共享句柄里的数据
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
- 上一节：[curl_setopt_array](curl_setopt_array.md)
- 下一节：[curl_share_close](curl_share_close.md)
