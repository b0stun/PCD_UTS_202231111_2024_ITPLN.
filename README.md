# PCD_UTS_202231111_2024_ITPLN.
#Penjelasan UTS pencit

1. MENGIMPOR LIBRARY

import cv2
import numpy as np
import matplotlib.pyplot as plt
import matplotlib.image as img
from IPython.display import Image

%matplotlib inline

Kode yang ada diatas merupakan beberapa pustaka Python yang umum digunakan:

1. `cv2`: Pustaka OpenCV, yang digunakan untuk pemrosesan citra.
2. `numpy as np`: NumPy, yang digunakan untuk operasi matematika dan manipulasi array.
3. `matplotlib.pyplot as plt`: Matplotlib, pustaka untuk membuat visualisasi seperti grafik, plot, dan gambar.
4. `matplotlib.image as img`: Modul Matplotlib untuk memanipulasi gambar.
5. `from IPython.display import Image`: IPython, yang digunakan untuk menampilkan gambar di dalam notebook.

Selain itu, `%matplotlib inline` adalah perintah ajaib Jupyter Notebook yang menjadikan plot matplotlib ditampilkan langsung di dalam notebook di bawah sel kode yang menghasilkannya. Itu memungkinkan Anda untuk melihat hasil plot tanpa memerlukan jendela pop-up terpisah.



2. MENDEKLARASIKAN GAMBAR 

color_image = img.imread('Namaku.jpg')
plt.imshow(color_image)

Kode yang Adalah kode  membaca gambar dengan nama file 'Namaku.jpg' menggunakan fungsi imread dari modul matplotlib.image dan kemudian menampilkan gambar tersebut menggunakan fungsi imshow dari matplotlib.pyplot.
Nama file 'Namaku' di masukkan sesuai nama yang ada dalam file



3. MENDEKLARASIKAN DAN MEMBAGI CITRA WARNA 

r = color_image[:, :, 0]
g = color_image[:, :, 1]
b = color_image[:, :, 2]

f, ((x1, x2, x3, x4)) = plt.subplots(1, 4, figsize=(20, 10))

x1.set_title('Citra Kontras')
x1.imshow(color_image)
x1.axis('off')

x2.set_title('Biru')
x2.imshow(b, cmap='gray')
x2.axis('off')

x3.set_title('Merah')
x3.imshow(r, cmap='gray')
x3.axis('off')

x4.set_title('Hijau')
x4.imshow(g, cmap='gray')
x4.axis('off')

plt.show()

jelaskan kode tersebut:

1. `r = color_image[:, :, 0]`, `g = color_image[:, :, 1]`, dan `b = color_image[:, :, 2]`: Membagi citra warna menjadi tiga saluran warna masing-masing untuk merah, hijau, dan biru.
  
2. `f, ((x1, x2, x3, x4)) = plt.subplots(1, 4, figsize=(20, 10))`: Membuat objek gambar dan empat subplot secara horizontal dengan ukuran total 20x10 inci. Subplot disimpan dalam variabel `x1`, `x2`, `x3`, dan `x4`.

3. Setiap subplot diberi judul dan gambar ditampilkan di dalamnya menggunakan fungsi `imshow`. Citra asli ditampilkan di subplot pertama, sementara salinan citra dengan masing-masing hanya menampilkan satu saluran warna (biru, merah, atau hijau) ditampilkan di subplot berikutnya. Pengaturan sumbu (axis) diatur ke 'off' untuk semua subplot agar sumbu tidak ditampilkan.

4. `plt.show()`: Menampilkan gambar lengkap yang berisi keempat subplot yang telah dikonfigurasi sebelumnya.

Ini adalah cara untuk membagi citra warna menjadi tiga saluran warna masing-masing dan menampilkan mereka dalam subplot terpisah dengan menggunakan matplotlib di jupyter/Python.



4. MENDEKLARASIKAN KEMBALI FILE 

color_image = cv2.imread('Namaku.jpg')

jelaskan kode tersebut:

1. `cv2.imread('Namaku.jpg')`: Ini adalah panggilan ke fungsi `imread` dari pustaka OpenCV (`cv2`). Fungsi ini digunakan untuk membaca gambar dari file yang disediakan. Parameter yang diberikan adalah nama file gambar, dalam hal ini 'Namaku.jpg'. Fungsi ini mengembalikan array NumPy yang mewakili gambar.

2. `color_image = cv2.imread('Namaku.jpg')`: Hasil dari fungsi `imread` disimpan dalam variabel `color_image`, yang akan berisi representasi citra warna dari file 'Namaku.jpg'.



5. MENGHITUNG DAN MENDEKLARASIKAN SETIAP WARNA

histogram_biru = cv2.calcHist([b], [0], None, [256], [0, 256])
histogram_hijau = cv2.calcHist([g], [0], None, [256], [0, 256])
histogram_merah = cv2.calcHist([r], [0], None, [256], [0, 256])
histogram_warna = cv2.calcHist([color_image], [0, 1, 2], None, [256, 256, 256], [0, 256, 0, 256, 0, 256])

