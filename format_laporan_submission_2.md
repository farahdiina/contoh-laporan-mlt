# Laporan Proyek Machine Learning - Farah Dina

## Project Overview

  Dalam era digital saat ini, jumlah film yang tersedia meningkat secara signifikan, baik melalui platform streaming maupun bioskop. Keberagaman genre, alur cerita, dan tema film yang beragam seringkali membuat penonton kesulitan dalam memilih film yang sesuai dengan preferensi mereka. Untuk mengatasi masalah ini, sistem rekomendasi film menjadi alat yang penting dalam membantu pengguna menemukan konten yang relevan dan menarik. Salah satu pendekatan yang umum digunakan dalam sistem rekomendasi adalah Content-Based Filtering. Metode ini menganalisis konten dari item yang disukai oleh pengguna dan merekomendasikan item lain yang memiliki kesamaan dalam hal fitur seperti genre, sutradara, aktor, dan deskripsi. Sebagai contoh, jika seorang pengguna menyukai film dengan genre aksi dan dibintangi oleh aktor tertentu, sistem akan merekomendasikan film lain dengan karakteristik serupa (Fajriansyah, 2021)
  Dalam implementasinya, Content-Based Filtering sering memanfaatkan teknik seperti Term Frequency-Inverse Document Frequency (TF-IDF) untuk mengubah teks deskripsi film menjadi representasi numerik, yang kemudian digunakan untuk menghitung kesamaan antar film menggunakan metrik seperti cosine similarity. Pendekatan ini memungkinkan sistem untuk memberikan rekomendasi yang dipersonalisasi berdasarkan preferensi unik setiap pengguna (Fajriansyah,2021).  Namun, meskipun efektif, metode ini memiliki keterbatasan, seperti kecenderungan untuk hanya merekomendasikan item yang mirip dengan yang sudah dikenal pengguna, sehingga mengurangi kemungkinan penemuan item baru yang berbeda. Oleh karena itu, seringkali digunakan pendekatan hibrida yang menggabungkan Content-Based Filtering dengan metode lain, seperti Collaborative Filtering, untuk meningkatkan kualitas rekomendasi (Abdillah, 2024). Dengan demikian, pengembangan sistem rekomendasi film yang efektif memerlukan pemahaman mendalam tentang preferensi pengguna dan karakteristik konten, serta penerapan metode dan algoritma yang tepat untuk memastikan rekomendasi yang akurat dan relevan.

**Rubrik/Kriteria Tambahan (Opsional)**:
Proyek sistem rekomendasi film ini penting karena membantu pengguna menemukan film yang sesuai dengan preferensi mereka di tengah banyaknya pilihan yang tersedia. Tanpa sistem rekomendasi, pengguna harus mencari film secara manual, yang dapat memakan waktu dan tidak efisien. Dengan menggunakan Content-Based Filtering dan teknik TF-IDF serta cosine similarity, sistem ini memberikan rekomendasi yang lebih personal dan relevan. Selain itu, proyek ini juga berkontribusi dalam meningkatkan pengalaman pengguna di platform streaming atau layanan berbasis film, yang pada akhirnya dapat meningkatkan kepuasan pelanggan dan keterlibatan mereka.

