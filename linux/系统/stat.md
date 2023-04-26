# stat
vim下获取文件指定行 ： r ! sed -n "n,mp" < filename

S_IFMT  过滤文件类型
if(stat.st_mode & S_IFMT == ...)****

S_IFSOCK   socket 文件
S_IFLINK   symbolic link 文件
S_IFREG    regular file  普通文件
S_IFBLK    block device   块设备
S_IFDIR    directory       目录
S_IFCHR   character device  字符设备
S_IFIFO    FIFO  管道