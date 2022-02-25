Memprediksi harga rumah

Permasalahan dari penelitian kali ini adalah bagaimana melakukan prediksi terhadap harga rumah, dalam menentukan harga rumah tentu sangat banyak feature/ciri yang mempengaruhi harga rumah mulai dari faktor internal maupun faktor eksternal, sebagai contoh jumlah ruangan di sebuah rumah pasti akan sangat berpengaruh terhadap harganya, selain itu letak posisi rumah secara geografis juga sangat menentukan misalnya terletak di kawasan bisnis perkotaan atau tidak faktor lain yang mempengaruhi antara lain adalah tingkat kriminalitas, oleh karena itu sangat dibutuhkan penelitian dari berbagai disiplin ilmu pengetahuan untuk menyelesaikan permasalahan dalam melakukan prediksi terhadap harga rumah, machine learning datang sebagai solusi untuk menjawab permasalahan ini.

Perlu diingat masalah kali ini adalah masalah regresi, jadi kita akan menggunakan algorima regresi pada machine learning

Berikut adalah penjelasan dari setiap fitur dataset.

Melakukan plot missing value untuk melihat apakah terdapat data yang bernilai kosong

Membagi dataset menjadi data training dan testing

disini saya melakukan set hyperparameter pada algoritma random forest mulai dari max_depth sampai min samples leaf

Membuat prepocessor untuk memisahkan feature numeric dan categoric

Serta membuat pipeline dimana data yang sudah di proces di preprocessor tadi akan di training menggunakan algoritma Random Forest Regressor
