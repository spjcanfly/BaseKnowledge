##1.Android Studio的安装的收获##
 
     1. 在那个520安卓自定义控件的文件夹中有个安卓资料，使用文档里面有安装的十分具体的方法，还有一个快捷键和代码模板用来导入as中（和eclipse的快捷键的使用十分相似），快捷键的使用文档。
     2. 在安装as的时候最好有网，才能在联网下下载一些需要使用的东西


##2.把不同版本的项目导入进来如何修改？

    第一：进入项目，有个build文件，进入，修改 dependencies {
        classpath 'com.android.tools.build:gradle:1.5.0'｝把改成你的版本

    第二：进入gradle---wrapper---gradle-wrapper中，distributionUrl=https\://services.gradle.org/distributions/gradle-2.8-all.zip，2.8是你的版本号，

    结束。
    
    2.1 将eclipse的工程导入AS中
    
    可以直接import module，也可以new module，里面有一个选项是
    Import Eclipse也可以导入。
    
##3.关于build.gradle的里面的关键编译的讲解

     compileSdkVersion 23  这个是api的版本，高的版本里面的方法多而且新，存放目录是C:\myprogram\sdk\platforms

      buildToolsVersion "23.0.1" 编译的版本 这个修改后可以直接从网上下载，自动下载的。

     最后，这两个最好一样，是23都是23最好。

##4.对于别人写的不错的布局，看不出来具体的安排，可以使用sdk中带的工具来看一下

    存放的位置是：E:\adt\adt-bundle-windows-x86_64_20140101\adt-bundle-windows-x86_64_20140101\sdk\tools\hierarchy viewer  然后双击打开即可  然后点击 activity 的名字即可

##5.一些记不住的快捷键的使用
  
     ctrl + shift + t 查找一个你输入的名字 看它继承谁，实现哪个接口

     ctrl + alt + / 提示方法的形参 

     alt + shift + f 将局部变量变成全局的

     alt + enter 万能使用

     shift + enter 切换到下一行
 
     ctrl + 箭头 ↓  复制到下一行

     alt + shift + q 抽取方法

     ctrl + e 在布局文件中直接跑到你想跑到的类中

     F4 获取当前接口的实现类

     ctrl + g 看看谁调用了这个方法

     ctrl + alt + c 变成常量
 
##6.Genymotion模拟器的安装
   
    1.首先点击安装程序，把路经选择好之后安装完毕，三个东西，genymotion，genymotionShell，虚拟机都要安装。
    2.点击Genymotion这个图标，进去后点击add，添加要下载的虚拟手机，有账号密码，下载后列表中就会出现你下载的机型
    3.然后打开 oracle vm virtualBox ，点击管理-导入虚拟电脑-点击文件夹，导入你下载的机型，打开即可。
    4.再次打开genymotion，就会出现你刚刚导入的机型，然后打开AS，点击运行后，然后genymotion那个虚拟机就会出来了，此时一定那个genymotion那个图标也要点击，运行中。想跟AS关联，就点击进入setting的界面,有个plugins,进入后可以搜索genymotion下载,也可以直接关联你下载的,以后就可以在as中打开使用了.
    5.genymotion的sd卡的目录查找：android device monitor里面的file explorer ，mnt/sdcard 最右边又有一个指向路径，后面的才是真实的sd卡路径

##1.5版本的androidStudio的bug

    当module建的多了，就会出现错误，解决方法是build中的Rebuild一下就好了。

##7.快捷键，模板的使用忘了时，
    setting 中 搜索Live Templates，第一个android里面就有快捷模板的设置
    搜索Keymap就会有 快捷键的设置

##8.什么时候继承view和viewgroup的区别

    如果组件固定的位置不变，则继承view
    如果组件的位置变化，例如侧滑，则继承viewgroup,是控件如何放

##9.getX，getRawX的区别。

    getX是自身布局的左上角为原点，相当于距离原点的宽度
    getRawX是屏幕的左上角为原点，相当于距离原点的高度

##10.scollX和scollY的意思，scollTo，scollBy的意思

    每次获得的scollX是相对于本身布局最开始的位置（结果是位移，左正右负），中间不管你移动多少次都是跟第一次的位置比较，而不是跟前一次比较。
    scollY也是一样的，只不过是垂直方向。
    scollTo是回到一个你括号中填写的坐标
    scollBy是移动了多少距离

##11.自定义viewGroup时，重写onTouchEvent方法时，把从父类继承的方法删掉，不然会报错。（也或者补上return true才会消费）

    在自定义LayOut类中，有个listView的宽度显示的不满意（和你设置的不匹配），因为此时你继承了BaseAdapter，它是自适应的，所以你应在你写的布局文件中，加上一个minHeight的属性，添上你需要的值


##12.想要平滑的移动，需要重写computeScroll方法，

       @Override
    public void computeScroll() {
        if (scroller.computeScrollOffset()) {
            scrollTo(scroller.getCurrX(), scroller.getCurrY());
            invalidate();//这个方法会使computeScroll不断的自己调用自己
        }
    }

##13.getWidth和getMeasuredWidth的区别

    getMeasuredWidth:在自定义view重写onLayout时、在我们用layoutinflater动态加载view后想获得view的原始宽度时。

    getWidth:一般在view已经布局后呈现出来了，想获取宽度时

##14.canvas 画布不是以屏幕的左顶点为基准，而是以白色背景的左顶点为基准。

##15.Android Studio 错误: 非法字符: '\ufeff' 解决方案|错误: 需要class, interface或enum

      如果遇到此种问题可以手动将UTF-8+BOM编码的文件转为普通的UTF-8文件。

     使用EdItPlus来转换，用EdItPlus打开.java文件依次：文档 → 文本编辑 → 转换文本编码 → 选择UTF-8编码即可如图：

#16.屏幕适配

以宽为例：

1.比如分辨率为320 × 480，则长宽比为1:1.5

2.比如屏幕尺寸为3.6英寸，则根据勾股定理得出，

宽 = (12.96/3.25)1/2 = 1.9969英寸

3.宽为320px，分布在1.9969英寸上，因此密度为320/ 1.9969 = 160.2467

4.因此此密度约为mdpi的密度 

屏幕密度从ldpi到xhdpi分别对应为120dpi、160dpi、240dpi、320dpi

设备优先匹配与它相近的尺寸的文件夹中的图片，通常来说，图片放在drawable-hdpi的文件夹中

安卓屏幕百分比适配：http://blog.csdn.net/lmj623565791/article/details/46767825. 

17.android studio在XML预览中出现Rendering Problems问题 

   解决方法：1.在styles.xml里的<style name="AppTheme" parent="Base.Theme.AppCompat.Light.DarkActionBar">
   原来是没有Base的，加上那个问题就没了。但是我不知道真正的原因。

   2.布局文件预览那里的API调到21以下，就没有了
   

18.dp与px的转换 
   分辨率540 x 960，屏幕尺寸4.5英寸的DPI分别是：540平方+960的平方开根号，除以4.5，等于244，dpi就约等于240.
   px=dp * (dpi/160) 
