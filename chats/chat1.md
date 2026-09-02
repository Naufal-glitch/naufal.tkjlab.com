# Sistem Pengaduan Sarpras Sekolah

_Started 2026-09-02 09:06 UTC_

---

## User

"Buatkan desain antarmuka (UI/UX) berbasis web modern untuk Aplikasi Layanan Pengaduan Sarana Prasarana Sekolah dengan role akses untuk Siswa, Petugas/Admin Sarpras, dan Kepala Sekolah. Gunakan gaya desain bersih, profesional, dan ramah pengguna (clean & modern corporate style) dengan kombinasi warna primer biru tua dan aksen hijau terang.

Halaman yang perlu dirancang meliputi:

Dashboard Siswa: Menampilkan tombol 'Buat Pengaduan Baru', ringkasan status laporan (Menunggu, Diproses, Selesai), dan daftar riwayat tiket aduan dengan badge status berwarna.

Formulir Pengaduan: Input judul kerusakan, kategori sarpras (Kelas, Lab, Lapangan, Toilet), lokasi spesifik, deskripsi kendala, serta fitur unggah foto bukti kerusakan.

Dashboard Petugas Sarpras: Tabel manajemen pengaduan masuk, tombol aksi untuk mengubah status pengerjaan, serta kolom catatan perbaikan.

Halaman Detail Tiket: Menampilkan timeline atau riwayat progres penanganan laporan dari awal dibuat hingga selesai."

## Assistant

_[tool: list_files]_

_[tool: read_file]_

_[tool: read_file]_

Membangun satu Design Component dengan empat halaman + role switcher.

_[tool: dc_write]_

Baik — saya buang dashboard-nya. Satu halaman: landing + formulir yang mengirim ke email.

_[tool: dc_write]_

_[tool: ready_for_verification]_

Sudah diganti jadi satu halaman minimal: hero + 3 langkah + formulir pengaduan, tanpa dashboard.

Tombol "Kirim ke email Sarpras" membuka aplikasi email dengan subjek dan isi laporan sudah terformat (panel gelap di samping menampilkan pratinjaunya). Foto harus dilampirkan manual di email — halaman statis tidak bisa mengunggah berkas sendiri; kalau mau otomatis, perlu layanan form seperti Formspree.

Alamat email tujuan bisa diubah di panel Tweaks.

## User

sesuaikan untuk ui desktop dan android style dan maksimalkan UX

## Assistant

_[tool: copy_starter_component]_

_[tool: dc_write]_

_[tool: dc_write]_

_[tool: show_html]_

_[tool: ready_for_verification]_

Sekarang ada dua tampilan, dipilih dari tab "Pratinjau" di atas: **Desktop** (landing 1080px) dan **Android** (frame Material 3, konten sama).

Peningkatan UX pada formulir: indikator kelengkapan, validasi inline setelah field ditinggalkan, batas 400 karakter, chip kategori + urgensi dengan target sentuh ≥44px, tombol kamera langsung di Android, daftar foto yang bisa dihapus, dan draf tersimpan otomatis di perangkat.

Formulir kini file terpisah (Form Pengaduan.dc.html) supaya dipakai bersama kedua tampilan — edit di satu tempat, berubah di keduanya.

## User

yang landing page fokus di UI non formulir, baru nanti akan ke halaman buat pengaduan baru muncul formulir pengaduan

## Assistant

_[tool: dc_write]_

_[tool: dc_js_str_replace]_

_[tool: dc_set_props]_

_[tool: ready_for_verification]_

Landing page sekarang murni non-formulir: hero + alur laporan, tiga langkah, empat kartu kategori, FAQ, kontak, dan banner penutup. Formulir pindah ke halaman "Buat pengaduan baru" — dibuka lewat tombol CTA di header/hero/banner, dengan tombol kembali ke beranda.

Klik kartu kategori di landing membuka formulir dengan kategori itu sudah terpilih. Berlaku sama di tampilan Desktop dan Android.

## User

Save as standalone HTML: `SIPRAS Layanan Pengaduan Sarpras.dc.html`

## Assistant

_[tool: grep]_

_[tool: grep]_

_[tool: read_file]_

_[tool: read_file]_

_[tool: grep]_

_[tool: run_script]_

_[tool: super_inline_html]_

_[tool: show_html]_

_[tool: multi_screenshot]_

Semuanya jalan offline — desktop, halaman formulir, dan frame Android (React + Babel + design system ikut dibundel, 1.3 MB).

_[tool: present_fs_item_for_download]_

Satu file HTML mandiri — bisa dibuka tanpa internet.

