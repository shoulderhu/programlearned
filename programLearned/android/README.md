## Android 筆記
- 用來記錄學習 Android 的重點
- 並可方便觀看查閱

---
## 以下是環境的問題處理方式

### 修改 gradle緩存資料夾位置
- 使用環境變量
  - 在環境變量中加上GRADLE_USER_HOME並指向你的新地址就OK
  - 再將原本的.gradle資料夾移過去即可
  
### Cannot resolve FragmentActivity, FragmentTransaction, and more in Android Studio
- try deleting "/.idea/libraries" from main folder. then sync project again.

### 不同電腦通用 debug apk方式(解決 :未安裝應用程式問題)
- 得到該電腦的 debug.keystore
- 透過另一台電腦的 Generate signed key 重新編譯 apk 即可解決
- debug.keystore alias & password

```
Keystore name: "debug.keystore"
Keystore password: "android"
Key alias: "androiddebugkey"
Key password: "android"
CN: "CN=Android Debug,O=Android,C=US"
```
- 相關連結 : <a href="https://stackoverflow.com/a/18590149/9151543">debug.keystore keyContent</a>
---
## 以下為可能常用之重要的解答

### Android: how to wait AsyncTask to finish in MainThread?
solution:https://stackoverflow.com/a/13079926/9151543

```java
class OpenWorkTask extends AsyncTask {

    @Override
    protected Boolean doInBackground(String... params) {
        // do something
        return true;
    }

    @Override
    protected void onPostExecute(Boolean result) {
        // The results of the above method
        // Processing the results here
        myHandler.sendEmptyMessage(0);
    }

}

Handler myHandler = new Handler() {

    @Override
    public void handleMessage(Message msg) {
        switch (msg.what) {
        case 0:
            // calling to this function from other pleaces
            // The notice call method of doing things
            break;
        default:
            break;
        }
    }
};
```



