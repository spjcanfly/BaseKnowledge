##1.spannableStringBuilder 功能：

    //用颜色标记文本

    //用超链接标记文本 

    //用样式标记文本（斜体）

    //获取Drawable资源

    添加图片主要用SpannableString和ImageSpan类：

具体需要的时候到下面地址查看：(http://blog.csdn.net/lovexjyong/article/details/17021235 "spannableString")

##2.百度地图SDK的功能与集成

    定位集成在项目中比较简单，不作赘述

    其他的功能有用的有，打开全景，获取周围的景色和内部的环境

    GPS导航，鹰眼轨迹追踪

##3.抽取成第三方库
    
    新建一个Module 选择Android Library，名字修改后，完成；

    然后，把需要的类，布局，选择器都准备好，这就完成了。

    最后，写一个简单的sample，可以让用这个的库人迅速的熟悉。  
    
##4.如何将屏幕上的Activity的标题去掉
   
    在创建好一个activity后，把extends AppCompatActivity 修改为 extends Activity 完成！
