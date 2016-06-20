# AndSes4Ass3
MainActivity.java
package me.rk.andses4ass3;

import android.content.Intent;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;

public class MainActivity extends AppCompatActivity {

    Button  gridView;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        gridView= (Button) findViewById(R.id.buttongrid);
        gridView.setOnClickListener(new View.OnClickListener(){

            @Override
            public void onClick(View v) {
                Intent intent= new Intent(MainActivity.this, GridViewScreen.class);
                startActivity(intent);
            }
        });
    }
}

GridViewScreen.java
package me.rk.andses4ass3;

import android.app.Activity;
import android.os.Bundle;
import android.widget.GridView;

/**
 * Created by airodyra on 6/20/2016.
 */
public class GridViewScreen extends Activity {

    private GridView mgridview;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.grid_view_layout);

        mgridview=(GridView) findViewById(R.id.gridlayout);

        final int[] imagesArray={R.drawable.gingerbread, R.drawable.honeycomb, R.drawable.icecream,
                R.drawable.jellyfish, R.drawable.kitkat, R.drawable.lollipop};

        CustomAdaptor customAdaptor= new CustomAdaptor(GridViewScreen.this, imagesArray);
        mgridview.setAdapter(customAdaptor);

    }
}

CustomeAdaptorScreen.java
package me.rk.andses4ass3;

import android.content.Context;
import android.view.View;
import android.view.ViewGroup;
import android.widget.BaseAdapter;
import android.widget.ImageView;

/**
 * Created by airodyra on 6/20/2016.
 */
public class CustomAdaptor extends BaseAdapter {
    private Context mContext;
    private int[] mimages;

    public CustomAdaptor (Context context, int[]images){
        mContext=context;
        mimages=images;
    }

    @Override
    public int getCount() {
        return mimages.length;
    }

    @Override
    public Object getItem(int position) {
        return position;
    }

    @Override
    public long getItemId(int position) {
        return position;
    }

    public class ViewHolder{
        ImageView imageView;
    }

    @Override
    public View getView(int position, View convertView, ViewGroup parent) {

        ViewHolder viewHolder;

        if (convertView==null){

            viewHolder=new ViewHolder();
            View rootView= View.inflate(mContext, R.layout.custom_view_layout, null);
            viewHolder.imageView= (ImageView) rootView.findViewById(R.id.image99);

            rootView.setTag(viewHolder);
            convertView=rootView;

        }else{
            viewHolder= (ViewHolder) convertView.getTag();

        }

        viewHolder.imageView.setImageResource(mimages[position]);
        return convertView;
    }
}

activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical" android:layout_width="match_parent"
    android:layout_height="match_parent">

    <GridView
        android:id="@+id/gridlayout"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:numColumns="auto_fit"
        android:stretchMode="columnWidth"/>
</LinearLayout>

grid_view_layout.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical" android:layout_width="match_parent"
    android:layout_height="match_parent">

    <GridView
        android:id="@+id/gridlayout"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:numColumns="auto_fit"
        android:stretchMode="columnWidth"/>
</LinearLayout>

custom_view_layout.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:layout_margin="10dp"
    android:padding="10dp">

    <ImageView
        android:id="@+id/image99"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:padding="9dp"
        android:background="@drawable/gingerbread"/>

</LinearLayout>


