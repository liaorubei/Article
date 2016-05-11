使用gradle packagingOptions给Apk"减肥"
在应用开发当中要集成PaypalSDK，但是Paypal SDK又引用了远程库card.io，本来没有问题，但是card.io开发组太负责了，支持了好几个平台armeabi mips 还有64位的
这一下子多出来好大的体积,比引用的Paypal还要大,由于不想apk文件体积太大,所以就打算在支持的平台上想办法,那就是只支持armeabi和armeabi-v7a,什么arm64-v8a,mips,x86,x86_64通通不支持,
没曾想,一不小心减了7M多的体积,可高兴了,本来我应用就没多大,这个card.io就用了相当多的一部分,而且这个功能还是平时用得不是很多的

具体主要代码是在build.gradle 的android{} 里面放上:
    packagingOptions {
        //exclude:vt. 排除；排斥；拒绝接纳；逐出
        exclude 'lib/arm64-v8a/libcardioDecider.so'
        exclude 'lib/arm64-v8a/libcardioRecognizer.so'
        exclude 'lib/arm64-v8a/libcardioRecognizer_tegra2.so'
        exclude 'lib/arm64-v8a/libopencv_core.so'
        exclude 'lib/arm64-v8a/libopencv_imgproc.so'
        //exclude 'lib/armeabi/libcardioDecider.so'
        //exclude 'lib/armeabi-v7a/libcardioDecider.so'
        //exclude 'lib/armeabi-v7a/libcardioRecognizer.so'
        //exclude 'lib/armeabi-v7a/libcardioRecognizer_tegra2.so'
        //exclude 'lib/armeabi-v7a/libopencv_core.so'
        //exclude 'lib/armeabi-v7a/libopencv_imgproc.so'
        exclude 'lib/mips/libcardioDecider.so'
        exclude 'lib/x86/libcardioDecider.so'
        exclude 'lib/x86/libcardioRecognizer.so'
        exclude 'lib/x86/libcardioRecognizer_tegra2.so'
        exclude 'lib/x86/libopencv_core.so'
        exclude 'lib/x86/libopencv_imgproc.so'
        exclude 'lib/x86_64/libcardioDecider.so'
        exclude 'lib/x86_64/libcardioRecognizer.so'
        exclude 'lib/x86_64/libcardioRecognizer_tegra2.so'
        exclude 'lib/x86_64/libopencv_core.so'
        exclude 'lib/x86_64/libopencv_imgproc.so'
    }

然后clean project,运行，效果立竿见影,直接少了7M多的体积.如果有谁也要到这个功能,那么可以这个写.
当然,不推荐全部平台都移除,不然这个功能真的就一点都不能用了	