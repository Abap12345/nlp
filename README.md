# nlpIn [1]:

#1 

#Java file 

package com.example.myapplication2;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;

public class MainActivity extends AppCompatActivity {

    @Override

    protected void onCreate(Bundle savedInstanceState) {

        super.onCreate(savedInstanceState);

        setContentView(R.layout.activity_main);

    }

}

#Xml file

<?xml version="1.0" encoding="utf-8"?>

<androidx.constraintlayout.widget.ConstraintLayout

    xmlns:android="http://schemas.android.com/apk/res/android"

    xmlns:app="http://schemas.android.com/apk/res-auto"

    xmlns:tools="http://schemas.android.com/tools"

    android:layout_width="match_parent"

    android:layout_height="match_parent"

    android:orientation="vertical"

    tools:context="com.example.myapplication2.MainActivity">

    <TextView

        android:layout_width="wrap_content"

        android:layout_height="wrap_content"

        android:layout_marginLeft="150dp"

        android:layout_marginTop="150dp"

        android:text="Hello World!"

        tools:ignore="MissingConstraints" />

    <ImageView

        android:layout_width="408dp"

        android:layout_height="430dp"

        android:src="@drawable/android"

        tools:ignore="MissingConstraints"

        tools:layout_editor_absoluteX="0dp"

        tools:layout_editor_absoluteY="122dp" />

</androidx.constraintlayout.widget.ConstraintLayout>

  File "<ipython-input-1-b86bd52d2983>", line 3

    package com.example.myapplication2;

            ^

SyntaxError: invalid syntax

In [2]:

#2 Create and Start Activity Lifecycle and Instance State

#java file

package com.example.activitylifecycle1;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;

import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    @Override

    protected void onCreate(Bundle savedInstanceState) {

        super.onCreate(savedInstanceState);

        setContentView(R.layout.activity_main);

        Toast.makeText(this, "activity created", Toast.LENGTH_SHORT).show();

    }

    @Override

    protected void onStart() {

        super.onStart();

        Toast.makeText(this, "activity started", Toast.LENGTH_SHORT).show();

    }

    @Override

    protected void onResume() {

        super.onResume();

        Toast.makeText(this, "activity resumed", Toast.LENGTH_SHORT).show();

    }

    @Override

    protected void onPause() {

        super.onPause();

        Toast.makeText(this, "activity paused", Toast.LENGTH_SHORT).show();

    }

    @Override

    protected void onStop() {

        super.onStop();

        Toast.makeText(this, "activity stopped", Toast.LENGTH_SHORT).show();

    }

    @Override

    protected void onRestart() {

        super.onRestart();

        Toast.makeText(this, "activity restarted", Toast.LENGTH_SHORT).show();

    }

    @Override

    protected void onDestroy() {

        super.onDestroy();

        Toast.makeText(this, "Destroyed", Toast.LENGTH_SHORT).show();

    }

}

#Xml file

<?xml version="1.0" encoding="utf-8"?>

<androidx.constraintlayout.widget.ConstraintLayout

    xmlns:android="http://schemas.android.com/apk/res/android"

    xmlns:app="http://schemas.android.com/apk/res-auto"

    xmlns:tools="http://schemas.android.com/tools"

    android:layout_width="match_parent"

    android:layout_height="match_parent"

    tools:context="com.example.activitylifecycle1.MainActivity">

    <TextView

        android:layout_width="wrap_content"

        android:layout_height="wrap_content"

        android:text="Hello World!"

        tools:ignore="MissingConstraints" />

</androidx.constraintlayout.widget.ConstraintLayout>

  File "<ipython-input-2-b1c78a3a2928>", line 3

    package com.example.activitylifecycle1;

            ^

SyntaxError: invalid syntax

In [3]:

#3 Create implicit intents 

#java file

package com.example.hello_world;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;

import android.net.Uri;

import android.os.Bundle;

import android.view.View;

import android.widget.Button;

import android.widget.EditText;

public class MainActivity extends AppCompatActivity {

