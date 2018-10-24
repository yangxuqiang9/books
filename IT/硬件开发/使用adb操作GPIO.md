# 使用adb操作GPIO

2018/7/18

##  步骤1:取得gpio信息

* 在终端输入$cat /sys/kernel/debug/gpio这个命令可以查看系统注册的gpio接口,可以查看是否注册成功.

* 计算gpio号码   32*bank+gpio_no=sum

  *比如 gpio3 gpio_d3   32*3+27=123

  

  ## 步骤2:gpio控制测试

  * $echo 123 > /sys/class/gpio/export; 注册123这个gpio口
  * $echo out > /sys/class/gpio/gpio123/direction;设置输出,in为输入,out为输出
  * $echo 1 > /sys/class/gpio/gpio123/value 输出高电平
  * $echo 0 > /sys/class/gpio/gpio123/value 输出低电平

  

  