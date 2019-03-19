## 內網自動更新 android 實現步驟

- 流程:
- 1 至網路位置比對版本號
    - 原因:
    - 避免套件之後無法存取
    - 避免增加apk的檔案變大
    - 減少解析apk時間與增加UX
- 2 跳出alertDialog詢問使用者是否安裝新版本
    - 確認使用者有業務需求需要更新
- 3 若有相同apk檔案則刪除
    - 避免內存過多無法存取新APK
- 4 進行下載(開啟進度條視窗)
    - 讓使用者看到進度避免更新失敗
- 5 自動開啟
    - 讓使用者無需再去尋找新檔案安裝更新

#### 實現:
- 1.在網路資料夾創建version.xml
```xml
<version>
    <versionCode>20181009</versionCode>
</version>
```

- 2.新增各項變數與設定androidManifest.xml:
    - versionName(以版本為主):
```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.mio.chemotherapy"
    android:versionCode="1"
    android:versionName="1.3.5.6" >
</manifest>
```

- 新增權限androidManifest.xml:

```xml
<uses-permission android:name="android.permission.INTERNET"/>
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />

<!--須包在application裡面,針對7.0以上版本的手機，在取得APK檔的Uri時，需要透FileProvider，才可正常運作-->
<provider
    android:name="android.support.v4.content.FileProvider"
    android:authorities="com.example.solinari.automaticallyopenapk.fileProvider"
    android:exported="false"
    android:grantUriPermissions="true" >
    <meta-data
        android:name="android.support.FILE_PROVIDER_PATHS"
        android:resource="@xml/file_paths" />
</provider>
```

- 新增參數檔:file_paths.xml:

```xml
<?xml version="1.0" encoding="utf-8"?>
<paths>
    <external-path path="." name="external_storage" />
</paths>
```

- 新增進度條視窗download_apk_dialog.xml:
    - 修改進度條樣式參考網址:https://stackoverflow.com/questions/18800290/how-to-change-progressbar-color

```xml
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:background="#ffffffff">

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/update"
        android:textColor="@color/black"
        android:textStyle="normal|bold"
        android:layout_marginTop="15dp"
        android:layout_marginLeft="15dp"/>
    <TextView
        android:id="@+id/textView2"
        android:layout_below="@id/textView"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="15dp"
        android:layout_marginLeft="15dp"
        android:text="@string/wait" />
    <ProgressBar
        android:id="@+id/download_progressBar"
        android:layout_below="@id/textView2"
        style="?android:attr/progressBarStyleHorizontal"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:indeterminate="false"
        android:layout_marginTop="15dp"
        android:layout_marginLeft="15dp"
        android:layout_marginRight="15dp"
        android:max="100" />
    <TextView
        android:id="@+id/txtProgress"
        android:layout_below="@id/download_progressBar"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginLeft="15dp"
        android:layout_marginBottom="15dp"
        android:textStyle="normal|bold"/>
</RelativeLayout>
```

- 新增字串參數:res > values > strings.xml

```xml
<string name="update">下载更新</string>
<string name="wait">下載中，請稍後...</string>
```

- 主程式:

```java
DownloadManager DM ;
DownloadManager.Request request;
private DownloadObserver downloadObserver;
private long LatestDownloadID;
String URL;
DialogFragmentHelper newFragment;
//預設版本號
String versionCode="0.0.0.0";
//目前版本號
String nowVersionCode;
//檔案儲存位置
static final Uri CONTENT_URI = Uri.parse("content://downloads/my_downloads");

@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);

    //版本比對與安裝新版本
    checkNewVersion();
}
```

- 3.設置判斷安裝新版本checkNewVersion方法:

