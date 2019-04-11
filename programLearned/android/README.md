## Android 筆記
- 用來記錄學習 Android 的重點
- 並可方便觀看查閱

---
## 以下是環境發生的小問題處理方式

### 修改 gradle緩存資料夾位置
- 使用環境變量
  - 在環境變量中加上GRADLE_USER_HOME並指向你的新地址就OK
  - 再將原本的.gradle資料夾移過去即可
  
### Cannot resolve FragmentActivity, FragmentTransaction, and more in Android Studio
- try deleting "/.idea/libraries" from main folder. then sync project again.

