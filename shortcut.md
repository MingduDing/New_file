## windows:

##### Cmd快捷键：

| 命令                  | 功能                             |
| --------------------- | -------------------------------- |
| dir /s                | 查看当前目录的所有子目录         |
| dir /a                | 查看包括隐含文件的所有文件       |
| cd \                  | 返回到根目录                     |
| cd ..                 | 退回到上一级目录                 |
| md 目录名             | 建立特定的文件夹                 |
| rd 目录名             | 删除特定的文件夹                 |
| cd.>a.txt             | 在当前目录新建a.txt文件          |
| echo a>a.txt          | 把字母a和回车换行覆盖输出到a.txt |
| echo b> >a.txt        | 把b和回车换行追加到文件末尾      |
| cls                   | 清除屏幕                         |
| del 文件名            | 删除一个文件(不能是文件夹)       |
| del \*.\*             | 删除当前文件夹所有文件           |
| ren 旧文件名 新文件名 | 更改文件名                       |
| ping 主机ip或名字     | 测试普通网络是否通畅             |
| ping -t               | 不停发送数据包                   |



##### PowerShell快捷键：

| 命令                            | 功能               |
| ------------------------------- | ------------------ |
| get-host                        | 查看PowerShell版本 |
| new-item 文件名 -type file      | 新建文件           |
| new-item 目录名 -type directory | 新建目录           |
| remove-item 文件或目录          | 删除文件或目录     |
| get-content 文件名              | 显示文本内容       |

##  Linux:

| 命令                     | 功能                            |
| :----------------------- | :------------------------------ |
| ifconfig                 | 获取ip                          |
| list ll                  | 列出当前目录下文件信息          |
| list -al                 | 列出当前所有文件信息            |
| touch 文件名             | 创建文件                        |
| clear                    | 清除屏幕                        |
| pwd                      | 打印工作目录                    |
| mkdir 目录名             | 创建目录                        |
| less -mN 文件名称        | 浏览文件内容                    |
| cp a b                   | 将文件a复制到文件b              |
| cp -r ./a ./b            | 将目录a复制到目录b              |
| mv a b                   | a复制到b，并删除a，剪切、重命名 |
| rm -f 文件名             | 删除文件                        |
| rm -rf 目录名            | 删除目录                        |
| find /目录/ -name ‘in*'  | 查找对应目录下以in开头的文件    |
| vim /目录/ 文件名        | 用vim编辑器打开文件             |
| cat /目录/a \| grep -i b | 查看a文件中包含b内容信息        |
| ps -ef                   | 任务管理器，查看进程            |
| ps -ef \| grep -i a      | 查看系统中a的进程信息           |
| kill -9 进程ID           | 杀死进程                        |