    @Override

    protected void onCreate(Bundle savedInstanceState) {

        super.onCreate(savedInstanceState);

        setContentView(R.layout.activity_main);

        final EditText editText1=(EditText)findViewById(R.id.editText1);

        Button button1;

        button1 = (Button)findViewById(R.id.button1);

       button1.setOnClickListener(new View.OnClickListener() {

           @Override

           public void onClick(View view) {

               String url=editText1.getText().toString();

               Intent intent=new Intent(Intent.ACTION_VIEW);

               intent.setData(Uri.parse(url));

               startActivity(intent);

           }

       });

    }

}

#Xml file

<?xml version="1.0" encoding="utf-8"?>

<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"

    xmlns:app="http://schemas.android.com/apk/res-auto"

    xmlns:tools="http://schemas.android.com/tools"

    android:id="@+id/btn"

    android:layout_width="match_parent"

    android:layout_height="match_parent"

    tools:context=".MainActivity">

    <EditText

        android:id="@+id/editText1"

        android:layout_width="150dp"

        android:layout_height="150dp"

        tools:layout_editor_absoluteX="3dp"

        tools:layout_editor_absoluteY="5dp"

        tools:ignore="MissingConstraints"/>

    <Button

        android:id="@+id/button1"

        android:layout_width="141dp"

        android:layout_height="52dp"

        android:layout_below="@+id/editText1"

        android:layout_centerHorizontal="true"

        android:text="Visit"

        tools:layout_editor_absoluteX="83dp"

        tools:layout_editor_absoluteY="210dp"

        tools:ignore="MissingConstraints"/>

</androidx.constraintlayout.widget.ConstraintLayout>

  File "<ipython-input-3-7e225890d3b9>", line 3

    package com.example.hello_world;

            ^

SyntaxError: invalid syntax

In [4]:

#4Make your First Interactive UI Using Layouts and Text View Elements

#java file 

package com.example.myapplication3;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;

import android.view.View;

import android.widget.Button;

import android.widget.EditText;

import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    EditText user,pass;

    Button btn;

    @Override

    protected void onCreate(Bundle savedInstanceState) {

        super.onCreate(savedInstanceState);

        setContentView(R.layout.activity_main);

        user=findViewById(R.id.user);

        pass=findViewById(R.id.pass);

        btn=findViewById(R.id.button);

        btn.setOnClickListener(new View.OnClickListener() {

            @Override

            public void onClick(View view) {

                if(user.getText().toString().equals("Admin") && pass.getText().toString().equals("11233")){

                    Toast.makeText(getApplicationContext(), "log in ", Toast.LENGTH_SHORT).show();

                }

                else

                    Toast.makeText(MainActivity.this, "not vaild", Toast.LENGTH_SHORT).show();

            }

        });

    }

}

#Xml file

<?xml version="1.0" encoding="utf-8"?>

<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"

    xmlns:app="http://schemas.android.com/apk/res-auto"

    xmlns:tools="http://schemas.android.com/tools"

    android:layout_width="match_parent"

    android:layout_height="match_parent"

    tools:context=".MainActivity">

    <TextView

        android:id="@+id/textView"

        android:layout_width="wrap_content"

        android:layout_height="wrap_content"

        android:text="Hello World!"

        app:layout_constraintBottom_toBottomOf="parent"

        app:layout_constraintLeft_toLeftOf="parent"

        app:layout_constraintRight_toRightOf="parent"

        app:layout_constraintTop_toTopOf="parent" />

    <EditText

        android:id="@+id/user"

        android:layout_width="wrap_content"

        android:layout_height="wrap_content"

        android:ems="10"

        android:inputType="textPersonName"

        android:minHeight="48dp"

        android:text="Name"

        app:layout_constraintBottom_toBottomOf="parent"

        app:layout_constraintEnd_toEndOf="parent"

        app:layout_constraintHorizontal_bias="0.417"

        app:layout_constraintStart_toStartOf="parent"

        app:layout_constraintTop_toTopOf="parent"

        app:layout_constraintVertical_bias="0.137" />

    <EditText

        android:id="@+id/pass"

        android:layout_width="wrap_content"

        android:layout_height="wrap_content"

        android:layout_marginTop="40dp"

        android:ems="10"

        android:inputType="textPassword"

        android:minHeight="48dp"

        app:layout_constraintEnd_toEndOf="parent"

        app:layout_constraintHorizontal_bias="0.417"

        app:layout_constraintStart_toStartOf="parent"

        app:layout_constraintTop_toBottomOf="@+id/user"

        tools:ignore="SpeakableTextPresentCheck" />

    <Button

        android:id="@+id/button"

        android:layout_width="wrap_content"

        android:layout_height="wrap_content"

        android:layout_marginTop="24dp"

        android:text="Button"

        app:layout_constraintEnd_toEndOf="parent"

        app:layout_constraintHorizontal_bias="0.476"

        app:layout_constraintStart_toStartOf="parent"

        app:layout_constraintTop_toBottomOf="@+id/pass" />

