# Linux Commands

## sudo apt-get update

## chmod o+w filename
修改文件或文件夹读写权限

## echo
`echo`: 用于向标准输出设备上输出文本字符串

```
$ echo Hello! World!  // Hello! World!
$ echo "Hello! World!" // Hello! World!
$ echo 'Hello! "zhangsan"' // Hello! "zhangsan"
$ echo "Hello! \"zhangsan\"" // Hello! "zhangsan"
$ echo -e "You know nothing. \n\t- Ygritte"  // -e: 激活转义字符
$ echo -e "#Learn Git" > README.md // 重定向输出(到一个文件)，文件不存在则创建一个新文件  > :文件被覆盖
$ echo -e "# Learn Git" >> README.md //重定向输出(到一个文件) 文件不存在则创建一个新文件 >>: 文件被添加
```

## touch
`touch`：allow us to update the timestamp on existing files and directories as well as creating new, empty files.
```
$ touch file1 //创建或修改一个文件
$ touch file1 file2 file3  //创建或修改多个文件
$ touch -C file1 // -C: --no-create  only update the timestamp ,otherwise it will do nothing
```





## 参考
![LinuxIZE.com](http://www.linuxize.com)
