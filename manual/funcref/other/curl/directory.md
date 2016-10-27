## 简介
PHP 支持 Daniel Stenberg 创建的 libcurl 库，能够连接通讯各种服务器、使用各种协议。libcurl 目前支持的协议有 http、https、ftp、gopher、telnet、dict、file、ldap。 libcurl 同时支持 HTTPS 证书、HTTP POST、HTTP PUT、 FTP 上传(也能通过 PHP 的 FTP 扩展完成)、HTTP 基于表单的上传、代理、cookies、用户名+密码的认证。

### 安装配置
* 需求  
    需要安装» libcurl包才能使用 PHP 的 cURL 函数。PHP 需要使用 7.10.5 或更高版本的 libcurl。

### CURL函数
* [curl_init](/curl_init.md) — 初始化一个cURL会话
* [curl_close](/curl_close.md) — 关闭一个cURL会话
* [curl_copy_handle](/curl_copy_handle.md) — 复制一个cURL句柄和它的所有选项