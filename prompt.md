**PROMPT:**

Bina sebuah permainan "Snake 3D" menggunakan HTML5, CSS3 dan JavaScript (tanpa backend). Gunakan Three.js untuk rendering 3D.

Keperluan permainan:

* Semua kod dalam satu fail HTML yang boleh terus dijalankan dalam browser.
* Gunakan Three.js melalui CDN.
* Paparkan arena berbentuk grid 3D di atas platform.
* Ular terdiri daripada blok-blok kubus 3D.
* Kepala ular berwarna hijau terang, badan hijau gelap.
* Makanan berupa sfera merah bercahaya.
* Kamera perspektif 3D dengan sudut isometrik yang boleh melihat keseluruhan arena.
* Lampu ambient dan directional untuk menghasilkan bayang yang realistik.
* Arena bersaiz 20x20 petak.
* Ular bergerak secara automatik setiap beberapa milisaat.
* Kawalan:

  * W = ke depan
  * S = ke belakang
  * A = ke kiri
  * D = ke kanan
* Apabila ular makan makanan:

  * Panjang bertambah 1 segmen.
  * Skor bertambah.
  * Makanan muncul di lokasi rawak yang tidak bertindih dengan badan ular.
* Jika kepala melanggar badan sendiri:

  * Paparkan "GAME OVER".
  * Hentikan permainan.
* Jika kepala keluar arena:

  * Game Over.
* Paparkan UI skor menggunakan HTML/CSS di atas canvas.
* Tambahkan animasi licin menggunakan interpolation atau tweening.
* Tambahkan efek glow pada makanan.
* Tambahkan partikel kecil apabila makanan dimakan.
* Tambahkan bayang (shadow mapping).
* Paparkan FPS counter.
* Tambahkan butang Restart.
* Gunakan struktur kod yang kemas dengan class:

  * Game
  * Snake
  * Food
  * ParticleSystem
* Berikan komen pada bahagian penting kod.
* Hasil akhir mesti kelihatan seperti game 3D moden, bukan sekadar grid 2D yang dipaparkan dalam ruang 3D.

Bonus:

* Kamera boleh diputar dengan mouse menggunakan OrbitControls.
* Tambah minimap.
* Tambah kesan day/night lighting.
* Tambah bunyi menggunakan Web Audio API.
* Tambah leaderboard tempatan menggunakan localStorage.

Hasilkan kod lengkap yang terus boleh disimpan sebagai `snake3d.html` dan dimainkan tanpa pemasangan tambahan selain sambungan internet untuk CDN Three.js.