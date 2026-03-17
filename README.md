# Ex.No:2a Develop program to create a text field and a button “Navigate”. When you enter “www.gmail.com” and press navigate button it should open google page using Implicit Intents.


## AIM:

To create a navigate button using Implicit Intent to display the gmail page using Android Studio.

## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:

Start the program. Create a new Android project in Android Studio. Name the project (e.g., MyNavigateApp). Select appropriate SDK and finish setup.

Design the UI (activity_main.xml): Add a TextView for instructions (optional). Add an EditText to allow the user to enter a URL (e.g., "www.gmail.com "). Add a Button with the text “Navigate”.

Open MainActivity.java (or MainActivity.kt): Initialize the EditText and Button using findViewById(). Set OnClickListener for the Button: When clicked, read the text entered in the EditText.

Prepend "https://" if it’s missing. Create an Implicit Intent: Use Intent(Intent.ACTION_VIEW, Uri.parse(url)).

Start the Activity with the Intent: Call startActivity(intent) to launch the browser and open the page. Run the application:

Enter "www.gmail.com" in the text field. Press the Navigate button. The default browser opens the Gmail page. Stop the program.


## PROGRAM:
```
/*
Program to print the text “Implicitintent”.
Developed by: Harshini R
Registeration Number : 212223220033
*/
```

# Main_Activity.java:
```
package com.example.implicit;

import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

import com.example.implicit.R;

public class MainActivity extends AppCompatActivity {

    EditText urlInput;
    Button navigateBtn;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        urlInput = findViewById(R.id.urlInput);
        navigateBtn = findViewById(R.id.navigateBtn);

        navigateBtn.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String url = urlInput.getText().toString().trim();

                if (url.isEmpty()) {
                    Toast.makeText(MainActivity.this, "Please enter a URL", Toast.LENGTH_SHORT).show();
                } else {
                    // Add http if missing
                    if (!url.startsWith("http://") && !url.startsWith("https://")) {
                        url = "http://" + url;
                    }

                    // Create implicit intent
                    Intent intent = new Intent(Intent.ACTION_VIEW, Uri.parse(url));

                    // Start browser
                    try {
                        startActivity(intent);
                    } catch (Exception e) {
                        Toast.makeText(MainActivity.this, "No app found to handle this request", Toast.LENGTH_SHORT).show();
                    }
                }
            }
        });
    }
}

```
# activity_main.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:padding="20dp"
    android:gravity="center"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <EditText
        android:id="@+id/urlInput"
        android:hint="Enter website (e.g. www.gmail.com)"
        android:inputType="textUri"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>

    <Button
        android:id="@+id/navigateBtn"
        android:text="Navigate"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="20dp"/>
</LinearLayout>

```

## OUTPUT

<img width="1913" height="1024" alt="image" src="https://github.com/user-attachments/assets/89fa3fbe-35b9-492c-84fd-d7026c9a4f9b" />

<img width="1917" height="1019" alt="Screenshot 2025-09-22 224008" src="https://github.com/user-attachments/assets/15a8ab22-5929-473d-aa21-0511c7e75211" />

<img width="1916" height="1028" alt="image" src="https://github.com/user-attachments/assets/24edf104-0e6c-4b6d-be2f-c86db8279a78" />



## RESULT
Thus a Simple Android Application create a navigate button using Implicit Intent to display the gmail page using Android Studio is developed and executed successfully.


