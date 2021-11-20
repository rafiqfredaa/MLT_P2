# Laporan Proyek Machine Learning - Rafiq Freda Aryanta

## Project Overview
 
<h3> Latar Belakang </h3>

Anime ((bahasa Jepang: アニメ) adalah animasi dari jepang yang digambar dengan tangan maupun menggunakan teknologi komputer. Kata _anime_ merupakan singkatan dari "_animation_" dalam bahasa Inggris, yang merujuk pada semua jenis animasi. Di luar Jepang, istilah ini digunakan secara spesifik untuk menyebutkan segala animasi yang diproduksi di Jepang. dengan melihat data pencarian anime di google seperti yang terdapat pada gambar diatas dapat diketahui sejak tahun 2004 hingga sekarang terjadi peningkatan dalam hal pencarian tetang anime. Terlebih, ketika masa pandemi sekarang kebanyak orang beraktifitas dirumah dan salah satu kegiatan yang dapat dilakukan adalah menonton film, series, anime, dan sebagainya. Dapat diketahui juga anime yang telah diproduksi sendiri sudah sangat banyak. Terdapat banyak website yang memuat anime entah legal maupun yang ilegal. Misalnya, myanimelist.net merupakan sebuah website yang memiliki konten anime yang dapat ditonton secara online. Menurut data dari google trends diketahui negara-negara dengan pengguna terbanyak yang melakukan pencarian tentang anime, yaitu Philippines, El Salvador, Bolivia, Indonesia, dan Myanmar. Terkadang pengguna kesulitan untuk memilih anime yang sesuai dengan preferensi mereka karena banyaknya anime yang ada dalam website. Sehingga diperlukan waktu yang lebih untuk melihat satu per satu anime yang akan ditonton apakah sesuai atau tidak dengan minat pengguna. Untuk itu, perlu dikembangkan sebuah sistem rekomendasi yang dapat membantu pengguna untuk mencari tahu anime yang sesuai dengan preferensi mereka atau mirip dengan anime yang mereka suka atau telah ditonton sebelumnya.

<p align="center">
  <img src="https://user-images.githubusercontent.com/68459186/142195763-7ea14895-8192-4d16-8043-fabe8a4e3914.png">
</p>

## Business Understanding

### Problem Statements

Menjelaskan pernyataan masalah:
- Bagaimana cara mengolah data dan memilih fitur pada data anime dan rating?
- Bagaimana membuat sistem rekomendasi yang dipersonalisasi dengan teknik _content-based filtering_?
- Bagaimana website myanimelist.net dapat merekomendasikan anime yang mungkin disukai atau diminati oleh pengguna?

### Goals

Menjelaskan tujuan proyek yang menjawab pernyataan masalah:
- Melakukan pengolahan data terhadap data anime dan rating sehingga dapat digunakan untuk membuat sistem rekomendasi, serta memilih fitur yang berguna.
- Membuat rekomendasi anime yang dipersonalisasi untuk pengguna menggunakan teknik _content-based filtering_.
- Membuat sejumlah rekomendasi anime yang sesuai dengan preferensi pengguna dan membuat daftar 10 anime yang mungkin belum pernah dilihat sebelumnya menggunakan teknik _content-based filtering_.

### Solution statements
Berikut ini merupakan solusi yang mungkin dapat dilakukan :
- Melihat data anime dan melihat secara menyeluruh setiap variabel untuk melihat hubungan antar variabel. Dengan begitu, dapat ditentukan variabel-variabel yang berhubungan dan sesuai dengan yang dibutuhkan. Pemrosesan data yang dapat dilakukan adalah membersihkan variabel name, menangani missing value, dan menghapus data yang duplikat.
- Model rekomendasi yang dikembangkan menggunakan teknik _content-based filtering_. Teknik ini melakukan pemfilteran berbasis konten, juga disebut sebagai pemfilteran kognitif, merekomendasikan item berdasarkan perbandingan antara konten item dan profil pengguna. Konten setiap item direpresentasikan sebagai kumpulan deskriptor atau istilah, biasanya kata-kata yang muncul dalam dokumen. Rekomendasi berbasis konten bekerja dengan data yang diberikan pengguna, baik secara eksplisit (peringkat) atau implisit (mengklik tautan). Berdasarkan data tersebut, profil pengguna dibuat, yang kemudian digunakan untuk memberikan saran kepada pengguna. Saat pengguna memberikan lebih banyak masukan atau mengambil tindakan berdasarkan rekomndasi, mesin menjadi lebih akurat.
- Rekomdasi yang dapat diberikan kepada pengguna dengan cara memberikan rekomendasi 10 anime terbaik yang memiliki rating paling tinggi, serta sesuai dengan preferensi pengguna.  

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

### Univariate Exploratory Data Analysis

Kumpulan data didapatkan dari myanimaelist.net API, berisikan informasi tentang data preferensi pengguna dari 73.516 pengguna pada 12.294 anime. Setiap pengguna dapat menambahkan anime ke daftar lengap mereka dan memberikan peringkat dan kumpulan data ini adalah kompilasi dari peringkat tersebut.

Variabel pada dataset :
- Anime
  - anime_id = id unik myanimelist.net yang mengidentifikasi anime.
  - name = nama lengkap anime.
  - genre = daftar genre yang dipisahkan koma untuk anime.
  - type = media untuk menonton/streaming (Movie, TV, OVA, Special, Music, ONA, dan nan).
  - episodes = berapa banyak episode dalam acara ini. (1 jika film).
  - rating = rating rata-rata dari 0 hingga 10 untuk anime.
  - members = jumlah anggota komunitas yang ada di anime (kelompok).

- Rating
  - user_id = ID pengguna yang dibuat secara acak yang tidak dapat diidentifikasi.
  - anime_id = anime yang telah dinilai oleh pengguna.
  - rating = rating dari 10 yang telah ditetapkan pengguna (-1 jika pengguna menentonnya tetapi tidak memberikan rating).   

### Data Preprocessing
- Menggabungkan data anime dengan data rating. Dilakukan dengan menggunakan fungsi 'pd.merge'. Hal ini dilakukan dengan tujuan agar kita dapat melihat informasi dengan lebih baik dan melihat informasi secara keseluruhan. Dengan begitu, dapat dilakukan proses visualisasi data untuk melihat persebaran data pada dataset yang digunakan. 
- Melihat data anime
  - Top 10 Anime Berdasarkan Jumlah Rating
    
    ![image](https://user-images.githubusercontent.com/68459186/142178348-e82e45d2-df46-4135-80fb-d2a8efeed730.png)
    
    10 anime dengan jumlah rating tertinggi. Peringkat pertama diduduki anime Death Note, kemudian disusul anime Sword Art Online pada posisi kedua dan pada posisi ketiga ada anime Shingeki no Kyojin. 

  - Top 10 Anime Berdasarkan Jumlah Anggota Komunitas
    
    ![image](https://user-images.githubusercontent.com/68459186/142178382-0071619b-1b78-4cb9-ac8f-054706044999.png)
    
    10 anime teratas berdasarkan jumlah anggota komunitasnya. Pada peringkat pertama ada anime Death Note, peringkat kedua ada anime Shingeki no Kyojin, dan posisi ketiga ada Sword Art Online.

  - Melihat Data Distribusi Rating
    
    ![image](https://user-images.githubusercontent.com/68459186/142178415-fe52dcf5-633d-499c-ba08-7b2f0680c39c.png)
    
    Didapatkan bahwa : 
    - Sebagian besar rating terdapat pada rentang 6 hingga 10
    - Nilai modus distribusi sekitar 7.5 hingga 8.0
    - Terdapat peringkat -1 sebagai outlier dalam rating user yang dapat dibuat menjadi NaN 

  - Media untuk Menonton/Streaming
    
    ![image](https://user-images.githubusercontent.com/68459186/142178442-587ce5af-0192-4874-adf0-02c4ecbb96de.png)
    
    Didapatkan bahwa :
    - Anime terbanyak ditayangkan di TV sejumlah 5.283.596 atau sektiar 67.6% dari total data. 
    - Anime penayangan melalui Movie sebanyak 13.5%.
    - Anime di streaming dalam OVA sebesar 10.2%. 
    - Anime ditonton dalam Special sebesar 7.16%.
    - Anime ditonton dalam ONA sebesar 1.18%.
    - Anime ditonton dalam music sebesar 0.339%.

  - Genre Anime yang Populer
    
    ![image](https://user-images.githubusercontent.com/68459186/142178461-bc3c742c-c6f1-4aad-812d-67ccd5da931d.png)
    
    Didapatkan bahwa terdapat banyak genre anime pada dataset, genre yang paling banyak adalah comedy, action, romace, drama, dan school, serta masih ada genre lainnya pada dataset.

## Data Preparation

Pada tahap ini dilakukan proses data preparation sebagai berikut : 
- Membersihkan Data pada Variabel name. Pada tahap ini dilakukan pembersihan pada variabel name dengan cara membuat sebuah fungsi "text_cleaning". Fungsi ini digunakan untuk menghapus kata-kata yang tidak diperlukan seperti &quot, &#039, &amp, dan sebagainya. Sehingga didapatkan data pada variabel name bersih dan hanya tersisa data judul anime yang sesuai. Dengan begitu, kita mendapatkan data pada variabel name bersih dan siap untuk digunakan untuk membuat model rekomendasi. 
- Mengatasi Missing Value. Pada tahap ini dilakukan penghapusan data yang memiliki nilai kosong atau NaN terkhusus pada bagian variabel rating. Sebelumnya, dilakukan proses penggantian pada variabel rating nilai -1 yang terdapat pada variabel rating diganti dengan nilai NaN. Setelah itu, data yang memiliki nilai NaN tersebut dihapus. Selanjutnya, juga dilakukan proses pengisian pada bagian variabel genre apabila ada data yang memiliki nilai NaN maka ada diisi dengan nilai string kosong. 
- Membuat pandas series dan mengembalikan series dengan menghilangkan data yang duplikat. Pada tahap ini dilakukan dengan menggunakan fungsi "pd.Series", serta fungsi "drop_duplicates" untuk mengembalikan nilai series dengan menghilangkan data yang duplikat. Dengan begitu, dibuat sebuah data baru yang berbentuk array berlabel satu dimensi yang mampu menampung data jenis apa pun. Label sumbu secara kolektif disebut indeks. Label tidak harus unik tetapi harus bertipe hashable. Objek mendukung pengindeksan berbasis bilangan bulat dan label, serta menyediakan sejumlah metode untuk melakukan operasi yang melibatkan indeks.  

## Modeling

Pada proses pemodelan dilakukan proses,
- TF-IDF (Term Frequency and Inverse Document Frequency), matrik yang digunakan untuk menemukan representasi fitur penting dari setiap genre anime. Parameter yang digunakan adalah 'min_df=3' berarti ketika membangun abaikan istilah yang memiliki frekuensi dokumen lebih rendah dari ambang batas yang diberikan, 'max_features=None' berarti membuat kosakata yang hanya mempertimbangkan max_features teratas yang diurutkan berdasarkan frekuensi istilah di seluruh korpus, 'strip_accents='unicode'' berarti melakukan penghapusan aksen dan melakukan normalisasi selama langkah prapemrosesan - metode yang sedikit lebih lambat yang bekerja pada karakter apa pun, 'analyzer='word'' berarti memilih fitur dari kata-kata, 'token_pattern=r'\w{1,}'' berarti ekspresi egular yang menunjukkan apa yang merupakan 'token', 'ngram_range=(1,3)' berarti batas bawah dan batas atas kisaran nilai-n untuk n-gram berbeda yang akan diekstraksi, dan 'stop_words='english'' berarti mendeteksi dan memfilter kata berhenti yang semuanya akan dihapus dari token yang dihasilkan. 
- Sigmoid kernel, melakukan fungsi sigmoid pada data yang sudah dilakukan metrik TF-IDF dengan menggunakan metrik berpasangan untuk merepresentasi koleksi padat dan jarang. Pada hal ini diperlukan menetapkan nilai 1 untuk anime yang direkomendasikan dan nilai 0 untuk anime yang tidak direkomendasikan. 

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
