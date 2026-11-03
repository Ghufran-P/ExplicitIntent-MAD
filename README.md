# Ex.No:2b To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.

## AIM:

To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.

## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:

1. Start the application.
2. Create a new Android project in Android Studio.
3. Design the first screen with: One EditText to accept a number, One Button labeled FACTORIAL.
4. Create a second activity to display the result.
5. In MainActivity, read the number entered by the user.
6. Create an Explicit Intent to open MainActivity2. Pass the entered number to MainActivity2 using putExtra().
7. In MainActivity2, receive the number using getIntent().getStringExtra(). Convert the received value into an integer.
8. Calculate the factorial of the number using a for loop. Display the factorial result in a TextView.
9. Run the application. Verify that the second screen displays the correct factorial.
10. Stop the application.

## PROGRAM:

### Program to print the text “ExplicitIntent”.

Developed by : KEERTHIVASAN S

Registeration Number : 212223220046

### activity_main.xml

```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="126dp"
        android:layout_height="23dp"
        android:text="Enter a Number"
        android:textSize="18sp"
        app:layout_constraintBottom_toTopOf="@+id/editTextText"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.548" />

    <EditText
        android:id="@+id/editTextText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="144dp"
        android:ems="10"
        android:inputType="text"
        android:text=""
        app:layout_constraintBottom_toTopOf="@+id/button"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent" />

    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="232dp"
        android:text="FACTORIAL"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.505"
        app:layout_constraintStart_toStartOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

### MainActivity.java

```
package com.example.explicitintent;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

public class MainActivity extends AppCompatActivity {
    EditText editText;
    Button button;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        editText = findViewById(R.id.editTextText);
        button = findViewById(R.id.button);
        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String num = editText.getText().toString();
                Intent intent = new Intent(MainActivity.this, MainActivity2.class);
                intent.putExtra("number", num);
                startActivity(intent);
            }
        });
    }
}
```

### activity_main2.xml

```
<?xml version="1.0" encoding="utf-8"?>

<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:id="@+id/result"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Factorial"
        android:textSize="30sp"
        android:textStyle="bold"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"/>

</androidx.constraintlayout.widget.ConstraintLayout>
```

### MainActivity2.java

```
package com.example.explicitintent;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.widget.TextView;

public class MainActivity2 extends AppCompatActivity {
    TextView result;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main2);
        result = findViewById(R.id.result);
        String number = getIntent().getStringExtra("number");
        if (number != null && !number.isEmpty()) {
            try {
                int n = Integer.parseInt(number);
                long fact = 1;
                for (int i = 1; i <= n; i++) {
                    fact = fact * i;
                }
                result.setText("Factorial of " + n + " = " + fact);
            } catch (NumberFormatException e) {
                result.setText("Invalid input");
            }
        }
    }
}
```

## OUTPUT

### Starting Screen

<img width="1919" height="1079" alt="ex2bop1" src="https://github.com/user-attachments/assets/9d0b91b4-1289-464f-ba47-f8839fdbca18" />

### Value Entered for Calculation

<img width="1919" height="1079" alt="ex2bop2" src="https://github.com/user-attachments/assets/3522e9a5-6f03-4afe-86c7-a3b292522767" />

### Result Value

<img width="1919" height="1079" alt="ex2bop3" src="https://github.com/user-attachments/assets/cb879ecd-2d75-4bf0-ae64-25a1300d22e9" />

## RESULT
Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.
