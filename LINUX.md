## 指令 --help
查看某一个指令的用法

## 命令英文全名
- ls = list
- cd = change directory
- cp = copy
- rm = remove
- mv = move
- pwd = print work directory
- ps = process status
- df = disk free
- du = disk usage
- mkdir = make directory
- rmdir = remove directory
- su = switch user
- chown = change owner
- chmod = change mode

## 参数英文全名
- -a = all
- -l = list
- -f = force
- -h = human readable（将文件大小转成以人可读的大小单位，如：K、M、G）
- -n = number
- -u = user
- -z = zip

## ls [-alhrtAFR]

ls -a 显示所有文件及目录 (与ls不加参数的区别是ls内定将文件名或目录名称开头为"."的视为隐藏档，不会列出，而-a会)  
ls -l 除文件名称外，亦将文件型态、权限、拥有者、文件大小等资讯详细列出  
ls -h 和ls -l一起使用时以K, M, G为单位表示文件大小  
ls -r 将文件以相反次序显示(原定依英文字母次序)  
ls -t 将文件依建立时间之先后次序列出  
ls -A 同-a，但不列出 "." (当前目录) 及 ".." (父目录)  
ls -F 在列出的文件名称后加一符号；例如可执行档则加 "*", 目录则加 "/"  
ls -S 根据文件大小排序  
ls -R 若目录下有文件，则以下之文件亦皆依序列出  

## cat/tac/more/less/head/tail/nl/od [file name]

### cat
> 从第一行开始显示文件的所有内容

### tac
> 从最后一行开始显示文件的所有内容

### more
> 一页一页的显示文件的所有内容，只能向下翻页，不能向上翻页

### less
> 一页一页的显示文件的所有内容，能向下翻页，也能向上翻页

shift + g 定位到文件的最后一页

### head
> 只看文件的头几行

### tail
> 只看文件的后几行

### nl
> 从第一行开始显示文件的所有内容，并在每一行的开始显示行号

### od
> 以二进制的形式显示文件的所有内容

## mkdir touch

### mkdir [-p] [dir name]
> 新建目录

mkdir a 在工作目录中新建一个名为a的目录  
mkdir -p a/b 建立一个名为b的子目录，若a目录原本不存在，则建立一个，若不加-p，且原本a目录不存在，则发生错误

### touch
> 新建文件，或者修改已存在文件的时间属性

touch file 新建一个名为file的空白文件  



## cd [path]

cd . 当前目录  
cd .. 上一级目录  
cd - 最新一次更换目录前所在的目录  
cd / 根目录  
cd ~ 当前用户的用户目录  

## ps 查看进程

ps -ef | grep java 查看名为java的进程，其中ps -ef为查看进程，|表示管道命令，grep表示查找

## find
-name `find /etc -name "*.conf"` 查看/etc目录下面所有的.conf结尾的文件
