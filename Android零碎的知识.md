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
    
##5.如何在横竖屏切换的时候不用再走一次Activity的生命周期

    在清单文件中，该Activity标签里添加：
    android:configChanges="keyboardHidden|orientation|screenSize"

##6.初始化第三方库的地方

    新建一个App名+application，继承Application，清单列表中加上 android:name=".类名"，
    通常这个类的位置是在与其他的文件夹同级。
    
##7.Gson解析数据

    //使用Gson解析商城热卖的json数据
    private SmartServicePagerBean parsedJson(String json) {

        return new Gson().fromJson(json,SmartServicePagerBean.class);

    }

     SmartServicePagerBean bean = parsedJson(json);
     datas = bean.getList();

     这个SmartServicePagerBean类中，有一个属性是List<SmartServicePagerBean.Wares> datas，所以解析完以后直接就是一个集合。里面有好多java对象，可以获得各个对象的属性。
