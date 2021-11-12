# Laporan Proyek Machine Learning - Rafiq Freda Aryanta

## Project Overview

Pada bagian ini, Kamu perlu menuliskan latar belakang yang relevan dengan proyek yang diangkat.

**Rubrik/Kriteria Tambahan (Opsional)**:
- Jelaskan mengapa proyek ini penting untuk diselesaikan.
- Menyertakan hasil riset terkait atau referensi. Referensi yang diberikan harus berasal dari sumber yang kredibel dan author yang jelas.
  
  Format Referensi: [Judul Referensi](https://scholar.google.com/) 
<h3> Latar Belakang </h3>

<p align="center">
  <img width="460" height="300" src="https://user-images.githubusercontent.com/68459186/138650396-7b5242eb-4287-4b70-af33-ab6465db02e1.png">
</p>

## Business Understanding

### Problem Statements

Menjelaskan pernyataan masalah:
- Bagaimana cara mengolah data yang dapat dilakukan pada data anime dan rating?
- Bagaimana membuat sistem rekomendasi yang dipersonalisasi dengan teknik content-based filtering dan collaborative filtering?
- Bagaimana website myanimelist.net dapat merekomendasikan anime yang mungkin disukai atau diminati oleh pengguna?

### Goals

Menjelaskan tujuan proyek yang menjawab pernyataan masalah:
- Melakukan pengolahan data terhadap data anime dan rating sehingga dapat digunakan untuk membuat sistem rekomendasi.
- Membuat sejumlah rekomendasi anime yang dipersonalisasi untuk pengguna menggunakan teknik content-based filtering dan collaborative filtering.
- Membuat sejumlah rekomendasi anime yang sesuai dengan preferensi pengguna dan membuat daftar top 10 anime yang mungkin belum pernah dilihat sebelumnya menggunakan teknik content-based filtering dan collaborative filtering.

### Solution statements
- Mengajukan 2 atau lebih solution approach (algoritma atau pendekatan sistem rekomendasi).

## Data Understanding

![image](https://user-images.githubusercontent.com/68459186/141079123-f30c3cfa-ce32-458d-8110-c116a8c2a5bb.png)

Informasi dataset :

| Hal                     | Keterangan                                                                              |
| ----------------------- | --------------------------------------------------------------------------------------- |
| Sumber                  | [Kaggle Dataset : Anime Recommendation Database](https://www.kaggle.com/CooperUnion/anime-recommendations-database) |
| Lisensi                 | CC0: Public Domain                                                                      |
| Kategori                | Movie and TV Shows, Anime and Manga, Comics and Animation, Popular Culture              |
| Rating Penggunaan       | 8.2                                                                                     |
| Jenis dan Ukuran Berkas | CSV (112.34 MB)                                                                         |

### Deskripsi Variabel

Kumpulan data didapatkan dari myanimaelist.net API, berisikan informasi tentang data preferensi pengguna dari 73.516 pengguna pada 12.294 anime. Setiap pengguna dapat menambahkan anime ke daftar lengap mereka dan memberikan peringkat dan kumpulan data ini adalah kompilasi dari peringkat tersebut.

Variabel pada dataset :
- Anime.csv
  - anime_id = id unik myanimelist.net yang mengidentifikasi anime.
  - name = nama lengkap anime.
  - genre = daftar genre yang dipidahkan koma untuk anime.
  - type = film, TV, OVA, dll.
  - episodes = berapa banyak episode dalam acara ini. (1 jika film).
  - rating = rating rata-rata dari 10 untuk anime.
  - members = jumlah anggota komunitas yang ada di anime (kelompok).

- Rating.csv
  - user_id = ID pengguna yang dibuat secara acak yang tidak dapat diidentifikasi.
  - anime_id = anime yang telah dinilai oleh pengguna.
  - rating = rating dari 10 yang telah ditetapkan pengguna (-1 jika pengguna menentonnya tetapi tidak memberikan rating).   

### Univariate Exploratory Data Analysis
- Data Anime
- Data Rating


### Data Preprocessing
- Menggabungkan data anime dengan data rating
- Melihat data anime


**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data beserta insight atau exploratory data analysis.


## Data Preparation

Pada tahap ini dilakukan proses data preparation sebagai berikut : 
- Mengatasi Missing Value
- Memfilter user_id
- Melakukan Pivot pada Tabel

Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
