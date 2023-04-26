# gcc
-E  预处理
-S  汇编
-c  二进制
-o  链接，可执行文件

-On n=0~3  编译优化程度

-Wall 显示所有警告信息
-Werror 把警告当错误处理

-D 定义宏(编译阶段)


-static .c -o 生成的filename静态编译 


静态库制作： 静态库命名： libxxx.a
1. gcc -c .. -o .. 将c源文件生成对应 .o 文件
2. ar -rcs libxxx.a .o .o ... 打包.o文件为.a库文件  (ar可将.a库文件 拆分出.o文件)
    1. r 更新
    2. c 创建
    3. s 建立索引
3. 使用静态库  gcc .c -L path -I(大写i) path -l(小写l) libname -o 生成文件    
    1. -L 库目录
    2. -I(i) 头文件目录
    3. -l(L) 库名
    

动态库制作：动态库命名： libxxx.so
1. gcc -fPIC(fpic)   -c .c    (pic position independent code) 创建地址无关编译程序
2. gcc -shared .o .o ..   -o libxxx.so   生成共享库
3. nm  libxxx.so  查看动态库对应函数
4. ldd filename   查看可执行文件的依赖动态库
 


让系统找到动态库的方法
    1. export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:库路径
    在标准输入中，临时设置
    永久设置，设置到~/.bashrc  或 /etc/profile 文件中  
    设置完成后 source ~/.bashrc 进行加载
    2. 添加到/etc/ld.so.conf文件，加入库文件所在目录的绝对路径
    sudo ldconfig -v  重建/etc/ld.so.cache文件
    3. 使用符号链接，使用绝对路径放到 /lib/ 目录下
    sudo ln -s /home/zhq227/test/libtest.so /lib/
    
