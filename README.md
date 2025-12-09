📘 Analisis Data Toyota Corolla

Dokumen ini berisi rangkuman proses analisis dan pemodelan pada dataset Toyota Corolla dengan sekitar 1.436 entri yang mencakup fitur teknis kendaraan, karakteristik model, serta variabel yang memengaruhi harga. Workflow dibangun menggunakan KNIME dengan kombinasi analisis statistik, pembersihan data, dan machine learning.

🔧 1. Persiapan dan Pengolahan Data
a. Penanganan Data Hilang

Sebelum model dilatih, dataset diperiksa untuk mendeteksi nilai kosong.

Nilai numerik yang hilang disubstitusi dengan nilai rata-rata kolom terkait.

Pendekatan ini menjaga keseragaman distribusi data sekaligus memastikan tidak ada baris penting yang dibuang.

b. Seleksi Kolom

Beberapa kolom yang tidak relevan atau tidak mendukung prediksi dihapus.

Proses ini menyisakan fitur inti seperti spesifikasi mesin, tahun kendaraan, tenaga, tipe bahan bakar, dan harga.

c. Pengolahan Fitur Kategorikal

Kolom kategori (fuel type, transmission, variant, dan lainnya) diubah menjadi format numerik menggunakan One-to-Many Encoding.

Setiap kategori dibuatkan kolom biner baru.

Tujuannya agar seluruh fitur dapat digunakan sebagai input untuk model seperti Decision Tree dan Random Forest.

d. Pembuatan Fitur Tambahan

Dengan node Math Formula, beberapa atribut dihitung ulang atau dibuat ulang (jika diperlukan oleh analisis).

Hal ini dilakukan untuk memperkaya data dan meningkatkan performa prediksi.

🤖 2. Proses Pembelajaran Model
a. Pembagian Dataset

Data dibagi menjadi dua subset menggunakan pemisahan acak:
