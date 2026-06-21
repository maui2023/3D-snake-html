**PROMPT UNTUK MENJANA PERMAINAN SNAKE 3D CYBERPUNK LENGKAP**

Tulis satu fail HTML5 lengkap bernama `snake3d.html` yang mengandungi struktur HTML, gaya CSS, dan logik JavaScript (Three.js) untuk membina permainan **Snake 3D - Cyberpunk Edition**. Permainan ini mesti boleh dijalankan secara terus dalam pelayar web tanpa sebarang backend.

---

### **Spesifikasi Reka Bentuk & Kawalan**

#### **1. Reka Bentuk UI & Responsif (CSS)**
- **Warna & Tema**: Cyberpunk Gelap. Gunakan pembolehubah CSS:
  - `--bg-color: #060612` (latar belakang malam gelap).
  - `--neon-green: #39ff14`, `--neon-red: #ff0055`, `--neon-blue: #00f0ff`, `--neon-yellow: #ffea00`.
  - `--glass-bg: rgba(10, 10, 25, 0.6)` dan `--glass-border: rgba(255, 255, 255, 0.1)`.
- **Gaya Glassmorphic**: HUD panel, kad menu, dan butang kawalan mestilah mempunyai kesan `backdrop-filter: blur(12px)` dengan sempadan nipis bersinar neon.
- **Responsif Skrin**:
  - **Skrin Desktop (Lebar > 768px)**: Canvas Three.js memenuhi ruang skrin penuh (`height: calc(100% - 32px)` untuk mengelakkan pertindihan marquee di bawah).
  - **Skrin Mudah Alih (Lebar ≤ 768px)**:
    - **Kawasan Permainan (`#canvas-container`)**: Tinggi dihadkan kepada **55%** dari tinggi viewport.
    - **Panel D-Pad Maya (`#mobile-controller`)**: Dipaparkan di bahagian bawah (**45%** tinggi viewport, di atas marquee) dengan latar belakang gelap.
    - **Bottom HUD (`#bottom-hud`)**: Dinaikkan ke atas dengan kedudukan `bottom: calc(45% + 15px)` supaya tidak bertindih dengan D-Pad maya.
- **Info Bergerak (Marquee)**: Di bahagian paling bawah skrin (`bottom: 0`, tinggi 32px), bina marquee yang memaparkan teks dengan warna neon kuning. Teks ini mestilah dibaca secara dinamik daripada fail `info.txt` menggunakan panggilan `fetch()` dengan teks sandaran (*fallback*) jika fail gagal dibaca.

#### **2. D-Pad Maya (Virtual Controller)**
- Hanya terpapar pada peranti mudah alih (skrin ≤ 768px).
- Reka letak berbentuk salib (cross layout):
  - Butang **Up** (▲) di atas, **Down** (▼) di bawah (warna hijau neon, border menyala).
  - Butang **Left** (◀) di kiri, **Right** (▶) di kanan (warna cyan neon, border menyala).
  - Butang tengah kosong sebagai pemisah bulatan glassmorphic.
- Butang mestilah responsif terhadap sentuhan (`touchstart`) dan klik tetikus (`mousedown`).
- Tambahkan panggilan `e.preventDefault()` pada event sentuhan dengan parameter `{ passive: false }` untuk menghalang gerak isyarat skrol (*scrolling*) dan zum (*zooming*) pelayar web semasa bermain.

#### **3. Pemandangan 3D & Arena (Three.js)**
- **Kamera & Auto-Zoom Dinamik**:
  - Kamera perspektif standard diletakkan secara isometrik.
  - Untuk peranti mudah alih atau mod menegak (portrait), kamera ditolak ke belakang secara dinamik menggunakan formula:
    `zoomFactor = Math.max(1.0, 1.75 / aspect)`
  - Skalakan kedudukan kamera `(0, 14.5 * zoomFactor, 14.5 * zoomFactor)` dan sasaran kawalan `(0, -2.2 * zoomFactor, 1.8 * zoomFactor)` supaya keseluruhan grid board 3D muat sepenuhnya di dalam skrin tanpa terpotong di kiri/kanan.