```java
private void checkNewVersion(){
    Boolean haveNewVersion;
    //得到新版本號
    Thread thread = new Thread(new Runnable() {
        @Override
        public void run() {
            try  {
                String url = "http://???/version.xml";
                Boolean connectOK = false;
                URL obj = new URL(url);
                HttpURLConnection con = (HttpURLConnection) obj.openConnection();
                con.setConnectTimeout(2000);
                connectOK =  con.getResponseCode() == HttpURLConnection.HTTP_OK;
                if(connectOK){
                    BufferedReader in = new BufferedReader(new InputStreamReader(con.getInputStream()));
                    String inputLine;
                    StringBuffer response = new StringBuffer();
                    while ((inputLine = in.readLine()) != null) {
                        response.append(inputLine);
                    }
                    in.close();
                    Document doc = DocumentBuilderFactory.newInstance().newDocumentBuilder()
                            .parse(new InputSource(new StringReader(response.toString())));
                    NodeList versionCodeTag = doc.getElementsByTagName("version");
                    if (versionCodeTag.getLength() > 0) {
                        Element qrcodeTag = (Element)versionCodeTag.item(0);
                        versionCode = qrcodeTag.getElementsByTagName("versionCode").item(0).getTextContent();
                    }
                }
            } catch (Exception e) {
                e.printStackTrace();
            }
        }
    });

   //必須等待連線完成得到新版本號進行比對
    try{
        thread.start();
        thread.join();
        //取得versionName
        nowVersionCode = getPackageManager().getPackageInfo(getPackageName(), 0).versionName;
    }catch(Exception e){
        Log.i("xxx","斷線");
    }

    //判斷是否有新版本
    haveNewVersion = compare(versionCode,nowVersionCode);

    //確認使用者是否要安裝新版本與有新的版本
    if(haveNewVersion){
        new AlertDialog.Builder(MainActivity.this)
                .setCancelable(false)//禁用返回鍵
                .setTitle("安裝新版本")
                .setMessage("是否安裝最新版本app")
                .setPositiveButton("是", new DialogInterface.OnClickListener() {
                    @Override
                    public void onClick(DialogInterface dialog, int which) {
                        //開始安裝新版本
                        DownloadNewVersion();
                    }
                }).show();
    }
}

private static boolean compare(String newVersionCode,String oldVersionCode) {
    if (newVersionCode == null) {
        return false;
    }
    newVersionCode = newVersionCode.replaceAll("[.]","");
    oldVersionCode = oldVersionCode.replaceAll("[.]","");
    if (Integer.parseInt(newVersionCode) > Integer.parseInt(oldVersionCode)) {
        return true;
    }
    return false;
}
```

- 4.設置安裝新版本DownloadNewVersion方法與DialogFragmentHelper.java:
- DownloadNewVersion:

```java
private void DownloadNewVersion(){
    //判斷檔案是否已存在,若存在需先刪除,避免內存塞滿
    File file = Environment.getExternalStoragePublicDirectory(Environment.DIRECTORY_DOWNLOADS);
    Uri apkPath = Uri.withAppendedPath(Uri.fromFile(file),"設置更新的apk名稱.apk");
    File fdelete = new File(apkPath.getPath());
    if (fdelete.exists()) {
        if (fdelete.delete()) {
            Log.i("apk","file Deleted :" + apkPath.getPath());
        }
    }

    //顯示進度條(DialogFragmentHelper)
    newFragment = new DialogFragmentHelper();
    newFragment.show(getSupportFragmentManager(),"download apk");
    DM = (DownloadManager) getSystemService(DOWNLOAD_SERVICE);
    URL = "http://???/設置下載的apk.apk";
    Uri uri = Uri.parse(URL);
    request = new DownloadManager.Request(uri);

    //設置標題與描述
    request.setTitle("安裝新版本");
    request.setDescription("已有新版本，是否允許安裝新版本");
    request.setVisibleInDownloadsUi(true);

    //設置可使網路類型
    request.setAllowedNetworkTypes(DownloadManager.Request.NETWORK_MOBILE
            | DownloadManager.Request.NETWORK_WIFI);
    request.setMimeType("application/vnd.android.package-archive");//設置MIME為Android APK檔

    //Android 6.0以上需要判斷使用者是否願意開啟儲存(WRITE_EXTERNAL_STORAGE)的權限
    if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.M) {
        CheckStoragePermission();
    }
    else{
        DownloadManagerEnqueue();
    }
}
```

- DialogFragmentHelper.java:

