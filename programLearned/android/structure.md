## 文件架構

#### 主要架構
- 在project選項選擇 Android 會發現主要資料夾
    - manifests(表現名單)資料夾:用於存放AndroidManifest.xml
    - java資料夾:主要程式存放區
    - assets(可能須手動增加):靜態檔案存放區
    - jniLibs(可能須手動增加):用來與ndk交互存放的資料夾
        - armabi 是针对旧的或者普通的ARM v5 CPU
        - armabi-v7a 是针对ARM v7 CPU
    - res:用來存放樣式

#### 資料夾解析
- jniLibs
    - jni:Java Native Interface(Java本地接口):跟本地其他类型语言（如C、C++）交互
    - 詳細:<a href="https://blog.csdn.net/carson_ho/article/details/73250163">JNI 與 NDK</a>
- res
    - drawable:用來存放圖片
    - layout:用來存放布局xml資料
    - mipmap:用來放入各尺寸app點選圖
    - values:存放各種字串顏色樣式