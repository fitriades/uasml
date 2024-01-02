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
Pertama kita import library yang dibutuhkan
```bash
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
import plotly.express as px
from sklearn.model_selection import train_test_split
from sklearn import tree
from sklearn.metrics import accuracy_score, confusion_matrix
from sklearn.tree import DecisionTreeClassifier, plot_tree
from sklearn.preprocessing import LabelEncoder, StandardScaler
from plotly.subplots import make_subplots
import pickle
```
selanjutnya kita import dataset nya
```bash
df = pd.read_csv("/content/hepatitis-data/hepatitis_csv.csv")
```
untuk lebih lengkap nya pada bagian ini bisa di cek pada bagian Jupyter Notebook pada repository ini

Selanjutnya kita bisa lakukan visualisasi data, contoh kita ingin mehilat jumlah kematiannya
```bash
class_counts = df['class'].value_counts()
plt.figure(figsize=(5, 5))
plt.pie(class_counts, labels=['Lived', 'Died'], autopct='%1.1f%%', colors=['skyblue', 'lightcoral'])
plt.title('Class Distribution')
plt.axis('equal')  # Equal aspect ratio ensures the pie chart is circular.

# Show the pie chart
plt.show()
```
![image](https://github.com/fitriades/uasml/assets/149255008/08de6428-086d-4d8f-8b40-1b16084d3626)

Kita juga bisa lihat penyebaran usia nya
```bash
plt.figure(figsize=(20, 10))
sns.displot(df.age, bins=40)
```
![image](https://github.com/fitriades/uasml/assets/149255008/43ac254b-3b61-4fdf-a939-a5e94f689d12)

selanjuta kita lihat tingkat bilirubin tertinggi di angka berapa
```bash
sns.kdeplot(df.bilirubin)
```
![image](https://github.com/fitriades/uasml/assets/149255008/0c6fd265-da74-4f1d-bfd3-43e2561d7830)

untuk lebih detailnya bisa di cek pada jupyter notebook pada repository ini.

Selanjutnya kita rubah kolom yang bertipe object dan boolean
```bash
cat_cols = df.select_dtypes(include = ['object', 'bool']).columns.to_list()
le = LabelEncoder()

for i in cat_cols:
    le.fit(df[i])
    df[i] = le.transform(df[i])
```
Kemudian jika sudah kita tinggal menentukan feature dan label


## Modeling
Kita tentukan feature dan lable terlebih dahulu
```bash
X = df.drop('class',axis=1)
y = df['class']
```
Lalu kita beri ketentuan untuk data test dan data train nya
```bash
X_train, X_test, y_train, y_test = train_test_split( X, y, test_size=0.3, random_state=0)
```
kita standarisasi data nya terlebih dahulu
```bash
scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)
```
lalu kita masukan algoritma decision tree kedalam modelnya
```bash
dtc = DecisionTreeClassifier(
    ccp_alpha=0.0, class_weight=None, criterion='entropy',
    max_depth=4, max_features=None, max_leaf_nodes=None,
    min_impurity_decrease=0.0, min_samples_leaf=1,
    min_samples_split=2, min_weight_fraction_leaf=0,
    random_state=42, splitter='best'
)

model = dtc.fit(X_train, y_train)

y_pred = dtc.predict(X_test)

dtc_acc = accuracy_score(y_test, dtc.predict(X_test))

print(f"Training Akurasi = {accuracy_score(y_train, dtc.predict(X_train))}")
print(f"Test Akurasi = {dtc_acc} \n")
```
```bash
Training Akurasi = 0.9351851851851852
Test Akurasi = 0.8085106382978723
```
Kita bisa lihat tingkat akurasi nya

## Evaluation
Kitalakukan penilaian dengan konfusion matrix
```bash
confusion_mat = confusion_matrix(y_test, y_pred)
plt.figure(figsize=(6, 6))
sns.heatmap(confusion_mat, annot=True, fmt="d", cmap="Blues", xticklabels=dtc.classes_, yticklabels=dtc.classes_)
plt.title('Confusion Matrix')
plt.xlabel('Predictions')
plt.ylabel('Actual')
plt.show()
```
![image](https://github.com/fitriades/uasml/assets/149255008/b5bb232f-91f1-423f-a815-aadeafd88165)

kita bisa lihat hasil visual dari algoritma tersebut
![image](https://github.com/fitriades/uasml/assets/149255008/077fd6e2-b501-4355-8209-c630702d5074)


## Deployment
[Klik disini](https://uasmld3.streamlit.app/)
![image](https://github.com/fitriades/uasml/assets/149255008/3f496ef9-45ba-452b-bf4b-377c2f40e583)


**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.

