安卓发布新版本时遇到的问题之versionCode与versionName

今天在更新新版本的时候,在两个应用市场中遇到更新包上传完成后被拒的问题,一个是Google Play另一个貌似是360.为什么会被拒呢?原来我项目的版本内容只修改了versionName,但是并没有修改versionCode,Google Play的Console在我上传完APK包之后,直接告诉我versionCode没有改变,所以无法添加更新包.
另一个市场也是这样.不过另一个市场不是太重要,我直接移除了原来的APK包,然后用新的覆盖了.但是Google找不到移除原来APK的地方,下架又怕出问题,最后是在代码中升级了一下versionCode,然后重新编译了一个APK上传了事.

原来Google给我们的项目设置了versionCode与versionName不是随便瞎弄出来的,而是至少经过了一点点的考虑的.versionCode要求是一个整型,容易比较,一般是用来面对开发者的,让开发者在代码中便于比较版本的新旧;versionName要求是一个String,可以写一些有意义的名字,如:新春版,V2015等,主要是面对使用者,比如已经修改过好几个小缺陷了,但是versionName也没有更改,或者更改比较少.
另外有时有一些不明显的缺陷,内部修改了之后,并不会马上发布,但是又表明了版本内容有了更新.
另外,在发布应用时,最好versionCode和versionName最好可以同时更改升级,这样一来,开发者与使用者都能各取所需,明确识别版本