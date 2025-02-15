# Laporan Proyek Machine Learning - Farah Dina

## Project Overview

  Dalam era digital saat ini, jumlah film yang tersedia meningkat secara signifikan, baik melalui platform streaming maupun bioskop. Keberagaman genre, alur cerita, dan tema film yang beragam seringkali membuat penonton kesulitan dalam memilih film yang sesuai dengan preferensi mereka. Untuk mengatasi masalah ini, sistem rekomendasi film menjadi alat yang penting dalam membantu pengguna menemukan konten yang relevan dan menarik. Salah satu pendekatan yang umum digunakan dalam sistem rekomendasi adalah Content-Based Filtering. Metode ini menganalisis konten dari item yang disukai oleh pengguna dan merekomendasikan item lain yang memiliki kesamaan dalam hal fitur seperti genre, sutradara, aktor, dan deskripsi. Sebagai contoh, jika seorang pengguna menyukai film dengan genre aksi dan dibintangi oleh aktor tertentu, sistem akan merekomendasikan film lain dengan karakteristik serupa (Fajriansyah, 2021)
  Dalam implementasinya, Content-Based Filtering sering memanfaatkan teknik seperti Term Frequency-Inverse Document Frequency (TF-IDF) untuk mengubah teks deskripsi film menjadi representasi numerik, yang kemudian digunakan untuk menghitung kesamaan antar film menggunakan metrik seperti cosine similarity. Pendekatan ini memungkinkan sistem untuk memberikan rekomendasi yang dipersonalisasi berdasarkan preferensi unik setiap pengguna (Fajriansyah,2021).  Namun, meskipun efektif, metode ini memiliki keterbatasan, seperti kecenderungan untuk hanya merekomendasikan item yang mirip dengan yang sudah dikenal pengguna, sehingga mengurangi kemungkinan penemuan item baru yang berbeda. Oleh karena itu, seringkali digunakan pendekatan hibrida yang menggabungkan Content-Based Filtering dengan metode lain, seperti Collaborative Filtering, untuk meningkatkan kualitas rekomendasi (Abdillah, 2024). Dengan demikian, pengembangan sistem rekomendasi film yang efektif memerlukan pemahaman mendalam tentang preferensi pengguna dan karakteristik konten, serta penerapan metode dan algoritma yang tepat untuk memastikan rekomendasi yang akurat dan relevan.

Proyek sistem rekomendasi film ini penting karena membantu pengguna menemukan film yang sesuai dengan preferensi mereka di tengah banyaknya pilihan yang tersedia. Tanpa sistem rekomendasi, pengguna harus mencari film secara manual, yang dapat memakan waktu dan tidak efisien. Dengan menggunakan Content-Based Filtering dan teknik TF-IDF serta cosine similarity, sistem ini memberikan rekomendasi yang lebih personal dan relevan. Selain itu, proyek ini juga berkontribusi dalam meningkatkan pengalaman pengguna di platform streaming atau layanan berbasis film, yang pada akhirnya dapat meningkatkan kepuasan pelanggan dan keterlibatan mereka.

