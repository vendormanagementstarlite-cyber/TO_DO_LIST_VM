# Dashboard To Do List VM

Dashboard web untuk "To Do list VM". Halaman ini statis (hanya `index.html` + `config.js`), data tetap
disimpan di Google Sheet dan diakses lewat Apps Script. Perubahan dari dashboard otomatis diumumkan ke grup WhatsApp.

## Pasang di GitHub Pages
1. Buat repo baru di GitHub (mis. `todo-vm`). Pilih **Private** bila ingin; GitHub Pages untuk repo private butuh paket berbayar, jadi untuk gratis pilih **Public** (data tetap aman: isi tugas tidak ada di repo, dan dashboard butuh kata sandi).
2. Unggah semua file di folder ini (`index.html`, `config.js`, `.nojekyll`, `README.md`) ke branch `main`.
3. `config.js` sudah berisi URL web app Anda (cek bila Anda membuat deployment baru).
4. Repo > **Settings > Pages > Build and deployment**: Source = *Deploy from a branch*, Branch = `main`, folder `/ (root)`, Save.
5. Tunggu 1-2 menit. Alamat dashboard: `https://<username>.github.io/<nama-repo>/`

## Sambungkan dengan bot
1. Di Apps Script, ganti isi `Code.gs` dan file `Dashboard` dengan versi terbaru, lalu **Deploy > Manage deployments > Edit > New version > Deploy**. Izinkan akses bila diminta.
2. Di **Project Settings > Script Properties** tambahkan `DASH_URL` = alamat GitHub Pages di atas (atau isi konstanta `DASH_URL` di `Code.gs`).
3. Pastikan `DASH_PASSWORD` sudah diisi.
4. Kirim satu pesan "BOT" di grup agar bot mengenali grup (untuk notifikasi).

Setelah itu setiap balasan bot diakhiri link dashboard, dan setiap tambah/ubah/hapus tugas di dashboard dikirim ke grup.

## Catatan
- Perubahan dari WhatsApp muncul di dashboard maksimal 1 menit (muat ulang otomatis), atau tekan "Muat ulang".
- Matikan notifikasi dashboard dengan `NOTIFY_DASH_CHANGES = false` di `Code.gs`; matikan link di balasan dengan `DASH_LINK_IN_REPLIES = false`.
