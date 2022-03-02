# Laporan Proyek Machine Learning - Alfandi Firnando

## Domain Proyek

Memprediksi harga rumah

Permasalahan dari penelitian kali ini adalah bagaimana melakukan prediksi terhadap harga rumah, dalam menentukan harga rumah tentu sangat banyak feature/ciri yang mempengaruhi harga rumah mulai dari faktor internal maupun faktor eksternal, sebagai contoh jumlah ruangan di sebuah rumah pasti akan sangat berpengaruh terhadap harganya, selain itu letak posisi rumah secara geografis juga sangat menentukan harganya, misal terletak di kawasan bisnis perkotaan atau tidak. Oleh karena itu sangat dibutuhkan penelitian dari berbagai disiplin ilmu pengetahuan untuk menyelesaikan permasalahan dalam melakukan prediksi terhadap harga rumah, dalam hal ini machine learning datang sebagai solusi untuk menjawab permasalahan tersebut. Caranya adalah dengan mengumpulkan data-data terkait dengan penentuan harga rumah, semakin banyak sampel tentu akan semakin besar peluang machine untuk bisa belajar lebih baik dari data yang ada dan melakukan prediksi dengan semakin baik.

Referensi: [Machine Learning based Predicting House Prices using Regression Techniques](https://ieeexplore.ieee.org/abstract/document/9074952)

## Business Understanding

Problem Statements :
- Bagaimana melakukan prediksi harga rumah menggunakan alogoritma machine learning
- Bagaimana cara melakukan feature engineering atau feature selection guna memilih feature yang berpengaruh terhadap harga rumah
- Bagaimana teknik evaluasi untuk masalah prediksi harga rumah

Goals :
- Untuk melakukan prediksi harga rumah menggunakan algoritma machine learning
- Untuk melakukan feature engineering pada dataset prediksi harga rumah
- Untuk menggunakan metrik evaluasi pada prediksi harga rumah

Solution Statement : 

- Hal pertama yang perlu diperhatikan ini adalah masalah regresi, jadi kita akan menggunakan algoritma regresi pada machine learning
- Menggunakan algoritma regresi seperti KNN dan Random Forest
- Melakukan feature engineering menggunakan teknik Exploratory Data Analysis (EDA)
- Metrik evaluasi yang akan kita gunakan adalah Mean Squared Error (MSE)

## Data Understanding

Disini saya menggunakan dataset [KC_Housesales_Data](https://www.kaggle.com/swathiachath/kc-housesales-data).
Dataset terdiri dari harga rumah dari King County sebuah area di Negara Bagian Washington AS, data ini juga mencakup Seattle. Dataset diperoleh dari Kaggle. Data ini diterbitkan/dirilis di bawah CC0: Domain Publik. Dataset terdiri dari 21 variabel dan 21.613 observasi

Variabel-variabel pada dataset tersebut adalah sebagai berikut:
- id : notasi untuk rumah
- date : tanggal Rumah dijual
- price : Harga adalah target prediksi
- bedrooms : Jumlah Kamar Tidur/Rumah
- bathrooms : Jumlah kamar mandi/kamar
- sqftliving : cuplikan persegi rumah
- floors : Total lantai (tingkat) di rumah
- waterfront : Rumah tepi laut yang memiliki pemandangan ke tepi laut
- view : Telah dilihat
- condition :  Seberapa baik kondisinya ( Secara Keseluruhan ). 1 menunjukkan properti usang dan 5 sangat baik
- grade : grade keseluruhan yang diberikan kepada unit perumahan, berdasarkan sistem penilaian King County. 1 buruk, 13 sangat baik.
- sqftabove : cuplikan persegi rumah terpisah dari ruang bawah tanah
- sqftbasement :  cuplikan persegi ruang bawah tanah
- yrbuilt : Tahun dibangun 
- yrrenovated: Tahun ketika rumah direnovasi
- zipcode : kode pos zip
- lat : Latitude koordinat
- long : Koordinat Bujur
- sqftliving15 : Area ruang tamu pada tahun 2015(menyiratkan-- beberapa renovasi) Ini mungkin atau mungkin tidak memengaruhi area loteng
- sqftlot15 : lotUkuran area pada 2015(menyiratkan-- beberapa renovasi)

Data Outliers :

Pada beberapa data yang saya lakukan visualisasi terdapat data outliers seperti gambar dibawah

![image](https://user-images.githubusercontent.com/50938896/156042655-cfac108b-d244-455d-aa62-52d5a275e23d.png)

- Correlation Matrix :

Disini saya juga memvisualisasikan Correlation Matrix untuk menyeleksi feature numerik

![image](https://user-images.githubusercontent.com/50938896/156177747-525a0c5a-d7af-4555-a6ac-b1bc67329a70.png)

Penanganan untuk data outliers dan seleksi feature numerik berdasarkan correlation matrix akan lebih lanjut dibahas pada bagian data preparation

## Data Preparation

Exploratory Data Analysis : 

- Drop columns :

Diawal saya memutuskan untuk melakukan drop columns pada kolom "id" dan "date", karena menurut saya kedua feature ini tidak memberi informasi yang cukup penting untuk untuk melakukan analisa regresi linear. Feature "date" atau data tanggal penjualan rumah diambil dari tahun mei 2014 sampai mei 2015 sehingga perubahan waktu ini tidak akan berdampak signifikan terhadap prediksi harga rumah.

![image](https://user-images.githubusercontent.com/50938896/156179844-783b1202-23f6-4693-9440-591b10ef68c2.png)

- Menangani Outliers :

Untuk menangani data outliers ini saya menggunakan solusi dengan metode IQR. disini saya akan menggunakan metode IQR untuk mengidentifikasi outlier yang berada di luar Q1 dan Q3

![image](https://user-images.githubusercontent.com/50938896/156042971-7d8319c7-e1f9-4a7e-a6d6-dabaf95a4914.png)

Dapat terlihat data menjadi berkurang setelah melakukan penghapusan data outlier.

- Correlation Matrix :

Pada Correlation Matrix kita bisa melihat hubungan korelasi antar fitur. 

Koefisien korelasi berkisar antara -1 dan +1. Ia mengukur kekuatan hubungan antara dua variabel serta arahnya (positif atau negatif). Mengenai kekuatan hubungan antar variabel, semakin dekat nilainya ke 1 atau -1, korelasinya semakin kuat. Sedangkan, semakin dekat nilainya ke 0, korelasinya semakin lemah.

Oleh karena itu saya melakukan drop columns terhadap feature yang korelasinya lemah. Berikut adalah daftar feature yang saya drop.

![image](https://user-images.githubusercontent.com/50938896/156178411-bce53fdd-b3ad-42af-abe5-0888ff7de02c.png)

- Train Test Split :

Pada tahap ini saya membagi dataset menjadi data latih (train) dan data uji (test) dengan perbandingan 80:20.

- Standarisasi :

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

![image](https://user-images.githubusercontent.com/50938896/156216244-082b218a-afbe-4260-98f4-f7bc2c4e1c61.png)

Saya juga melakukan visualiasi terhadap hasil evaluasi:

![image](https://user-images.githubusercontent.com/50938896/156216301-f5e32d8a-3c59-4605-9ea8-8634ccc49484.png)

Dari gambar di atas, terlihat bahwa, model Random Forest memberikan nilai eror yang paling kecil. Model random forest inilah yang akan kita pilih sebagai model terbaik untuk melakukan prediksi harga rumah