</androidx.constraintlayout.widget.ConstraintLayout>

  File "<ipython-input-4-4f08eabceeae>", line 3

    package com.example.myapplication3;

            ^

SyntaxError: invalid syntax

In [5]:

#5Using an Options Menu

#java file 

package com.example.myapplicationmenu;

import androidx.appcompat.app.AppCompatActivity;

import androidx.appcompat.app.AlertDialog;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;

import android.view.Menu;

import android.view.MenuItem;

import android.widget.Toast;

import android.content.DialogInterface;

import android.os.Bundle;

import android.view.Menu;

import android.content.DialogInterface;

public class MainActivity extends AppCompatActivity {

    @Override

    protected void onCreate(Bundle savedInstanceState) {

        super.onCreate(savedInstanceState);

        setContentView(R.layout.activity_main);

    }

    @Override

    public boolean onCreateOptionsMenu(Menu menu) {

        menu.add(0,0,0,"Show alter dialog");

        menu.add(0,1,1,"Show Toast Message");

        menu.add(0,2,2,"Close Activity");

        return true;

    }

    @Override

    public boolean onOptionsItemSelected(MenuItem item) {

        switch (item.getItemId()){

            case 0: {

                AlertDialog.Builder dialogBuilder = new

                        AlertDialog.Builder(MainActivity.this);

                dialogBuilder.setMessage("Do you want to close the app?")

                        .setCancelable(false)

                        .setPositiveButton("Yes", new

                                DialogInterface.OnClickListener() {

                                    public void onClick(DialogInterface dialog, int id) {

                                        finish();

                                    }

                                })

                        .setNegativeButton("No", new

                                DialogInterface.OnClickListener() {

                                    public void onClick(DialogInterface dialog, int id) {

                                        dialog.cancel();

                                    }

                                });

                AlertDialog alert = dialogBuilder.create();

                alert.setTitle("AlertDialogExample");

                alert.show();

            }

            break;

            case 1:

                Toast.makeText(MainActivity.this,"This is a Toast Message",Toast.LENGTH_LONG).show();

                break;

            case 2:

                finish();

                break;

            default:

                break;

        }

        return false;

    }

}

#xml file 

<?xml version="1.0" encoding="utf-8"?>

<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"

    xmlns:app="http://schemas.android.com/apk/res-auto"

    xmlns:tools="http://schemas.android.com/tools"

    android:layout_width="match_parent"

    android:layout_height="match_parent"

    tools:context=".MainActivity">

    <TextView

        android:layout_width="wrap_content"

        android:layout_height="wrap_content"

        android:text="Hello World!"

        app:layout_constraintBottom_toBottomOf="parent"

        app:layout_constraintLeft_toLeftOf="parent"

        app:layout_constraintRight_toRightOf="parent"

        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>

  File "<ipython-input-5-602954cb206d>", line 4

    package com.example.myapplicationmenu;

            ^

