<h1> Deret Fibonacci Toast java</h1>

Nama : Faisal Arya Yudanto
NIM : 312210555
Kelas : TI.22.A5

Mata Kuliah : Pemrograman Mobile 1


Tugas :  Buatlah Method Program java Toast Number, dengan menghasilkan Bilangan Fibonacci

Fibonacci Sequence (Deret angka Fibonacci) adalah deret angka yang diperoleh dengan menjumlahkan dua angka didepannya / sebelumnya:

## Daftar Isi
____________________________________________________________
| No.| Isi        |                                        |
|----|------------|----------------------------------------|
| 1. | Layout     | [disini](#layout)                      |
| 2. | Java       | [disini](#java-class)                  |
| 3. | Design     | [disini](#tampilan-design)             |
| 4. | Hasil Run  | [disni](#hasil-run)                    |
|____|_____________________________________________________|
> - Disini, saya akan mengerjakan dan menjelaskan tugas dari mata kuliah "Pemrograman Mobile 1" yaitu membuat sebuah aplikasi untuk menampilkan bilangan Fibonacci. Selain itu saya juga akan merubah sedikit tampilan dari yang diperintahkan pada tugas, yaitu menambah tombol `Restart` dan menambah tombol `Masukkan Angka Limit` 


## Layout
Pada layout ini, saya membuat tiga button dan satu textview :
1. `button_limit`, berfungsi sebagai tombol “Set Limit” yang nantinya ketika di tekan akan muncul sebuah pop-up untuk masukan limit angka yang ingin kita hitung.
2. `button_count`, berfungsi sebagai tombol “count” yang nantinya ketika tombol ditekan akan menghitung bilangan fibonaccinya sesuai dengan yang kita limit. Juga berbeda warna pada setiap angka, agar tidak keliru.
3. 'button_restart', berfungsi sebagai tombol restart yang nantinya angka akan kembali ke awal.
4. Textview `show_count`, yang berfungsi untuk menampilkan angka atau bilangan fibonaccinya yang tepat berada di tengah.

Berikut adalah coding pada menu layout :

> - **activity_toast.xml**
<?xml version="1.0" encoding="utf-8"?>: Ini adalah deklarasi XML yang menunjukkan versi XML yang digunakan dan jenis encoding yang digunakan.

<androidx.constraintlayout.widget.ConstraintLayout ...>: Ini adalah elemen root dari tata letak. ConstraintLayout adalah tata letak yang fleksibel yang digunakan dalam pengembangan aplikasi Android untuk menentukan hubungan antara elemen-elemen tampilan. Dalam kode ini, ConstraintLayout memiliki atribut yang mengatur lebar dan tinggi tampilan untuk mengisi seluruh layar.

xmlns:android="http://schemas.android.com/apk/res/android", xmlns:app="http://schemas.android.com/apk/res-auto", xmlns:tools="http://schemas.android.com/tools": Ini adalah deklarasi namespace yang digunakan dalam dokumen XML. Namespace ini diperlukan untuk mengakses atribut dan elemen yang didefinisikan oleh Android, AndroidX, dan alat pengembangan.

android:layout_width="match_parent" dan android:layout_height="match_parent": Ini mengatur lebar dan tinggi dari tampilan root (ConstraintLayout) agar sesuai dengan ukuran layar penuh perangkat.

tools:ignore="ExtraText": Ini adalah atribut yang digunakan untuk mengabaikan peringatan alat (tools) yang mungkin muncul dalam lingkungan pengembangan, seperti Android Studio. Dalam hal ini, peringatan "ExtraText" diabaikan.

tools:context="com.example.fibonaccisequence.MainActivity": Ini adalah atribut yang menunjukkan kelas Activity yang terkait dengan tampilan ini dalam konteks pengembangan.

Selanjutnya, tampilan dalam ConstraintLayout:

<Button ...>: Ini adalah elemen tombol. Dalam kode ini, terdapat tiga tombol: "button_limit", "button_count", dan "button_restart". Setiap tombol memiliki atribut yang mengatur ID, lebar, tinggi, teks yang ditampilkan, warna latar belakang, metode yang akan dipanggil saat tombol ditekan, dan tata letak relatifnya terhadap tampilan lainnya.

<TextView ...>: Ini adalah elemen teks yang digunakan untuk menampilkan angka. Ini memiliki atribut yang mengatur ID, lebar, tinggi, teks yang ditampilkan, warna latar belakang, warna teks, ukuran teks, dan beberapa atribut lainnya. TextView ini digunakan untuk menampilkan angka yang akan diubah sesuai dengan tindakan pengguna.

Kode ini menggambarkan tampilan aplikasi Android yang memungkinkan pengguna untuk mengatur "limit" dan menghitung angka dalam urutan tertentu. Semua elemen tampilan ditempatkan dan diatur relatif satu sama lain menggunakan ConstraintLayout, sehingga tampilan dapat beradaptasi dengan berbagai ukuran layar dan orientasi perangkat.
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:ignore="ExtraText"
    tools:context="com.example.fibonaccisequence.MainActivity">


    <Button
        android:id="@+id/button_limit"
        android:layout_width="409dp"
        android:layout_height="84dp"
        android:layout_marginStart="8dp"
        android:layout_marginTop="16dp"
        android:layout_marginEnd="8dp"
        android:background="@color/colorPrimary"
        android:onClick="setLimit"
        android:text="Masukkan Angka Limit"
        android:textColor="@android:color/white"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.507"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        tools:ignore="UsingOnClickInXml,VisualLintButtonSize" />

    <Button
        android:id="@+id/button_count"
        android:layout_width="190dp"
        android:layout_height="80dp"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="24dp"
        android:background="@color/colorPrimary"
        android:onClick="countUp"
        android:text="Count"
        android:textColor="@android:color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.039"
        app:layout_constraintStart_toStartOf="parent"
        tools:ignore="UsingOnClickInXml,VisualLintButtonSize" />

    <Button
        android:id="@+id/button_restart"
        android:layout_width="190dp"
        android:layout_height="80dp"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="24dp"
        android:background="@color/colorPrimary"
        android:onClick="back1"
        android:text="Restart"
        android:textColor="@android:color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.965"
        app:layout_constraintStart_toStartOf="parent"
        tools:ignore="UsingOnClickInXml" />

    <TextView
        android:id="@+id/show_count"
        android:layout_width="417dp"
        android:layout_height="649dp"
        android:layout_marginStart="8dp"
        android:layout_marginTop="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="8dp"
        android:background="#FFFF00"
        android:gravity="center_vertical"
        android:text="1"
        android:textAlignment="center"
        android:textColor="@color/colorPrimary"
        android:textSize="160sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toTopOf="@id/button_count"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@id/button_limit"
        app:layout_constraintVertical_bias="0.0"
        tools:ignore="RtlCompat" />

</androidx.constraintlayout.widget.ConstraintLayout>
```



> - **Strings.xml**
```
<resources>
    <string name="app_name">FibonacciSequence</string>
    <string name="button_label_toast">Toast</string>
    <string name="button_label_count">Count</string>
    <string name="count_initial_value">1</string>
    <string name="toast_massage">Hello Toast!</string>
    <string name="button_label_restart">Restart</string>
    <string name="enter_fibonacci_limit">Masukkan Angka Limit</string>
</resources>
```

> - **Colors.xml**
```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="black">#FF000000</color>
    <color name="white">#FFFFFFFF</color>
    <color name="blue">#3700B3</color>
    <color name="pink">#FFC0CB</color>
    <color name="colorPrimary">#3F5185</color>
    <color name="colorPrimaryDark">#303F9F</color>
    <color name="colorAccent">#FF4081</color>
    <color name="birumuda">#ABCBFA</color>
    <color name="salem">#F8C6E6</color>
    <color name ="purple">#E3A2ED</color>
    <color name="hijau">#92A676</color>
    <color name="biru">#8FC2EA</color>
    <color name="hijaumuda">#C2E69C</color>
    <color name="kuning">#FFEB3B</color>
    <color name="orange">#FF9800</color>
    <color name="cream">#E6C18A</color>
</resources>
```


## Java class
Pada Java class `MainActivity.java` berisi semua coding untuk menjalankan aplikasi. Seperti fungsi untuk tombol-tombol, dialog set limit, warna yang berbeda pada setiap angka, lalu warna background yang bisa berubah dan rumus bilangan fibonacci.
countUp digunakan untuk menghitung angka berikutnya dalam deret dan mengubah tampilan teks.
back1 digunakan untuk mengatur ulang perhitungan menjadi awal.
setLimit memungkinkan pengguna untuk mengatur batasan deret Fibonacci melalui dialog.
```
package com.example.fibonaccisequence;

import android.app.AlertDialog;
import android.content.DialogInterface;
import android.graphics.Color;
import android.os.Bundle;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;


public class MainActivity extends AppCompatActivity {
    private TextView show_count;
    private int count = 1;
    private long fibNMinus1 = 1;
    private long fibNMinus2 = 1;
    private int limit = -1; // Inisialisasi limit dengan nilai default

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_toast);

        show_count = findViewById(R.id.show_count);
    }

    public void countUp(View view) {
        if (count == 0) {
            show_count.setText("0");
        }
        else if (count == 1) {
            show_count.setText("1");
        }
        else {
            if (limit != -1 && count > limit) {
                // Jika count melebihi limit, atur ulang perhitungan
                count = 0;
                fibNMinus1 = 1;
                fibNMinus2 = 0;
                show_count.setText(getString(R.string.count_initial_value));
            }
            else {
                long fibCurrent = fibNMinus1 + fibNMinus2;
                fibNMinus2 = fibNMinus1;
                fibNMinus1 = fibCurrent;

                //Mengatur warna teks berdasarkan angka Fibonacci
                int colorResId = R.color.orange; // Warna Default
                switch (count % 11) {
                    case 1:
                        colorResId = R.color.orange; // Warna Orange
                        break;
                    case 2:
                        colorResId = R.color.hijaumuda; // Warna Hijau Muda
                        break;
                    case 3:
                        colorResId = R.color.purple; // Warna Ungu
                        break;
                    case 4:
                        colorResId = R.color.salem; // Warna Salem
                        break;
                    case 5:
                        colorResId = R.color.birumuda; // Warna Biru Muda
                        break;
                    case 6 :
                        colorResId = R.color.kuning; // Warna Kuning
                        break;
                    case 7:
                        colorResId = R.color.hijau; // Warna Hijau
                        break;
                    case 8:
                        colorResId = R.color.cream; // Warna Cream
                        break;
                    case 9:
                        colorResId = R.color.pink; // Warna Pink
                        break;
                    case 10:
                        colorResId = R.color.biru; // Warna Biru
                        break;
                    case 11:
                        colorResId = R.color.colorAccent; // Warna Pink Tua
                        break;
                }
                show_count.setTextColor(getResources().getColor(colorResId));
                show_count.setText(String.valueOf(fibCurrent));
                show_count.setBackgroundColor(Color.DKGRAY);
            }
        }

        count++;
    }

    public void back1(View view) {
        count = 1;
        fibNMinus1 = 1;
        fibNMinus2 = 0;
        show_count.setText(getString(R.string.count_initial_value));
    }

    public void setLimit(View view) {
        // Create and display a dialog to set the limit
        AlertDialog.Builder builder = new AlertDialog.Builder(this);
        builder.setTitle("Set Limit");

        final EditText input = new EditText(this);
        input.setInputType(android.text.InputType.TYPE_CLASS_NUMBER);
        builder.setView(input);

        builder.setPositiveButton("OK", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialog, int which) {
                // Get the limit from the input and set it for calculations
                String limitStr = input.getText().toString();
                limit = Integer.parseInt(limitStr);
            }
        });

        builder.setNegativeButton("Cancel", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialog, int which) {
                dialog.cancel();
            }
        });

        builder.show();
    }
}
```


## Tampilan design



![Screenshot (116)](https://github.com/syifaaurellia/DeretBilanganFibonacci/assets/115867244/3ce9415d-bf44-45fc-a8eb-cdf5734ffd3c)



## Hasil Run 





https://github.com/syifaaurellia/DeretBilanganFibonacci/assets/115867244/66f7c216-ba05-4d3b-912e-108e10b25726

