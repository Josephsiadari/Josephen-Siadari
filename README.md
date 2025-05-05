# Penjelasan DataMining UTS_Josephen Siadari: Model Pohon Keputusan pada Dataset Digits

## Bagian pertama (Mempersiapkan data dan pelatihan model):

### `from sklearn import datasets`
**Import:** Mengimpor pustaka `datasets` dari `sklearn`, yang menyediakan berbagai dataset yang dapat digunakan untuk eksperimen machine learning, termasuk dataset `digits`.

### `dir(datasets)`
**Melihat atribut:** Menampilkan semua atribut dan fungsi yang ada dalam objek `datasets`. Ini memberikan informasi tentang fungsi atau dataset yang tersedia dalam pustaka tersebut.

### `data = datasets.load_digits()`
**Memuat dataset:** Fungsi `load_digits()` memuat dataset `digits`, yang berisi gambar 8x8 pixel angka (digit) dan labelnya. Dataset ini sering digunakan dalam klasifikasi citra.

### `dir(data)`
**Melihat atribut dalam data:** Melihat semua atribut yang tersedia dalam objek `data`. Ini akan menunjukkan informasi tentang data, seperti fitur dan targetnya.

### `data.data`
**Akses data fitur:** `data.data` berisi fitur (gambar angka yang dikonversi menjadi array satu dimensi dari pixel) yang digunakan untuk pelatihan model.

### `x = data.data`  
### `y = data.target`
**Membagi data:** Menyimpan fitur dalam variabel `x` dan target (label angka yang sesuai dengan gambar) dalam variabel `y`.

### `from sklearn.model_selection import train_test_split`
**Import:** Mengimpor fungsi `train_test_split` dari `sklearn.model_selection`, yang digunakan untuk membagi data menjadi data pelatihan dan data pengujian.

### `x_train, x_test, y_train, y_test = train_test_split(x, y, test_size=0.2, random_state=50)`
**Membagi dataset:** `train_test_split` membagi dataset menjadi data pelatihan (80%) dan data pengujian (20%), berdasarkan nilai `test_size=0.2`. `random_state=50` memastikan bahwa pembagian data tetap konsisten jika kode dijalankan berulang kali.

### `from sklearn.metrics import accuracy_score`
**Import:** Mengimpor `accuracy_score` dari `sklearn.metrics`, yang digunakan untuk mengukur akurasi model setelah pengujian.

### `from sklearn.tree import DecisionTreeClassifier`
**Import:** Mengimpor `DecisionTreeClassifier` dari `sklearn.tree`, yang digunakan untuk membangun model klasifikasi pohon keputusan.

### `model = DecisionTreeClassifier()`
**Inisialisasi model:** Membuat objek model pohon keputusan menggunakan `DecisionTreeClassifier`.

### `model.fit(x_train, y_train)`
**Melatih model:** Melatih model dengan data pelatihan (`x_train` dan `y_train`) menggunakan algoritma pohon keputusan.

### `y_pred = model.predict(x_test)`
**Prediksi:** Menggunakan model yang telah dilatih untuk memprediksi hasil pada data pengujian (`x_test`).

### `accuracy = accuracy_score(y_test, y_pred)`
**Menghitung akurasi:** Menghitung akurasi dengan membandingkan hasil prediksi (`y_pred`) dengan nilai asli dari data pengujian (`y_test`).

### `print(f"Akurasi: {accuracy* 100:.2f}%")`
**Menampilkan akurasi:** Mencetak akurasi model dalam persen dengan format dua angka di belakang koma.

---

## Bagian kedua (Plotting Pohon Keputusan):

### `from sklearn.datasets import load_digits`  
### `from sklearn.tree import DecisionTreeClassifier, plot_tree`  
### `import matplotlib.pyplot as plt`
**Import:** Mengimpor pustaka yang dibutuhkan untuk memuat dataset `digits`, membuat model pohon keputusan, dan menggambar visualisasi pohon keputusan dengan menggunakan `matplotlib`.

### `digits = load_digits()`
**Memuat dataset:** Memuat dataset `digits` lagi, mirip dengan langkah sebelumnya.

### `X = digits.data`  
### `y = digits.target`
**Menyimpan data dan target:** Menyimpan fitur (data citra) dalam variabel `X` dan target (label digit) dalam variabel `y`.

### `model = DecisionTreeClassifier(random_state=50)`
**Inisialisasi model:** Membuat objek model pohon keputusan dengan parameter `random_state=50`, yang memastikan hasil yang konsisten setiap kali kode dijalankan.

### `model.fit(X, y)`
**Melatih model:** Melatih model pohon keputusan menggunakan seluruh dataset (`X` dan `y`).

### `plt.figure(figsize=(40, 20))`
**Menyiapkan ukuran gambar:** Menyiapkan ukuran gambar (plot) untuk visualisasi pohon keputusan agar cukup besar untuk menampilkan seluruh pohon dengan jelas.

### `plot_tree(model, filled=True, feature_names=[f'Pixel {i}' for i in range(X.shape[1])], class_names=[str(i) for i in digits.target_names])`
**Plotting pohon keputusan:** Fungsi `plot_tree` digunakan untuk menggambar pohon keputusan. Parameter `filled=True` memberikan warna pada node berdasarkan kelas prediksi. `feature_names` adalah nama fitur yang dihasilkan berdasarkan indeks pixel, dan `class_names` adalah nama kelas (angka 0-9) yang sesuai dengan label digit.

### `plt.show()`
**Menampilkan plot:** Menampilkan gambar pohon keputusan yang telah digambar dengan `plot_tree`.
