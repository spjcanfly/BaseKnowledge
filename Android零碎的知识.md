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

    // 第一种解析，使用Gson解析商城热卖的json数据
    private SmartServicePagerBean parsedJson(String json) {

        return new Gson().fromJson(json,SmartServicePagerBean.class);

    }

     SmartServicePagerBean bean = parsedJson(json);
     datas = bean.getList();

     这个SmartServicePagerBean类中，有一个属性是List<SmartServicePagerBean.Wares> datas，所以解析完以后直接就是一个集合。里面有好多java对象，可以获得各个对象的属性。
     
      第二种解析，也可以这样解析：
     
       JSONObject jsonObject = new JSONObject(json);
            JSONArray trailers = jsonObject.optJSONArray("trailers");
            for (int i = 0; i < trailers.length(); i++) {
                JSONObject item = (JSONObject) trailers.get(i);
                if (item != null) {
                    MediaItem mediaitem = new MediaItem();

                    String name = item.optString("movieName");
                    mediaitem.setName(name);

                    String desc = item.optString("videoTitle");
                    mediaitem.setDesc(desc);

                    String imageUrl = item.optString("coverImg");
                    mediaitem.setImageUrl(imageUrl);

                    String data = item.optString("url");
                    mediaitem.setData(data);

                    mediaItems.add(mediaitem);
                    }
                
##8.关于drawable，drawable-hdpi和drawable-xhdpi的使用

    drawable 里面放置的是选择器，还有一些.9图片（边缘看起来不会模糊）

    drawable-hdpi 通常放置的是控件之类的图片

    drawable-xhdpi 通常放置的是进去后首个页面的图标，比如四个Fragment切换时候的图标，因为这样可以看起来图标比较小，更好看些。

##9.  如果导入别人的包会有错误，看看setting.gradle中是否缺少某些项目的名字，然后照原有的格式添加进去

##10.反编译一个apk，得到里面的资源文件

      app\build\outputs\apk，的.apk，后缀名改为.zip，然后打开即可
      
##11.科大讯飞，语音识别，人脸识别