jelaskan setiap baris kode:

1. `histogram_biru = cv2.calcHist([b], [0], None, [256], [0, 256])`: Ini adalah panggilan ke fungsi `calcHist` dari OpenCV (`cv2`). Fungsi ini digunakan untuk menghitung histogram dari saluran warna biru (variabel `b`) dari gambar. Parameter pertama adalah daftar dari saluran warna yang ingin dihitung histogramnya, parameter kedua adalah indeks dari saluran warna yang ingin dihitung (0 untuk saluran biru), parameter ketiga adalah maska (dalam kasus ini, None berarti tidak ada maska), parameter keempat adalah jumlah bin histogram (256 untuk 8-bit gambar), dan parameter kelima adalah rentang nilai piksel yang ingin dihitung histogramnya (dari 0 hingga 255).

2. `histogram_hijau = cv2.calcHist([g], [0], None, [256], [0, 256])`: Ini adalah panggilan yang serupa seperti di atas, tetapi untuk saluran warna hijau (variabel `g`).

3. `histogram_merah = cv2.calcHist([r], [0], None, [256], [0, 256])`: Ini adalah panggilan yang serupa seperti di atas, tetapi untuk saluran warna merah (variabel `r`).

4. `histogram_warna = cv2.calcHist([color_image], [0, 1, 2], None, [256, 256, 256], [0, 256, 0, 256, 0, 256])`: Ini adalah panggilan yang serupa seperti di atas, tetapi kali ini kita menghitung histogram untuk seluruh gambar warna. Parameter pertama adalah daftar dari saluran warna yang ingin dihitung histogramnya (0, 1, dan 2 untuk saluran biru, hijau, dan merah), parameter kedua adalah jumlah bin histogram untuk setiap saluran warna (256 untuk masing-masing saluran warna), dan parameter ketiga adalah rentang nilai piksel untuk setiap saluran warna (dari 0 hingga 255 untuk setiap saluran warna).

Jadi, dengan kode ini, kita menghitung histogram untuk saluran warna biru, hijau, dan merah secara terpisah, serta histogram untuk seluruh gambar warna.



6. MENAMPILKAN HISTOGRAM DARI MASING-MASING WARNA

plt.figure(figsize=(12, 8))

plt.subplot(2, 2, 1)  # Subplot 1 (atas kiri)
plt.plot(histogram_biru, color='b')
plt.title('Histogram Biru')
plt.xlim([0, 256])

plt.subplot(2, 2, 2)  # Subplot 2 (atas kanan)
plt.plot(histogram_hijau, color='g')
plt.title('Histogram Hijau')
plt.xlim([0, 256])

plt.subplot(2, 2, 3)  # Subplot 3 (bawah kiri)
plt.plot(histogram_merah, color='r')
plt.title('Histogram Merah')
plt.xlim([0, 256])

plt.subplot(2, 2, 4)  # Subplot 4 (bawah kanan)
plt.plot(histogram_warna.flatten(), color='gray')  # Flatten histogram multi-dimensi
plt.title('Histogram Warna')
plt.xlim([0, 256])

Dalam kode ini, kita menggunakan `plt.figure(figsize=(12, 8))` untuk membuat gambar dengan ukuran 12x8 inci.

Kemudian, kita menggunakan `plt.subplot(2, 2, 1)` untuk membuat subplot pertama di posisi (2 baris, 2 kolom) dan kita mengatur subplot saat ini ke subplot 1 (di atas kiri). Setelah itu, kita menggunakan `plt.plot` untuk membuat plot dari histogram biru dengan warna biru (`color='b'`). Judul plot diatur dengan `plt.title('Histogram Biru')` dan batas sumbu x diatur dengan `plt.xlim([0, 256])`.

Kemudian, langkah yang sama diulangi untuk subplot-subplot berikutnya (`subplot(2, 2, 2)`, `subplot(2, 2, 3)`, dan `subplot(2, 2, 4)`) dengan plot yang sesuai dan judul yang sesuai pula.

Pada subplot terakhir, kita menggunakan `histogram_warna.flatten()` untuk meratakan histogram warna multi-dimensi menjadi satu dimensi sebelum membuat plotnya. Ini dilakukan karena matplotlib hanya dapat membuat plot dari data satu dimensi.

Dengan kode ini, kita menghasilkan gambar dengan empat subplot yang menampilkan histogram dari saluran warna biru, hijau, dan merah, serta histogram untuk seluruh gambar warna.



7. KONTRAS GAMBAR

#Membaca gambar
color_image = cv2.imread('Namaku.jpg')

#Konversi citra ke dalam ruang warna HSV
hsv_image = cv2.cvtColor(color_image, cv2.COLOR_BGR2HSV)

#Definisikan rentang warna untuk setiap warna
lower_blue = np.array([90, 100, 100])
upper_blue = np.array([130, 255, 255])