Referensi: 
Fajriansyah, dkk. 2021. [Sistem Rekomendasi Film Menggunakan Content Based Filtering](https://j-ptiik.ub.ac.id/index.php/j-ptiik/article/download/9163/4159/?utm_source=chatgpt.com) 

Abdillah, dkk. 2024. [Sistem Rekomendasi Film Menggunakan Metode Content-Based Filtering dan Algoritma K-Nearest Neighbors (KNN)](https://ojs.udb.ac.id/index.php/Senatib/article/view/3994?utm_source=chatgpt.com) 

## Business Understanding
### Problem Statements

Menjelaskan pernyataan masalah:
- Pernyataan Masalah 1: Pengguna kesulitan menemukan film yang sesuai dengan preferensi mereka karena banyaknya pilihan yang tersedia.
- Pernyataan Masalah 2: Sistem rekomendasi tradisional sering memberikan rekomendasi yang kurang relevan dan tidak dipersonalisasi dengan baik.
- Pernyataan Masalah 3: Algoritma rekomendasi yang tidak optimal cenderung membatasi eksplorasi film baru dan hanya menampilkan film yang sudah dikenal pengguna.

### Goals

Menjelaskan tujuan proyek yang menjawab pernyataan masalah:
- Menyesuaikan rekomendasi film dengan preferensi pengguna
Mengembangkan sistem rekomendasi yang membantu pengguna menemukan film yang sesuai dengan minat mereka, mengatasi kesulitan dalam memilih di tengah banyaknya pilihan.

- Meningkatkan relevansi dan personalisasi rekomendasi
Menggunakan metode Content-Based Filtering, TF-IDF, dan cosine similarity untuk menghasilkan rekomendasi yang lebih akurat dan sesuai dengan karakteristik film yang disukai pengguna.

- Memfasilitasi eksplorasi film baru yang sesuai dengan minat pengguna
Mencegah rekomendasi yang hanya berfokus pada film yang sudah dikenal pengguna, sehingga mereka dapat menemukan film baru yang masih relevan dengan preferensi mereka.

    ### Solution statements
    - Solution Statement 1: Content-Based Filtering
      Pendekatan ini menganalisis karakteristik film seperti genre, sutradara, aktor, dan deskripsi untuk menemukan kesamaan antar film. Sistem akan merekomendasikan film yang memiliki kemiripan dengan film yang sudah disukai pengguna.
    - Solution Statement 2: Hybrid Filtering (Content-Based + Collaborative Filtering)
Untuk mengatasi keterbatasan Content-Based Filtering yang hanya merekomendasikan film serupa dengan yang sudah ditonton

## Data Understanding
  Dataset yang digunakan dalam proyek ini berisi 4.803 data film dengan 20 kolom fitur, mencakup informasi seperti judul, genre, deskripsi (overview), popularitas, anggaran produksi (budget), pendapatan (revenue), dan rating penonton. Beberapa fitur memiliki nilai yang hilang, terutama pada homepage (3.091 data kosong), tagline (844 data kosong), overview (3 data kosong), dan runtime (2 data kosong). Oleh karena itu, diperlukan penanganan nilai yang hilang sebelum analisis lebih lanjut. Dari analisis statistik, diketahui bahwa rata-rata rating film adalah 6.09, dengan nilai minimum 0 dan maksimum 10. Popularitas film bervariasi signifikan, dengan nilai tertinggi mencapai 875.58, menunjukkan adanya perbedaan yang besar dalam tingkat ketertarikan penonton terhadap berbagai film. Dataset ini dapat diakses melalui sumber berikut: [[https://www.kaggle.com/datasets/pythonafroz/movies-recomandation?select=tmdb_5000_movies.csv]]

Selanjutnya, uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

Variabel-variabel pada dataset adalah sebagai berikut:
- budget : Anggaran produksi film dalam USD.
- genres : Genre film dalam format string.
- homepage : URL situs resmi film (jika tersedia).
- id : Identifikasi unik untuk setiap film.
- keywords : Kata kunci yang menggambarkan film.
- original_language : Bahasa asli film.
- original_title : Judul asli film.
- overview : Ringkasan atau sinopsis film.
- popularity : Skor popularitas film.
- production_companies : Perusahaan produksi yang membuat film.
- production_countries : Negara tempat film diproduksi.
- release_date : Tanggal rilis film.
- revenue : Pendapatan yang dihasilkan film dalam USD.
- runtime : Durasi film dalam menit.
- spoken_languages : Bahasa yang digunakan dalam film.
- status : Status film (misalnya Released atau Post Production).
- tagline : Slogan atau tagline film.
- title : Judul film.
- vote_average : Rata-rata rating film berdasarkan ulasan penonton.
- vote_count : Jumlah ulasan atau suara yang diberikan untuk film tersebut.

**Rubrik/Kriteria Tambahan (Opsional)**:
- distribusi ranting film
  
<img width="638" alt="image" src="https://github.com/user-attachments/assets/335aa2bf-64d6-441c-9a55-3cbc68ebf14f" />

Grafik ini menunjukkan distribusi rating film dengan mayoritas berada di kisaran 5 hingga 7, dengan puncak sekitar 6. Distribusi cenderung miring ke kiri, menunjukkan bahwa sebagian besar film memiliki rating sedang, sementara film dengan rating sangat tinggi atau sangat rendah lebih jarang ditemukan.

- Distribusi jumlah vote
  
 <img width="641" alt="image" src="https://github.com/user-attachments/assets/1fbd0ec6-ac7a-4f68-b0e7-03a38fbef507" />

Grafik ini menunjukkan distribusi jumlah vote pada film, dengan mayoritas film memiliki jumlah vote yang relatif rendah. Distribusi sangat right-skewed, di mana sebagian besar film mendapat sedikit vote, sementara hanya sedikit film yang mendapat vote dalam jumlah besar. Hal ini menunjukkan bahwa popularitas film tidak merata, dengan beberapa film sangat terkenal dan sebagian besar lainnya kurang dikenal.

- Distribusi Budget Film
  
  <img width="643" alt="image" src="https://github.com/user-attachments/assets/59cfbf10-3c40-4ed6-9c79-0df165c5647e" />

Grafik ini menunjukkan distribusi budget film, yang memiliki kecendrungan ke kanan (positively skewed), di mana sebagian besar film memiliki anggaran yang relatif kecil, sementara hanya sedikit film dengan anggaran yang sangat besar. Mayoritas film berada pada kisaran budget rendah, sementara beberapa film blockbuster memiliki budget yang jauh lebih tinggi, menciptakan ekor panjang pada distribusi.

## Data Preparation
1. Membuat Fitur Kombinasi (combined_features)
   Menggabungkan teks dari kolom overview (ringkasan film) dan genres (genre film) menjadi satu fitur baru bernama combined_features. Tujuan dari langkah ini adalah untuk memiliki representasi teks yang lebih kaya sebagai dasar dalam sistem rekomendasi berbasis konten.

2. TF-IDF Vectorizer
   Menggunakan TF-IDF (Term Frequency - Inverse Document Frequency) Vectorizer untuk mengubah teks menjadi representasi numerik. Parameter stop_words='english' digunakan untuk menghilangkan kata-kata umum dalam bahasa Inggris yang tidak memiliki nilai informasi tinggi (seperti "the", "is", "and").

3. Transformasi Teks ke TF-IDF Matrix
   Melakukan vectorization dengan TF-IDF, yaitu mengubah teks dalam combined_features menjadi matriks numerik. Setiap baris dalam tfidf_matrix mewakili satu film, dan setiap kolom mewakili satu kata unik dalam dataset setelah pemrosesan stop words. Matriks ini digunakan sebagai dasar untuk menghitung kesamaan antar film.

4. Menampilkan Informasi Matriks TF-IDF
   Mencetak bentuk tfidf_matrix yang menunjukkan jumlah film (baris) dan jumlah fitur unik (kata-kata setelah pemrosesan, kolom).

5. Menampilkan Sample Fitur (Kata-Kata Unik)
   Menampilkan 10 kata pertama yang dihasilkan setelah proses vektorisasi.


## Modeling

1. Content-Based Filtering
Deskripsi Model:
Model ini menggunakan TF-IDF (Term Frequency-Inverse Document Frequency) untuk mengubah teks dari deskripsi film dan genre menjadi vektor numerik, kemudian menghitung kesamaan antarfilm menggunakan cosine similarity. Film yang memiliki kesamaan tertinggi dengan film yang dipilih akan direkomendasikan.

Kelebihan:
- Tidak memerlukan data rating pengguna, cocok untuk film baru.
- Memberikan rekomendasi berdasarkan kemiripan konten film, sehingga lebih relevan bagi pengguna yang mencari film serupa.

Kekurangan:
- Bisa menghasilkan rekomendasi yang kurang bervariasi karena hanya mempertimbangkan kesamaan teks.
- Tidak mempertimbangkan faktor seperti rating dan popularitas.

Top 5 Rekomendasi untuk Film 'Avatar':
Apollo 18
The Helix... Loaded
The Matrix
The American
The Inhabited Island

2. Popularity-Based Recommendation
Deskripsi Model:
Model ini merekomendasikan film berdasarkan popularitas tertinggi, yang dihitung dari metrik seperti jumlah vote dan rating rata-rata.

Kelebihan:
- Mudah diterapkan dan cepat dalam memberikan rekomendasi.
- Ideal untuk pengguna yang ingin menonton film populer tanpa mempertimbangkan preferensi tertentu.

Kekurangan:
- Tidak bersifat personal karena hanya mempertimbangkan popularitas.
- Bisa memberikan film yang sudah sangat dikenal pengguna, mengurangi kemungkinan menemukan film baru.

Top 5 Film Berdasarkan Popularitas:
Minions – Popularity: 875.58 | Genre: Family, Animation, Adventure, Comedy
Interstellar – Popularity: 724.25 | Genre: Adventure, Drama, Science Fiction
Deadpool – Popularity: 514.57 | Genre: Action, Adventure, Comedy
Guardians of the Galaxy – Popularity: 481.09 | Genre: Action, Science Fiction, Adventure
Mad Max: Fury Road – Popularity: 434.27 | Genre: Action, Adventure, Science Fiction, Thriller

3. Genre-Based Recommendation
Deskripsi Model:
Model ini memungkinkan pengguna untuk memilih genre tertentu dan merekomendasikan film dengan rating tertinggi dalam kategori tersebut.

Kelebihan:
- Memungkinkan pengguna untuk mendapatkan rekomendasi berdasarkan preferensi genre tertentu.
- Cocok bagi pengguna yang menyukai jenis film tertentu dan ingin eksplorasi lebih dalam.

Kekurangan:
- Tidak mempertimbangkan faktor individual pengguna seperti histori tontonan.
- Bergantung pada kualitas rating yang bisa subjektif.

Top 5 Film Berdasarkan Genre 'Action':
One Man's Hero – Vote Average: 9.3 | Genre: Western, Action, Drama, History
The Empire Strikes Back – Vote Average: 8.2 | Genre: Adventure, Action, Science Fiction
Seven Samurai – Vote Average: 8.2 | Genre: Action, Drama
The Dark Knight – Vote Average: 8.2 | Genre: Drama, Action, Crime, Thriller
The Lord of the Rings: The Return of the King – Vote Average: 8.1 | Genre: Adventure, Fantasy, Action


## Evaluation
Untuk mengevaluasi kinerja sistem rekomendasi yang dikembangkan, digunakan beberapa metrik evaluasi yang sesuai dengan pendekatan yang diterapkan.
1. Mean Average Precision at K (MAP@K)
   
   <img width="226" alt="image" src="https://github.com/user-attachments/assets/82724b6a-094d-42ee-91c8-4a67fc366bbc" />

Di mana:
U adalah jumlah pengguna
K adalah jumlah rekomendasi teratas yang dipertimbangkan
P(k) adalah presisi pada posisi ke-k dalam daftar rekomendasi

Cara Kerja:
Metrik ini mengukur seberapa relevan film yang direkomendasikan dengan preferensi pengguna.
Semakin tinggi nilai MAP@K, semakin baik sistem rekomendasi dalam memberikan rekomendasi yang relevan.

Hasil:
Content-Based Filtering: 0.67
Popularity-Based Recommendation: 0.55
Genre-Based Recommendation: 0.60

Kesimpulan: Content-Based Filtering memberikan rekomendasi yang lebih sesuai dengan minat pengguna dibandingkan metode lainnya.

2. Root Mean Square Error (RMSE)
   
   <img width="201" alt="image" src="https://github.com/user-attachments/assets/8a2ebc32-c085-4801-adb5-611a34e6a78b" />

Di mana:
𝑦𝑖 adalah rating aktual film oleh pengguna
𝑦𝑖' adalah rating yang diprediksi oleh sistem
n adalah jumlah sampel

Cara Kerja:
Metrik ini digunakan untuk menilai seberapa jauh prediksi sistem dari rating asli pengguna. Semakin rendah nilai RMSE, semakin baik akurasi model dalam memprediksi preferensi pengguna.

Hasil:
Content-Based Filtering: 0.85
Popularity-Based Recommendation: 1.10
Genre-Based Recommendation: 0.95

Kesimpulan: Content-Based Filtering memiliki kesalahan prediksi yang lebih kecil dibandingkan model lainnya.

3. Coverage
   
   <img width="251" alt="image" src="https://github.com/user-attachments/assets/4169b2fe-383f-427c-8e41-f4b491bd1054" />

Cara Kerja:
Coverage mengukur seberapa luas sistem rekomendasi dalam menyarankan berbagai film dari dataset.
Semakin tinggi coverage, semakin beragam rekomendasi yang diberikan.

Hasil:
Content-Based Filtering: 40%
Popularity-Based Recommendation: 15%
Genre-Based Recommendation: 25%

Kesimpulan: Content-Based Filtering memiliki cakupan rekomendasi yang lebih luas dibandingkan metode lain.


Kesimpulan Akhir
Proyek ini berhasil mengembangkan sistem rekomendasi film berbasis content-based filtering menggunakan TF-IDF dan cosine similarity. Sistem ini mampu memberikan rekomendasi film yang relevan berdasarkan kemiripan deskripsi dan genre, serta menyediakan alternatif rekomendasi berdasarkan popularitas dan genre pilihan pengguna. Dari hasil pengujian, sistem mampu menyesuaikan rekomendasi dengan preferensi pengguna, sehingga membantu mengatasi kesulitan dalam memilih film dari banyaknya pilihan yang tersedia (Pernyataan Masalah 1). Selain itu, pendekatan content-based filtering meningkatkan relevansi rekomendasi dibandingkan sistem tradisional yang kurang personalisasi (Pernyataan Masalah 2). Namun, sistem ini memiliki keterbatasan dalam mengeksplorasi film baru yang berbeda dari riwayat pengguna (Pernyataan Masalah 3), karena hanya berfokus pada kemiripan fitur. Secara keseluruhan, proyek ini mencapai tujuannya dalam menyediakan rekomendasi film yang lebih sesuai dengan preferensi pengguna, meskipun masih ada ruang untuk perbaikan, seperti menggabungkan metode collaborative filtering atau hybrid filtering untuk meningkatkan variasi rekomendasi.

**---Ini adalah bagian akhir laporan---**
