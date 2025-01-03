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
   ![Energy_vs_Loudness_dari_Genre](https://raw.githubusercontent.com/bubuu2k/Analisis_bigData/main/Assets_new/Energy_vs_Loudness_dari_Genre.png)


2. Energy vs Loudness oleh Genre (each)
   ![Energy_vs_Loudness_dari_Genre](https://raw.githubusercontent.com/bubuu2k/Analisis_bigData/main/Assets_new/Energy_vs_Loudness_dari_Genre2.png)
   **Hubungan Umum:**

1. Terdapat korelasi positif yang signifikan antara tingkat energi dan loudness.
2. Lagu dengan energi tinggi cenderung memiliki loudness yang lebih besar (mendekati 0 dB).
3. Pola ini terlihat konsisten di seluruh genre musik yang dianalisis.

**Analisis per Genre:**

1. **EDM**: Terkonsentrasi pada energi dan loudness tinggi (0.8-1.0 untuk energy dan lebih dari -5 dB untuk loudness).
2. **Rock**: Distribusinya mirip dengan EDM, menunjukkan bahwa rock cenderung memiliki energi dan loudness tinggi.
3. **Pop**: Sebarannya merata pada rentang energi menengah hingga tinggi (0.4-0.9).
4. **Rap**: Cenderung memiliki loudness yang tinggi meskipun energi lagu berada pada rentang menengah.
5. **Latin**: Memiliki variasi yang luas antara energi dan loudness.
6. **R&B**: Lebih terkonsentrasi pada rentang energi menengah (0.4-0.8).

**Implikasi:**

1. Karakteristik audio lagu dipengaruhi oleh genre musiknya.
2. Produsen musik sering mengikuti standar produksi khas untuk setiap genre.
3. Ada tumpang tindih yang signifikan antar genre pada rentang energi dan loudness tertentu.

Regresion Result: 
   | Score    | Regression Result           |
   |----------|---------------------------|
   | 0.458       | R-Squared              |
   | 11.178    | Coefficient                  |
   | -14.529      | Intercept                  |

   **R-squared: 0.458**

1.   Nilai R-squared sebesar 0.458 berarti 45.8% dari variasi loudness dapat dijelaskan oleh variasi energi pada lagu.
2.   Hal ini menunjukkan bahwa energi berperan penting dalam menentukan seberapa keras sebuah lagu.

**Koefisien: 11.178**

1.   Koefisien regresi sebesar 11.178 menunjukkan bahwa setiap peningkatan satu unit energi akan mengarah pada peningkatan loudness rata-rata sebesar 11.178 unit.
2.   Ini menunjukkan hubungan positif yang signifikan antara energi dan loudness, dimana lagu dengan energi lebih tinggi cenderung lebih keras.

**Intercept: -14.529**

1.   Intersep sebesar -14.529 mengindikasikan nilai loudness saat energi bernilai nol.
2.   Meskipun nilai intersep ini dapat dihitung, dalam kenyataannya, energi nol pada lagu tidak mungkin terjadi, sehingga interpretasinya lebih bersifat teoritis.

#Anova
   Analisis ANOVA digunakan untuk mengevaluasi apakah terdapat perbedaan signifikan dalam tingkat energi (energy) antara genre musik yang berbeda (playlist_genre).
    | Score    | ANOVA Result         |
   |----------|---------------------------|
   | 1045.987       | F-statistic             |
   | 0.00    | P-value                 |

   Analisis ANOVA dilakukan untuk menguji apakah terdapat perbedaan yang signifikan dalam tingkat energi (energy) di antara berbagai genre musik (playlist_genre).

**F-statistic: 1045.987 p-value: 0.000**

1.   Nilai F-statistik yang sangat besar (1045.987) menunjukkan adanya perbedaan yang signifikan antara rata-rata tingkat energi antar genre.
2.   Semakin tinggi nilai F-statistik, semakin besar perbedaan antar kelompok dibandingkan dengan variasi dalam kelompok tersebut.
3.   Nilai p-value yang sangat kecil (p < 0.001) menunjukkan bahwa hasil uji ini sangat signifikan secara statistik.
4.   Dengan demikian, kita dapat menolak hipotesis nol (H0) yang menyatakan bahwa tidak ada perbedaan dalam rata-rata tingkat energi antar genre.
5.   Secara keseluruhan, ini mengindikasikan bahwa terdapat perbedaan signifikan dalam tingkat energi di antara genre musik yang berbeda.

   
2. Sejauh mana pengaruh penggunaan instrumen akustik mempengaruhi tingkat energi sebuah lagu, dan bagaimana perbedaan pengaruh tersebut berdasarkan periode atau tahun rilis musik?
   Correlation by year:
   | Correlation_score    | Year                  |
|----------|---------------------------|
| -1.000000| 1957                  |
| Nan| 1958                |
| Nan| 1959              |
| 0.780188   | 1960          |
| Nan| 1961            |
| Nan| 1962          |
| ......| ...  |
| -0.546348| 2016             |
| -0.546348| 2017               |
| -0.587997| 2018            |
| -0.545316| 2019         |
| -0.580525  | 2020              |
**Era Awal (1957-1962):**

1.   Pada tahun 1957, korelasi antara energi dan tingkat akustik adalah -1.000, yang menunjukkan hubungan negatif yang sempurna. Ini berarti semakin tinggi energi, semakin rendah penggunaan instrumen akustik, dan sebaliknya.
2.   Pada tahun 1958 dan beberapa tahun lainnya, terdapat nilai NaN. Hal ini kemungkinan disebabkan oleh jumlah data yang sangat sedikit atau bahkan tidak ada data yang dapat dihitung untuk korelasi.

**Era Modern (2016-2020):**

1.   Hubungan negatif antara energi dan akustik masih terlihat, dengan nilai korelasi antara -0.522 hingga -0.580. Ini menunjukkan bahwa hubungan negatif antara kedua variabel ini tetap ada di era modern.
2.   Pada tahun 2020, korelasi negatif tercatat cukup signifikan (-0.580), yang mengindikasikan bahwa lagu-lagu dengan elemen akustik cenderung memiliki energi lebih rendah dibandingkan dengan lagu-lagu yang didominasi elemen elektronik.

   **Visualisasi**
   1. Energy vs acousticness oleh year (all)
        ![Energy_vs_acousticness_dari_Year](https://raw.githubusercontent.com/bubuu2k/Analisis_bigData/main/Assets_new/Energy_vs_acousticness_dari_Year.png)
   2. Energy vs acousticness oleh year (each)
      ![Energy_vs_acousticness_dari_Year2](https://raw.githubusercontent.com/bubuu2k/Analisis_bigData/main/Assets_new/Energy_vs_acousticness_dari_Year2.png)
      **Relasi Umum:**

1.   Ditemukan korelasi negatif yang signifikan antara tingkat energi dan tingkat akustik suatu lagu.
2.   Ketika nilai acousticness meningkat, energi lagu cenderung menurun, dan sebaliknya.
3.   Pola ini dapat diamati secara konsisten pada berbagai rentang tahun (1965-2010).

**Pola Berdasarkan Periode:**

1.   Lagu-lagu dari periode 2010-an (kuning) lebih cenderung berada di area dengan energi tinggi dan akustik rendah.
2.   Lagu-lagu dari periode 1965-1980 (biru tua) tersebar lebih merata di seluruh rentang energi dan akustik.
3.   Tahun 1995 (cyan) menunjukkan transisi dari musik dengan elemen akustik ke dominasi musik digital.
4.   Terdapat perubahan bertahap dalam warna yang mencerminkan perubahan dalam gaya dan produksi musik dari waktu ke waktu.

**Kontribusi terhadap Penelitian:**

1.   Mendukung RQ2 mengenai bagaimana karakteristik musik telah berkembang seiring berjalannya waktu.
2.   Menunjukkan adanya pergeseran dalam cara musik diproduksi, dari akustik menuju lebih banyak produksi elektronik.
3.   Memberikan wawasan tentang tren dan standarisasi dalam produksi musik modern.

Regression with Year Control:
|Cross-Validation_Score||0.182 (+/- 0.209)|
**Skor Rata-rata Cross-validation**: Hasil rata-rata cross-validation sebesar 0.182 menunjukkan bahwa model regresi linier dapat menjelaskan sekitar 18.2% variasi energi lagu berdasarkan acousticness dan tahun. Ini menunjukkan adanya hubungan, namun kontribusinya terhadap energi masih relatif kecil.

**Deviasi Standar Cross-validation**: Deviasi standar sebesar ±0.209 mengindikasikan adanya variasi yang cukup besar dalam performa model di setiap fold. Hal ini mengindikasikan bahwa model tidak sepenuhnya stabil, kemungkinan disebabkan oleh ketidakseragaman data antar fold.

kesimpulan

--
5.1 Summary Table
5.2 Final Consolidated Results
5.3 Kesimpulan Rumusan Masalah
