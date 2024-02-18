# CALIFORNIA HOUSING PRICE

### Referensi

1. Dataset : https://drive.google.com/drive/folders/19YA_f36uGR86hTnZuX-Ech59s3AFzXXo?q=parent:19YA_f36uGR86hTnZuX-Ech59s3AFzXXo

2. Penjelasan California : https://id.wikipedia.org/wiki/California

3. Berita rumah penduduk California : https://www.detik.com/properti/berita/d-7060568/mayoritas-penduduk-california-baru-punya-rumah-di-atas-usia-49-tahun-kok-bisa

4. Metric Evaluation : https://www.trivusi.web.id/2023/03/perbedaan-mae-mse-rmse-dan-mape.html
5. Kategori Income : https://www.cekindo.com/blog/upper-middle-income-status

### Contents

1. Business Problem Understanding
2. Data Understanding
3. Data Preprocessing
4. Modeling
5. Conclusion
6. Recommendation

# Business Problem Understanding

### Context

California Housing Price adalah sebuah Dataset yang berisi mengenai data kependudukan dan perumahan di California dari sensus pada 1990. California sendiri merupakan negara bagian yang ada di Amerika Serikat barat dengan Scramento sebagai ibukotanya. Saat ini total penduduk California mencapai 39,2 juta jiwa. Luas negara bagian California yaitu 163.696 mil persegi (423.970 km2) [2].
Tingginya harga rumah di California berdampak pada mayoritas penduduk baru memiliki rumah diatas usia 49 Tahun [3]. Hal ini dikarenakan harga rumah di California mengalami kenaikan besar - besaran dan melampaui pendapatan dari penduduknya. Tidak hanya permasalahan jumlah penduduk yang kepemilikan rumah menurun, bahkan untuk penduduk yang sudah memiliki rumah masih terkendala untuk melunasi cicilannya. Oleh sebab itu diperlukan referensi acuan harga rumah yang sesuai dengan sepesifikasi rumah, lokasi dll.

### Problem Statement

Sesuai informasi diatas memang rata - rata penduduk California memiliki rumah diatas usia 49 Tahun, namun tidak menutup kemungkinan bahwa ada rezeki yang diperoleh. Apalagi mendapatkan rumah yang sesuai dengan keinginan, budget, lokasi, dan spesifikasi yang sesuai dapat memakan waktu yang lama. Jika harga rumah rendah dari pasaran memang akan menguntungkan bagi pembeli, namun berdampak pada pendapatan penjual yang berkurang. Sebaliknya jika harga rumah tinggi, maka pembeli akan ragu dan akan berpikir sangat lama untuk menetukan keputusan. **Agar memudahkan penduduk California baik penjual maupun pembeli maka perlu adanya referensi harga acuan rumah yang tepat**.

### Goals

Berdasarkan masalah tersebut. Tentu perusahaan penyedia jasa penjualan rumah memiliki tools yang dapat memprediksi dan membantu untuk dapat menentukan harga rumah di California. **Dengan adanya tools model ini diharapkan dapat membantu penjual dan pembeli sebagai alat pendukung keputusan dalam menjual dan membeli rumah**.

### Analytic Approach

Jadi, yang perlu kita lakukan adalah menganalisis data untuk dapat menemukan pola dari fitur-fitur yang ada pada dataset. Selanjutnya, kita akan membangun suatu model regresi yang bertujuan untuk menetukan harga, dan model metric mana yang terbaik.

### Metric Evaluation

Metric Evaluation yang akan dibuat yaitu :

1. Root Mean Squared Error (RMSE) : menghitung rata-rata dari selisih kuadrat antara nilai prediksi dan nilai aktual kemudian diambil akar kuadratnya.
2. Mean Absolute Error (MAE) : menghitung rata-rata dari selisih absolut antara nilai prediksi dan nilai aktual.
3. Mean Absolute Percentage Error (MAPE) : menghitung rata-rata dari selisih persentase antara nilai prediksi dan nilai aktual.
4. R-Square: mengukur kemampuan model dalam menjelaskan hasil prediksi

Selain itu, kita akan menggunakan R Square yang digunakan untuk mengukur kemampuan model untuk menjelaskan hasil prediksi

# Data Understanding

Dataset ini berisi informasi terkait data kependudukan dan perumahan di California dari sensus 1990, yaitu:

