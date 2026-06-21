# Snake 3D - HTML5 & Three.js

Sebuah permainan klasik "Snake" yang diberi nafas baru dalam dimensi 3D yang moden, dinamik, dan interaktif. Permainan ini dibina sepenuhnya menggunakan HTML5, CSS3, JavaScript, dan pustaka **Three.js** untuk pemaparan grafik 3D. Seluruh kod permainan terkandung di dalam satu fail HTML sahaja, memudahkan ia dijalankan terus pada mana-mana pelayar web moden tanpa memerlukan sebarang pemasangan server atau backend.

---

## 🌟 Ciri-ciri Utama

* **Grafik 3D Penuh**: Arena, ular (blok kubus), dan makanan (sfera bercahaya) dipaparkan dalam ruang 3D dengan pencahayaan dan bayang yang realistik (shadow mapping).
* **Kesan Khas & Glow**: Makanan mempunyai kesan pencahayaan emissive (glow effect).
* **Sistem Partikel**: Kesan partikel dinamik yang meletus setiap kali ular memakan makanan.
* **Pergerakan Licin**: Animasi pergerakan ular yang diinterpolasikan untuk mengelakkan pergerakan yang tersangkut-sangkut.
* **FPS Counter**: Pengesan kadar bingkai sesaat untuk memantau prestasi permainan secara langsung.
* **Antara Muka (UI) Moden**: HUD untuk paparan skor dan skrin Game Over yang bersih dengan butang Restart.
* **Struktur Kod Bersih**: Dibina dengan reka bentuk berorientasikan objek (OOP) menggunakan kelas-kelas JavaScript (`Game`, `Snake`, `Food`, `ParticleSystem`).

### 🎁 Ciri Bonus
* **Kawalan Kamera**: Putar dan zum pandangan menggunakan tetikus menerusi `OrbitControls`.
* **Minimap**: Paparan peta pandangan atas (2D top-down) untuk memudahkan perancangan pergerakan.
* **Kesan Cahaya Siang/Malam**: Pencahayaan persekitaran yang bertukar secara dinamik mengikut masa.
* **Kesan Bunyi (Web Audio API)**: Audio retro untuk aksi makan dan Game Over.
* **Leaderboard Tempatan**: Sistem skor tinggi yang disimpan secara automatik dalam `localStorage` pelayar web.

---

## 🎮 Kawalan Permainan

Permainan ini menggunakan papan kekunci untuk mengawal arah ular dan tetikus untuk kawalan kamera:

| Butang / Input | Fungsi |
| :--- | :--- |
| **W** | Bergerak ke depan |
| **S** | Bergerak ke belakang |
| **A** | Bergerak ke kiri |
| **D** | Bergerak ke kanan |
| **Klik kiri + Seret Tetikus** | Memutar kamera (OrbitControls) |
| **Scroll Tetikus** | Zum masuk / keluar |

---

## 🛠️ Teknologi yang Digunakan

* **HTML5** & **CSS3**: Struktur halaman dan tindihan antaramuka (UI Overlay).
* **JavaScript (ES6+)**: Logik permainan, fizik mudah, dan pengurusan keadaan (state management).
* **Three.js**: Pustaka 3D untuk menguruskan scene, kamera, pencahayaan, mesh, material, dan bayang.
* **OrbitControls.js**: Pustaka tambahan Three.js untuk kawalan interaktif kamera.

---

## 🚀 Cara Menjalankan Permainan

Permainan ini sangat mudah untuk dijalankan:

1. Dapatkan fail `snake3d.html` (kod penuh permainan).
2. Pastikan anda mempunyai sambungan internet (diperlukan untuk memuatkan pustaka Three.js daripada CDN).
3. Klik dua kali pada fail `snake3d.html` atau buka fail tersebut menggunakan mana-mana pelayar web moden (Google Chrome, Mozilla Firefox, Microsoft Edge, Safari, dll.).
4. Nikmati permainan!

---

## 📁 Struktur Fail Utama

* [prompt.md](file:///home/maui/github/3D-snake-html/prompt.md): Fail asal yang mengandungi spesifikasi dan keperluan permainan.
* [PRD.md](file:///home/maui/github/3D-snake-html/PRD.md): Dokumen Keperluan Produk yang memperincikan skop teknikal dan logik kelas permainan.
* [README.md](file:///home/maui/github/3D-snake-html/README.md): Fail ini, yang menerangkan maklumat umum projek dan cara penggunaannya.