SyntaxError: invalid syntax

In [6]:

#6Set and retreive shared preferences

#java file

package com.example.set_retrieve_preferences;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;

import android.app.Activity;

import android.content.Context;

import android.content.SharedPreferences;

import android.view.Menu;

import android.view.View;

import android.widget.TextView;

import java.util.jar.Attributes;

public class MainActivity<Email, Name, name> extends AppCompatActivity {

    SharedPreferences sharedpreferences;

    TextView name;

    TextView email;

    public static final String mypreference = "mypref";

    public static final String Name = "nameKey";

    public static final String Email = "emailKey";

    @Override

    protected void onCreate(Bundle savedInstanceState) {

        super.onCreate(savedInstanceState);

        setContentView(R.layout.activity_main);

        name = (TextView) findViewById(R.id.etName);

        email = (TextView) findViewById(R.id.etEmail);

        sharedpreferences = getSharedPreferences(mypreference,

                Context.MODE_PRIVATE);

        if (sharedpreferences.contains(Name)) {

            name.setText(sharedpreferences.getString(Name, ""));

        }

        if (sharedpreferences.contains(Email)) {

            email.setText(sharedpreferences.getString(Email, ""));

        }

    }

    public void Save(View view) {

        String n = name.getText().toString();

        String e = email.getText().toString();

        SharedPreferences.Editor editor = sharedpreferences.edit();

        editor.putString(Name, n);

        editor.putString(Email, e);

        editor.commit();

    }

    public void clear(View view) {

        name = (TextView) findViewById(R.id.etName);

        email = (TextView) findViewById(R.id.etEmail);

        name.setText("");

        email.setText("");

    }

    public void Get(View view) {

        name = (TextView) findViewById(R.id.etName);

        email = (TextView) findViewById(R.id.etEmail);

        sharedpreferences = getSharedPreferences(mypreference,

                Context.MODE_PRIVATE);

        if (sharedpreferences.contains(Name)) {

            name.setText(sharedpreferences.getString(Name, ""));

        }

        if (sharedpreferences.contains(Email)) {

            email.setText(sharedpreferences.getString(Email, ""));

        }

    }

}

# xml file

<?xml version="1.0" encoding="utf-8"?>

<androidx.constraintlayout.widget.ConstraintLayout

    xmlns:android="http://schemas.android.com/apk/res/android"

    xmlns:app="http://schemas.android.com/apk/res-auto"

    xmlns:tools="http://schemas.android.com/tools"

    android:layout_width="match_parent"

    android:layout_height="match_parent"

    tools:context="com.example.set_retrieve_preferences.MainActivity">

    <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"

        android:layout_width="match_parent"

        android:layout_height="match_parent"

        >

        <Button

            android:id="@+id/btnSave"

            android:layout_width="wrap_content"

            android:layout_height="wrap_content"

            android:layout_centerVertical="true"

            android:layout_alignParentLeft="true"

            android:layout_alignParentStart="true"

            android:onClick="Save"

            android:text="Save"

            tools:ignore="MissingConstraints" />

        <Button

            android:id="@+id/btnRetr"

            android:layout_width="wrap_content"

            android:layout_height="wrap_content"

            android:layout_centerHorizontal="true"

            android:layout_centerVertical="true"

            android:onClick="Get"

            android:text="Retrieve"

            tools:ignore="MissingConstraints" />

        <Button

            android:id="@+id/btnClear"

            android:layout_width="wrap_content"

            android:layout_height="wrap_content"

            android:layout_alignRight="@+id/etEmail"

            android:layout_centerVertical="true"

            android:onClick="clear"

            android:text="Clear"

            tools:ignore="MissingConstraints" />

        <EditText

            android:id="@+id/etEmail"

            android:layout_width="match_parent"

            android:layout_height="wrap_content"

            android:ems="10"

            android:hint="Email"

            android:inputType="textEmailAddress"

            android:layout_below="@+id/etName"

            android:layout_marginTop="20dp"

            tools:ignore="MissingConstraints" />

        <EditText

            android:id="@+id/etName"

            android:layout_width="match_parent"

            android:layout_height="wrap_content"

            android:ems="10"

            android:hint="Name"

            android:inputType="text"

            tools:ignore="MissingConstraints" />

    </RelativeLayout>

</androidx.constraintlayout.widget.ConstraintLayout>

  File "<ipython-input-6-8b43e26470fe>", line 3

    package com.example.set_retrieve_preferences;

            ^

SyntaxError: invalid syntax

In [7]:

#7 .Implement a simple content provider

#java file 

package com.example.myapplicationcontent;

import androidx.appcompat.app.AppCompatActivity;

import androidx.core.app.ActivityCompat;

import android.Manifest;

import android.annotation.SuppressLint;

import android.database.Cursor;

import android.provider.ContactsContract;

import android.os.Bundle;

import android.widget.ArrayAdapter;

import android.widget.ListView;

import java.util.ArrayList;

public class MainActivity extends AppCompatActivity {

    ListView lv;

    ArrayList al=new ArrayList();

    @SuppressLint("Range")

    @Override

    protected void onCreate(Bundle savedInstanceState) {

        super.onCreate(savedInstanceState);

        //setContentView(R.layout.activity_main);

        ActivityCompat.requestPermissions(MainActivity.this,new String[]

                {Manifest.permission.READ_CONTACTS},1);

        setContentView(R.layout.activity_main);

        lv=(ListView)findViewById(R.id.list);

        Cursor c=getContentResolver().query(ContactsContract.CommonDataKinds.Phone.CONTENT_URI,null,null,null,null,null);

        while (c.moveToNext()){

            String name;

            name = c.getString(c.getColumnIndex(ContactsContract.CommonDataKinds.Phone.DISPLAY_NAME));

            al.add(name);

        }

        lv.setAdapter(new

                ArrayAdapter(MainActivity.this,android.R.layout.simple_list_item_1,al));

    }

}

#xml file 

<?xml version="1.0" encoding="utf-8"?>

<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"

    xmlns:app="http://schemas.android.com/apk/res-auto"

    xmlns:tools="http://schemas.android.com/tools"

    android:layout_width="match_parent"

    android:layout_height="match_parent"

    tools:context=".MainActivity">

    <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"

        xmlns:app="http://schemas.android.com/apk/res-auto"

        xmlns:tools="http://schemas.android.com/tools"

        android:layout_width="match_parent"

        android:layout_height="match_parent"

        android:paddingTop="16dp"

        android:paddingRight="16dp"

        android:paddingLeft="16dp"

        android:paddingBottom="16dp"

        tools:context="com.example.contentprovider.MainActivity">

        <ListView

            android:id="@+id/list"

            android:layout_width="match_parent"

            android:layout_height="match_parent"

            tools:layout_editor_absoluteX="8dp"

            tools:layout_editor_absoluteY="8dp" />

    </RelativeLayout>

</androidx.constraintlayout.widget.ConstraintLayout>

#manifest

<?xml version="1.0" encoding="utf-8"?>

<manifest xmlns:android="http://schemas.android.com/apk/res/android"

    package="com.example.myapplicationcontent">

    <uses-permission android:name="android.permission.READ_CONTACTS"/>

    <application

        android:allowBackup="true"

        android:icon="@mipmap/ic_launcher"

        android:label="@string/app_name"

        android:roundIcon="@mipmap/ic_launcher_round"

        android:supportsRtl="true"

        android:theme="@style/Theme.MyApplicationcontent">

        <activity

            android:name=".MainActivity"

            android:exported="true">

            <intent-filter>

                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />

            </intent-filter>

        </activity>

    </application>

</manifest>

  File "<ipython-input-7-bc67ddaf578b>", line 3

    package com.example.myapplicationcontent;

            ^

SyntaxError: invalid syntax

In [ ]:

#10  Program to implement Broadcast Receivers

#java file 1

#java file 2

#xml file