```java
import android.os.Bundle;
import android.support.annotation.Nullable;
import android.support.v4.app.DialogFragment;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.view.Window;
import android.widget.Button;
import android.widget.ProgressBar;
import android.widget.TextView;

public class DialogFragmentHelper extends DialogFragment{
    private ProgressBar progressBar;//下載新版APP時ProgressBar
    private TextView txtProgress;//下載新版APP時顯示文字百分比
    @Nullable
    @Override
    public View onCreateView(LayoutInflater inflater, @Nullable ViewGroup container, @Nullable Bundle savedInstanceState) {
        getDialog().requestWindowFeature(Window.FEATURE_NO_TITLE);//取消Dialog title列
        getDialog().setCanceledOnTouchOutside(false);//不能點擊Dialog以外區域
        //禁用返回鍵
        getDialog().setOnKeyListener(new DialogInterface.OnKeyListener() {
            @Override
            public boolean onKey(DialogInterface dialog, int keyCode, KeyEvent event) {
                if (keyCode == KeyEvent.KEYCODE_BACK) {
                    return true;
                }
                return false;
            }
        });
        View v = inflater.inflate(R.layout.download_apk_dialog, container, false);//進度條畫面
        progressBar = (ProgressBar) v.findViewById(R.id.download_progressBar);
        txtProgress = (TextView) v.findViewById(R.id.txtProgress);
        txtProgress.setText("0%");
        return v;
    }
    protected void setProgress(int progress){//更新進度條
        progressBar.setProgress(progress);
        txtProgress.setText(Integer.toString(progress) + "%");
    }
}

```

- 5.檢視手機android版本問題:

```java
//Android 6.0檢查是否開啟儲存(WRITE_EXTERNAL_STORAGE)的權限，若否，出現詢問視窗
private void CheckStoragePermission() {
    if (ContextCompat.checkSelfPermission(this,
            Manifest.permission.WRITE_EXTERNAL_STORAGE)
            != PackageManager.PERMISSION_GRANTED && ContextCompat.checkSelfPermission(this,
            Manifest.permission.READ_EXTERNAL_STORAGE)
            != PackageManager.PERMISSION_GRANTED)
    {//Can add more as per requirement
        ActivityCompat.requestPermissions(this,
                new String[]{Manifest.permission.WRITE_EXTERNAL_STORAGE,Manifest.permission.READ_EXTERNAL_STORAGE},
                20);
    } else {
        DownloadManagerEnqueue();
    }
}

 @Override//Android 6.0以上 接收使用者是否允許使用儲存權限
public void onRequestPermissionsResult(int requestCode, @NonNull String[] permissions, @NonNull int[] grantResults) {
    super.onRequestPermissionsResult(requestCode, permissions, grantResults);
    PermissionManager.onRequestResult(requestCode, permissions, grantResults);
    switch (requestCode) {
        case 20: {
            if (grantResults.length > 0
                    && grantResults[0] == PackageManager.PERMISSION_GRANTED) {
                DownloadManagerEnqueue();
            } else {
                CheckStoragePermission();
            }
            return;
        }
    }
}
```

- 6.設置下載項目所需設定DownloadManagerEnqueue方法:

```java
private void DownloadManagerEnqueue(){
    //創建目錄
    Environment.getExternalStoragePublicDirectory(Environment.DIRECTORY_DOWNLOADS).mkdir() ;
    //設定APK儲存位置與apk名稱(這裡提醒欲刪除的apk名稱需與儲存apk名稱一樣)
    request.setDestinationInExternalPublicDir(  Environment.DIRECTORY_DOWNLOADS  , "設置下載後apk名稱.apk" ) ;
    //註冊廣播接收器
    DownloadCompleteReceiver receiver = new DownloadCompleteReceiver(getApplicationContext());
    registerReceiver(receiver, new IntentFilter(DownloadManager.ACTION_DOWNLOAD_COMPLETE));//註冊DOWNLOAD_COMPLETE-BroadcastReceiver
    downloadObserver = new DownloadObserver(null);
    getContentResolver().registerContentObserver(CONTENT_URI, true, downloadObserver);//註冊ContentObserver
    LatestDownloadID= DM.enqueue(request);
    //利用SharedPreferencesHelper儲存DownloadID
    SharedPreferencesHelper sp = new SharedPreferencesHelper(getApplicationContext());
    sp.setDownloadID(LatestDownloadID);//儲存DownloadID
}

class DownloadObserver extends ContentObserver{
    public DownloadObserver(Handler handler) {
        super(handler);
    }
    @Override
    public void onChange(boolean selfChange) {
        DownloadManager.Query query = new DownloadManager.Query();
        query.setFilterById(LatestDownloadID);
        DownloadManager dm = (DownloadManager) getSystemService(Context.DOWNLOAD_SERVICE);
        final Cursor cursor = dm.query(query);
        if (cursor != null && cursor.moveToFirst()) {
            final int totalColumn = cursor.getColumnIndex(DownloadManager.COLUMN_TOTAL_SIZE_BYTES);
            final int currentColumn = cursor.getColumnIndex(DownloadManager.COLUMN_BYTES_DOWNLOADED_SO_FAR);
            int totalSize = cursor.getInt(totalColumn);
            int currentSize = cursor.getInt(currentColumn);
            float percent = (float) currentSize / (float) totalSize;
            final int progress = Math.round(percent * 100);
            runOnUiThread(new Runnable() {//確保在UI Thread執行
                @Override
                public void run() {
                    newFragment.setProgress(progress);
                }
            });
        }
    }
}
```

