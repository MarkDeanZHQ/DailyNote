# open 和 close函数
系统调用提供打开接口 open

c语言通过 可变长参数 做到 重载函数的功能


man
1. 命令
2. 系统
3. 库


## open 函数
int open(const char* pathname , int flags);
int open(const char* pathname , int flags , made_t mode);

pathname : 绝对/相对 路径
falgs : 打开文件的行为标志， 必选项(O_RDONLY , O_WRONLY , O_RDWR)
mode : 创建文件时，该参数生效， 指定创建文件的权限(文件所属者，文件所属组，其他组)  可使用数字法


flags可选项 【使用按位或连接】
|取值|含义|
|---|---|
|O_CREAT|文件不存在则创建文件|
|O_EXCL|文件存在则报错|
|O_TRUNC|打开并清空文件|
|O_APPEND|追加模式|
|O_NONBLOCK|对与设备文件，做非阻塞I/O|

## close 函数
int close(int fd):
fd : 文件描述符，open()的返回值

