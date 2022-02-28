# Laporan Proyek Machine Learning - Alfandi Firnando

## Domain Proyek

Memprediksi harga rumah

Permasalahan dari penelitian kali ini adalah bagaimana melakukan prediksi terhadap harga rumah, dalam menentukan harga rumah tentu sangat banyak feature/ciri yang mempengaruhi harga rumah mulai dari faktor internal maupun faktor eksternal, sebagai contoh jumlah ruangan di sebuah rumah pasti akan sangat berpengaruh terhadap harganya, selain itu letak posisi rumah secara geografis juga sangat menentukan harganya, misal terletak di kawasan bisnis perkotaan atau tidak. Oleh karena itu sangat dibutuhkan penelitian dari berbagai disiplin ilmu pengetahuan untuk menyelesaikan permasalahan dalam melakukan prediksi terhadap harga rumah, dalam hal ini machine learning datang sebagai solusi untuk menjawab permasalahan tersebut. Caranya adalah dengan mengumpulkan data-data terkait dengan penentuan harga rumah, semakin banyak sampel tentu akan semakin besar peluang machine untuk bisa belajar lebih baik dari data yang ada dan melakukan prediksi dengan semakin baik.

Referensi : Manasa J, Radha Gupta, "Machine Learning based Predicting House Prices using Regression Techniques"

## Business Understanding

Problem Statements :
1. Bagaimana melakukan prediksi harga rumah menggunakan alogoritma machine learning
2. Bagaimana cara melakukan feature engineering atau feature selection guna memilih feature yang berpengaruh terhadap harga rumah
3. Bagaimana teknik evaluasi untuk masalah prediksi harga rumah

Goals :
1. Menerapkan algoritma regresi pada machine learning seperti algoritma KNN dan Random Forest
2. Melakukan Exploratory Data Analysis (EDA) untuk menyeleksi feature
3. Menggunakan metrik evaluasi Mean Absolute Error (MSE) untuk permasalahan regresi

Solution Statement : Hal pertama yang perlu diperhatikan ini adalah masalah regresi, jadi kita akan menggunakan algoritma regresi pada machine learning, solusinya kita bisa menggunakan algoritma regresi KNN dan Random Forest, untuk melakukan feature engineering kita bisa menggunakan teknik Exploratory Data Analysis (EDA), dan metrik evaluasi yang akan kita gunakan adalah Mean Squared Error (MSE)

## Data Understanding

Disini saya menggunakan dataset [KC_Housesales_Data](https://www.kaggle.com/swathiachath/kc-housesales-data).
Dataset terdiri dari harga rumah dari King County sebuah area di Negara Bagian Washington AS, data ini juga mencakup Seattle. Dataset diperoleh dari Kaggle. Data ini diterbitkan/dirilis di bawah CC0: Domain Publik. Dataset terdiri dari 21 variabel dan 21.613 observasi

Variabel-variabel pada dataset tersebut adalah sebagai berikut:
id : notasi untuk rumah
date : tanggal Rumah tanggal dijual
price : Harga adalah target prediksi
bedrooms : Jumlah Kamar Tidur/Rumah
bathrooms : Jumlah kamar mandi/kamar
sqftliving : cuplikan persegi rumah
floors : Total lantai (tingkat) di rumah
waterfront : Rumah tepi laut yang memiliki pemandangan ke tepi laut
view : Telah dilihat
condition :  Seberapa baik kondisinya ( Secara Keseluruhan ). 1 menunjukkan properti usang dan 5 sangat baik
grade : grade keseluruhan yang diberikan kepada unit perumahan, berdasarkan sistem penilaian King County. 1 buruk, 13 sangat baik.
sqftabove : cuplikan persegi rumah terpisah dari ruang bawah tanah
sqftbasement :  cuplikan persegi ruang bawah tanah
yrbuilt : Tahun dibangun 
yrrenovated: Tahun ketika rumah direnovasi
zipcode : kode pos zip
lat : Latitude koordinat
long : Koordinat Bujur
sqftliving15 : Area ruang tamu pada tahun 2015(menyiratkan-- beberapa renovasi) Ini mungkin atau mungkin tidak memengaruhi area loteng
sqftlot15 : lotUkuran area pada 2015(menyiratkan-- beberapa renovasi)

Exploratory Data Analysis : Menangani Outliers
Pada beberapa data yang saya lakukan visualisasi terdapat data outliers seperti gambar dibawah 
![image](https://user-images.githubusercontent.com/50938896/156042655-cfac108b-d244-455d-aa62-52d5a275e23d.png)
untuk menangani data outliers ini saya menggunakan solusi dengan metode IQR. disini saya akan menggunakan metode IQR untuk mengidentifikasi outlier yang berada di luar Q1 dan Q3
![image](https://user-images.githubusercontent.com/50938896/156042971-7d8319c7-e1f9-4a7e-a6d6-dabaf95a4914.png)
Dapat terlihat data menjadi berkurang setelah melakukan penghapusan data outlier.

Disini saya juga memvisualisasikan Correlation Matrix untuk Menyeleksi Fitur Numerik.

## Data Preparation

Pada tahap ini saya membagi dataset menjadi data latih (train) dan data uji (test) dengan perbandingan 80:20.
Selanjutnya saya melakukan standarisasi membantu untuk membuat fitur data menjadi bentuk yang lebih mudah diolah oleh algoritma.
![image](https://user-images.githubusercontent.com/50938896/156043819-1ce59b06-387a-46bf-8448-c67a24757793.png)
Standarisasi yang saya gunakan adalah StandardScaler. StandardScaler melakukan proses standarisasi fitur dengan mengurangkan mean (nilai rata-rata) kemudian membaginya dengan standar deviasi untuk menggeser distribusi.

## Modeling

Perlu diperhatikan ini adalah masalah regresi, jadi saya akan menggunakan algoritma regresi pada machine learning, solusinya kita bisa menggunakan algoritma regresi seperti KNN dan Random Forest. 
Pada algoritma KNN Kita menggunakan k = 10 tetangga dan metric Euclidean untuk mengukur jarak antara titik. Algoritma KNN menggunakan ‘kesamaan fitur’ untuk memprediksi nilai dari setiap data yang baru,  algoritma KNN mudah dipahami dan digunakan.
Pada algoritma Random Forest saya menyetel hyperparameter n_estimators=50 dan max_depth=16. Algoritma Random forest merupakan salah satu model ML yang termasuk ke dalam kategori ensemble, yaitu model prediksi yang terdiri dari beberapa model dan bekerja secara bersama-sama. Ide dibalik model ensemble adalah sekelompok model yang bekerja bersama menyelesaikan masalah. Sehingga, tingkat keberhasilan akan lebih tinggi dibanding model yang bekerja sendirian.

## Evaluation

Metrik yang akan saya gunakan pada prediksi ini adalah MSE atau Mean Squared Error yang menghitung jumlah selisih kuadrat rata-rata nilai sebenarnya dengan nilai prediksi.

Hasil evaluasi pada data latih dan data test adalah sebagai berikut :
![image](https://user-images.githubusercontent.com/50938896/156045496-a263ea2d-ec07-4faa-99c1-9fc8fc062f5a.png)

Saya juga melakukan visualiasi terhadap hasil evaluasi:
![image](https://user-images.githubusercontent.com/50938896/156045639-2f119dca-665b-4a36-8eda-494de2991603.png)

Dari gambar di atas, terlihat bahwa, model Random Forest memberikan nilai eror yang paling kecil. Model random forest inilah yang akan kita pilih sebagai model terbaik untuk melakukan prediksi harga rumah