-	longitude
-	latitude
-	Housing median age
-	total_rooms
-	total_bedrooms
-	population
-	households
-	median_income
-	median house value
-	ocean_proximity

Secara garis besar kita mendapat informasi sebagai berikut :

1. Dataset memiliki 10 kolom dan 14.448 baris.
2. Kolom longitude dan Latitude adalah kolom unik yang saling berkaitan, karena jika kedua kolom digabung akan menjadikan koordinat lokasi.
3. Dari semua field data, Ocean proximity adalah satu satunya tipe object. Karena berisi dan menjelaskan mengenai lokasi berada.

Secara garis besar kita mendapatkan informasi :
1. Rentang usia perumahan yang tersebar di California yaitu 10 hingga 50 tahun.
2. Pendapatan penduduk yang berada di pinggir laut terindikasi lebih tinggi.
3. Harga perumahan di daerah dekat laut, pulau, dan teluk realtif lebih tinggi dibandingkan INLAND 

Secara garis besar kita mmeperoleh informasi bahwa ritme jumlah Housing, households, dan POpulation berdasatkan Ocean Proximity memiliki pola yang sama, yaitu jumlah <1H Ocean menjadi yang terbanyak, diikuti Inland, Near Ocean, Near Bay, dan Island.

0.945228% jumlah baris yang kosong yaitu sebanyak 137 Baris. Dikarenakan persentase yang kecil dan juga memperhitungkan efisiensi kerja, kita akan melakukan penghapusan untuk data tersebut. Sehingga tidak diperlukan treatment khusus.

Didapatkan informasi bahwa Housing Median Age untuk nilai 52 tahun sangat tinggi dibandingkan yang lain. Diasumsikan bahwa petugas sensus memberi nilai 52 tahun untuk nilai yang lebih dari 50. Untuk meminimalisir bias, maka kita akan menghapusnya.

Berdasarkan hasil evaluasi diatasdi dapat bahwa terdapat 3 model yang baik, yaitu, Linear Regresion, Random Forest dan  XGBOOST. Selanjutnya kita akan membandingkan ketiga model tersebut pada prediksi dataset X test.


Hasil prediksi menunjukkan bahwa XGB lebih unggul dalam memprediksi, dengan evaluasi metrik sbb :
- RMSE = 45171, nilai error antara prediksi dan nilai sebenarnya adalah USD 45171 USD
- MAE = 30334, nilai absolut error prediksi adalah USD 30334.
- MAPE = 0.177, nilai error prediksi dari nilai sebenarnya adalah 0.177%

Model mengalamai kenaikan performance :
1. RMSE : terjadi penurunan jumlah sebesar 969.378121
2. MAE : terjadi penurunan jumlah sebesar 309.718411
3. MAPE : terjadi pengingkatan persentasi mape 0.002174


Secara gari besar, semakin tinggi nilai independent variable  maka akan berkontribusi positif serta dependent variable juga akan naik. Korelasi negatif antara independent variable dengan dependent variable akan berbanding terbalik dari korelasi positif dimana semakin tinggi nilai independent variable maka akan berkontribusi kepada semakin rendahnya nilai dependent variable, dan sebaliknya.

# Conclusion

1. Diantara 3 model regresi, XGBoost terbukti adalah model regresi dalam memberikan prediksi nilai rumah pada dataset ini.
2. Variabel penting pada dataset yaitu One Hot Ocean Proximity Inland.
3. hasil perbandingan antara model XGBoost sebelum tunning dan setelah tunning, didapatkan hasil performanya mengalami kenaikan untuk semua aspek (RMSE, MAE, dan MAPE). hal ini terbukti karena memang fungsi dari data tunning yaitu untuk mencari nilai optimal dan memperbaiki kinerja model.
4. Hasil dari R-square seteleh proses Tunning didapat R-Square 0.787%.

5. # Recomendation

1. Penelitian selanjutnya dapat menambah dan memberikan kategori - kategori yang lebih relefan dan berkaitan satu sama lainnya.
2. melibatkan penggunaan regresi yang lebih banyak lagi, sehingga akan menemukan regresi yang terbaik.
3. menggunakan variasi model yang lebih banyak. terlebih menggunakan model yang memang lebih cocok untuk penentuan harga.

