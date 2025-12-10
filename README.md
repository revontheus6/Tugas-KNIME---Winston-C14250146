# 🚗 Analisis Data Toyota Corolla – KNIME Machine Learning Workflow

Repository ini berisi workflow KNIME untuk melakukan analisis dan prediksi harga mobil Toyota Corolla. Workflow mencakup proses data preprocessing, feature engineering, model training, dan model evaluation menggunakan algoritma Decision Tree dan Random Forest.

Tujuan utama proyek ini adalah memahami faktor-faktor yang memengaruhi harga mobil serta membangun model prediksi yang akurat dan mudah direplikasi.

# 📊 Dataset

Dataset berisi 1.436 baris data mobil Toyota Corolla yang dijual pada pasar Eropa.
Tiap baris merepresentasikan satu unit kendaraan dengan informasi teknis maupun kondisi mobil.

Kolom penting mencakup:

Price — harga jual mobil (target prediksi)

Age — usia mobil dalam bulan

KM — jarak tempuh (kilometer)

HP — tenaga mesin

Fuel Type — kategori bahan bakar

MetColor — metallic color (0/1)

Automatic — status transmisi

Gears, Doors, Weight

Dan fitur teknis lainnya

Dataset memiliki kombinasi numerik dan kategorikal, sehingga perlu dilakukan beberapa tahap processing sebelum model dijalankan.

# 🔧 Data Preparation

Tahap ini bertujuan memastikan data bersih, konsisten, dan siap digunakan untuk model ML.

1. Missing Value Handling

Missing value pada kolom numerik diisi menggunakan mean.

Teknik ini digunakan agar dataset tetap lengkap tanpa menghapus baris.

Menghindari bias terhadap model yang peka terhadap missing entries.

2. Column Filtering

Membersihkan kolom yang tidak relevan, redundant, atau tidak diperlukan model.

Mengurangi kompleksitas dan memperbaiki performa model.

3. Encoding Fitur Kategorikal

Fitur seperti Fuel Type, Doors, dan beberapa atribut kategorikal lain di-encode menggunakan One-Hot Encoding.

Encoding diperlukan agar model ML memahami kategori sebagai representasi numerik.

4. Normalisasi / Transformasi Fitur (opsional)

Beberapa fitur dapat dinormalisasi jika memengaruhi kinerja algoritma tertentu.

Normalisasi tidak dilakukan pada target karena harga tetap harus dalam satuan asli.

5. Data Splitting

Pembagian dataset menggunakan node Partitioning:

Training set: 80%

Testing set: 20%

Random sampling dengan fixed seed untuk hasil yang konsisten setiap run.

Pembagian ini memastikan model memiliki cukup data untuk belajar, namun tetap menyisakan data independen untuk evaluasi.

# 🤖 Modeling

Workflow menggunakan dua algoritma utama:

1. Decision Tree Regression

Model dasar yang mudah dipahami dan divisualisasikan.

Memberikan gambaran hierarki faktor yang memengaruhi harga.

Menghasilkan pohon keputusan yang dapat diekspor atau divisualisasikan di KNIME.

2. Random Forest Regression

Model ensemble yang menggabungkan banyak Decision Tree.

Lebih stabil, lebih akurat, dan lebih tahan terhadap noise.

Sering menjadi baseline regression model yang kuat.

Random Forest biasanya mengungguli Decision Tree pada dataset dengan banyak variabel seperti ini.

# 📈 Evaluasi Model

Beberapa metrik evaluasi yang digunakan:

MAE (Mean Absolute Error)
Mengukur rata-rata kesalahan absolut antara prediksi dan nilai sebenarnya.

RMSE (Root Mean Squared Error)
Lebih sensitif terhadap outlier; semakin kecil semakin baik.

R² Score
Menunjukkan seberapa besar variasi harga dapat dijelaskan oleh model.

Perbandingan umum yang ditemukan:

Decision Tree → lebih mudah diinterpretasi tapi cenderung overfit

Random Forest → memberikan error lebih rendah dan prediksi lebih stabil

# 📝 Insight Utama


<img width="1580" height="980" alt="image" src="https://github.com/user-attachments/assets/891347db-d49b-44d2-8704-c5e52fe13d7f" />

🔍 Insight dari Grafik Tren Harga Mobil 1998–2004

Harga mobil menunjukkan tren kenaikan yang stabil setiap tahun.
Dari 1998 hingga 2004, grafik memperlihatkan peningkatan rata-rata harga kendaraan tanpa adanya penurunan, mencerminkan pola pertumbuhan konsisten.

Lonjakan harga terbesar terjadi antara 1999–2000 dan 2001–2002.
Dua periode ini mengalami peningkatan tajam, yang mengindikasikan adanya faktor eksternal seperti inovasi teknologi besar, perubahan pasar, atau kenaikan signifikan biaya produksi.

Kenaikan harga setelah 2002 tetap terjadi tetapi lebih landai.
Ini menunjukkan bahwa pasar mulai mencapai stabilitas setelah fase pertumbuhan cepat.

<img width="1580" height="980" alt="image" src="https://github.com/user-attachments/assets/041fe207-a82c-4065-82b5-8ab6c3070c54" />


