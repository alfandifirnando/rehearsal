# Laporan Proyek Machine Learning - Alfandi Firnando

## Domain Proyek

Rekomendasi film

Menonton film merupakan cara sebagian orang untuk menghibur diri dan mengusir kebosanan, semua orang ingin menonton film bagus yang memiliki konten hebat. Tapi sayangnya kebanyakan dari orang-orang ini banyak membuang waktu untuk mencari film yang sesuai dengan preferensi dan keinginan mereka. Salah satu solusinya adalah membuat sistem rekomendasi film. Membangun sistem rekomendasi selalu menjadi hal yang menarik dan menjadi tantangan bagi para peneliti. Pada penelitian kali ini akan fokus kepada masalah rekomendasi film, yaitu bagaimana cara merekomendasikan film yang tepat kepada pengguna. Memberikan rekomendasi film bisa dilakukan berdasarkan konten yang mirip antara satu film dengan film yang lain, tantangannya adalah bagaimana caranya mendefenisikan kemiripan konten tersebut. Kemiripannya berdasarkan konten apa, misalnya berdasarkan kategori film, genre,synopsis, kemiripan keyword atau konten yang lain. Semua hal ini tentu akan menjadi tantangan sendiri tentang bagaimana memberikan rekomendasi film secara baik dan tepat. Oleh karena itu sangat dibutuhkan penelitian untuk merekomendasikan film dengan baik dan tepat, teknik machine learning sangat mendukung untuk penyelesaian masalah ini.

Referensi: [Movie recommendation system using enhanced content-based filtering algorithm based on user demographic data](https://ieeexplore.ieee.org/document/9489125)

## Business Understanding

Problem Statements :
- Bagaimana membangun sistem rekomendasi film dengan machine learning
- Bagaimana cara mengembangkan sistem rekomendasi film dengan pendekatan content based filtering

Goals :
- Untuk membangun sistem rekomendasi film dengan machine learning
- Untuk mengembangkan sistem rekomendasi film dengan pendekatan content based filtering

Solution Statement : 

- Mengidentifikasi content mana yang paling berpengaruh terhadap kemiripan rekomendasi film
- kita akan menghitung derajat kesamaan (similarity degree) antar content film dengan teknik cosine similarity

## Data Understanding

Disini saya menggunakan dataset [Film Recommendation content_by_synopsis](https://github.com/WiraDKP/recommendation_system/tree/master/20%20-%20Recommendation%20System/data).

Variabel-variabel pada dataset tersebut adalah sebagai berikut:
- title : berisi judul film
- overview : berisi synopsis/overview yaitu penjelasan terhadap film secara singkat

## Data Preparation


## Modeling


## Evaluation

Metrik yang akan saya gunakan pada prediksi ini adalah MSE atau Mean Squared Error yang menghitung jumlah selisih kuadrat rata-rata nilai sebenarnya dengan nilai prediksi.

Berikkut adalah formula dari MSE 

![image](https://user-images.githubusercontent.com/50938896/156517755-8f8afad0-5768-456f-badc-d9eb85cfbe25.png)

dengan keterangan sebagai berikut :

N = jumlah dataset

yi = nilai sebenarnya

y_pred = nilai prediksi

Hasil evaluasi pada data latih dan data test adalah sebagai berikut :

![image](https://user-images.githubusercontent.com/50938896/156216244-082b218a-afbe-4260-98f4-f7bc2c4e1c61.png)

Saya juga melakukan visualiasi terhadap hasil evaluasi:

![image](https://user-images.githubusercontent.com/50938896/156518104-b9e07436-108e-4a2c-b33b-79f556d53564.png)

Dari gambar di atas, terlihat bahwa, model Random Forest memberikan nilai eror yang paling kecil. Model random forest inilah yang akan kita pilih sebagai model terbaik untuk melakukan prediksi harga rumah
