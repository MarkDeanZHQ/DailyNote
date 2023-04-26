# makefile
命令格式  make -f file [option]  [targets]
make 默认执行文件名 makefile/Makefile
option
    -v 版本信息
    -w 执行前后的工作路径
    -C dir 以 dir 为工作路径执行
    -n 查看要执行的命令，但不执行
    -s 执行，不显示步骤
    
[targets]
    执行的目标  默认为makefile文件中的第一个目标
    执行目标后，即退出
    可指定执行目标为 一个 或 多个 (空格隔开)
    
 
makefile 文件内容格式和规则：
    目标:依赖1  依赖2
        完成依赖后，执行命令
        
<details>
<summary>    文件变量：</summary>
        定义方法  变量名=变量值
        引用变量  $(变量名)或 ${变量名}
    
    makeifle变量的命名规则：
        * 可以数字开头
        * 大小写敏感
        * 一般 头部定义
        * 几乎可于文件内任何地方使用
    应用提供变量：
        - CC --- gcc
        - CPPFLAGS --- C预处理选项
        - CFLAGS  --- C编译器选项
        - LDFLAGS --- 连接器选项 

    自动变量
        * $@：规则中的目标 
        * $<: 规则中的第一个条件
        * $^: 规则中的所有条件(组成一个列表，用空格隔开，若有重复项，消除重复项)
</details>
        
<details>
    <summary>   参考示例： </summary>

    #变量
    OBJS=add.o sub.o mul.o div.o test.o add.o
    TARGET=test
    CC=gcc

    ​

    #$@: 表示目标
    #$<: 表示第一个依赖
    #$^: 表示所有的依赖

    ​

    $(TARGET):$(OBJS)
        #$(CC) $(OBJS) -o $(TARGET) 
        $(CC) $^ -o $@
        echo $@
        echo $<
        echo $^

    add.o:add.c
        $(CC) -c $< -o $@ 
    ​

    sub.o:sub.c
        $(CC) -c $< -o $@ 

    mul.o:mul.c
        $(CC) -c $< -o $@ 
        
    div.o:div.c
        $(CC) -c $< -o $@ 

    test.o:test.c
        $(CC) -c $< -o $@

    clean:
        rm -rf $(OBJS) $(TARGET)
</details>


模式规则：

    %.o:%.c    //%表示匹配所有
    $(CC) -c $(CLFAGS) $(CPPFLAGS) $< -o $@
    
<details>
    <summary>Makefile第三个版本：</summary>

    OBJS=test.o add.o sub.o mul.o div.o
    TARGET=test
    $(TARGET):$(OBJS)
        gcc $(OBJS) -o $(TARGET) 
    %.o:%.c
        gcc -c $< -o $@
</details>


两个常用函数：
    1. 查找指定目录下的指定文件   ---   wildcard 
        * src = $(wildcard *.c)  // 找到当前目录下所有为 .c 的文件，并赋值给src
    2. 匹配替换   ---   patsubst
        * obj = $(patsubst %.c,%.o,\$(src))  // 把src变量里的所有 .c 替换成 .o
        

伪目标： 不判断目标 存在或更新 与否，强制执行
使用方式：对目标进行伪目标声明， .PHONY:clean

特殊符号的功能 与 使用
 "-"  此命令出错，继续执行后续命令
 "@"  不显示命令本身
 例：-rm mian.o
      @echo clean done
      

<details> 
        <summary>Makefile第五个版本</summary>
            
    SRC=$(wildcard *.c)
    OBJS=$(patsubst %.c, %.o, $(SRC))
    TARGET=test
    $(TARGET):$(OBJS)
        gcc $(OBJS) -o $(TARGET) 
    ​

    %.o:%.c
        gcc -c $< -o $@
    .PHONY:clean

    clean:
        rm -rf $(OBJS) $(TARGET)
        
</details>

总结： 一条规则，两个函数，三个变量。
    <details><summary>一条规则</summary>
> %.o:%.c
> 
> $(CC) -c $(CFLAGS) $(CPPFLAGS) $< -o $@
    </details>
    <details><summary>两个函数</summary>
> 1.  wildcard – 查找指定目录下的指定类型的文件
> 
> src = $(wildcard \*.c) //找到当前目录下所有后缀为.c的文件,赋值给src
> 
> 2.  patsubst – 匹配替换
> 
> obj = $(patsubst %.c,%.o, $(src)) //把src变量里所有后缀为.c的文件替换成.o
    </details>
    <details><summary>三个变量</summary>
    *   $@: 表示规则中的目标
    *   $<: 表示规则中的第一个条件
    *   $^: 表示规则中的所有条件, 组成一个列表, 以空格隔开,如果这个列表中有重复的项则消除重复项。    
    </details>