<img width="1580" height="980" alt="image" src="https://github.com/user-attachments/assets/2b02c4cf-f422-4d9c-aa15-7d6ab4967a18" />

Grafik bar chart menunjukkan perubahan rata-rata harga mobil dari tahun 1998 hingga 2004. Terlihat bahwa setiap batang semakin tinggi seiring bertambahnya tahun, yang berarti harga mobil mengalami peningkatan konsisten dari tahun ke tahun. Kenaikan paling signifikan tampak pada periode 1999–2000 dan 2001–2002, di mana harga melonjak cukup tajam dibanding tahun-tahun sebelumnya. Pola ini menggambarkan adanya faktor-faktor seperti inflasi, peningkatan fitur kendaraan, teknologi mesin yang semakin maju, dan perubahan tren pasar yang menyebabkan harga mobil terus naik. Secara keseluruhan, bar chart menegaskan bahwa tahun produksi memiliki hubungan langsung dengan tinggi-rendahnya harga, di mana mobil keluaran tahun lebih baru selalu berada pada kategori harga yang lebih tinggi.

Tren keseluruhan menunjukkan bahwa tahun produksi memiliki pengaruh kuat terhadap harga.
Semakin baru tahun produksi, semakin tinggi kisaran harga rata-ratanya.

Hasil analisis menunjukkan:

Age adalah faktor paling signifikan: mobil yang lebih tua memiliki harga lebih rendah.

KM (kilometer) juga sangat berpengaruh—semakin tinggi KM, semakin turun harga.

HP (tenaga mesin) dan variabel teknis lain turut memengaruhi harga, namun efeknya tidak sebesar Age dan KM.

Mobil dengan warna metallic, mesin lebih bertenaga, dan kondisi lebih baik cenderung memiliki harga lebih tinggi.

Model Random Forest berhasil mempelajari pola ini dengan cukup baik dibandingkan Decision Tree.

# 📊 Visualisasi & Analisis Tambahan

Beberapa visualisasi yang dapat dilihat dalam workflow:

Distribusi KM, Age, dan Price

Scatter plot hubungan fitur vs Price

Korelasi antar fitur

Feature importance dari Random Forest

Error plot atau residual analysis

Visualisasi ini membantu memahami karakteristik data dan perilaku model.

# ▶️ Cara Menjalankan Workflow

Install dan buka KNIME Analytics Platform

Import file workflow .knwf

Pastikan path dataset sesuai pada node CSV Reader

Jalankan workflow dari awal (click Execute all upstream nodes)

Lihat hasil prediksi, grafik, dan evaluasi pada node output seperti:

Random Forest Predictor

Scorer / Numeric Scorer

Table View / Histogram

# 🗂 Struktur Repository
📁 data/         → Dataset mentah atau hasil preprocessing  
📁 workflow/     → File workflow KNIME (.knwf)  
📁 output/       → Grafik, evaluasi, dan file hasil model (opsional)  
README.md        → Dokumentasi ini  

# 📝 Kesimpulan

Analisis data Toyota Corolla menggunakan workflow KNIME memberikan gambaran komprehensif mengenai faktor-faktor yang mempengaruhi harga mobil serta efektivitas model prediksi yang digunakan. Dengan memanfaatkan empat fitur utama seperti Price (target), Age, KM, dan HP, model dapat mempelajari pola harga dengan cukup baik meskipun jumlah fitur yang digunakan relatif sedikit.

Dari hasil preprocessing dan eksplorasi, terlihat bahwa Age (usia mobil) dan KM (jarak tempuh) merupakan variabel yang paling menentukan dalam penurunan harga. Mobil yang lebih tua dan memiliki kilometer tinggi menunjukkan penurunan nilai yang signifikan, menggambarkan pola depresiasi alami kendaraan. HP (tenaga mesin) memiliki pengaruh tambahan terhadap harga, di mana mobil dengan tenaga lebih besar cenderung lebih bernilai, meskipun kontribusinya tidak sebesar Age dan KM.

Dalam pemodelan, Decision Tree memberikan interpretasi awal yang mudah dipahami namun rentan overfitting. Sementara Random Forest terbukti lebih unggul dengan error yang lebih rendah dan stabilitas prediksi yang lebih baik. Model ini mampu menangkap hubungan non-linear antar fitur dan mengurangi fluktuasi yang muncul pada model pohon tunggal.

Proses workflow KNIME secara keseluruhan bekerja sangat baik dalam menangani seluruh tahapan: mulai dari cleaning, transforming, partitioning, hingga evaluasi. Penggunaan node seperti Missing Value, Column Filter, One-Hot Encoder, dan Partitioning (80/20) memastikan data yang digunakan bersih, representatif, dan sesuai untuk pemodelan.

Secara keseluruhan, kombinasi fitur Age, KM, dan HP sudah cukup memberikan gambaran kuat mengenai nilai pasar Toyota Corolla. Penggunaan Random Forest sebagai model utama memberikan hasil prediksi yang akurat serta mudah direplikasi dalam workflow. Hasil ini menunjukkan bahwa model regresi berbasis ensemble efektif digunakan untuk masalah prediksi harga kendaraan dengan dataset sederhana maupun terbatas.
