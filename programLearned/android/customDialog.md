## 客製化彈出視窗

- 假設情況為 Edittext用 dialog 來選擇輸入
- 製作 dialog 介面(dialog.xml)
- 撰寫 dialog 頁面控制(CustomDialog.java)
- 於 Activity 呼叫:

```java
//Activity 主頁面使用:
editText.setClickable(true);//需先設置:android:focusableInTouchMode="false"
editText.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                new CustomDialog(BloodTransfusionCheckActivity.this,choice,editText).show();
            }
        });
```

```xml
<!-- dialog.xml -->
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:gravity="center">

    <TextView
        android:id = "@+id/txtTitle"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:gravity="top"
        android:textSize="16sp"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:textColor="@color/black" />

    <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
        android:orientation="horizontal"
        android:layout_width="match_parent"
        android:layout_height="wrap_content">

        <EditText
            android:id = "@+id/txtKeyBoard"
            android:layout_width = "wrap_content"
            android:layout_height = "wrap_content"
            android:layout_weight="10"
            android:background="@drawable/edit_style"
            android:gravity="center"
            android:textColor = "@color/black"
            android:textSize="16sp"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:singleLine = "true"
            android:inputType="numberDecimal"/>

        <Button
            android:id="@+id/btn_determine"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:minHeight="0dp"
            android:minWidth="0dp"
            android:layout_weight="1"
            android:textSize="14sp"
            android:text="@string/determine"
            android:textAppearance="?android:attr/textAppearanceSmall"/>
        <Button
            android:id="@+id/btn_giveUp"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:minHeight="0dp"
            android:minWidth="0dp"
            android:layout_weight="1"
            android:textSize="14sp"
            android:text="@string/giveUpInput"
            android:textAppearance="?android:attr/textAppearanceSmall"/>

    </LinearLayout>

    <TableLayout xmlns:android="http://schemas.android.com/apk/res/android"
        android:id="@+id/chooseTable"
        android:stretchColumns="0,1,2,3,4,5,6,7,8,9,10"
        android:layout_width="match_parent"
        android:layout_height="wrap_content">
    </TableLayout>
</LinearLayout>
```

