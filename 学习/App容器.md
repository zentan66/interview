## App容器



### 桥通道

#### Android

1. 定义与WebView JS上下文建立映射关系的Android JavaScriptInterface实现类以及call方法

```java
// package
import android.webkit.JavascriptInterface
public class JSBridgeChannel {
  @JavascriptInterface
  public void call(String api, String options) {
    //
  }
}
```

2. 在WebView的loadUrl时机，通过WebView的addJavascriptInterface方法建立Android类实例对象与JS对象的映射关系

```java
@Override
public void loadUrl(String url) {
  mWebView.addJavascriptInterface(new JSBridgeChannel(), 'JSBridge')
}
```

3. WebView里JS即可同步调用

```javascript
window.JSBridge.call("api", JSON.stringify(options));
```

