# Shell
>简介：
用户 对内核交互的 桥梁

功能特性：
* 调用命令行工具完成
* 胶水语言，整合其他编程语言

## shell 的查看和配置

### 查看 shell
* cat /etc/shells    系统默认安装的 shell
* echo $SHELL    当前用户默认 shell
* echo $0     查看当前 shell


### 配置

#### 通过名称(非目录文件)调用脚本
>脚本路径包含在 $PATH 变量中
1. 临时加入path变量
    * PATH=$PATH:/New/path  
2. 永久修改变量
    * .bash_profile 用户 / profile 系统
    * .bashrc  
    * 添加 export 语句
    <font color=red>注意：该文件分系统和个人用户两种：系统在 /etc/   个人在家目录</font>
    系统的是全局变量
    用户的是局部变量/新开bash则失效
    
添加方法：  source ~/.bash  更新文件
在export PATH后面
例如：
export PATH
a=200   #定义a=200



#### 后台执行脚本
1. ./file &  后台运行
2. nohup ./my_script.sh  &  脚本在退出shell后也能运行

<font color=red>注意：</font>
1. 脚本标准输出和标准错误重定向到nohup.out 文件
2. jobs 查看后台进程
 





## shell 的语法和使用
>注释符： #    放在开头也可作为 shebang 记号



1. 指定脚本解释器
    * 一般在脚本第一行
    * 格式如下：#!/bin/...
2. 执行方式
    1. sh file
    2. ./file
    
### 变量
>命名规则：
1. 数字、字母、下划线
2. 开头 字母、下划线

常识：
1. 变量没有数据类型  variable=value 即可
2. 调用变量时，要在变量名前+$ 如： $a
3. 支持自增自减符号
4. ** 求幂
5. % 求余

定义变量格式：
1. vari=val
2. vari='val'   单引号代表纯字符
3. vari="val"    双引号会展开变量
4. \`pwd`     反引号使用命令，并将输出结果传递进来

括号使用：
1. {}  花括号      变量隔开符号
2. $[]      整数算术运算：可在里面完成算数运算 $[\$COUNT+1]

#### 特定变量
$0  执行脚本名字
$2  第二个参数名
$#  参数的个数
!$  上一个参数
!命令    引用上一次使用该命令的参数
!数字    history里面的命令号
!?字符串     使用最近一次包含该字符串的命令







#### 类型
1. 环境变量
2. 用户定义变量

#### 查看变量
1. printenv  全局变量
2. set   查看某个进程中的所有变量



### 编程语句

#### if语句
语法: 
```bash
if command #(判断条件 状态码为 0 则继续执行)
    then
        commands
    elif command
        then
    fi
        
fi

```

##### 判断值相等
```bash

while((1))
do
        read gnum
        if [ $num == $gnum ]
        then
                echo "You win!"
                break
        else
                echo "Please guess again."

        fi

done


```

##### 判断对应文件名文件是否存在
```bash
file_name=$1 #获取第一个参数
if [ -a $file_name ] #-a 判断文件是否存在    -f 判断文件是否存在且是普通文件
then
    ...
else
    ...
fi
```





#### case
语法：
```bash

case val in
    pattern1 | pattern2) commands1;; #满足val 等于 1 或 2 的时候执行
    pattern3) commands2;;  #满足val == 3 的时候 执行
    *)default commands;; #上述都不满足时执行
```
    

#### 循环语句
1. for
2. while
3. until
4. 循环控制符
    1. break
    2. continue
    
##### for
* shell风格

###### 循环数值
```bash
for i in {1..10}
    do
        printf "$i\n"
    done

```

```bash
for ((i = 1; i<10;i++))
    do
        echo "Hello"
    done
```


###### 99乘法表
```bash

#!/bin/bash
for (( i=1; i<=9; i++)) do
        for ((j=1; j<=i; j++)) do
                let "temp=i*j"
                echo -n "$i*$j=$temp "
        done
        printf "\n"
done

```


###### 循环命令 
打印 ls 命令输出
```bash
for file in $(ls)
    do
        echo "file: $file"
    done

```

```bash
for HOST in host1 host2 host3;do echo $HOST;done

for HOST in host{1..3};do echo $HOST;done

for EVEN in ${seq 2 2 8};do echo $EVEN;done;# seq 表示 从 2 开始 每隔 2个数取一个值， 到 8 结束
```



##### while 和 util

```bash
#!/bin/bash
sum=0；i=1
while((i <= 100)) # 或者填写 until((1>100))
do 
    let"sum+=i"
    let"i+=2"
done
    echo "sum=$sum"
```


###### 循环传入参数
```bash
while [ $1 ]
do
    if [ -f $1 ]
    ...
    fi
    shift
done
```



