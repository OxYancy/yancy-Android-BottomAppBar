# BottomAppBar的使用

## 准备
引入依赖
```groovy
implementation 'com.google.android.material:material:1.1.0-alpha06'
```
在res/menu目录新建bootom-app-bar.xml
加入3个菜单

```xml
<item android:title="个人" />
<item android:title="设置" />
<item android:title="关于" />
```
activity_main.xml文件
```xml
 <androidx.coordinatorlayout.widget.CoordinatorLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent">

        <com.google.android.material.bottomappbar.BottomAppBar
            android:id="@+id/bottomAppBar"
            style="@style/Widget.MaterialComponents.BottomAppBar.Colored"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_gravity="bottom"
            app:fabCradleRoundedCornerRadius="16dp"
            app:navigationIcon="@drawable/ic_menu_black_24dp" />

        <com.google.android.material.floatingactionbutton.FloatingActionButton
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_margin="16dp"
            android:src="@drawable/ic_add_black_24dp"
            app:fabSize="normal"
            android:id="@+id/floatbtn"
            app:layout_anchor="@+id/bottomAppBar" />

    </androidx.coordinatorlayout.widget.CoordinatorLayout>
```

MainActivity
```java
//        设置 menu
        setSupportActionBar(bottomAppBar);
//        点击监听事件
        floatbtn.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Snackbar.make(v, "你点击了", Snackbar.LENGTH_SHORT).show();
            }
        });
//    创建 menu 菜单
    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        getMenuInflater().inflate(R.menu.bottom_app_bar, menu);
        return true;
    }
```