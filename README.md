# kmeans-clustering
Sebagai peneliti yang ingin menganalisis distribusi alamat IP sumber dalam log jaringan, kita dapat menggunakan teknik clustering untuk mengidentifikasi pola atau kelompok alamat IP yang serupa. Dalam skenario ini, kita menggunakan algoritma K-Means clustering, yang merupakan teknik pembelajaran mesin tanpa pengawasan. Algoritma ini bertujuan untuk mempartisi n observasi menjadi k cluster di mana setiap observasi termasuk dalam cluster dengan rata-rata terdekat (yaitu, centroid cluster).

Berikut adalah terjemahan dari script Python yang diberikan, lengkap dengan penjelasan rumus matematika yang terkait:

1. **Ekstraksi Fitur Numerik dari Alamat IP**:
   - Pertama, kita memisahkan setiap segmen alamat IP (yang biasanya dipisahkan oleh titik) menjadi angka terpisah.
   $$ IP = a.b.c.d \rightarrow IP_{numeric} = [a, b, c, d] $$
   - Ini menghasilkan representasi numerik dari alamat IP yang dapat digunakan dalam perhitungan matematis.

2. **Normalisasi Data (Standard Scaling)**:
   - Menggunakan `StandardScaler` dari library sklearn untuk menskala fitur sehingga memiliki rata-rata 0 dan deviasi standar 1.
   $$ z = \frac{(x - \mu)}{\sigma} $$
   - Di mana \( \mu \) adalah rata-rata dan \( \sigma \) adalah deviasi standar.

3. **Menentukan Jumlah Cluster Optimal**:
   - Menggunakan skor siluet untuk mengevaluasi efektivitas jumlah cluster yang berbeda. Skor siluet mengukur seberapa serupa sebuah objek ke klusternya sendiri dibandingkan dengan kluster lain.
   $$ s = \frac{b - a}{max(a, b)} $$
   - Di mana \( a \) adalah jarak rata-rata sampel ke semua titik lain dalam cluster yang sama, dan \( b \) adalah jarak rata-rata sampel ke semua titik dalam cluster terdekat berikutnya.

4. **Visualisasi Skor Siluet**:
   - Membuat plot untuk menampilkan skor siluet untuk jumlah cluster dari 2 hingga 10, memungkinkan kita untuk memilih jumlah cluster dengan skor siluet tertinggi sebagai yang optimal.

5. **K-Means Clustering**:
   - Menerapkan K-Means dengan jumlah cluster optimal yang ditemukan.
   - Algoritma K-Means mencoba meminimalkan inersia dalam cluster, yaitu total jarak kuadrat dalam-cluster.
   $$ \text{Inersia} = \sum_{i=0}^{n}\min_{\mu_j \in C}(||x_i - \mu_j||^2) $$
   - Di mana \( x_i \) adalah titik data, \( \mu_j \) adalah centroid cluster, dan \( C \) adalah set centroid.

6. **Visualisasi Distribusi Alamat IP dalam Cluster**:
   - Setelah clustering, kita visualisasi jumlah alamat IP dalam setiap cluster untuk mendapatkan pemahaman tentang distribusi alamat IP yang diblokir.

Dengan mengikuti langkah-langkah ini, seorang peneliti dapat mengidentifikasi pola dalam lalu lintas jaringan yang diblokir, seperti apakah ada kelompok alamat IP yang menunjukkan perilaku serangan yang serupa. Ini dapat membantu dalam mengembangkan mekanisme pertahanan yang lebih baik dan dalam menargetkan investigasi keamanan lebih lanjut.
