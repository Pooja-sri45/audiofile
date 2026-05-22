# Ex.No:3 Develop a simple application to play and control the audio file in android studio.


## AIM:

To develop a simple application, to play and control the audio file and to perfrom the start,pause and stop opeartion in Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Min.required Artic Fox)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as audiofile and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml and create start,pause and stop button.

Step 6: Display message give in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
```
/*
Program to play and control the audio file”.
Developed by: POOJASRI L
Registeration Number : 212223220076
*/
```
## MainActivity.java
```
package com.example.pmdexpt2;

import androidx.appcompat.app.AppCompatActivity;
import android.media.MediaPlayer;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    private MediaPlayer mediaPlayer;
    private Button btnPlay, btnPause, btnStop;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Initialize buttons
        btnPlay = findViewById(R.id.btnPlay);
        btnPause = findViewById(R.id.btnPause);
        btnStop = findViewById(R.id.btnStop);

        // Create MediaPlayer
        mediaPlayer = MediaPlayer.create(this, R.raw.audio);

        // If using assets folder instead, use:
        // mediaPlayer = new MediaPlayer();
        // try {
        //     mediaPlayer.setDataSource("file:///android_asset/audio.mp3");
        //     mediaPlayer.prepare();
        // } catch (Exception e) {
        //     e.printStackTrace();
        // }

        // PLAY Button
        btnPlay.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if (mediaPlayer != null && !mediaPlayer.isPlaying()) {
                    mediaPlayer.start();
                    showToast("Playing audio...");
                }
            }
        });

        // PAUSE Button
        btnPause.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if (mediaPlayer != null && mediaPlayer.isPlaying()) {
                    mediaPlayer.pause();
                    showToast("Audio paused");
                }
            }
        });

        // STOP Button
        btnStop.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if (mediaPlayer != null) {
                    if (mediaPlayer.isPlaying()) {
                        mediaPlayer.stop();
                    }
                    mediaPlayer.reset();
                    try {
                        mediaPlayer = MediaPlayer.create(MainActivity.this, R.raw.audio);
                    } catch (Exception e) {
                        e.printStackTrace();
                    }
                    showToast("Audio stopped");
                }
            }
        });
    }

    private void showToast(String message) {
        Toast.makeText(this, message, Toast.LENGTH_SHORT).show();
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        if (mediaPlayer != null) {
            mediaPlayer.release();
        }
    }
}
```
## Activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="20dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Audio Player in Android"
        android:textSize="20sp"
        android:textStyle="bold"
        android:layout_marginBottom="30dp"/>

    <Button
        android:id="@+id/btnPlay"
        android:layout_width="150dp"
        android:layout_height="60dp"
        android:text="PLAY"
        android:textSize="16sp"
        android:textColor="#FFFFFF"
        android:backgroundTint="#00BCD4"
        android:layout_margin="10dp"/>

    <Button
        android:id="@+id/btnPause"
        android:layout_width="150dp"
        android:layout_height="60dp"
        android:text="PAUSE"
        android:textSize="16sp"
        android:textColor="#FFFFFF"
        android:backgroundTint="#00BCD4"
        android:layout_margin="10dp"/>

    <Button
        android:id="@+id/btnStop"
        android:layout_width="150dp"
        android:layout_height="60dp"
        android:text="STOP"
        android:textSize="16sp"
        android:textColor="#FFFFFF"
        android:backgroundTint="#00BCD4"
        android:layout_margin="10dp"/>

</LinearLayout>
```

## OUTPUT

<img width="1917" height="1078" alt="EX 3 A" src="https://github.com/user-attachments/assets/f643ca4f-ece4-45cc-9ffb-a4260642be4e" />

<img width="1917" height="1078" alt="EX 3 B" src="https://github.com/user-attachments/assets/08740998-840e-4ad9-9dda-6b074c9b7ee7" />

<img width="1918" height="1078" alt="EX 3 C" src="https://github.com/user-attachments/assets/f6a7b089-dcad-4f12-b0bd-ddd26882de14" />

<img width="1918" height="1078" alt="ex 3 d" src="https://github.com/user-attachments/assets/164b692f-43b6-4068-b906-c40f2c5a39cf" />




## RESULT
   Thus a simple application, to play and control the audio file and to perfrom the start,pause and stop opeartion in Android Studio is developed and executed successfully.
