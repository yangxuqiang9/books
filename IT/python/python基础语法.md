#python
##环境
mac直接使用brew命令安装

```
brew install python
```
##中文编码
两种方式解决

```
1.# -*- coding: UTF-8 -*-
2.#coding=UTF-8
```
两种方式都需要在文件第一行添加
##基础语法
####python标识符
> 
    在python里，标识符有子母、数字、下划线组成
    区分大小写。以下划线开头的字符有特殊意义，以单下划线开头的
    字符代表不能直接访问的类属性，需要通过提供的接口进行访问，不能
    用“from xxx import *"导入。以双下划线开头的标识符代表私有
    成员。以双下划线开头和结尾的字符在python里是特殊方法的专用标
    识符 如：__init__()代表类的构造函数
    python可以在同一行显示多条语句，方法是用分号”;“分看
    
####python保留字符
> 	
    and exec not assert finally or break for pass class from print continue global raise def if return del import try elif in while else is with except lambda yield
    
    
####行和缩进

