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
![Distribusi Data](https://raw.githubusercontent.com/bubuu2k/Analisis_bigData/main/Assets/Distribusi_data.png)

**Distribusi Energy (kiri atas):**

1. **Bentuk**: Distribusi hampir normal dengan sedikit kemiringan ke kiri.
2. **Rentang**: 0-1 (ternormalisasi).
3. **Puncak**: Terletak di sekitar 0.7-0.8, menunjukkan bahwa sebagian besar lagu memiliki tingkat energi tinggi.
4. **Interpretasi**: Sebagian besar lagu dalam dataset memiliki karakteristik energik, sesuai dengan kecenderungan pendengar musik streaming.

**Distribusi Loudness (kanan atas):**

1. **Bentuk**: Distribusi hampir normal dengan ekor panjang di sisi kiri.
2. **Rentang**: -40 dB hingga 0 dB.
3. **Puncak**: Sekitar -5 dB hingga -7 dB.
4. **Interpretasi**: Mayoritas lagu memiliki loudness standar, dengan beberapa outlier yang sangat pelan.

**Distribusi Acousticness (kiri bawah):**

1. **Bentuk**: Cenderung sangat skewed ke kanan.
2. **Rentang**: 0-1 (ternormalisasi).
3. **Dominasi**: Nilai rendah (0-0.2).
4. **Interpretasi**: Mayoritas lagu tidak akustik, mencerminkan dominasi musik modern yang diproduksi secara digital.

**Distribusi Tahun (kanan bawah):**

1. **Bentuk**: Sangat skewed ke kanan dengan lonjakan tajam pada tahun-tahun terbaru.
2. **Rentang**: 1960-2020.
3. **Puncak**: Terletak antara 2015-2020.
4. **Interpretasi**: Dataset lebih banyak berisi lagu-lagu baru, mencerminkan dominasi musik kontemporer dan pertumbuhan pesat konten digital di era streaming.

**Insight Utama:**

1. Dataset mencerminkan kecenderungan terhadap lagu yang enerjik (energi tinggi), modern (akustik rendah), dan kontemporer (tahun rilis baru).
2. Loudness lebih terstandarisasi, menunjukkan adanya normalisasi volume dalam produksi musik.
3. Dominasi lagu non-akustik menggambarkan tren dalam produksi musik digital.
4. Distribusi temporal cenderung tidak merata, dengan fokus lebih pada musik era streaming.



4.2 Menjawab Rumusan Masalah
1. Bagaimana hubungan antara tingkat energi lagu dan loudness di berbagai genre musik di Spotify, serta apakah pola ini tetap sama di seluruh genre?
   Hubungan antara energi dan loudness (0-1)
   | Playlist_genre    | Correlation_score           |
   |----------|---------------------------|
   | edm      | 0.638214                  |
   | latin    | 0.587487                  |
   | pop      | 0.673739                  |
   | r&b      | 0.602092                  |
   | rap      | 0.723875                  |
   | rock     | 0.749934                  |

   **EDM (0.638):**

1. Hubungan antara energi dan loudness cukup kuat dan positif.
2. Lagu EDM yang lebih energik cenderung memiliki volume lebih tinggi, sesuai dengan sifat genre yang sering digunakan dalam pesta atau klub.

**Latin (0.587):**

1. Korelasi positif yang signifikan menunjukkan bahwa lagu latin dengan energi tinggi juga cenderung memiliki volume yang lebih besar.
2. Ini mencerminkan ritme dan energi khas yang ada dalam musik latin.

**Pop (0.674):**

1. Korelasi positif yang kuat menunjukkan bahwa lagu pop yang lebih enerjik memiliki loudness yang lebih tinggi.
2. Genre pop cenderung diproduksi untuk menarik perhatian, dengan fokus pada elemen yang dinamis dan menarik.

**R&B (0.602):**

1. Korelasi positif ini menunjukkan hubungan yang cukup kuat antara tingkat energi dan loudness dalam musik R&B.
2. Lagu R&B yang lebih energik biasanya diproduksi dengan loudness lebih tinggi untuk menonjolkan dinamika dan emosi.

**Rap (0.724):**

1. Rap memiliki korelasi tinggi antara energi dan loudness, dengan lagu yang lebih energik cenderung lebih keras.
2. Ini sesuai dengan produksi rap yang sering menonjolkan vokal kuat dan beat yang tegas.

**Rock (0.750):**

1. Rock memiliki korelasi tertinggi, menunjukkan hubungan yang sangat kuat antara energi dan loudness.
2. Musik rock sering menggunakan volume tinggi untuk menciptakan intensitas dan daya tarik emosional, mencerminkan karakter pemberontakan dan semangat dalam genre ini.

Visualisasi
Berikut merupakan visualisasi dari korelasi antara energy dan loudness.
1. Energy vs Loudness oleh Genre (all)
   ![Distribusi Data](https://raw.githubusercontent.com/bubuu2k/Analisis_bigData/main/Assets/Assets/Energy_vs_Loudness_dari_Genre.png)
2. Energy vs Loudness oleh Genre (each)

   
2. Sejauh mana pengaruh penggunaan instrumen akustik mempengaruhi tingkat energi sebuah lagu, dan bagaimana perbedaan pengaruh tersebut berdasarkan periode atau tahun rilis musik?
kesimpulan


--
5.1 Summary Table
5.2 Final Consolidated Results
5.3 Kesimpulan Rumusan Masalah
