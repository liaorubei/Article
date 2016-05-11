Android shape ring
最近想要做一个进度加载的动画,就是那个一直转圈的圆环,一开始加载动画是图片做的,有点模糊,看着纠结,于是下定决心整改成shape.

<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android"
    android:shape="ring"
    android:useLevel="false">
    <gradient
        android:endColor="#0000A478"
        android:startColor="#00A478"
        android:type="sweep" />
</shape>

当要做成圆环时,shape节点的两个属性必须要有,一个是android:shape="ring",别一个是android:useLevel="false"
当然,要想在加载时的动画有明显的对比效果,在shape节点下还得加一个渐变的节点,gradient而不是加solid或者其他
同时gradient的开始颜色和结束颜色要不一样,渐变效果选择android:type="sweep",而不是线性,或者射线类型,这样你就可以得到一个清晰的圆环了,而且还不会因为屏幕的更改而失真