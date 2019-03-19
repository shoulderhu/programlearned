## webView

#### webView連接外部連結
- 範例為按下按鈕連結至webView
- 範例程式:

```java
yourButton.setOnClickListener(new Button.OnClickListener() {
    @Override
    public void onClick(View v) {
        setContentView(yourWebViewLayout);
        
        //為了避免input被軟鍵盤遮蔽,重新調整版面
        getWindow().setSoftInputMode(WindowManager.LayoutParams.SOFT_INPUT_ADJUST_RESIZE);
        //得到webView物件
        yourWebView = (WebView) findViewById(R.id.yourWebView);
        //得到裡面設定
        WebSettings webSettings = yourWebView.getSettings();
        //設置支援Js
        webSettings.setJavaScriptEnabled(true);
        //處理Js中的Alert對話方塊
        yourWebView.setWebChromeClient(new WebChromeClient() {
            @Override
            public boolean onJsAlert(WebView view, String url, String message, final JsResult result) {
                AlertDialog dialog = new AlertDialog.Builder(view.getContext()).
                        setTitle("提示").
                        setMessage(message).
                        setPositiveButton("OK", new DialogInterface.OnClickListener() {
                            @Override
                            public void onClick(DialogInterface dialog, int which) {
                                //do nothing
                            }
                        }).create();
                dialog.show();
                result.confirm();
                return true;
            }
        });

        //當連接裡面url時不讓webView消失
        yourWebView.setWebViewClient(new WebViewClient());
        //連接網址
        yourWebView.loadUrl("http://"+yourUrl);
        //設定按下返回鍵效果
        yourWebViewBackBtn.setOnClickListener(new Button.OnClickListener() {
            @Override
            public void onClick(View v) {
                Intent intent = new Intent();
                //這邊activity傳交給自己(因需重返到未按下按鈕畫面)
                intent.setClass(yourActivity.this,yourActivity.class);
                startActivity(intent);
                yourActivity.this.finish();
            }
        });
    }
});
```

#### webView顯示靜態html
-  將網址改成連接至app內部asset文件夾內:

```java 
yourWebView.loadUrl("file:///android_asset/Html/yourHtml.html");
```
- Html範例檔(因在同一文件夾內可直接連接內部asset的html檔):

```html
<head>
<title>標題</title>
<link rel="stylesheet" type="text/css">
</head>

<html>
<body>
    <nav class="wrapper">
        <p><a class="button1" href="help1.html">
        <img src="images/help1button.png" width="280" height="45" /></a>
        <br>
        </p>

        <p><a class="button2" href="help2.html">
        <img src="images/help2button.png" width="280" height="45" /></a>
        <br>
        </p>
        
        <p><a class="button3" href="help3.html">
        <img src="images/help3button.png" width="280" height="45" /></a>
        <br>
        </p>
        
        <p><a class="button4" href="help4.html">
        <img src="images/help4button.png" width="280" height="45" /></a>
        <br>
        </p>
        
        <p><a class="button5" href="help5.html">
        <img src="images/help5button.png" width="280" height="45" /></a>
        </p> 
	</nav>
	<div class="main"><img src="images/main.png" width="100%" height="100%" style="min-height:470px;"></div>
</body>
</html>
```

