## SurfaceView 的使用

#### SurfaceView 誕生

```
Android提供了View進行繪圖處理，View可以滿足大部分的繪圖需求，但在某些時候也會心有餘而力不足。
我們知道，View通過刷新來重繪視圖，Android系統通過發出VSYNC信號來進行屏幕的重繪，刷新的時間間隔為16ms。
如果在16ms內View完成了你所需要執行的所有操作，那麼用戶在視覺上就不會產生卡頓的感覺；
而如果執行的操作邏輯太多，特別是需要頻繁刷新的界面上，例如游戲界面，就會不斷阻塞主線程，從而導致畫面卡頓。
很多情況下，在自定義View的log中會看到如下的警告：
“Skipped 47 frames! The application may be doing too much work on its main thread.”
為了避免這一問題的產生，Android系統提供了SurfaceView組件。
```

#### View 和 SurfaceView 的區別
- View 主要適用於主動更新的情況下，而SurfaceView 主要適用於被動更新，例如頻繁地刷新。
- View 在主線程中對畫面進行刷新，而SurfaceView 通常會通過一個子線程來進行頁面的刷新。
- View在繪圖時沒有使用雙緩衝機制，而SurfaceView在底層實現機制中就已經實現了雙緩衝機制。
總結:如果你的自定義View需要頻繁刷新，或者刷新時數據處理量比較大，那麼你就可以考慮使用SurfaceView來取代View了

#### SurfaceView 模板範例

```java
public class MySurfaceView extends SurfaceView implements SurfaceHolder.Callback, Runnable {

    private SurfaceHolder mHolder;
    //用于绘图的canvas
    private Canvas mCanvas;
    //子线程标志位
    private boolean mIsDrawing;

    int x = 0;
    int y = 400;
    private Path mPath = new Path();
    private Paint mPaint = new Paint();

    public MySurfaceView(Context context) {
        super(context);
        initView();
    }

    public MySurfaceView(Context context, AttributeSet attrs) {
        super(context, attrs);
        initView();
    }

    public MySurfaceView(Context context, AttributeSet attrs, int defStyleAttr) {
        super(context, attrs, defStyleAttr);
        initView();
    }

    //初始化物件
    private void initView() {
        //註冊SurfaceHolder的回調方法
        mHolder = getHolder();
        mHolder.addCallback(this);
        setFocusable(true);
        setFocusableInTouchMode(true);
        this.setKeepScreenOn(true);

        //設定起始位置
        mPath.moveTo(x, y);
        //設定線條風格
        mPaint.setStyle(Paint.Style.STROKE);
        //設定線條寬度
        mPaint.setStrokeWidth(10);
    }

    @Override
    public void surfaceCreated(SurfaceHolder holder) {
        //開始作畫
        mIsDrawing = true;
        new Thread(this).start();
    }

    @Override
    public void surfaceChanged(SurfaceHolder holder, int format, int width, int height) {

    }

    @Override
    public void surfaceDestroyed(SurfaceHolder holder) {
        mIsDrawing = false;
    }

    @Override
    public void run() {
        while (mIsDrawing) {
            draw();
            x += 1;
            y = (int) (100 * Math.sin(x * 2 * Math.PI / 180) + 400);
            mPath.lineTo(x, y);
        }
    }

    private void draw() {
        try {
            mCanvas = mHolder.lockCanvas();
            mCanvas.drawColor(Color.BLACK);
            mCanvas.drawPath(mPath, mPaint);
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            //確保每次都能將內容提交故須放在finally
            if (null != mCanvas) {
                mHolder.unlockCanvasAndPost(mCanvas);
            }
        }
    }
}
```
