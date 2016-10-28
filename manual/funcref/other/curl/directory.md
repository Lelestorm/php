## 简介
PHP 支持 Daniel Stenberg 创建的 libcurl 库，能够连接通讯各种服务器、使用各种协议。libcurl 目前支持的协议有 http、https、ftp、gopher、telnet、dict、file、ldap。 libcurl 同时支持 HTTPS 证书、HTTP POST、HTTP PUT、 FTP 上传(也能通过 PHP 的 FTP 扩展完成)、HTTP 基于表单的上传、代理、cookies、用户名+密码的认证。

### 安装配置
* 需求  
    需要安装» libcurl包才能使用 PHP 的 cURL 函数。PHP 需要使用 7.10.5 或更高版本的 libcurl。

### CURL函数
* [curl_close](curl_close.md) — 关闭一个cURL会话
* [curl_copy_handle](curl_copy_handle.md) — 复制一个cURL句柄和它的所有选项
* [curl_errno](curl_errno.md) — 返回最后一次的错误号
* [curl_error](curl_error.md) — 返回一个保护当前会话最近一次错误的字符串
* [curl_escape](curl_escape.md) — 使用 URL 编码给定的字符串
* [curl_exec](curl_exec.md) — 执行一个cURL会话
* [curl_file_create](curl_file_create.md) — 创建一个 CURLFile 对象
* [curl_getinfo](curl_getinfo.md) — 获取一个cURL连接资源句柄的信息
* [curl_init](curl_init.md) — 初始化一个cURL会话
* [curl_multi_add_handle](curl_multi_add_handle.md) — 向curl批处理会话中添加单独的curl句柄
* [curl_multi_close](curl_multi_close.md) — 关闭一组cURL句柄
* [curl_multi_exec](curl_multi_exec.md) — 运行当前 cURL 句柄的子连接
* [curl_multi_getcontent](curl_multi_getcontent.md) — 如果设置了CURLOPT_RETURNTRANSFER，则返回获取的输出的文本流
* [curl_multi_info_read](curl_multi_info_read.md) — 获取当前解析的cURL的相关传输信息
* [curl_multi_init](curl_multi_init.md) — 返回一个新cURL批处理句柄
* [curl_multi_remove_handle](curl_multi_remove_handle.md) — 移除curl批处理句柄资源中的某个句柄资源
* [curl_multi_select](curl_multi_select.md) — 等待所有cURL批处理中的活动连接
* [curl_multi_setopt](curl_multi_setopt.md) — 为 cURL 并行处理设置一个选项
* [curl_multi_strerror](curl_multi_strerror.md) — 返回错误码的字符串描述
* [curl_pause](curl_pause.md) — 暂停和恢复运行 cURL 句柄的连接
* [curl_reset](curl_reset.md) — 重置一个 libcurl 会话句柄的所有的选项
* [curl_setopt_array](curl_setopt_array.md) — 为cURL传输会话批量设置选项
* [curl_setopt](curl_setopt.md) — 设置一个cURL传输选项
* [curl_share_close](curl_share_close.md) — 关闭一个 cURL 共享句柄
* [curl_share_init](curl_share_init.md) — 初始化一个 cURL 共享句柄
* [curl_share_setopt](curl_share_setopt.md) — 设置一个cURL 共享句柄传输选项.
* [curl_strerror](curl_strerror.md) — 返回给定的错误码的错误描述
* [curl_unescape](curl_unescape.md) — 解码给定的 URL 编码的字符串
* [curl_version](curl_version.md) — 获取cURL版本信息
* [curl_errno](curl_errno.md)
* [curl_errno](curl_errno.md)
* [curl_errno](curl_errno.md)
* [curl_errno](curl_errno.md)

### CURLFile 类
* [CURLFile::__construct]() — 创建 CURLFile 对象
* [CURLFile::getFilename]() — 获取被上传文件的 文件名
* [CURLFile::getMimeType]() — 获取被上传文件的 MIME 类型
* [CURLFile::getPostFilename]() — 获取 POST 请求时使用的 文件名
* [CURLFile::setMimeType]() — 设置被上传文件的 MIME 类型
* [CURLFile::setPostFilename]() — 设置 POST 请求时使用的 文件名
* [CURLFile::__wakeup]() — 反序列化句柄

##链接