- SharedPreferencesHelper.java:

```java
package com.rayhahah.qrcodedemo;
import android.content.Context;
import android.content.SharedPreferences;

/*
需要暫存DownloadManager下載時所產生的DownloadID，
這個ID可以在Android 6.0以上版本的手機，順利取得APK的Uri，
使用SharedPreferences來儲存這個ID值。
 */
public class SharedPreferencesHelper {
    final String SP_Name = "你的package名稱_SP";
    public final String DownloadID = "LoginID";
    public SharedPreferences settings;
    public SharedPreferences.Editor PE;
    public SharedPreferencesHelper(Context context) {
        settings = context.getSharedPreferences(SP_Name, 0);
        PE = settings.edit();
    }
    public void setDownloadID(long id) {//儲存DownloadID
        PE.putLong(DownloadID,id);
        PE.commit();
    }
    public long getDownloadID() {
        return settings.getLong(DownloadID, -1);
    }//取得DownloadID
}
```
- DownloadCompleteReceiver.java:

```java
package com.rayhahah.qrcodedemo;

import android.annotation.SuppressLint;
import android.app.DownloadManager;
import android.content.BroadcastReceiver;
import android.content.Context;
import android.content.Intent;
import android.database.Cursor;
import android.net.Uri;
import android.os.Build;
import android.support.v4.content.FileProvider;
import android.text.TextUtils;
import java.io.File;

public class DownloadCompleteReceiver extends BroadcastReceiver {
    static SharedPreferencesHelper sp ;
    Context con;
    public DownloadCompleteReceiver(Context context){
        con = context;
        sp = new SharedPreferencesHelper(context);
    }
    @SuppressLint("NewApi")
    public void onReceive(Context context, Intent intent) {
        long downLoadId = intent.getLongExtra(DownloadManager.EXTRA_DOWNLOAD_ID, -1);
        long cacheDownLoadId = sp.getDownloadID();
        if (cacheDownLoadId == downLoadId) {
            Intent install = new Intent(Intent.ACTION_VIEW);
            File apkFile = queryDownloadedApk(context);
            if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.N) {//Android 7.0 需要透過FileProvider來取得APK檔的Uri
                install.setFlags(Intent.FLAG_GRANT_READ_URI_PERMISSION);
                Uri contentUri = FileProvider.getUriForFile(context, BuildConfig.APPLICATION_ID + ".fileProvider", apkFile);
                install.setDataAndType(contentUri, "application/vnd.android.package-archive");
            } else {
                install.setDataAndType(Uri.fromFile(apkFile), "application/vnd.android.package-archive");
                install.setFlags(Intent.FLAG_ACTIVITY_NEW_TASK);
            }
            context.startActivity(install);//開啟安裝畫面
        }
    }

    //透過downLoadId尋找下載的apk檔，解决6.0以上版本安裝問題
    public static File queryDownloadedApk(Context context) {
        File targetApkFile = null;
        DownloadManager downloader = (DownloadManager) context.getSystemService(Context.DOWNLOAD_SERVICE);

        long downloadId =sp.getDownloadID();
        if (downloadId != -1) {
            DownloadManager.Query query = new DownloadManager.Query();
            query.setFilterById(downloadId);
            query.setFilterByStatus(DownloadManager.STATUS_SUCCESSFUL);
            Cursor cur = downloader.query(query);
            if (cur != null) {
                if (cur.moveToFirst()) {
                    String uriString = cur.getString(cur.getColumnIndex(DownloadManager.COLUMN_LOCAL_URI));
                    if (!TextUtils.isEmpty(uriString)) {
                        targetApkFile = new File(Uri.parse(uriString).getPath());
                    }
                }
                cur.close();
            }
        }
        return targetApkFile;
    }
}
```
- 以上完成及實現自動更新
