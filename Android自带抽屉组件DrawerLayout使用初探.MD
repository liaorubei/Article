Android自带抽屉组件DrawerLayout使用初探
主要方法

1.DrawerLayout.addDrawerListener(DrawerListener listener)
  DrawerLayout.setDrawerListener(DrawerListener listener)
为抽屉组件添加一个监听,该监听可以在组件滑动过程,抽屉打开,抽屉关闭,状态改变时触发;
        drawer.addDrawerListener(new DrawerLayout.DrawerListener() {
            @Override
            public void onDrawerSlide(View drawerView, float slideOffset) {

            }

            @Override
            public void onDrawerOpened(View drawerView) {

            }

            @Override
            public void onDrawerClosed(View drawerView) {

            }

            @Override
            public void onDrawerStateChanged(int newState) {

            }
        });
		
2.DrawerLayout.openDrawer(int gravity)	
打开抽屉组件的指定抽屉,比如左边的,或者右边的,
参数gravity是Gravity.LEFT,Gravity.RIGHT,GravityCompat.START,GravityCompat.END四个中的一个,其他的没有测试过,不过应该也可以.

3.DrawerLayout.closeDrawer(int gravity)
关闭指定方向上的抽屉组件,
参数gravity也是Gravity.LEFT,Gravity.RIGHT,GravityCompat.START,GravityCompat.END四个中的一个

4. DrawerLayout.closeDrawers();
关闭所有的抽屉组件

5.DrawerLayout.isDrawerOpen(int drawerGravity)
顾名思义,判断指定方向上的抽屉组件是否在关闭状态,参数就不用再说了

相关类:ActionBarDrawerToggle












