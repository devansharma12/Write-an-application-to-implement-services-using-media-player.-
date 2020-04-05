# Write-an-application-to-implement-services-using-media-player.-

Ans: -

package com.example.myservice;

import android.app.Service;

import android.content.Intent;

import android.media.MediaPlayer;

import android.os.IBinder;

import android.provider.Settings;

import android.widget.Toast;

public class MyService extends Service {

MediaPlayer player;

@Override

public IBinder onBind(Intent intent) {

return null;

}

@Override

public int onStartCommand(Intent intent, int flags, int startId) { Toast.makeText(this,"service started", Toast.LENGTH_SHORT);

player = MediaPlayer.create(this, Settings.System.DEFAULT_RINGTONE_URI);

player.setLooping(true);

player.start();

return START_NOT_STICKY;

}

@Override

public void onDestroy() {

super.onDestroy();

player.stop();

}

}
 

package com.example.myservice;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;

import android.os.Bundle;

import android.view.View;



public class MainActivity extends AppCompatActivity { @Override

protected void onCreate(Bundle savedInstanceState) { super.onCreate(savedInstanceState); setContentView(R.layout.activity_main);

}

public void startPlayer(View view)

{

Intent in=new Intent(this,MyService.class);

startService(in);

}

public void stopPlayer(View view)

{

Intent in=new Intent(this,MyService.class);

stopService(in);

}

}
 

OUTPUT:

