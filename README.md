# 自备资料

如果侵权，纯属意外。一经告知，立刻删除。

# TVBoxOS

在大神q215613905/TVBoxOS目录的同步下

修改默认配置

一、设置修改

1、默认搜索显示缩略图

2、默认开启硬解

///取消3、默认开启dns

二、图标背景名字内置修改

仅供测试使用

技巧

1、修改软件名称地址

https://github.com/nxjonson/TVBoxOS/blob/main/app/src/main/res/values/strings.xml

https://gitee.com/nxniuniu/TVBoxOS/blob/main/app/src/main/res/values/strings.xml

2、修改版本号

https://github.com/nxjonson/TVBoxOS/blob/main/app/src/main/AndroidManifest.xml

https://gitee.com/nxniuniu/TVBoxOS/blob/main/app/src/main/AndroidManifest.xml

3、修改图标、背景

https://github.com/nxjonson/TVBoxOS/tree/main/app/src/main/res

https://gitee.com/nxniuniu/TVBoxOS/tree/main/app/src/main/res

4、修改内置源

俊老仓库打开下面,第83行

https://github.com/nxjonson/TVBoxOS/blob/main/app/src/main/java/com/github/tvbox/osc/api/ApiConfig.java

takagen99大佬仓库 改这里;app/src/main/res/values-zh/strings.xml

5、修改默认缩略图、硬解、dns

地址：

https://github.com/nxjonson/TVBoxOS/blob/main/app/src/main/java/com/github/tvbox/osc/base/App.java

代码

@@ -53,9 +53,19 @@ private void initParams() {

        if (!Hawk.contains(HawkConfig.PLAY_TYPE)) {

            Hawk.put(HawkConfig.PLAY_TYPE, 1);

        }

        //自定义默认配置-硬解-安全dns-缩略图

        if (!Hawk.contains(HawkConfig.IJK_CODEC)) {

            Hawk.put(HawkConfig.IJK_CODEC, "硬解码");

        }

        if (!Hawk.contains(HawkConfig.DOH_URL)) {

            Hawk.put(HawkConfig.DOH_URL, 2);

        }

        if (!Hawk.contains(HawkConfig.SEARCH_VIEW)) {

            Hawk.put(HawkConfig.SEARCH_VIEW, 2);

        }

    }

    public static App getInstance() {

        return instance;

    }

# 关于打包
https://sspai.com/post/70427
