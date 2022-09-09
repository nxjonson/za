# 1、修改软件名称地址

https://github.com/nxjonson/Box/blob/main/app/src/main/res/values/strings.xml

https://gitee.com/nxniuniu/Box/blob/main/app/src/main/res/values/strings.xml

# 2、修改版本号

https://github.com/nxjonson/Box/blob/main/app/src/main/AndroidManifest.xml

https://gitee.com/nxniuniu/Box/blob/main/app/src/main/AndroidManifest.xml

# 3、修改图标、背景

https://github.com/nxjonson/Box/tree/main/app/src/main/res

https://gitee.com/nxniuniu/Box/tree/main/app/src/main/res

# 4、修改内置源

https://github.com/nxjonson/Box/blob/main/app/src/main/res/values-zh/strings.xml

# 5、修改默认缩略图、硬解、dns

  地址：

  https://github.com/nxjonson/Box/blob/main/app/src/main/java/com/github/tvbox/osc/base/App.java

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

# 6、小窗口默认开启(把show_priew  相关的默认值都改成false 就是关闭了)

## 这里：app/src/main/java/com/github/tvbox/osc/ui/fragment/ModelSettingFragment.java

@@ -81,7 +81,7 @@ protected void init() {
        tvFastSearchText = findViewById(R.id.showFastSearchText);	        tvFastSearchText = findViewById(R.id.showFastSearchText);
        tvFastSearchText.setText(Hawk.get(HawkConfig.FAST_SEARCH_MODE, false) ? "已开启" : "已关闭");	        tvFastSearchText.setText(Hawk.get(HawkConfig.FAST_SEARCH_MODE, false) ? "已开启" : "已关闭");
        tvShowPreviewText = findViewById(R.id.showPreviewText);	        tvShowPreviewText = findViewById(R.id.showPreviewText);
        tvShowPreviewText.setText(Hawk.get(HawkConfig.SHOW_PREVIEW, false) ? "开启" : "关闭");	        tvShowPreviewText.setText(Hawk.get(HawkConfig.SHOW_PREVIEW, true) ? "开启" : "关闭");
        tvDebugOpen = findViewById(R.id.tvDebugOpen);	        tvDebugOpen = findViewById(R.id.tvDebugOpen);
        tvParseWebView = findViewById(R.id.tvParseWebView);	        tvParseWebView = findViewById(R.id.tvParseWebView);
        tvMediaCodec = findViewById(R.id.tvMediaCodec);	        tvMediaCodec = findViewById(R.id.tvMediaCodec);
@@ -513,7 +513,7 @@ public void onChange() {
            @Override	            @Override
            public void onClick(View v) {	            public void onClick(View v) {
                FastClickCheckUtil.check(v);	                FastClickCheckUtil.check(v);
                Hawk.put(HawkConfig.SHOW_PREVIEW, !Hawk.get(HawkConfig.SHOW_PREVIEW, false));	                Hawk.put(HawkConfig.SHOW_PREVIEW, !Hawk.get(HawkConfig.SHOW_PREVIEW, true));
                tvShowPreviewText.setText(Hawk.get(HawkConfig.SHOW_PREVIEW, true) ? "开启" : "关闭");	                tvShowPreviewText.setText(Hawk.get(HawkConfig.SHOW_PREVIEW, true) ? "开启" : "关闭");
            }	            }
        });	        });
 
## 这里：app/src/main/java/com/github/tvbox/osc/ui/activity/DetailActivity.java

@@ -553,7 +553,6 @@ public void onChanged(AbsXml absXml) {
                    llPlayerFragmentContainer.setVisibility(View.GONE);	                    llPlayerFragmentContainer.setVisibility(View.GONE);
                    llPlayerFragmentContainerBlock.setVisibility(View.GONE);	                    llPlayerFragmentContainerBlock.setVisibility(View.GONE);
                }	                }
                if(absXml != null && absXml.msg != null && !absXml.msg.isEmpty())Toast.makeText(DetailActivity.this, absXml.msg, Toast.LENGTH_SHORT).show();	
            }	            }
        });	        });
    }	    }
@@ -805,7 +804,7 @@ public boolean dispatchTouchEvent(MotionEvent ev) {


    // preview	    // preview
    VodInfo previewVodInfo = null;	    VodInfo previewVodInfo = null;
    boolean showPreview = Hawk.get(HawkConfig.SHOW_PREVIEW, false);; // true 开启 false 关闭	    boolean showPreview = Hawk.get(HawkConfig.SHOW_PREVIEW, true);; // true 开启 false 关闭
    boolean fullWindows = false;	    boolean fullWindows = false;
    ViewGroup.LayoutParams windowsPreview = null;	    ViewGroup.LayoutParams windowsPreview = null;
    ViewGroup.LayoutParams windowsFull = null;	    ViewGroup.LayoutParams windowsFull = null;
