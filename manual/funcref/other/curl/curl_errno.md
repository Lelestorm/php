
## curl_errno()
(PHP 4 >= 4.0.3, PHP 5, PHP 7)  
curl_errno — 返回最后一次的错误号

#### 说明  
```php
int curl_errno ( resource $ch )
```

返回最后一次cURL操作的错误号。

#### 参数   
$ch  
&nbsp;&nbsp;&nbsp;&nbsp;由 curl_init() 返回的 cURL 句柄。  

#### 返回值
返回错误号或 0 (零) 如果没有错误发生。

#### 范例   
---  
Example #1 curl_errno() example
```php
<?php
// 创建一个指向一个不存在的位置的cURL句柄
$ch = curl_init('http://404.php.net/');

// 执行
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_exec($ch);

// 检查是否有错误发生
if(curl_errno($ch))
{
    echo 'Curl error: ' . curl_error($ch);
}

// 关闭句柄
curl_close($ch);
?>
```

---   

** libcurl error codes **

<table>
    <thead>
        <tr>
            <td>code常量</td>
            <td>code</td>
            <td>说明</td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>CURLE_OK</code></td>
            <td>0</td>
            <td>没有错误发生</td>
        </tr>
        <tr>
            <td><code>CURLE_UNSUPPORTED_PROTOCOL</code></td>
            <td>1</td>
            <td>libcurl不支持使用的URL协议。你可能没有使用一个编译时的选项，而是一个拼错的字符串协议或没有编码的libcurl协议</td>
        </tr>
        <tr>
            <td><code>CURLE_FAILED_INIT</code></td>
            <td>2</td>
            <td>
            Very early initialization code failed. This is likely to be an internal error or problem, or a resource problem where something fundamental couldn't get done at init time.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_URL_MALFORMAT</code></td>
            <td>3</td>
            <td>ULR格式化错误</td>
        </tr>
        <tr>
            <td><code>CURLE_NOT_BUILT_IN </code></td>
            <td>4</td>
            <td>
            A requested feature, protocol or option was not found built-in in this libcurl due to a build-time decision. This means that a feature or option was not enabled or explicitly disabled when libcurl was built and in order to get it to function you have to get a rebuilt libcurl.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_COULDNT_RESOLVE_PROXY</code></td>
            <td>5</td>
            <td>代理解析失败，无法解析指定的代理服务器</td>
        </tr>
        <tr>
            <td><code>CURLE_COULDNT_RESOLVE_HOST </code></td>
            <td>6</td>
            <td>主机解析失败，无法解析指定的主机服务器</td>
        </tr>
        <tr>
            <td><code>CURLE_COULDNT_CONNECT</code></td>
            <td>7</td>
            <td>链接主机或代理失败</td>
        </tr>
        <tr>
            <td><code>CURLE_FTP_WEIRD_SERVER_REPLY</code></td>
            <td>8</td>
            <td>The server sent data libcurl couldn't parse. This error code is used for more than just FTP and is aliased as CURLE_WEIRD_SERVER_REPLY since 7.51.0.</td>
        </tr>
        <tr>
            <td><code>CURLE_REMOTE_ACCESS_DENIED</code></td>
            <td>9</td>
            <td>被拒绝访问网址的资源。在FTP中发生在试图改变远程目录</td>
        </tr>
        <tr>
            <td><code>CURLE_FTP_ACCEPT_FAILED</code></td>
            <td>10</td>
            <td>
                While waiting for the server to connect back when an active FTP session is used, an error code was sent over the control connection or similar.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_FTP_WEIRD_PASS_REPLY</code></td>
            <td>11</td>
            <td>
                After having sent the FTP password to the server, libcurl expects a proper reply. This error code indicates that an unexpected code was returned.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_FTP_ACCEPT_TIMEOUT</code></td>
            <td>12</td>
            <td>
                During an active FTP session while waiting for the server to connect, the CURLOPT_ACCEPTTIMEOUT_MS (or the internal default) timeout expired.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_FTP_WEIRD_PASV_REPLY </code></td>
            <td>13</td>
            <td>
                libcurl failed to get a sensible result back from the server as a response to either a PASV or a EPSV command. The server is flawed.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_FTP_WEIRD_227_FORMAT</code></td>
            <td>14</td>
            <td>
                FTP servers return a 227-line as a response to a PASV command. If libcurl fails to parse that line, this return code is passed back.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_FTP_CANT_GET_HOST</code></td>
            <td>15</td>
            <td>
                An internal failure to lookup the host used for the new connection.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_HTTP2</code></td>
            <td>16</td>
            <td>
                A problem was detected in the HTTP2 framing layer. This is somewhat generic and can be one out of several problems, see the error buffer for details.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_FTP_COULDNT_SET_TYPE</code></td>
            <td>17</td>
            <td>
                Received an error when trying to set the transfer mode to binary or ASCII.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_PARTIAL_FILE</code></td>
            <td>18</td>
            <td>
                A file transfer was shorter or larger than expected. This happens when the server first reports an expected transfer size, and then delivers data that doesn't match the previously given size.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_FTP_COULDNT_RETR_FILE</code></td>
            <td>19</td>
            <td>
                This was either a weird reply to a 'RETR' command or a zero byte transfer complete.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_QUOTE_ERROR</code></td>
            <td>21</td>
            <td>
                When sending custom "QUOTE" commands to the remote server, one of the commands returned an error code that was 400 or higher (for FTP) or otherwise indicated unsuccessful completion of the command.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_HTTP_RETURNED_ERROR</code></td>
            <td>22</td>
            <td>
                This is returned if CURLOPT_FAILONERROR is set TRUE and the HTTP server returns an error code that is >= 400.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_WRITE_ERROR</code></td>
            <td>23</td>
            <td>
                An error occurred when writing received data to a local file, or an error was returned to libcurl from a write callback.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_UPLOAD_FAILED</code></td>
            <td>25</td>
            <td>
                Failed starting the upload. For FTP, the server typically denied the STOR command. The error buffer usually contains the server's explanation for this.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_READ_ERROR</code></td>
            <td>26</td>
            <td>
                There was a problem reading a local file or an error returned by the read callback.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_OUT_OF_MEMORY</code></td>
            <td>27</td>
            <td>
                A memory allocation request failed. This is serious badness and things are severely screwed up if this ever occurs.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_OPERATION_TIMEDOUT</code></td>
            <td>28</td>
            <td>
                Operation timeout. The specified time-out period was reached according to the conditions.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_FTP_PORT_FAILED</code></td>
            <td>30</td>
            <td>
                The FTP PORT command returned error. This mostly happens when you haven't specified a good enough address for libcurl to use. See CURLOPT_FTPPORT.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_FTP_COULDNT_USE_REST</code></td>
            <td>31</td>
            <td>
                The FTP REST command returned error. This should never happen if the server is sane.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_RANGE_ERROR</code></td>
            <td>33</td>
            <td>The server does not support or accept range requests.</td>
        </tr>
        <tr>
            <td><code>CURLE_HTTP_POST_ERROR</code></td>
            <td>34</td>
            <td>
                This is an odd error that mainly occurs due to internal confusion.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_SSL_CONNECT_ERROR</code></td>
            <td>35</td>
            <td>
                A problem occurred somewhere in the SSL/TLS handshake. You really want the error buffer and read the message there as it pinpoints the problem slightly more. Could be certificates (file formats, paths, permissions), passwords, and others.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_BAD_DOWNLOAD_RESUME</code></td>
            <td>36</td>
            <td>
                The download could not be resumed because the specified offset was out of the file boundary.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_FILE_COULDNT_READ_FILE</code></td>
            <td>37</td>
            <td>
                A file given with FILE:// couldn't be opened. Most likely because the file path doesn't identify an existing file. Did you check file permissions?
            </td>
        </tr>
        <tr>
            <td><code>CURLE_LDAP_CANNOT_BIND </code></td>
            <td>38</td>
            <td>LDAP cannot bind. LDAP bind operation failed.</td>
        </tr>
        <tr>
            <td><code>CURLE_LDAP_SEARCH_FAILED </code></td>
            <td>39</td>
            <td>LDAP search failed.</td>
        </tr>
        <tr>
            <td><code>CURLE_FUNCTION_NOT_FOUND </code></td>
            <td>41</td>
            <td>Function not found. A required zlib function was not found.</td>
        </tr>
        <tr>
            <td><code>CURLE_ABORTED_BY_CALLBACK</code></td>
            <td>42</td>
            <td>Aborted by callback. A callback returned "abort" to libcurl.</td>
        </tr>
        <tr>
            <td><code>CURLE_BAD_FUNCTION_ARGUMENT</code></td>
            <td>43</td>
            <td>Internal error. A function was called with a bad parameter.</td>
        </tr>
        <tr>
            <td><code>CURLE_INTERFACE_FAILED</code></td>
            <td>45</td>
            <td>
                Interface error. A specified outgoing interface could not be used. Set which interface to use for outgoing connections' source IP address with CURLOPT_INTERFACE.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_TOO_MANY_REDIRECTS</code></td>
            <td>47</td>
            <td>
                Too many redirects. When following redirects, libcurl hit the maximum amount. Set your limit with CURLOPT_MAXREDIRS.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_UNKNOWN_OPTION</code></td>
            <td>48</td>
            <td>
                An option passed to libcurl is not recognized/known. Refer to the appropriate documentation. This is most likely a problem in the program that uses libcurl. The error buffer might contain more specific information about which exact option it concerns.
            </td>
        </tr>
        <tr>
            <td><code>CURLE_TELNET_OPTION_SYNTAX </code></td>
            <td>49</td>
            <td>A telnet option string was Illegally formatted.</td>
        </tr>
        <tr>
            <td><code>CURLE_PEER_FAILED_VERIFICATION </code></td>
            <td>51</td>
            <td>The remote server's SSL certificate or SSH md5 fingerprint was deemed not OK.</td>
        </tr>
        <tr>
            <td><code>CURLE_GOT_NOTHING </code></td>
            <td>52</td>
            <td>Nothing was returned from the server, and under the circumstances, getting nothing is considered an error.</td>
        </tr>
        <tr>
            <td><code>CURLE_SSL_ENGINE_NOTFOUND </code></td>
            <td>53</td>
            <td>The specified crypto engine wasn't found.</td>
        </tr>
        <tr>
            <td><code>CURLE_SSL_ENGINE_SETFAILED </code></td>
            <td>54</td>
            <td>Failed setting the selected SSL crypto engine as default!</td>
        </tr>
        <tr>
            <td><code>CURLE_SEND_ERROR </code></td>
            <td>55</td>
            <td>Failed sending network data.</td>
        </tr>
        <tr>
            <td><code>CURLE_RECV_ERROR</code></td>
            <td>56</td>
            <td>Failure with receiving network data.</td>
        </tr>
        <tr>
            <td><code>CURLE_SSL_CERTPROBLEM </code></td>
            <td>58</td>
            <td>problem with the local client certificate.</td>
        </tr>
        <tr>
            <td><code>CURLE_SSL_CIPHER </code></td>
            <td>59</td>
            <td>Couldn't use specified cipher.</td>
        </tr>
        <tr>
            <td><code>CURLE_SSL_CACERT </code></td>
            <td>60</td>
            <td>Peer certificate cannot be authenticated with known CA certificates.</td>
        </tr>
        <tr>
            <td><code>CURLE_BAD_CONTENT_ENCODING </code></td>
            <td>61</td>
            <td>Unrecognized transfer encoding.</td>
        </tr>
        <tr>
            <td><code>CURLE_LDAP_INVALID_URL </code></td>
            <td>62</td>
            <td>Invalid LDAP URL.</td>
        </tr>
        <tr>
            <td><code>CURLE_FILESIZE_EXCEEDED </code></td>
            <td>63</td>
            <td>Maximum file size exceeded.</td>
        </tr>
        <tr>
            <td><code>CURLE_USE_SSL_FAILED </code></td>
            <td>64</td>
            <td>Requested FTP SSL level failed.</td>
        </tr>
        <tr>
            <td><code>CURLE_SEND_FAIL_REWIND</code></td>
            <td>65</td>
            <td>When doing a send operation curl had to rewind the data to retransmit, but the rewinding operation failed.</td>
        </tr>
        <tr>
            <td><code>CURLE_SSL_ENGINE_INITFAILED</code></td>
            <td>66</td>
            <td>Initiating the SSL Engine failed.</td>
        </tr>
        <tr>
            <td><code>CURLE_LOGIN_DENIED</code></td>
            <td>67</td>
            <td>The remote server denied curl to login (Added in 7.13.1)</td>
        </tr>
        <tr>
            <td><code>CURLE_TFTP_NOTFOUND </code></td>
            <td>68</td>
            <td>File not found on TFTP server.</td>
        </tr>
        <tr>
            <td><code>CURLE_TFTP_PERM </code></td>
            <td>69</td>
            <td>Permission problem on TFTP server.</td>
        </tr>
        <tr>
            <td><code>CURLE_REMOTE_DISK_FULL </code></td>
            <td>70</td>
            <td>Out of disk space on the server.</td>
        </tr>
        <tr>
            <td><code>CURLE_TFTP_ILLEGAL</code></td>
            <td>71</td>
            <td>Illegal TFTP operation.</td>
        </tr>
        <tr>
            <td><code>CURLE_TFTP_UNKNOWNID </code></td>
            <td>72</td>
            <td>Unknown TFTP transfer ID.</td>
        </tr>
        <tr>
            <td><code>CURLE_REMOTE_FILE_EXISTS </code></td>
            <td>73</td>
            <td>File already exists and will not be overwritten.</td>
        </tr>
        <tr>
            <td><code>CURLE_TFTP_NOSUCHUSER </code></td>
            <td>74</td>
            <td>This error should never be returned by a properly functioning TFTP server.</td>
        </tr>
        <tr>
            <td><code>CURLE_CONV_FAILED </code></td>
            <td>75</td>
            <td>Character conversion failed.</td>
        </tr>
        <tr>
            <td><code>CURLE_CONV_REQD </code></td>
            <td>76</td>
            <td>Caller must register conversion callbacks.</td>
        </tr>
        <tr>
            <td><code>CURLE_SSL_CACERT_BADFILE </code></td>
            <td>77</td>
            <td>Problem with reading the SSL CA cert (path? access rights?)</td>
        </tr>
        <tr>
            <td><code>CURLE_REMOTE_FILE_NOT_FOUND </code></td>
            <td>78</td>
            <td>The resource referenced in the URL does not exist.</td>
        </tr>
        <tr>
            <td><code>CURLE_SSH </code></td>
            <td>79</td>
            <td>An unspecified error occurred during the SSH session.</td>
        </tr>
        <tr>
            <td><code>CURLE_SSL_SHUTDOWN_FAILED </code></td>
            <td>80</td>
            <td>Failed to shut down the SSL connection.</td>
        </tr>
        <tr>
            <td><code>CURLE_AGAIN </code></td>
            <td>81</td>
            <td>Socket is not ready for send/recv wait till it's ready and try again. This return code is only returned from curl_easy_recv and curl_easy_send (Added in 7.18.2)</td>
        </tr>
        <tr>
            <td><code>CURLE_SSL_CRL_BADFILE </code></td>
            <td>82</td>
            <td>Failed to load CRL file (Added in 7.19.0)</td>
        </tr>
        <tr>
            <td><code>CURLE_SSL_ISSUER_ERROR</code></td>
            <td>83</td>
            <td>Issuer check failed (Added in 7.19.0)</td>
        </tr>
        <tr>
            <td><code>CURLE_FTP_PRET_FAILED </code></td>
            <td>84</td>
            <td>The FTP server does not understand the PRET command at all or does not support the given argument. Be careful when using CURLOPT_CUSTOMREQUEST, a custom LIST command will be sent with PRET CMD before PASV as well. (Added in 7.20.0)</td>
        </tr>
        <tr>
            <td><code>CURLE_RTSP_CSEQ_ERROR </code></td>
            <td>85</td>
            <td>Mismatch of RTSP CSeq numbers.</td>
        </tr>
        <tr>
            <td><code>CURLE_RTSP_SESSION_ERROR </code></td>
            <td>86</td>
            <td>Mismatch of RTSP Session Identifiers.</td>
        </tr>
        <tr>
            <td><code>CURLE_FTP_BAD_FILE_LIST </code></td>
            <td>87</td>
            <td>Unable to parse FTP file list (during FTP wildcard downloading).</td>
        </tr>
        <tr>
            <td><code>CURLE_CHUNK_FAILED </code></td>
            <td>88</td>
            <td>Chunk callback reported error.</td>
        </tr>
        <tr>
            <td><code>CURLE_NO_CONNECTION_AVAILABLE </code></td>
            <td>89</td>
            <td>(For internal use only, will never be returned by libcurl) No connection available, the session will be queued. (added in 7.30.0)</td>
        </tr>
        <tr>
            <td><code>CURLE_SSL_PINNEDPUBKEYNOTMATCH </code></td>
            <td>90</td>
            <td>Failed to match the pinned key specified with CURLOPT_PINNEDPUBLICKEY.</td>
        </tr>
        <tr>
            <td><code>CURLE_SSL_INVALIDCERTSTATUS </code></td>
            <td>91</td>
            <td>Status returned failure when asked with CURLOPT_SSL_VERIFYSTATUS.</td>
        </tr>
        <tr>
            <td><code>CURLE_HTTP2_STREAM</code></td>
            <td>92</td>
            <td>Stream error in the HTTP/2 framing layer.</td>
        </tr>
        <tr>
            <td><code>CURLE_OBSOLETE*</code></td>
            <td></td>
            <td>These error codes will never be returned. They were used in an old libcurl version and are currently unused. </td>
        </tr>
    </tbody>
</table>

## 链接

- [curl函数](directory.md)
- 上一节：[curl_copy_handle](curl_copy_handle.md)
- 下一节：[curl_error](curl_error.md)
