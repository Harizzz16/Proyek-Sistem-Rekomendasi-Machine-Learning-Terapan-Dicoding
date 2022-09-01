# Proyek-Sistem-Rekomendasi-Machine-Learning-Terapan-Dicoding
# Proyek-Pertama-Predictive-Analytics-ML-Terapan-Dicoding
# Laporan Proyek Machine Learning Prediksi Biaya Premi Asuransi - Haris Amaldi

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
![gabungan](https://user-images.githubusercontent.com/106704301/187963423-67bf9e26-ef0c-4fe1-a5c3-8bc5a5f282fd.png)
- mengecek keberadaan missing data dan menghapus missing data
![menghapus null](https://user-images.githubusercontent.com/106704301/187963505-3795136f-832f-48ca-93e9-4b915509115a.png)
- Memisahkan tahun rilis dari judul menjadi 1 kolom tersendiri dan menghapusnya dari kolom judul
![tahunrilis](https://user-images.githubusercontent.com/106704301/187963559-04660400-d27a-4219-af1a-1e3595883c47.png)
- Mengubah timestamp agar bisa dibaca sistem
![tanggalan](https://user-images.githubusercontent.com/106704301/187963588-39607de7-beae-44d6-89cf-32afdd53e56e.png)
- Menghapus nilai rating yang tidak bulat
![ratingbaru](https://user-images.githubusercontent.com/106704301/187963622-15d7b0a5-1702-4bff-ba6b-618739c17a57.png)
- Mengecek adanya film yang hanya dirating oleh <10 pengguna dan menghapusnya agar permodelan bisa lebih efektif dan efisien
![10 pengguna](https://user-images.githubusercontent.com/106704301/187963681-9c315c35-922d-447c-946b-a15266426fd3.png)
- Mengurutkan berdasarkan movieId dan Mengedrop duplikat
![sort dan dropduplikat](https://user-images.githubusercontent.com/106704301/187963736-84fef66b-dd88-4b54-8ba1-2552187b90c6.png)
- Membuat list
![list](https://user-images.githubusercontent.com/106704301/187963767-414b3527-e4c4-48bc-804e-49dc0ca1ad15.png)
- Membuat dictionary baru
![dictbaru](https://user-images.githubusercontent.com/106704301/187963786-9957739b-fd5c-415b-a435-c446e3d12dc8.png)

## Modeling
Modeling dilakukan dengan menggunakan metode content-based filtering yang dilakukan dengan tahapan-tahapan sebagai berikut:
- TF-IDF Vectorizer
![tfidf1](https://user-images.githubusercontent.com/106704301/187963814-c322a892-12fe-4e1b-89f8-569043a538cf.png)
![tfidf2](https://user-images.githubusercontent.com/106704301/187963903-3c4edefb-82a0-4f44-a74b-5b1018758291.png)
![tfidf3](https://user-images.githubusercontent.com/106704301/187963933-06f01b3f-1103-4b32-869a-e5dcdcef7b8f.png)

- Cosine Similarity
![cosine](https://user-images.githubusercontent.com/106704301/187963988-259c7cf6-5037-4172-98a2-36b61e7d7197.png)

- Mendapatkan Rekomendasi
![rekomendasi](https://user-images.githubusercontent.com/106704301/187964009-7d37985d-44f0-4d06-997b-574381737ce9.png)

Hasilnya adalah sebagai berikut:
![hasil rekomendasi](https://user-images.githubusercontent.com/106704301/187964026-2b6b9d50-c71c-4e24-ad86-85838051d51c.png)

Bisa dilihat bahwa setelah saya mencari film "Toy Story", saya akan mendapatkan rekomendasi film "Emperor's New Groove, The", "Moana", "Monsters, Inc.", "Antz", dan "Toy Story 2".
## Evaluation
- Evaluasi pada proyek ini adalah tingkat ketelitiannya sangat bagus dimana Toy Story disandingkan dengan Moana, Monster Inc yang sama sama animasi dan petualangan dan bahkan dengan Toy Story 2 yang merupakan lanjutan kedua dari franchise film sequel Toy Story
- Dibutuhkan uji coba untuk menggunakan Collaborative-based di percobaan proyek selanjutnya untuk menyarankan dengan tepat sesuai tema dan rating dari masing-masing pengguna layanan streaming (Bisa dicoba di lain waktu, tapi sekarang tidak dulu. Mepet deadline habis billing soalnya).

**---Ini adalah bagian akhir laporan---**

