Android锁屏息屏状态下直接亮屏并操作

要实现这个功能相当简单,只需要在我们的Activity的onCreate方法里添加如下代码就可以了
getWindow().addFlags(WindowManager.LayoutParams.FLAG_SHOW_WHEN_LOCKED | WindowManager.LayoutParams.FLAG_TURN_SCREEN_ON);

添加了这个代码之后,如果该Activity在手机锁屏并息屏状态下启动,如收到广播之后启动一个Activity,手机屏幕就会从锁屏息屏状态直接亮屏,并且不用输入开机密码就可以操作.
当然,如果你想要操作别的应用,还是要输入密码的,而且屏幕在过一段时间没有操作之后还是会息屏的.就好像闹钟一样,时间到了,弹出界面,可以让你关闭闹钟或者多睡一会,但是你想躺床上发个微博说你起床了,就得输入密码解锁手机.