lower_green = np.array([40, 100, 100])
upper_green = np.array([80, 255, 255])

lower_red1 = np.array([0, 100, 100])
upper_red1 = np.array([10, 255, 255])
lower_red2 = np.array([160, 100, 100])
upper_red2 = np.array([180, 255, 255])

#Deteksi warna biru
mask_blue = cv2.inRange(hsv_image, lower_blue, upper_blue)
#Deteksi warna hijau
mask_green = cv2.inRange(hsv_image, lower_green, upper_green)

#Deteksi warna merah
mask_red1 = cv2.inRange(hsv_image, lower_red1, upper_red1)
mask_red2 = cv2.inRange(hsv_image, lower_red2, upper_red2)
mask_red = cv2.bitwise_or(mask_red1, mask_red2)

#Gabungkan masker untuk warna merah dan biru
mask_red_blue = cv2.bitwise_or(mask_red, mask_blue)
# Gabungkan masker untuk warna merah dan biru
mask_red_blue_green = cv2.bitwise_or(cv2.bitwise_or(mask_red, mask_blue), mask_green)

#Plot hasil

#gambar 1
gray = cv2.cvtColor(color_image, cv2.COLOR_RGB2GRAY)
fig, axs = plt.subplots (2, 2, figsize=(10,10))

(thresh, binary1) = cv2.threshold(gray, 0, 0, cv2.THRESH_BINARY)
axs[0,0].imshow(binary1, cmap = 'gray')
axs[0,0].set_title('NONE')

#gambar 2
plt.subplot(2, 2, 2)
plt.imshow(mask_blue, cmap='gray')
plt.title('Blue')
plt.xticks(np.arange(0, mask_blue.shape[1]+1, 800))
plt.yticks(np.arange(0, mask_blue.shape[0]+1, 500))
plt.axis('on')

#gambar 3
plt.subplot(2, 2, 3)
plt.imshow(np.maximum(mask_red, mask_blue), cmap='gray')
plt.title('reed-blue')
plt.xticks(np.arange(0, mask_green.shape[1], 800))
plt.yticks(np.arange(0, mask_green.shape[0], 500))
plt.axis('on')

#gambar 4
plt.subplot(2, 2, 4)
plt.imshow(mask_red_blue_green, cmap='gray')
plt.title('Red-blue-green')
plt.xticks(np.arange(0, mask_green.shape[1], 800))
plt.yticks(np.arange(0, mask_green.shape[0], 500))
plt.axis('on')

#menampilkan output
plt.tight_layout()
plt.show()

Kode ini bertujuan untuk mendeteksi dan memvisualisasikan area di dalam gambar yang sesuai dengan rentang warna tertentu dalam ruang warna HSV (Hue, Saturation, Value).

Mari kita jelaskan setiap bagian dari kode tersebut:

1. `color_image = cv2.imread('Namaku.jpg')`: Membaca gambar dengan nama file 'Namaku.jpg' menggunakan OpenCV dan menyimpannya dalam variabel `color_image`.

2. `hsv_image = cv2.cvtColor(color_image, cv2.COLOR_BGR2HSV)`: Mengonversi citra warna dari format BGR (yang digunakan oleh OpenCV secara default) ke format HSV menggunakan fungsi `cvtColor` dari OpenCV.

3. Definisikan rentang warna untuk setiap warna (biru, hijau, dan merah) dalam ruang warna HSV menggunakan batas bawah (`lower_...`) dan batas atas (`upper_...`).

4. Deteksi warna biru, hijau, dan merah dalam gambar menggunakan fungsi `cv2.inRange`, yang menghasilkan masker biner yang menunjukkan area di mana warna tersebut ditemukan.

5. Gabungkan masker untuk warna merah dan biru menggunakan operasi bitwise OR, dan simpan hasilnya dalam variabel `mask_red_blue`.

6. Gabungkan masker untuk warna merah, biru, dan hijau menggunakan operasi bitwise OR, dan simpan hasilnya dalam variabel `mask_red_blue_green`.

7. Memplot hasil deteksi warna pada empat subplot:
   - Subplot pertama menampilkan citra dalam skala keabuan.
   - Subplot kedua menampilkan masker untuk warna biru.
   - Subplot ketiga menampilkan masker untuk kombinasi warna merah dan biru.
   - Subplot keempat menampilkan masker untuk kombinasi warna merah, biru, dan hijau.

8. Mengatur judul dan label sumbu pada setiap subplot.

9. `plt.tight_layout()`: Mengatur layout subplot agar tidak tumpang tindih.

10. `plt.show()`: Menampilkan gambar dengan empat subplot yang telah dikonfigurasi sebelumnya.

kode ini memberikan visualisasi tentang bagaimana cara deteksi warna berbeda diimplementasikan dalam ruang warna HSV, dan bagaimana operasi bitwise OR digunakan untuk menggabungkan hasil deteksi warna tersebut.
