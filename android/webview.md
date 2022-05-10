webview 

### android 파일 선택창 커스터마이즈
https://www.blueswt.com/118

### error - Mixed Content The page at was loaded over HTTPS
webView.getSettings().setMixedContentMode(WebSettings.MIXED_CONTENT_ALWAYS_ALLOW);

### WebView 에서 window.open 기능과 a태그의 target='_blank' 새창 기능 구현하기
https://wonpaper.tistory.com/437

### WebView 체크하기
```java
      mWebView = (WebView) findViewById(R.id.webView);
      mWebView.getSettings().setJavaScriptEnabled(true);
    	String userAgent = mWebView.getSettings().getUserAgentString();
    	mWebView.getSettings().setUserAgentString(userAgent+" APP_WISHRROM_Android");
```
