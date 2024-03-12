# 文件和目录

```bash
cd /home 进入 '/ home' 目录'
cd .. 返回上一级目录
cd ../.. 返回上两级目录
cd 进入个人的主目录; cd ~user1 进入个人的主目录
cd - 返回上次所在的目录
pwd 显示工作路径
ls 查看目录中的文件
ls -F 查看目录中的文件
ls -l 显示文件和目录的详细资料
ls -lh 显示文件和目录的详细资料,以及文件大小
ls -a 显示隐藏文件
ls *[0-9]* 显示包含数字的文件名和目录名
mkdir dir1 创建一个叫做 'dir1' 的目录'
mkdir dir1 dir2 同时创建两个目录
rm -f file1 删除一个叫做 'file1' 的文件'
rmdir dir1 删除一个叫做 'dir1' 的目录'
rm -rf dir1 删除一个叫做 'dir1' 的目录并同时删除其内容
rm -rf dir1 dir2 同时删除两个目录及它们的内容
mv dir1 new_dir 重命名/移动 一个目录
cp file1 file2 复制一个文件
cp dir/* . 复制一个目录下的所有文件到当前工作目录
```

# 文件的权限 - 使用 "+" 设置权限，使用 "-" 用于取消

```bash
chmod +x file1 给所有用户执行权限 等同于chmod a+x file1--all，other，group，user
```

# 查看文件内容

```bash
head -2 file1 查看一个文件的前两行
tail -2 file1 查看一个文件的最后两行
cat file1 从第一个字节开始正向查看文件的内容
tac file1 从最后一行开始反向查看一个文件的内容
```

# 文本处理

```bash
cat -n file1 查看文件并显示行数
```

# 其他资料

[常用命令全拼](https://www.runoob.com/w3cnote/linux-command-full-fight.html)