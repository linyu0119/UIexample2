activity_main
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:layout_marginTop="100dp"
    android:orientation="vertical" >

    <Button
        android:id="@+id/text1"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:gravity="center"
        android:text="弹出dialog"

        />
    <Button
        android:id="@+id/button2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@id/text1"
        android:gravity="center"
        android:text="next"

        />
</LinearLayout>

update_manage_dialog.xml
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#00FFFFFF" >

    <RelativeLayout
        android:layout_width="250dp"
        android:layout_height="200dp"
        android:layout_centerInParent="true"
        android:background="#ffffff" >

        <TextView
            android:id="@+id/dialog_title"
            android:layout_width="match_parent"
            android:layout_height="50dp"
            android:gravity="center"
            android:background="#FFD700"
            android:text="ANDROID APP"
            android:textColor="#FFFFFF"
            android:textSize="20sp" />

        <EditText
            android:id="@+id/username"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_below="@+id/dialog_title"
            android:layout_marginTop="10dp"
            android:layout_marginLeft="30dp"
            android:layout_marginRight="30dp"
            android:hint="Username"
            android:textColorHint="#AAAAAA"
            android:textSize="14sp" />
        <EditText
            android:id="@+id/password"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_below="@+id/username"
            android:layout_marginTop="10dp"
            android:layout_marginLeft="30dp"
            android:layout_marginRight="30dp"
            android:hint="Password"
            android:textColorHint="#AAAAAA"
            android:textSize="14sp" />

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_alignParentBottom="true"
            android:orientation="horizontal" >

            <Button
                android:id="@+id/dialog_btn_cancel"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:text="Cancel"
                android:background="@null"
                android:textSize="14sp" />

            <Button
                android:id="@+id/dialog_btn_sure"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:text="Sign in"
                android:background="@null"
                android:textSize="14sp" />
        </LinearLayout>
    </RelativeLayout>

</RelativeLayout>

mainactivity

  public class MainActivity extends Activity implements OnClickListener{
  
    private TextView text1;
    
    private Button nexbut;
    
    private Context mContext;
    
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        requestWindowFeature(Window.FEATURE_NO_TITLE);
        setContentView(R.layout.activity_main);
        mContext = this;
        initView();
        nexbut = findViewById(R.id.button2);
    }
    private void initView() {
        text1 = (TextView) findViewById(R.id.text1);
        text1.setOnClickListener(this);
    }

    public void onClick(View v) {

        dialogShow1();

    }
    private void dialogShow1() {
        AlertDialog.Builder builder = new AlertDialog.Builder(mContext);
        LayoutInflater inflater = LayoutInflater.from(mContext);
        View v = inflater.inflate(R.layout.update_manage_dialog, null);
        TextView content = (TextView) v.findViewById(R.id.dialog_title);
        final EditText username = (EditText) v.findViewById(R.id.username);
        final EditText password = (EditText) v.findViewById(R.id.password);
        Button btn_sure = (Button) v.findViewById(R.id.dialog_btn_sure);
        Button btn_cancel = (Button) v.findViewById(R.id.dialog_btn_cancel);
        final Dialog dialog = builder.create();
        dialog.show();
        dialog.getWindow().setContentView(v);
        btn_sure.setOnClickListener(new OnClickListener() {
            @Override
            public void onClick(View v) {
                dialog.dismiss();
                Toast.makeText(mContext, "ok",LENGTH_SHORT).show();
            }
        });

        btn_cancel.setOnClickListener(new OnClickListener() {

            @Override
            public void onClick(View arg0) {
                dialog.dismiss();
                Toast.makeText(mContext, "no", LENGTH_SHORT).show();
            }
        });
    }
}

结果截图：https://github.com/linyu0119/UIexample2/blob/master/images/2.png
