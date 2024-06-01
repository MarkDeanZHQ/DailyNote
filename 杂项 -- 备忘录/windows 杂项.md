# 杀死多个相同进程名
taskkill 命令
taskkill /f /t /im chrome.exe
1
/f 表示强制终止进程。如果不指定，那么 taskkill 会给进程发送终止信号，但进程可以阻止退出（例如提示文档需要保存）。指定了，就会强杀进程。 

/t 表示结束此进程和其子进程。

/im 用来指定进程的影映像名称（有 .exe 后缀）。

```cmd
@echo off
taskkill /f /im xxxx.exe # 删除某个进程
set n=0


:run
set /a n=%n%+1
echo 第%n%调用
timeout 1
if %n% equ 5 exit
goto run
```