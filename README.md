# Monk Defense — Prototype

Prototype playable (canvas) untuk game biksu defensif — kini **Active Time Battle (ATB) real-time** ala FF9.

## Jalankan
- Lokal: `python3 -m http.server` di folder ini, lalu buka `http://localhost:8000`.
- GitHub Pages: upload semua isi folder ke repo, Settings > Pages > Deploy from branch (root).

## Struktur
- `index.html`, `style.css` — halaman dan styling
- `game.js` — logika game (aturan, AI musuh, spawn grapple, input, render)
- `assets.js` — daftar aset (path PNG + aspect ratio)
- `assets/` — sprite, kartu, ikon intensi

## Sistem ATB
- Setiap karakter punya bar di bawahnya yang terisi otomatis. Biksu: 0→100% dalam 4 detik. Musuh: 5–7 detik (diacak ulang tiap putaran).
- Musuh memilih aksi berdasarkan kondisi saat itu (ikon di kanan), lalu intensi itu terkunci. Saat bar penuh musuh menjalankannya apa pun yang terjadi (gagal jika terhalang, serangan kena siapa pun yang ada di tile target), baru kemudian memilih aksi berikutnya.
- Bar biksu penuh = boleh beraksi (gerak / putar / kartu / buang kartu). Aksi mengosongkan bar. Boleh tidak berbuat apa-apa dan menahan bar penuh sampai momen yang pas.
- Spawn musuh acak waktunya (tali grapple muncul, musuh naik ±3 detik kemudian). Gauge di atas tile tali menunjukkan kapan musuh naik (jadi merah di akhir).
- Tombol jeda (kiri atas) membekukan semua timer.
- Angka tuning ada di atas `game.js`: `PLAYER_MS, FOE_MIN, FOE_MAX, SPAWN_MIN, SPAWN_MAX, HOOK_MS, MAXF`.

## Kontrol
Swipe atas/bawah = gerak, kiri/kanan = putar. Drag kartu ke atas = pakai, drag ke bawah = buang semua.
Keyboard: panah, 1-3 untuk kartu, D untuk discard.
