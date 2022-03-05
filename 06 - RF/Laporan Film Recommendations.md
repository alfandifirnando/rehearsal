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

Variabel-variabel pada dataset tersebut adalah sebagai berikut:
- title : berisi judul film
- overview : berisi synopsis/overview yaitu penjelasan terhadap film secara singkat

## Data Preparation
- Melakukan encode terhadap keseluruhan feature overview pada dataset
- Encode overview untuk film index ke-0 yaitu film Toy Story (Rekomendasi akan dilakukan berdasarkan film ini)

## Modeling

- Pada tahap ini kita akan menghitung derajat kesamaan (similarity degree) antar content synopsis/overview film dengan teknik cosine distances

## Evaluation

- Memberi top 10 rekomendasi film berdasarkan kemiripan content sinopsis untuk film index ke-0

![image](https://user-images.githubusercontent.com/50938896/156879779-c68a7faf-8842-4d4b-a63e-cfb0727363ef.png)

Dapat kita lihat sistem berhasil memberikan sistem rekomendasi berupa Top 10 rekomendasi film berdasarkan film Toy story yang kita inputkan, terlihat sistem memberikan rekomendasi film Toy Story 2 dan Toy Story 3

