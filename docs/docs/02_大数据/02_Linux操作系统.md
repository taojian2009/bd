### 7. linux系统概述

`Linus Benedict Torvalds`，1969年12月28日

发行版： `ubuntu`, `centOS`, `red Hat`, `deepIn`, `debian`

#### 7.1 linux目录结构
windows 类似森林； linux树形结构；

/bin: 二进制可执行文件

/etc: 系统配置，启动程序；

/home: 普通用户在home 

/root: 超级用户的home 

/sbin: 系统管理的命令 

/usr: 系统安装的软件

/opt: 自己安装的软件  

必须要学会必要的命令行；


#### 7.2 常见的linux命令

`ls`:  
+ -a: 所有文件
+ -l: 显示文件详情
+ -h: 友好的方式显示文件大小；
```shell
ls -Slha   # 显示当前目录所有文件，并按照大小排序，文件大小以human readable方式展示；

du -Sh  # 显示当前文件下的所有文件，并按照大小排序；

```
`pwd`: 查看当前路径；

`mkdir`: 创建文件夹
在当前目录递归创建多层文件夹 

```shell
mkdir -p tableNames/hive/prod
```

`rm`: 删除文件
```shell
rm -rf tableNames/hive
```


`cd`: 切换文件夹
```shell
cd 
cd ..
cd - # 最近进入的文件夹切换
```

`touch`: 创建文件 

```shell
touch a.txt b.txt c.txt d.txt e.txt f.txt  # 创建多个文件
touch /root/a.txt   
```

`mv`: 1. 移动文件或者文件夹  **2. 重命名**   
```shell
mv a.txt dir   # 移动文件到文件夹， dir必须存在
mv a.txt b.txt  # 重命名文件
mv dir  dir1   # 重命名文件夹， dir1不能存在
```

`cat`: 查看文件内容  



`cp`: 复制文件或者文件夹

```shell
cp a.txt b.txt     # cp file 
cp -r dir1/*   dir2  # cp files in dir1 to dir2
scp username@ip:/home/jian.tao01/data.csv .  # copy remote file to local 
```

`tar`: 压缩和解压  

参数 | 解释
:---:|:---:
-C | create a new tar file
-X | decompress a file 
-v | view the information 
-f | file, what file
-z | 调用gzip压缩命令进行压缩
-t | 查看压缩文件的内容  
linux里面一般是`.tar.gz` 结尾的压缩文件
```shell
# 解压 decompression
tar -zxvf redis.tar.gz  # 将此压缩文件解压到当前文件夹
tar -zxvf redis.tar.gz ~/redis # 将压缩文件解压到指定文件夹
# 压缩  compression 
tar -zcvf redis.tar.gz maybe  # 创建压缩文件 
```
`zip`: zip and unzip 

```shell
zip -r dir1.zip dir1  # zip dir1 
unzip -d ~/opt dir.zip    # unzpi dir1 
```

`find`: 查找符合条件的整个文件 

```shell
find . -name 'code*'  # find  targer folder -name 'regex'
# 结果  ./code.zip
find . -name '*.py'  
```

`grep`: 查找文件中的文本内容  
grep命令一般很少单独使用
```shell script
grep 大数据 02_大数据/01_大数据概念.md --color
```

`which`: 查找可执行文件的路径  

```shell
which oss  # 查找可执行文件oss的位置 
```

##### 系统管理命令

`ps`: 
```shell script
ps -ef # 查看所有的进程
```
`kill`:
```shell
kill -9  $pid  #杀死某个进程
kill -l # 查看所有的信号
```
`-9 表示给这个进程第9号信号，杀死的意思`

`管道命令`: | 第一个命令的输出，变为第二个命令的输入；


`用户相关命令`：
```shell
useradd username  # 添加用户
passwd username  # 创建密码
userdel -r username # 删除用户
```

##### 权限管理命令

```
-r--------    1   staff     9B  5 25  2020 .CFUserTextEncoding
drwx------    2   staff    64B 11 13 15:06 .Trash
drwxr-xr-x    2   staff    64B  5 26  2020 .android
```
`d`: dir ； 
`-`； 文件

`d rwx rwx rwx `: 
 ```shell
r # 可读
w # 可写
x # 可执行 
```
`为啥有三个呢`： 

1.所属用户: 文件的创建者   `u`: user
2.所属用户组: 用户往往在一个用户组里，组里的人对这个文件的权限  `g`: group 
3.其他用户: 其他用户 `o`: other 

```shell
-| rw-|  r--| r--   
# 文件类型|可读写，不可执行|可读，不可写和执行|可读，不可写和执行
```
```chmod```: 修改权限

```shell

chmod 777 a.txt   # 添加所有权限
chmod u+x a.txt   # 为当前用户添加x的权限
chmod g-x a.txt   # 为当前用户组减少所有权限
chmod u+rwx a.txt  # 为挡墙用户添加rwx的权限  
chmod u=x a.txt # 去掉当前用户的所有权限
chmod +x a.txt # 为所有用户添加执行权限
```

##### 网络管理命令

`hostname`: node1 

`ifconfig`: 查看ip地址

A类IP： 255.0.0.0

B类IP： 255.255.0.0

C类IP： 255.255.255.0

`service`: service 命令；
```shell script
service network status
service network stop
service network start 
service network restart 
```

##### 其他命令

`ln`: 软连接
```shell
ln -s /opt/ossutil /usr/local/bin/oss    # 建立软连接
ln -s 真实文件   快捷方式
```
`l`: link; `-`: file; `d`: directory


#### Vim编辑器

有三种模式： `命令行模式`, `编辑模式`, `底行模式` 

`i` : 插入

`o`: 换行插入

`O`: 在上行插入

`ecs`： 切换模式  

`:`: 进入底行模式

`yy`: 复制
`5yy`: 复制5行
`p`: 粘贴 
`u`: 撤销
`dd`： 删除
`5dd`: 删除5行


`gg`: 回到文件首部
`G`: 到文件底部 
`/hello`: 查找  


`wq`: 保存退出

`q`: 退出

`q!`: 强制退出 



`vi`: 简单模式

`vim`: 丰富模式  


`set nu`: 显示行号 


`:123`: 将光标定在123行  

`%s/hello/haha`: 将hello 替换成haha 










