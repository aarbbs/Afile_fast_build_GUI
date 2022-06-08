# Afile_fast_build_GUI

使用 aardio + web.view（WebView2） 制作，批量管理本地 makefile 工程文件，用于快速筛选指定工程和一键构建。

特色功能：makefile 工程文件分类、常用构建指令配置和快速选用、一键构建工程、error 信息高亮显示等...

## 运行演示

![87cc8aad69c5b2cfec25d23ea6c886f7.gif](https://img.aarbbs.com:1024/images/2022/06/08/87cc8aad69c5b2cfec25d23ea6c886f7.gif)

## 更新日志

### 2022-06-08

#### 变更

* 参照 aardio 作者 Jacen He 更新的 “web.view（WebView2） + 调用本地 ping 命令，并回显到页面示例”，简化程序代码，利于后期维护。
> 很赞同 aardio 作者所说的“扬长避短是智慧，倒行逆施最累人”，但作为一名 aardio 菜鸟用户，我是很乐意学习不同的实现目的的方法，因为我使用 aardio 写程序是个人兴趣，因为喜欢，所以想多了解一些时当然的啦。


### 2022-06-05

#### 优化

* 使用一位好心的群友【Runy】大佬给的process回显方法