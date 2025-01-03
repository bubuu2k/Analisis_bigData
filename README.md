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
![Image Description](https://camo.githubusercontent.com/77e4a074311b53e10682a43b1385ca71ca7701136dcd9817602be08ff50c2ffe/68747470733a2f2f696d616765732e756e73706c6173682e636f6d2f70686f746f2d313439353433343934323231342d3962353235626261373465393f69786c69623d72622d312e322e3126697869643d65794a6863484266615751694f6a45794d446439266175746f3d666f726d6174266669743d63726f7026773d3133353026713d3830)
Data dalam penelitian ini bersumber dari Github [TidyTuesday](https://github.com/rfordatascience/tidytuesday/blob/main/data/2020/2020-01-21/readme.md).

**3.2 Spesifikasi Data
1. Tujuan Awal Data : Data ini dikhususkan untuk analisis metada lagu di platform spotify. Data ini dikumpulkan pada '21 Januari 2020' oleh [TidyTuesday](https://github.com/rfordatascience/tidytuesday/blob/main/data/2020/2020-01-21/readme.md).
2. Jumlah Variabel : Dataset ini mencakup 23 variabel yang berisi fitur audio, metadata, dan popularitas lagu.
   
**3.3 Data Cleaning **
**3.4 Data Cleaned Information**

Eksplorasi dan Analisa Data
--
4.1 Eksploratory Data Analysis
4.2 Menjawab Rumusan Masalah

kesimpulan 
--
5.1 Summary Table
5.2 Final Consolidated Results
5.3 Kesimpulan Rumusan Masalah
