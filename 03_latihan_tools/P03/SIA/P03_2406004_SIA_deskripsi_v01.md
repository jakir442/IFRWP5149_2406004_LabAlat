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
