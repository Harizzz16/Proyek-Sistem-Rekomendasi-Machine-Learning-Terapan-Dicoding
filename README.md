# Proyek-Sistem-Rekomendasi-Machine-Learning-Terapan-Dicoding
# Laporan Proyek Machine Learning Rekomendasi Film - Haris Amaldi

## Domain Proyek

Film adalah salah satu entertaiment yang sangat menarik bagi banyak orang. Menonton film bisa dijadikan sebagai sarana healing yang dipilih oleh banyak orang karena kegiatannya yang tidak butuh tenaga dan effort yang besar, tapi tetap berkesan. Maka dari itu industri perfilman menjadi industri yang padat karya dan selalu aktif memberikan film-film produksinya dari berbagai genre untuk para penikmat film.
Akan tetapi dengan banyaknya genre, penonton dibuat bingung untuk memilih film mana yang sesuai dengan genre kesukaannya dan pihak penyedia layanan streaming film juga bingung untuk memilihkan saran film yang mungkin disukai oleh penggunanya.
Maka dari itu, proyek ini dibuat agar penyedia layanan streaming film bisa memilihkan film rekomendasi mereka berdasarkan genre yang para penggunanya suka agar para pengguna tetap betah nonton di layanan tersebut dan penyedia layanan streaming tersebut trafficnya bisa terjaga dan semakin menyebar ke film yang "mirip-mirip".


## Business Understanding
Dataset yang digunakan pada proyek ini didapatkan dari link di bawah ini:
https://www.kaggle.com/datasets/gargmanas/movierecommenderdataset

### Problem Statements

Masalah pada proyek ini antara lain:
- Apa saja film-film yang akan keluar sebagai rekomendasi jika saya menuliskan judul film "Toy Story"?
- Apakah model bisa merekomendasikan film-film rekomendasi dengan cukup akurat?


### Goals

Tujuan dari proyek ini antara lain:
- Menentukan apa sajakah film film rekomendasi yang muncul jika saya mencari "Toy Story".
- Mengetahui apakah film film rekomendasi mendekati genre dari film "Toy Story".

### Solution statements
- Solusi ini akan menggunakan Content-based Filtering Recommendation


## Data Understanding
Dataset ini terdiri atas dua csv, antara lain movies.csv dan ratings.csv. Untuk movies.csv terdiri atas 9742 data film yang memiliki kolom kolom seperti:
- movieId = Kode film
- title = Judul film
- genres = Tema film
Sedangkan ratings.csv adalah kumpulan rating-rating yang dikirim oleh 610 pengguna ke berbagai film yang memiliki kolom kolom seperti:
- movieId = Kode film
- title = Judul film
- rating = Rating film dari pengguna layanan streaming terdiri dari 0,5; 1; 1,5; 2,....sampai 5 (Harus diubah agar bisa bulat semua)
- timestamp = waktu pemberian rating
## Data Preparation
Preparasi data dilakukan dengan tahapan sebagai berikut:
- Menggabungkan seluruh movieId pada data film dan rating dan menyatukannya menjadi 1 tabel bernama "filmrating"
- mengecek keberadaan missing data dan menghapus missing data
  Hal ini dibutuhkan agar run tidak terhambat oleh missing data
- Memisahkan tahun rilis dari judul menjadi 1 kolom tersendiri dan menghapusnya dari kolom judul
  Dilakukan untuk memperlancar run dan mempermudah pembacaan tabel
- Mengecek adanya film yang hanya dirating oleh <10 pengguna dan menghapusnya agar permodelan bisa lebih efektif dan efisien
  Karena pada kenyataannya, di dataset ini terdapat film yang hanya dinilai oleh kurang dari 10 pengguna. Ini hanya memperlambat run. Jadi, bisa dihapus agar run bisa lebih cepat.
- Mengurutkan berdasarkan movieId dan Mengedrop duplikat
  Agar lebih tertata rapi dan agar tidak terjadi duplikat, urutkan berdasarkan movieId dan drop duplikatnya
- Membuat list
  Untuk mengonversi data series 'movieId', 'title', 'genres' menjadi dalam bentuk list
- Membuat dictionary baru
  Dictionary baru digunakan untuk menentukan key-value data movieId, title, dan genres yang sudah dipersiapkan pada saat membuat list

## Modeling
Modeling dilakukan dengan menggunakan metode content-based filtering yang dilakukan dengan tahapan-tahapan sebagai berikut:
- TF-IDF Vectorizer
  Digunakan untuk membangun sistem rekomendasi sederhana untuk proyek rekomendasi film ini, tf tersebut selanjutnya akan di fit dan di todense lalu dibuat matrix untuk memunculkan kecocokan

- Cosine Similarity
  Dilakukan untuk menghitung derajat kesamaan antar film dengan genrenya.

- Mendapatkan Rekomendasi
  Rekomendasi diberikan kepada pelanggan dengan menggunakan cosine similarity yang terbaik 
Hasilnya adalah sebagai berikut:
![hasil rekomendasi](https://user-images.githubusercontent.com/106704301/187964026-2b6b9d50-c71c-4e24-ad86-85838051d51c.png)

Bisa dilihat bahwa setelah saya mencari film "Toy Story", saya akan mendapatkan rekomendasi film "Emperor's New Groove, The", "Moana", "Monsters, Inc.", "Antz", dan "Toy Story 2".
## Evaluation
- Evaluasi pada proyek ini adalah tingkat ketelitiannya sangat bagus dimana Toy Story disandingkan dengan Moana, Monster Inc yang sama sama animasi dan petualangan dan bahkan dengan Toy Story 2 yang merupakan lanjutan kedua dari franchise film sequel Toy Story
- Dibutuhkan uji coba untuk menggunakan Collaborative-based di percobaan proyek selanjutnya untuk menyarankan dengan tepat sesuai tema dan rating dari masing-masing pengguna layanan streaming (Bisa dicoba di lain waktu, tapi sekarang tidak dulu. Mepet deadline habis billing soalnya).

**---Ini adalah bagian akhir laporan---**

