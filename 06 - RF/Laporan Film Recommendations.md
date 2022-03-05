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
- Menghitung derajat kesamaan (similarity degree) antar content film dengan teknik cosine similarity

## Data Understanding

Disini saya menggunakan dataset [Film Recommendation content_by_synopsis](https://github.com/WiraDKP/recommendation_system/tree/master/20%20-%20Recommendation%20System/data).
Dataset berisi informasi tentang judul film dan overview yang berisi synopsis singkat mengenai isi film. Dataset berjumlah 41362 raw baris data data dan 2 variabel, setiap kolom data berisi lengkap tanpa adanya mising value pada data. 

Variabel-variabel pada dataset tersebut adalah sebagai berikut:
- title : berisi judul film
- overview : berisi synopsis/overview yaitu penjelasan terhadap film secara singkat

## Data Preparation

- Encode Feature :
Menyandikan (encode) feature 'overview' ke dalam indeks integer (bentuk matrix)

Melakukan encode terhadap keseluruhan feature overview pada dataset dan melakukan encode overview untuk film index ke-0 yaitu film Toy Story (Rekomendasi akan dilakukan berdasarkan film ini) 

## Modeling

- Pada tahap ini kita akan menghitung derajat kesamaan (similarity degree) antar content synopsis/overview dengan judul film yang sudah di encode dengan teknik cosine distances. Pada kasus ini cosine distances digunakan untuk menghitung tingkat kesamaan feature 'title' dengan 'overview'.
- Memberi top 5 rekomendasi film berdasarkan kemiripan content sinopsis untuk film index ke-0

![image](https://user-images.githubusercontent.com/50938896/156892694-e45f600e-e741-4e53-8761-97a474f3abb7.png)

Sistem memberikan rekomendasi film berdasarkan tingkat kesamaan antara feature overview satu judul film dengan film yang lain. Dapat kita lihat sistem berhasil memberikan sistem rekomendasi berupa Top 5 rekomendasi film berdasarkan film Toy Story yang kita inputkan, terlihat sistem memberikan rekomendasi film Toy Story 2 dan Toy Story 3


## Evaluation

-  Metrik precision :
Pada kasus ini metrik yang digunakan adalah metric precision, berikut formulanya :

![image](https://user-images.githubusercontent.com/50938896/156893250-e5d65214-58dc-40a5-a45e-9c2181191198.png)

Berdasarkan 5 item rekomendasi film yang diberikan, terdapat 2 item film memiliki tingkat kesamaan yang berkaitan satu sama lain yaitu item film Toy Story 2 dan Toy Story 3.
Jadi didapatkan hasil precision = 3/5, jadi presisinya 40 %
Jika kita perhatikan item film lain yang direkomendasikan mengandung kata 'Andy', sistem sepertinya menganggap ini fitur yang penting padahal dari judul film tidak ada keterkaitan. jadi dapat disimpulkan ini menjadi salah satu kelemahan dari teknik content-filtering


