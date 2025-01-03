# Analisis_bigData


Khairun Nazmy_202110370311117

Link Colab :[Click Here](https://colab.research.google.com/drive/1AbCdEfGhIjKlMnOpQrStUvWxYz123456)


**DAFTAR ISI**
----------------------

- [Pendahuluan](#pendahuluan)
- [Package yang Diperlukan](#package-yang-diperlukan)
- [Data Preparation](#data-preparation)
- [Eksplorasi dan Analisa Data](#eksplorasi-dan-analisa-data)
- [Kesimpulan](#kesimpulan)

---


**Pendahuluan**
---
Dataset "Spotify Songs" yang digunakan dalam penelitian ini berasal dari [TidyTuesday](https://github.com/rfordatascience/tidytuesday/blob/main/data/2020/2020-01-21/readme.md), sebuah sumber data terbuka untuk keperluan analisis. Dataset ini mencakup beragam fitur audio, metadata lagu, serta metrik popularitas seperti `danceability`, `energy`, `tempo`, `acousticness`, dan `popularity`. Data ini menyajikan informasi penting dari platform Spotify yang memungkinkan analisis tentang pola konsumsi lagu oleh audiens. Dengan total 23 variabel, dataset ini memberikan kesempatan menarik bagi para peneliti untuk mengeksplorasi hubungan antara karakteristik audio dan tingkat popularitas lagu.  
Namun, kompleksitas data tersebut menghadirkan sejumlah tantangan. Perbedaan skala dan distribusi antar fitur audio membuat identifikasi pola menjadi sulit. Selain itu, keberadaan nilai yang hilang atau anomali dalam beberapa variabel dapat memengaruhi keakuratan hasil analisis.  

Untuk menghadapi tantangan ini, dilakukan berbagai langkah seperti pembersihan data, analisis statistik deskriptif, dan visualisasi untuk mengenali pola utama. Penelitian ini bertujuan untuk memahami hubungan antara fitur audio dengan jenis lagu secara lebih mendalam. Dengan begitu, diharapkan hasil penelitian dapat memberikan wawasan bagi musisi dalam menyusun strategi penciptaan lagu yang sesuai dengan selera pendengar.

**1.1 Rumusan Masalah**

Berdasarkan latar belakang yang telah dijelaskan, rumusan masalah yang menjadi fokus dalam penelitian ini adalah sebagai berikut:

1. Sejauh mana tingkat energi lagu memengaruhi loudness pada berbagai genre musik di Spotify, dan apakah hubungan tersebut serupa di semua genre?
2. Seberapa besar kontribusi instrumen akustik terhadap tingkat energi lagu, serta bagaimana perbedaannya berdasarkan era atau tahun perilisan musik?
   
**1.2 Solusi Mengatasi Masalah**

Solusi dalam penelitian ini difokuskan untuk menjawab rumusan masalah yang telah dirumuskan. Berdasarkan rumusan masalah tersebut, solusi yang diusulkan adalah sebagai berikut:  

1. Melakukan eksplorasi data untuk memahami distribusi dari setiap fitur dalam dataset.  
2. Mengkaji hubungan antara fitur energi lagu dengan loudness pada masing-masing genre musik.  
3. Menganalisis dampak fitur akustik terhadap energi lagu, serta melihat variasinya berdasarkan periode atau tahun perilisan.
   
**1.3 Teknik Analisis Yang diusulkan**

Dalam mencari solusi, saya menerapkan beberapa teknik analisis berikut:  

1. Pembersihan data dan ringkasan awal untuk memahami struktur dan konten dataset.  
2. Analisis statistik deskriptif guna mengidentifikasi pola dan tren utama.  
3. Visualisasi data menggunakan histogram dan scatterplot untuk mengeksplorasi hubungan antara variabel.
   
**1.4 Manfaat Analisis**

Dalam mencari solusi, saya  menerapkan beberapa teknik analisis berikut:  

1. Pembersihan data dan ringkasan awal untuk memahami struktur dan konten dataset.  
2. Analisis statistik deskriptif guna mengidentifikasi pola dan tren utama.  
3. Visualisasi data menggunakan histogram dan scatterplot untuk mengeksplorasi hubungan antara variabel.  


**Package yang diperlukan**
--

**2.1 Python**

Sebelum melakukan penelitian ini, instalasi python pada environment local yang diperlukan. Python yang digunakan pada penelitian ini adalah python 3.10. Untuk mempelajarinya lebih lanjut, tekan [click here](https://www.python.org/downloads/release/python-3100/).

Selanjutnya, instalasi beberapa library pyton juga diperlukan. Kamu dapat melakukan instalasi library pada terminal python menggunakan 'pip'. Library ini yaitu sebagai berikut :
- **Pandas - Latest**
  ```bash
  pip install pandas

- **Numpy - Latest**
  ```bash
  pip install numpy

- **matplotlib - Latest**
  ```bash
  pip install matplotlib

- **seaborn - Latest**
  ```bash
  pip install seaborn

- **scipy - Latest**
  ```bash
  pip install scipy


- **sklearn - Latest**
  ```bash
  pip install sklearn


**Data Preparation**
--
**3.1 Sumber Data**
Data dalam penelitian ini bersumber dari Github [TidyTuesday](https://github.com/rfordatascience/tidytuesday/blob/main/data/2020/2020-01-21/readme.md).

**3.2 Spesifikasi Data**
1. Tujuan Awal Data : Data ini dikhususkan untuk analisis metada lagu di platform spotify. Data ini dikumpulkan pada '21 Januari 2020' oleh [TidyTuesday](https://github.com/rfordatascience/tidytuesday/blob/main/data/2020/2020-01-21/readme.md).
2. Jumlah Variabel : Dataset ini mencakup 23 variabel yang berisi fitur audio, metadata, dan popularitas lagu.

berikut adalah tabel yang ada di data spotify : 
| Class    | Variable                  |
|----------|---------------------------|
| character| track_id                  |
| character| track_name                |
| character| track_artist              |
| double   | track_popularity          |
| character| track_album_id            |
| character| track_album_name          |
| character| track_album_release_date  |
| character| playlist_name             |
| character| playlist_id               |
| character| playlist_genre            |
| character| playlist_subgenre         |
| double   | danceability              |
| double   | energy                    |
| double   | key                       |
| double   | loudness                  |
| double   | mode                      |
| double   | speechiness               |
| double   | acousticness              |
| double   | instrumentalness          |
| double   | liveness                  |
| double   | valence                   |
| double   | tempo                     |
| double   | duration_ms               |

Data Uniqueness : Terdapat beberapa data kosong di kolom `track_album_release_date`



   
**3.3 Data Cleaning **

Pertama data di load menggunakan library pandas `name_file.read_csv` untuk membaca file csv dari data spotify.

Teknik data cleaning yang diterapkan adalah sebagai berikut.

* Pengecekan Data Duplikat: Proses ini berguna untuk memastikan tidak ada entri yang terulang, yang dapat mempengaruhi keakuratan analisis baik dalam statistik deskriptif maupun visualisasi.
*Pengecekan Data Null: Langkah ini penting untuk mengidentifikasi dan menghapus data yang memiliki nilai kosong, guna menghindari ketidakpastian dalam analisis.
* Ekstraksi Tahun: Tahapan ini digunakan untuk mengambil informasi tahun dari kolom `track_album_release_date`, yang nantinya akan dimanfaatkan untuk analisis tren.


**3.4 Data Cleaned Information**

Setelah melakukan proses data cleaning, maka data yang akan di analisis pun sudah siap. Berikut ringkasan awal dari data yang sudah di bersihkan.
**Jumlah Data (Count):**

1. Terdapat 32,828 lagu yang dianalisis.
2. Semua variabel (energy, loudness, acousticness) memiliki jumlah data yang konsisten.
3. Tidak ada data yang hilang, karena jumlahnya identik antara Before dan After.

**Energy:**

1. Rata-rata (Mean): 0.698603, yang menunjukkan bahwa sebagian besar lagu memiliki tingkat energi yang tinggi (skala 0-1).
2. Standar deviasi (Std): 0.180916, menandakan variasi energi yang relatif kecil.
3. Rentang (Min-Max): 0.000175 hingga 1.000000, menggambarkan spektrum dari lagu yang sangat tenang hingga sangat energik.
4. Median (50%): 0.721000, sedikit lebih tinggi dari rata-rata, mengindikasikan distribusi yang cenderung miring ke kiri.

**Loudness:**

1. Rata-rata (Mean): -6.719529 dB, menggambarkan tingkat volume rata-rata lagu.
2. Standar deviasi (Std): 2.988641, menunjukkan variasi yang cukup besar dalam loudness.
3. Minimum: -46.448000 dB (sangat pelan).
4. Maksimum: 1.275000 dB (sangat keras).
5. Median: -6.166000 dB, yang dekat dengan rata-rata, menunjukkan distribusi yang simetris.

**Acousticness:**

1. Rata-rata (Mean): 0.175352, yang mengindikasikan sebagian besar lagu cenderung non-akustik.
2. Standar deviasi (Std): 0.219644, menunjukkan variasi tingkat akustik yang sedang.
3. Rentang (Min-Max): 0.000000 hingga 0.994000, dari lagu yang sepenuhnya elektronik hingga hampir sepenuhnya akustik.
4. Distribusi cenderung miring ke kanan (mean > median 0.080400).

**Distribusi Data:**

1. Energy: Terpusat di rentang tinggi (75% data memiliki nilai > 0.581000).
2. Loudness: Terdistribusi secara normal dengan beberapa outlier yang sangat pelan.
3. Acousticness: Sebagian besar lagu memiliki nilai rendah, dengan beberapa lagu yang sangat akustik.

**Kesimpulan Utama:**

1. Sebagian besar lagu di Spotify memiliki tingkat energi yang tinggi (mean energy 0.69).
2. Loudness terdistribusi normal dengan variasi yang cukup.
3. Sebagian besar lagu cenderung non-akustik (75% lagu memiliki acousticness < 0.255000).

Eksplorasi dan Analisa Data
--
4.1 Eksploratory Data Analysis
Setelah melakukan eksplorasi dataset, maka ditemukan informasi penting mengenai distribusi data.
![Distribusi Data](https://raw.githubusercontent.com/bubuu2k/Analisis_bigData/main/Assets/Distribusi_data/Distribusi_data.png)


4.2 Menjawab Rumusan Masalah

kesimpulan 
--
5.1 Summary Table
5.2 Final Consolidated Results
5.3 Kesimpulan Rumusan Masalah