Referensi: 
Fajriansyah, dkk. 2021. [Sistem Rekomendasi Film Menggunakan Content Based Filtering](https://j-ptiik.ub.ac.id/index.php/j-ptiik/article/download/9163/4159/?utm_source=chatgpt.com) 

Abdillah, dkk. 2024. [Sistem Rekomendasi Film Menggunakan Metode Content-Based Filtering dan Algoritma K-Nearest Neighbors (KNN)](https://ojs.udb.ac.id/index.php/Senatib/article/view/3994?utm_source=chatgpt.com) 

## Business Understanding
### Problem Statements

Menjelaskan pernyataan masalah:
- Pernyataan Masalah 1: Pengguna kesulitan menemukan film yang sesuai dengan preferensi mereka karena banyaknya pilihan yang tersedia.
- Pernyataan Masalah 2: Algoritma rekomendasi yang tidak optimal cenderung membatasi eksplorasi film baru dan hanya menampilkan film yang sudah dikenal pengguna.

### Goals

Menjelaskan tujuan proyek yang menjawab pernyataan masalah:
- Menyesuaikan rekomendasi film dengan preferensi pengguna
Mengembangkan sistem rekomendasi yang membantu pengguna menemukan film yang sesuai dengan minat mereka, mengatasi kesulitan dalam memilih di tengah banyaknya pilihan.

- Meningkatkan relevansi dan personalisasi rekomendasi
Menggunakan metode Content-Based Filtering, TF-IDF, dan cosine similarity untuk menghasilkan rekomendasi yang lebih akurat dan sesuai dengan karakteristik film yang disukai pengguna.

- Memfasilitasi eksplorasi film baru yang sesuai dengan minat pengguna
Mencegah rekomendasi yang hanya berfokus pada film yang sudah dikenal pengguna, sehingga mereka dapat menemukan film baru yang masih relevan dengan preferensi mereka.

    ### Solution statements
  Solution Statement: Content-Based Filtering
  Pendekatan ini menganalisis karakteristik film seperti genre, sutradara, aktor, dan deskripsi untuk menemukan kesamaan antar film. Sistem akan merekomendasikan film yang memiliki kemiripan dengan film yang sudah disukai pengguna.
    
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

Exploratory Data Analysis
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
1. Menangani Missing Values
  Mengisi nilai kosong (NaN) pada kolom overview, genres, dan release_date agar tidak menyebabkan error saat analisis data.
- Kolom overview diisi dengan string kosong '' agar tetap bisa diproses dalam analisis teks.
- Kolom genres diisi dengan string '[]' agar tetap berbentuk list kosong dalam string.
- Kolom release_date diisi dengan tanggal default '1900-01-01' untuk menghindari nilai kosong pada data waktu.
- Mengonversi release_date ke format datetime agar mudah digunakan dalam analisis berbasis waktu.

2. Membuat Fitur Kombinasi (combined_features)
  Fungsi process_genres() digunakan untuk memproses data genre yang berbentuk string JSON-like agar lebih mudah digunakan dalam analisis. Jika nilai genre kosong (NaN), fungsi akan mengembalikan string kosong (''). Dengan menggunakan ast.literal_eval(), string genre dikonversi menjadi daftar Python. Selanjutnya, nama-nama genre diekstrak dan digabungkan menjadi satu string dengan spasi sebagai pemisah. Jika terjadi kesalahan seperti ValueError, SyntaxError, atau KeyError, fungsi akan mencetak pesan error dan mengembalikan string kosong untuk menghindari gangguan pada pemrosesan data.

3. Mengonversi format JSON-like
   mengonversi format JSON-like menjadi string yang berisi nama-nama genre yang dipisahkan oleh spasi. Dengan cara ini, data genre menjadi lebih bersih dan mudah digunakan untuk analisis atau pemodelan sistem rekomendasi.

4. memastikan bahwa kolom genre ada dan tidak kosong

5. Membuat Fitur Kombinasi (combined_features)
   Menggabungkan teks dari kolom overview (ringkasan film) dan genres (genre film) menjadi satu fitur baru bernama combined_features. Tujuan dari langkah ini adalah untuk memiliki representasi teks yang lebih kaya sebagai dasar dalam sistem rekomendasi berbasis konten.

6. TF-IDF Vectorizer
   Menggunakan TF-IDF (Term Frequency - Inverse Document Frequency) Vectorizer untuk mengubah teks menjadi representasi numerik. Parameter stop_words='english' digunakan untuk menghilangkan kata-kata umum dalam bahasa Inggris yang tidak memiliki nilai informasi tinggi (seperti "the", "is", "and").

7. Transformasi Teks ke TF-IDF Matrix
   Melakukan vectorization dengan TF-IDF, yaitu mengubah teks dalam combined_features menjadi matriks numerik. Setiap baris dalam tfidf_matrix mewakili satu film, dan setiap kolom mewakili satu kata unik dalam dataset setelah pemrosesan stop words. Matriks ini digunakan sebagai dasar untuk menghitung kesamaan antar film.

8. Menampilkan Informasi Matriks TF-IDF
   Mencetak bentuk tfidf_matrix yang menunjukkan jumlah film (baris) dan jumlah fitur unik (kata-kata setelah pemrosesan, kolom).

9. Menampilkan Sample Fitur (Kata-Kata Unik)
   Menampilkan 10 kata pertama yang dihasilkan setelah proses vektorisasi.


## Modeling

1. Content-Based Filtering
   Deskripsi Model
   Model ini membangun sistem rekomendasi berdasarkan kemiripan antarfilm menggunakan cosine similarity. Setiap film direpresentasikan dalam bentuk vektor fitur berdasarkan deskripsi dan genre film, kemudian dihitung kesamaannya dengan film lain. Film dengan nilai kesamaan tertinggi akan direkomendasikan kepada pengguna.
   
   Kelebihan:
   - Tidak memerlukan data rating pengguna, sehingga tetap dapat memberikan rekomendasi untuk film baru.
   - Memberikan rekomendasi yang lebih relevan karena didasarkan pada kemiripan konten film.
   
   Kekurangan:
   - Bisa menghasilkan rekomendasi yang kurang bervariasi karena hanya mempertimbangkan kesamaan teks.
   - Tidak mempertimbangkan faktor lain seperti rating dan popularitas film.
   
   Top 5 Rekomendasi untuk Film 'Avatar':

   <img width="418" alt="image" src="https://github.com/user-attachments/assets/bf8e3f0a-008a-4e02-bbef-bb07762dc14f" />

2. Popularity-Based Recommendation
   Deskripsi Model:
   Model ini merekomendasikan film berdasarkan popularitas tertinggi, yang dihitung dari metrik seperti jumlah vote dan rating rata-rata.
   
   Kelebihan:
   - Mudah diterapkan dan cepat dalam memberikan rekomendasi.
   - Ideal untuk pengguna yang ingin menonton film populer tanpa mempertimbangkan preferensi tertentu.
     
   Kekurangan:
   - Tidak bersifat personal karena hanya mempertimbangkan popularitas.
   - Bisa memberikan film yang sudah sangat dikenal pengguna, mengurangi kemungkinan menemukan film baru.
   - 
     Top 5 Film Berdasarkan Popularitas:

     <img width="554" alt="image" src="https://github.com/user-attachments/assets/6a4c80b7-75f8-4b2d-b0af-182a9f308a7c" />

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

   <img width="553" alt="image" src="https://github.com/user-attachments/assets/71ff4668-b6a3-40a7-aaff-425e17889a2a" />


## Evaluation
Untuk mengevaluasi kinerja sistem rekomendasi yang dikembangkan, digunakan beberapa metrik evaluasi yang sesuai dengan pendekatan yang diterapkan.

1. Precision@K & Recall@K
  
   <img width="229" alt="image" src="https://github.com/user-attachments/assets/dfae7253-7a45-4fa3-8c58-62f89aa3b6d3" />

   Cara Kerja:
   - Precision@K mengukur proporsi item yang relevan di antara K rekomendasi teratas.
   - Recall@K mengukur seberapa banyak item relevan yang berhasil ditemukan dalam K rekomendasi teratas.
   
   Hasil  :

   <img width="415" alt="image" src="https://github.com/user-attachments/assets/dff162f2-7617-414c-9526-7c85d534dc0f" />

   - Content-Based Filtering: Precision@3 = 0.44, Recall@3 = 0.44

     Metode ini berhasil merekomendasikan item yang cukup relevan bagi pengguna, dengan 44% dari 3 rekomendasi teratas benar-benar relevan. Selain itu, metode ini juga berhasil menangkap 44% dari semua item relevan yang ada dalam daftar pengguna.

   - Popularity-Based Recommendation: Precision@3 = 0.22, Recall@3 = 0.22

     Popularitas saja tidak menjamin relevansi yang tinggi bagi pengguna tertentu. Hanya 22% dari 3 rekomendasi teratas yang benar-benar sesuai dengan preferensi pengguna. Sistem ini juga hanya berhasil menangkap 22% dari total item relevan yang dimiliki pengguna.

   - Genre-Based Recommendation: Precision@3 = 0.44, Recall@3 = 0.44

     Sama dengan Content-Based Filtering, metode ini mampu memberikan 44% rekomendasi yang relevan. Selain itu, recall juga menunjukkan bahwa metode ini dapat menangkap 44% dari total film yang benar-benar relevan.

2. Coverage

   <img width="329" alt="image" src="https://github.com/user-attachments/assets/de0e0c3e-3ac7-4b9b-98be-82a5c7d4e726" />

   Cara Kerja:

   Coverage mengukur seberapa luas sistem rekomendasi dalam menyarankan berbagai film dari dataset. Semakin tinggi coverage, semakin beragam rekomendasi yang diberikan.

   Hasil perhitungan Coverage:

   <img width="420" alt="image" src="https://github.com/user-attachments/assets/e7e4b3c2-9486-403a-b97c-23736d072987" />

   - Content-Based Filtering (0.10%) → Model hanya merekomendasikan film yang mirip dengan yang pernah ditonton pengguna. Jika film dengan fitur serupa jumlahnya sedikit, maka cakupan rekomendasi juga terbatas.
   - Popularity-Based Recommendation (0.10%) → Model ini hanya merekomendasikan film yang paling populer, yang jumlahnya lebih sedikit dibanding total film dalam dataset.
   - Genre-Based Recommendation (0.10%) → Model ini merekomendasikan film berdasarkan genre tertentu yang dipilih, yang berarti cakupannya j

Kesimpulan Akhir

Proyek ini berhasil mengembangkan sistem rekomendasi film berbasis content-based filtering menggunakan TF-IDF dan cosine similarity. Sistem ini mampu memberikan rekomendasi film yang relevan berdasarkan kemiripan deskripsi dan genre, serta menyediakan alternatif rekomendasi berdasarkan popularitas dan genre pilihan pengguna. Dari hasil pengujian, sistem mampu menyesuaikan rekomendasi dengan preferensi pengguna, sehingga membantu mengatasi kesulitan dalam memilih film dari banyaknya pilihan yang tersedia. Namun, sistem ini memiliki keterbatasan dalam mengeksplorasi film baru yang berbeda dari riwayat pengguna karena hanya berfokus pada kemiripan fitur. Secara keseluruhan, proyek ini mencapai tujuannya dalam menyediakan rekomendasi film yang lebih sesuai dengan preferensi pengguna, meskipun masih ada ruang untuk perbaikan, seperti menggabungkan metode collaborative filtering atau hybrid filtering untuk meningkatkan variasi rekomendasi.

