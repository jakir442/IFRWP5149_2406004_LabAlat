Langkah 1 — Catat kebutuhan dan batas
Simpan skenario, SIA-R03 sampai SIA-R06, asumsi, dan aturan ke
P03_SIA_kebutuhan_v01.md.

Langkah 2 — Identifikasi aktor dan use case

- Mahasiswa: Aktor utama
- Dosen Wali: Aktor yang meninjau pemeriksaan KRS
- Admin Akademik: Aktor pendukung (otomatis) yang menjalankan proses validasi (kelengkapan, prasyarat, dan benturan jadwal) serta menyimpan status pengajuan.

Langkah 3 & 4 — Tentukan include & extend
| ID | Nama use case | Peran dalam model
| SIA-UC01 | Lihat jadwal kuliah | Fungsi utama mahasiswa
| SIA-UC02 | Kelola jadwal kuliah | Fungsi utama admin akademik
| SIA-UC03 | Ajukan KRS | Fungsi utama mahasiswa
| SIA-UC04 | Validasi KRS | Perilaku yang disertakan UC03 (include)
| SIA-UC05 | Unduh bukti pengajuan | Tambahan bersyarat pada UC03 (extend)
| SIA-UC06 | Proses keputusan KRS | Fungsi utama dosen wali

Langkah 5 — Susun deskripsi
|Elemen | LAB-UC03 — Ajukan peminjaman
|Tujuan | Menghasilkan pengajuan KRS yang tersimpan berstatus menunggu persetujuan dosen wali
|Aktor utama | Mahasiswa
|Sumber kebutuhan | SIA-R03, SIA-R04, SIA-R05
|Pemicu | Mahasiswa memilih fungsi pengajuan KRS dan memilih mata kuliah
|Prasyarat | Mahasiswa telah terautentikasi; periode pengisian KRS sedang aktif
|Pascakondisi berhasil | Pengajuan KRS tersimpan dengan status Menunggu persetujuan dosen wali
|Pascakondisi gagal | Tidak ada pengajuan KRS baru yang berhasil tersimpan; pesan kesalahan validasi ditampilkan
|Include | SIA-UC04 — Validasi KRS
|Extension point | Konfirmasi penyimpanan KRS, pada langkah 6
|Extend | SIA-UC05 jika [mahasiswa memilih mengunduh bukti pengajuan]

Langkah 6 — Gambar diagram
|Sumber | Hubungan | Tujuan
|Mahasiswa | Asosiasi | SIA-UC01
|Admin akademik | Asosiasi | SIA-UC02
|Mahasiswa | Asosiasi | SIA-UC03
|Mahasiswa | Asosiasi | SIA-UC05
|Dosen wali | Asosiasi | SIA-UC06
|SIA-UC03 | «include» | SIA-UC04
|SIA-UC05 | «extend» | SIA-UC03

Langkah 7 — Uji konsistensi
Periksa tiga situasi:
a. Validasi berhasil dan mahasiswa tidak mengunduh bukti.
Alur Eksekusi: 
    - Mahasiswa menjalankan Ajukan KRS (SIA-UC03).
    - Sistem secara otomatis mengeksekusi Validasi KRS (SIA-UC04) via relasi <<include>>. 
    - Hasil Validasi: Berhasil (semua kriteria aturan bisnis terpenuhi, mencakup ketiadaan benturan jadwal, pemenuhan mata kuliah prasyarat, serta kesesuaian batasan beban SKS).
    - Sistem menyimpan pengajuan KRS dengan status Menunggu Persetujuan Dosen Wali. 
    - Sistem menampilkan konfirmasi penyimpanan beserta opsi untuk mengunduh bukti. 
    - Mahasiswa memilih tidak mengunduh bukti (alur <<extend>> ke SIA-UC05 tidak dipanggil/diabaikan).

Konsistensi Model: KONSISTEN. Pengajuan KRS tetap berhasil disimpan meskipun use case extend (Unduh Bukti) tidak dieksekusi, karena relasi <<extend>> bersifat opsional.

b. Validasi gagal.
Alur Eksekusi:
    - Mahasiswa menjalankan Ajukan KRS (SIA-UC03) dengan memilih mata kuliah.
    - Sistem secara otomatis mengeksekusi Validasi KRS (SIA-UC04) via relasi <<include>>.
    - Hasil Validasi: Gagal (terdapat benturan jadwal / prasyarat belum dipenuhi / SKS melebihi batas).
    - Sistem membatalkan proses penyimpanan dan menampilkan pesan detail kegagalan validasi.
    - Pengajuan KRS tidak tersimpan ke basis data dan status tidak berubah.
    - Titik perluasan (extension point) untuk mengunduh bukti tidak pernah tercapai, sehingga Unduh Bukti Pengajuan (SIA-UC05) tidak aktif.

Konsistensi Model: KONSISTEN. Karena SIA-UC04 dipanggil wajib secara <<include>>, kegagalan pada validasi langsung menghentikan alur utama SIA-UC03 sebelum sampai pada tahap konfirmasi penyimpanan.

c. Validasi berhasil dan mahasiswa memilih mengunduh bukti.
Alur Eksekusi:
    - Mahasiswa menjalankan Ajukan KRS (SIA-UC03) dengan memilih mata kuliah.
    - Sistem secara otomatis mengeksekusi Validasi KRS (SIA-UC04) via relasi <<include>>.
    - Hasil Validasi: Berhasil.
    - Sistem menyimpan pengajuan KRS dengan status Menunggu Persetujuan Dosen Wali.
    - Sistem menampilkan konfirmasi penyimpanan (Extension Point tercapai).
    - Mahasiswa memilih mengunduh bukti pengajuan, sehingga sistem mengeksekusi Unduh Bukti Pengajuan (SIA-UC05) melalui relasi <<extend>>.
    - Berkas bukti pengajuan terunduh ke perangkat mahasiswa.

Konsistensi Model: KONSISTEN. Relasi <<extend>> sukses dipicu pada kondisi bersyarat setelah base use case (SIA-UC03) menyelesaikan tahap simpan.

Langkah 8 — Review dan revisi
Revisi:
    1. Merubah kosakata pada usecase jadi kata kerja