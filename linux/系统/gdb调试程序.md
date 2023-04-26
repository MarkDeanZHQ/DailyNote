# gdb调试程序
进入调试条件：
1. 生成调试信息 gcc/g++ -g xxx.c 
2. 进入调试     gdb a.out


设置运行参数：
    set args   指定运行时的参数
    show args  查看设置好的运行参数
    
启动程序：
    run: 执行程序，若有断点，则停在断点处
    start: 从入口函数开始执行
    

## 调试功能
1. 查看原代码  
    * list   缩写 l
    * 用法：l linenum
    * l function
    * l - 显示前面的
    * l - 显示后面的
    * set listsize count  设置一次显示原代码行数
    * 查看当前的listsize的设置
    
2. 设置断点
    * break  缩写 b
    * b linenum  
    * b func 
    * 条件断电
    * b xxx.c:linenum if Value == val
    
3. 维护断点
    * info b  查看断点
    * enable [n-m] 
    * disable []
    * delete   []
    
4. 调试代码
    * run 
    * next
    * step 
    * finish  退出进入函数
    * until linenum  用于结束循环
    * continue  缩写 c
    * quit  缩写 q
    
5. 对变量进行的操作
    * display  自动显示变量
        * info display
        * undisplay num (info 编号)
        * delete display num
        * disable
        * enable
    * ptype val  查看变量类型
    * p val   打印变量
    * set var Val = val   将变量Val设置为 val
        * set var 告诉gdb后面跟的值不是参数，而是变量
        