```java
//CustomDialog.java
package cathay.hospital.blood;

import android.app.Activity;
import android.app.Dialog;
import android.content.res.Resources;
import android.graphics.Color;
import android.graphics.Paint;
import android.graphics.drawable.ShapeDrawable;
import android.graphics.drawable.shapes.RectShape;
import android.os.Bundle;
import android.os.Handler;
import android.text.InputType;
import android.view.Gravity;
import android.view.View;
import android.view.Window;
import android.view.WindowManager;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TableLayout;
import android.widget.TableRow;
import android.widget.TextView;

public class CustomDialog extends Dialog implements android.view.View.OnClickListener{
    public Activity activity;
    public int choice;
    private TextView txtTitle;
    private EditText inputText,txtKeyBoard;
    private Button btn_determine,btn_giveUp;
    private TableLayout chooseTable;

    public CustomDialog(Activity activity, int choice, EditText inputText){
        super(activity);
        this.activity = activity;//設定要顯示dialog的畫面
        this.choice = choice;//設定顯示第幾個選擇表
        this.inputText = inputText;//設定要輸入的輸入框
    }

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        requestWindowFeature(Window.FEATURE_NO_TITLE);
        setContentView(R.layout.dialog);

        init();//初始化
        setCancelable(true);//可透過返回鍵將dialog關閉
        setCanceledOnTouchOutside(true);//可透過點擊dialog以外區域來關閉
        displayTable();//顯示表單
    }

    public void init(){
        txtTitle = findViewById(R.id.txtTitle);
        txtKeyBoard = findViewById(R.id.txtKeyBoard);
        btn_determine = findViewById(R.id.btn_determine);
        btn_giveUp = findViewById(R.id.btn_giveUp);
        chooseTable = findViewById(R.id.chooseTable);

        btn_determine.setOnClickListener(this);
        btn_giveUp.setOnClickListener(this);

        //因應不同的選擇表給予不同的高度
        WindowManager.LayoutParams lp = getWindow().getAttributes();
        lp.width = Resources.getSystem().getDisplayMetrics().widthPixels;
        switch(choice){
            case 1:
                txtTitle.setText("標題1");
                lp.height = Resources.getSystem().getDisplayMetrics().heightPixels/2;
                break;
            case 2:
                txtTitle.setText("標題2");
                txtKeyBoard.setInputType(InputType.TYPE_CLASS_NUMBER);
                lp.height = Resources.getSystem().getDisplayMetrics().heightPixels;
                break;
            case 3:
                txtTitle.setText("標題3");
                txtKeyBoard.setInputType(InputType.TYPE_CLASS_NUMBER);
                lp.height = Resources.getSystem().getDisplayMetrics().heightPixels/2;
                break;
            case 4:
                txtTitle.setText("標題4");
                txtKeyBoard.setInputType(InputType.TYPE_CLASS_NUMBER);
                lp.height = Resources.getSystem().getDisplayMetrics().heightPixels;
                break;
        }
        getWindow().setAttributes(lp);
    }

    /**
     * 設定表格資料
     */
    public void displayTable(){
        String[] tdText = {"","0","1","2","3","4","5","6","7","8","9"};
        switch(choice){
            case 1:
                for(int i = 0;i <= 10;i++){
                    tdText[0] = Integer.toString(i);
                    addRow(getTr(tdText));
                }
                break;
            case 2:
                for(int i = 0;i <= 10;i++){
                    tdText[0] = Integer.toString(i);
                    addRow(getTr(tdText));
                }
                ;break;
            case 3:
                for(int i = 0;i <= 10;i++){
                    tdText[0] = Integer.toString(i);
                    addRow(getTr(tdText));
                }
                break;
            case 4:
                for(int i = 0;i <= 10;i++){
                    tdText[0] = Integer.toString(i);
                    addRow(getTr(tdText));
                }
                break;
        }
    }

    /**
     * 新增一列資料
     */
    public void addRow(TableRow tr){
        chooseTable.addView(tr, new TableLayout.LayoutParams(
                TableLayout.LayoutParams.MATCH_PARENT,
                TableLayout.LayoutParams.WRAP_CONTENT));
    }

    /**
     * 製作一列資料
     */
    public TableRow getTr(String[] tdText){
        int textSize = 18;
        TableRow tr = new TableRow(getContext());
        tr.setLayoutParams(new TableRow.LayoutParams(
                TableRow.LayoutParams.MATCH_PARENT,
                TableRow.LayoutParams.WRAP_CONTENT));

        //設定文字顏色
        for(int i = 0;i < tdText.length;i++){
            if(i == 0){
                //第一行無點擊則無輸出
                tr.addView(getTd(tdText[i],textSize,Color.BLUE,tdText[0],"",true));
            }else{
                tr.addView(getTd(tdText[i],textSize,Color.BLACK,tdText[0],tdText[i],false));
            }
        }
        return tr;
    }

    /**
     * 製作欄位資料
     */
    public TextView getTd(String text, int textSize, int textColor, final String headValue, final String chooseValue, boolean isHead){
        TextView td = new TextView(getContext());

        //格內型式
        td.setWidth(Resources.getSystem().getDisplayMetrics().widthPixels/12);
        td.setText(text); // set the text for the header
        td.setTextSize(textSize);
        td.setTextColor(textColor); // set the color
        td.setGravity(Gravity.CENTER);
        if(isHead){
            //設定背景與框線
            td.setBackgroundResource(R.drawable.td_head_textview);
        }else{
            td.setBackgroundResource(R.drawable.td_textview);

            if(choice == 1){
                td.setOnClickListener(new View.OnClickListener() {
                    String result = headValue+"."+chooseValue;
                    public void onClick(View view) {
                        //點擊之後textView換背景顏色
                        view.setBackgroundResource(R.drawable.td_clicked_textview);
                        inputText.setText(result);
                        sleep(200);
                    }
                });
            }else{
                td.setOnClickListener(new View.OnClickListener() {
                    String result = Integer.toString((Integer.parseInt(headValue)+Integer.parseInt(chooseValue)));
                    public void onClick(View view) {
                        view.setBackgroundResource(R.drawable.td_clicked_textview);
                        inputText.setText(result);
                        sleep(200);
                    }
                });
            }
        }

        return td;
    }


    @Override
    public void onClick(View v) {
        switch (v.getId()) {
            case R.id.btn_determine:
                inputText.setText(txtKeyBoard.getText());
                break;
            case R.id.btn_giveUp:
                break;
        }

        //關閉 dialog
        dismiss();
    }

    public void sleep(int millis){
        //設計使用者點選回饋(點選textView背景變色)
        Handler handler = new Handler();
        handler.postDelayed(new Runnable(){
                @Override
                public void run() {
                    dismiss();
                }
            }, millis
        );

    }
}

```


```xml
<!-- td_head_textview.xml -->
<?xml version="1.0" encoding="UTF-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android">
    <solid android:color="#40FF00"/>
    <stroke android:width="1dp" android:color="#ff000000" />
</shape>
```

```xml
<!-- td_textview.xml -->
<?xml version="1.0" encoding="UTF-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android">
    <!--背景顏色-->
    <solid android:color="#ffffff"/>
    <!--框線顏色-->
    <stroke android:width="1dp" android:color="#ff000000" />
</shape>
```

```xml
<!-- td_clicked_textview.xml -->
<?xml version="1.0" encoding="UTF-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android">
    <!--背景顏色-->
    <solid android:color="#FFFF00"/>
    <!--框線顏色-->
    <stroke android:width="1dp" android:color="#ff000000" />
</shape>
```