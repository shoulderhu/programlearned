## android 添家依賴的三種方式

### 1.拷貝到libs目錄
- 選擇project文件架構
- 至app底下的libs增加
- 打開Module下的build.gradle文件，可以看到，新增了添加的庫

### 2.Project Structure（File->Project Structure)
- 選擇app -> 選擇Dependencies
- 點選 + 號 
- 選擇 dependency：
    - 選擇Module dependency, 可以選擇Project下的依賴Module
    - 選擇File dependency, 可以選擇添加該Project下面的庫。
- 打開Module下的build.gradle文件，可以看到，新增了添加的庫

### 3.使用”Library dependency“方式添加
- “Library dependency”這個選擇規入了第三種添加方式。
    - 原因是這裡我們並不會直接去操作jar包，而是把它交給了Gradle去管理。
- 打開 Project Structure->Modules 的 app->Dependencies->”+”->Library dependency。輸入你要添加的jar包名字。
- 打開Module下的build.gradle文件，可以看到，新增了添加的庫
- 那麼下載jar包在哪裡?(若第三方庫有更新的版本，可方便替換)
    - 於project 的 External Libraries 選種添加的庫點右鍵 -> Library Properties...可看到下載位址
- 依賴庫的添加網站方式介紹：
    - Android Studio是從build.gradle裡面定義的Maven倉庫服務器上下載library
    - jcenter就是一個標準的Android library文件服務器，通過gradle導入的jar包皆從http://bintray.com/bintray/jcenter 這個倉庫上抓下來的。
    - 若網站上沒有，則無法通過gradle方式來導入。

### 依賴範圍(Project Structure->Dependencies中的Scrope)
- Dependency scope是用來限制Dependency的作用範圍的,影響項目在各個生命週期時導入的庫的狀態。
    - compile：默認選項，是對所有的build type以及favlors都會參與編譯並且打包到最終的apk文件中。
    - provided：是對所有的build type以及favlors只在編譯時使用，類似eclipse中的external-libs,只參與編譯，不打包到最終apk。 
    - APK：只會打包到apk文件中，而不參與編譯，所以不能再代碼中直接調用jar中的類或方法，否則在編譯時會報錯。 
    - Test compile：針對單元測試代碼的編譯編譯以及最終打包測試apk時有效，而對正常的debug或者release apk包不起作用。
    - Debug compile：針對debug模式的編譯和最終的debug apk打包
    - Release compile：針對Release模式的編譯和最終的Release apk打包。
    
### gradle 引入包的幾種方式:
- 1.引入一個jar包：

```
dependencies {
    compile files('libs/domoarigato.jar')
}
```

- 2.引入libs里全部的jar包：

```
dependencies {
       compile fileTree('libs')
       //默認情況下
       compile fileTree(dir: 'libs', include: ['*.jar'])
}
```


