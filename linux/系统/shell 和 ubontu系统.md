# shell 和 ubontu系统

快捷搜索方式
有道词典

chsh  修改用户shell  
#!/bin/...    声明使用语言类型

## 创建子进程执行shell脚本

1. /bin/sh   sh    /bin/bash  bash

2. (cd .. ; ls -l)     直接输入
    括号创建子进程 shell 
    分号隔开多个命令
    

## 不创建子进程, 在当前shell中 执行
1. soucrce ./xx.sh
2. . ./xx.sh
3. 不加括号
    1.  (cd .. ; ls -l)     直接输入
    
注意： . 和 source  是同义词

变量：
    varname=value   //等号两边不留空格
    使用变量 $+变量名
    {}用来分隔变量名
    


sed  c\xxx   覆盖
     i\ xxxx  匹配行上方插入
     