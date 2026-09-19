
# Ex.No:12 Design an application that draws basic graphical primitives on the screen.


## AIM:

To create and design an android application that draws basic graphical primitives on the screen using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as “graphical″ and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Draw basic object details give in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
```
/*
Program to create and design an android application that draws basic graphical primitives on the screen.
Developed by: Dharshini
Registeration Number : 212225220024
*/
```
## activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <ImageView
        android:id="@+id/imageView"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
## MainActivity.java
```
package com.example.shapes;

import androidx.appcompat.app.AppCompatActivity;
import android.graphics.Bitmap;
import android.graphics.Canvas;
import android.graphics.Color;
import android.graphics.Paint;
import android.graphics.Path;
import android.graphics.RectF;
import android.graphics.drawable.BitmapDrawable;
import android.os.Bundle;
import android.widget.ImageView;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Create a blank Bitmap
        Bitmap bg = Bitmap.createBitmap(720, 1280, Bitmap.Config.ARGB_8888);

        // Set the Bitmap to the ImageView
        ImageView i = (ImageView) findViewById(R.id.imageView);
        i.setBackgroundDrawable(new BitmapDrawable(bg));

        // Create a Canvas to draw on the Bitmap
        Canvas canvas = new Canvas(bg);

        // Paint setup (pink color, filled)
        Paint paint = new Paint();
        paint.setColor(Color.MAGENTA);
        paint.setStyle(Paint.Style.FILL);  // FILL instead of STROKE
        paint.setAntiAlias(true);
        paint.setTextSize(50);

        // Draw shapes without overlapping (spaced properly)

        // Circle
        canvas.drawText("Circle", 70, 120, paint);
        canvas.drawCircle(180, 250, 100, paint);

        // Rectangle
        canvas.drawText("Rectangle", 420, 120, paint);
        canvas.drawRect(400, 170, 650, 350, paint);

        // Square
        canvas.drawText("Square", 90, 550, paint);
        canvas.drawRect(60, 580, 260, 780, paint);

        // Line
        canvas.drawText("Line", 480, 550, paint);
        Paint linePaint = new Paint();
        linePaint.setColor(Color.MAGENTA);
        linePaint.setStrokeWidth(15);
        canvas.drawLine(470, 600, 670, 780, linePaint);

        // Star
        canvas.drawText("Star", 300, 1050, paint);
        drawFilledStar(canvas, 370, 900, 100, paint);
    }

    // Method to draw a filled 5-point star
    private void drawFilledStar(Canvas canvas, float cx, float cy, float radius, Paint paint) {
        Path path = new Path();
        double angle = Math.PI / 2 * 3;
        float step = (float) Math.PI / 5;

        path.moveTo(cx, cy - radius);

        for (int i = 0; i < 5; i++) {
            path.lineTo(
                    (float) (cx + Math.cos(angle) * radius),
                    (float) (cy + Math.sin(angle) * radius)
            );
            angle += step;
            path.lineTo(
                    (float) (cx + Math.cos(angle) * (radius / 2)),
                    (float) (cy + Math.sin(angle) * (radius / 2))
            );
            angle += step;
        }
        path.close();

        canvas.drawPath(path, paint);
    }
}
```
## OUTPUT
<img width="1918" height="1017" alt="image" src="https://github.com/user-attachments/assets/9f5913f7-28ae-4fa5-9953-39b3c7a9b66b" />

## RESULT
Thus a Simple Android Application to create and design an android application that draws basic graphical primitives on the screen using Android Studio is developed and executed successfully.
