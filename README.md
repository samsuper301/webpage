# webpage

Flutter Widgets 
runApp() - # it is the first widget to run an app 
stless - State less widget for running hot reload, i've to make sure to call it in runApp()

for update to version 2.0 

Solution:

1) Open your MainActivity.java file from below path android/app/src/main/java/[your/package/name]/MainActivity.java

2) Replace FlutterActivity import with below imports

import io.flutter.embedding.android.FlutterActivity;
import io.flutter.embedding.engine.FlutterEngine;
3) Open AndroidManifest.xml file from below path

android/app/src/main/AndroidManifest.xml

4) Delete the reference to android:name under <application> tag

Before

<application
        android:name="io.flutter.app.FlutterApplication"
       >
       <!-- code omitted -->
   </application>
After

  <application
       >
       <!-- code omitted -->
    </application>


5) Replace entire <meta-data> tag in AndroidManfest.xml file with below

<meta-data
    android:name="flutterEmbedding"
    android:value="2" />
6) Replace below block of code in MainActivity.java

public class MainActivity extends FlutterActivity {
@Override
    protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    GeneratedPluginRegistrant.registerWith(this);
    }
}
With below

public class MainActivity extends FlutterActivity {
@Override
    public void configureFlutterEngine(FlutterEngine flutterEngine) {
    GeneratedPluginRegistrant.registerWith(flutterEngine);
    }
}