- **Pencahayaan & Kitaran Siang/Malam**:
  - Pencahayaan menggunakan Ambient Light dan Directional Light (dengan Shadow Map yang lembut).
  - Latar belakang scene, ambient light, dan directional light mestilah berubah warna secara beransur-ansur (*color morphing*) mengikut masa (kitaran siang/malam bertema neon biru, neon magenta, dan neon hijau).
- **Platform Arena**:
  - Platform bersaiz $20 \times 20$ grid.
  - Jubin grid dihasilkan secara prosedural menggunakan 2D canvas texture (jubin hitam `#0a0a20` dengan garisan pembahagi cyan separa telus).
  - Sempadan platform dihiasi dengan pagar neon 3D bercahaya cyan yang menghasilkan bayang pada platform.

#### **4. Reka Bentuk Objek Realistik 3D**
- **Ular (Snake)**:
  - **Kepala**: Merupakan kumpulan objek 3D terdiri daripada Rahang Atas (Upper Jaw) sfera yang dispesifikasikan saiznya, Rahang Bawah (Lower Jaw) sfera yang boleh bergerak, sepasang mata bersinar amber dengan anak mata hitam, dan lidah merah bercabang.
  - **Badan**: Segmen-segmen badan ular berbentuk sfera dengan warna kuning terang neon (`#ffea00`) yang kelihatan menyala malap dalam gelap.
  - **Pergerakan**: Pergerakan ular mestilah licin dengan animasi interpolasi linear (lerping) antara selang masa logik tick (tidak melompat dari petak ke petak secara kasar).
  - **Animasi Mengunyah (Chewing)**: Apabila makan, cetuskan animasi rahang bawah membuka/menutup dan lidah bergerak keluar/masuk.
- **Makanan (Food - Katak 3D)**:
  - Makanan digambarkan sebagai katak 3D ringkas yang dibina menggunakan kumpulan sfera berwarna merah bercahaya (badan, sepasang mata, kaki kecil).
  - Tambahkan animasi katak terapung (hover) naik-turun secara dinamik dan berputar perlahan-lahan.

#### **5. Logik Permainan & Sistem Sokongan**
- **Kitaran Game Loop**:
  - Mengandungi tiga fasa keadaan: `START`, `PLAYING`, dan `GAMEOVER`.
  - Logik tick pergerakan bermula pada 200ms dan menjadi lebih laju secara progresif berdasarkan markah yang dikumpul.
- **Leaderboard Tempatan**:
  - Menyimpan 5 skor tertinggi menggunakan `localStorage`.
  - Jika mencapai skor rekod baru semasa Game Over, paparkan borang input untuk pemain memasukkan nama mereka.
- **Kesan Bunyi (Web Audio API)**:
  - Bunyi makan: Frekuensi menaik mendadak secara eksponen.
  - Bunyi Game Over: Bunyi buzz mendatar rendah yang malap.
  - Sediakan butang Mute Bunyi dalam HUD bawah yang mengemas kini teks dan ikon.
- **Minimap & FPS**:
  - Minimap 2D bulat di penjuru atas memaparkan kedudukan grid 2D ular (kepala hijau, badan kuning) dan makanan (merah).
  - Kaunter FPS dinamik dipaparkan dalam HUD bawah.

---

### **Struktur Kod JavaScript**
Bina kod menggunakan pengaturcaraan berorientasikan objek (OOP) dengan kelas-kelas berikut:
1. `SoundEffects` - Mengawal kesan bunyi synth Web Audio API.
2. `ParticleSystem` - Letupan partikel neon magenta apabila ular makan katak.
3. `Food` - Mengawal visual 3D katak, spawns rawak (mengelakkan badan ular), dan animasi terapung.
4. `Snake` - Menguruskan koordinat grid segmen ular, visual kepala & badan kuning, lerping pergerakan, dan kemas kini visual.
5. `Game` - Menguruskan logik kitaran permainan, Three.js scene, OrbitControls, pengiraan zoom aspect ratio, papan pendahulu, minimap, kitaran siang/malam, dan loop animasi utama.

Hasilkan kod lengkap yang kemas, berprestasi tinggi, dan terus boleh dimainkan sebaik sahaja disimpan sebagai `snake3d.html`.