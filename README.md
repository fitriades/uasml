# Laporan Proyek Machine Learning
### Nama : Fitria Desiyani
### Nim : 211351057
### Kelas : Pagi B

## Domain Proyek

Pengidap penyakit hepatitis sejatinya beresiko untuk meninggal dunia dan survive. Pada project ini pengidap hepatitis bisa melakukan perhitungan apakah beresiko untuk meninggal dunia atau punya kesempatan untuk survive.

## Business Understanding

Data menunjukan untuk gejala dan penyakit hepatitis berdasarkan beberapa pertanyaan baik itu gender sspesifik dan pengaruh pengobatan lainya dapat menjadikan penyakit itu memiliki resiko kematian. Maka dari itu, dengan algoritma svm linear saya coba klasifikasikan apakah penyakit hepatitis yang di derita si pasien beresiko menyebabkan kematian atau tidak.

Bagian laporan ini mencakup:

### Problem Statements

- Resiko kematian pasien penyakit hepatitis

 
### Goals

- Meningkatkan kewaspadaan terhadap resiko kematian penyakit hepatitis
- Sebagai early warning untuk para pengidap penyakit hepatitis

    ### Solution statements
    - Dilakukanya proses klasifikasi untuk pengidap penyakit hepatitis
    - Menggunakan algoritma svm linear untuk proses klasifikasi

## Data Understanding
Data di dapatkan dari kaggle dengan dataset tentang penyakit hepatitis dan resiko kematian nya.

[Hepatitis Data](https://www.kaggle.com/datasets/codebreaker619/hepatitis-data/).


### Variabel-variabel pada Hepatitis Data Dataset adalah sebagai berikut:
- age = usia dari si pengidap hepatitis, bertipe integer
- sex = jenis kelamin si pengidap hepatitis, bertipe boolean
- steroid = apakah si pasien sedang mengkonsumsi steroid, bertipe boolean
- antivirals = apakah si pasien sedang mengkonsumsi obat yang bersifat antivirus, bertipe boolean
- fatigue = apakah si pasien sering mengalami kelelahan, bertipe boolean
- malaise = apakah si pasien juga mengidap malaise, bertipe boolean
- anorexia = apakah si pasien juga mengidap anorexia, bertipe boolean
- liver_big = apakah si pasien mengalami pembengkakan pada liver, bertipe boolean
- liver_firm = apakash si pasien mengalami pengerasan pada liver, bertipe boolean
- spleen_palpable = apakah si dapat merasakan limpanya secara jelas, bertipe boolean
- spiders = apakah si pasien mengalami spider nevus, bertipe boolean
- ascites = apakah si pasien mengalami ascites, bertipe boolean
- varices = apakah si pasien memiliki varises, bertipe boolean
- bilirubin = jumlah kadar bilirubin si pasien, bertipe float
- alk_phosphate = kandungan alkalin dalah darah si pasien, bertipe float
- sgot = kandungan Serum Glutamic Oxaloacetic Transaminase si pasien, bertipe float
- albumin = tingkat albumin dalam tubuh si pasien, bertipe float
- protime = Jumlah waktu untuk Prothrombin time dalam tubuh si pasien, bertipe float
- histology = histology liver si pasien, bertipe boolean

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. Anda perlu menjelaskan tahapan dan parameter yang digunakan pada proses pemodelan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan kelebihan dan kekurangan dari setiap algoritma yang digunakan.
- Jika menggunakan satu algoritma pada solution statement, lakukan proses improvement terhadap model dengan hyperparameter tuning. **Jelaskan proses improvement yang dilakukan**.
- Jika menggunakan dua atau lebih algoritma pada solution statement, maka pilih model terbaik sebagai solusi. **Jelaskan mengapa memilih model tersebut sebagai model terbaik**.

## Evaluation
Pada bagian ini anda perlu menyebutkan metrik evaluasi yang digunakan. Lalu anda perlu menjelaskan hasil proyek berdasarkan metrik evaluasi yang digunakan.

Sebagai contoh, Anda memiih kasus klasifikasi dan menggunakan metrik **akurasi, precision, recall, dan F1 score**. Jelaskan mengenai beberapa hal berikut:
- Penjelasan mengenai metrik yang digunakan
- Menjelaskan hasil proyek berdasarkan metrik evaluasi

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

## Deployment
pada bagian ini anda memberikan link project yang diupload melalui streamlit share. boleh ditambahkan screen shoot halaman webnya.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.

