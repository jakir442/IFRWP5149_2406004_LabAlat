Langkah 2: Katalog Use Case Gabungan (Kumulatif)

ID Use Case | Nama Use Case | Aktor Terkait | Sumber Kebutuhan | Status
SIA-UC01 | Lihat Jadwal Kuliah | Mahasiswa, Dosen (via Civitas Akademika) | SIA-R01 | Tetap
SIA-UC02 | Kelola Jadwal Kuliah | Admin Akademik | SIA-R02 | Tetap
SIA-UC03 | Ajukan KRS | Mahasiswa | SIA-R03 | Tetap
SIA-UC04 | Validasi KRS | Mahasiswa | (SIA-UC03 include) | SIA-R04 | Tetap
SIA-UC05 | Unduh Bukti Pengajuan KRS | Mahasiswa | (SIA-UC05 extend SIA-UC03) | SIA-R05 | Tetap
SIA-UC06 | Proses Keputusan KRS | Dosen Wali | SIA-R06 | Tetap
SIA-UC07 | Lihat Kalender Akademik | Civitas Akademika | SIA-R07 | Baru
SIA-UC08 | Input Nilai Mata Kuliah | Dosen | SIA-R08 | Baru
SIA-UC09 | Lihat KHS | Mahasiswa | SIA-R09 | Baru
SIA-UC10 | Kelola Data Mahasiswa | Admin Akademik | SIA-R10 | Baru
SIA-UC11 | Tambah Data Mahasiswa | Admin Akademik | (via SIA-UC10) | SIA-R11 | Baru
SIA-UC12 | Ubah Data Mahasiswa | Admin Akademik | (via SIA-UC10) | SIA-R11 | Baru
SIA-UC13 | Hapus Data Mahasiswa | Admin Akademik | (via SIA-UC10) | SIA-R11 | Baru

Langkah 3: Generalization Aktor
Hierarki: - Aktor Umum: Civitas Akademika - Aktor Khusus: Mahasiswa, Dosen (keduanya mewarisi Civitas Akademika)
Fungsi yang Diwarisi: - SIA-UC07: Lihat Kalender Akademik - SIA-UC01: Lihat Jadwal Kuliah

Alasan Pemodelan:
Mencegah redudansi garis asosiasi. Fungsi-fungsi yang dapat diakses baik oleh Mahasiswa maupun Dosen cukup dihubungkan satu kali saja ke Aktor Umum (Civitas Akademika). Aktor Mahasiswa dan Dosen secara otomatis mewarisi akses tersebut melalui panah Generalization (garis lurus dengan ujung panah segitiga berongga mengarah ke Civitas Akademika).

Langkah 4: Generalization Use Case

- Use Case Umum: SIA-UC10: Kelola Data Mahasiswa
- Use Case Khusus:
  SIA-UC11: Tambah Data Mahasiswa
  SIA-UC12: Ubah Data Mahasiswa
  SIA-UC13: Hapus Data Mahasiswa
- Perilaku Pembeda:
  SIA-UC11 (Tambah Data Mahasiswa): Membuat rekam data profil dan identitas mahasiswa baru ke dalam sistem.
  SIA-UC12 (Ubah Data Mahasiswa): Memperbarui data identitas atau status profil mahasiswa yang sudah terdaftar.
  SIA-UC13 (Hapus Data Mahasiswa): Menghapus data mahasiswa dari sistem dengan syarat mahasiswa tersebut tidak lagi memiliki data akademik aktif.

Langkah 5: Collaboration
Collaboration ID: SIA-CO01
Nama Collaboration: Input Nilai Mata Kuliah
Realizes Use Case: SIA-UC08 Input Nilai Mata Kuliah
Collaboration ID: SIA-CO02
Nama Collaboration: Lihat KHS
Realizes Use Case: SIA-UC09 Lihat KHS

Langkah 6: Use Case Description
Deskripsi Lengkap: SIA-UC08 Input Nilai Mata Kuliah
ID & Nama Use Case: SIA-UC08 Input Nilai Mata Kuliah
Collaboration: SIA-CO01 Input Nilai Mata Kuliah
Aktor Utama: Dosen
Deskripsi Singkat: Dosen menginput nilai mata kuliah yang diampunya setelah masa perkuliahan berakhir.
Prasyarat:
Dosen telah terautentikasi ke dalam sistem.
Dosen merupakan pengampu resmi dari mata kuliah yang bersangkutan.
Masa perkuliahan semester berjalan telah berakhir.
Alur Utama (Main Success Scenario):
Dosen memilih mata kuliah dan kelas yang diampu.
Sistem menampilkan daftar mahasiswa yang terdaftar di kelas tersebut.
Dosen memasukkan nilai komponen/akhir untuk setiap mahasiswa.
Sistem memvalidasi rentang nilai yang dimasukkan.
Dosen menyimpan data nilai.
Sistem menyimpan nilai dan merubah status nilai menjadi tersimpan (belum terpublikasi).
Alur Alternatif:
4a. Nilai di luar rentang yang sah: Sistem menolak nilai yang diinput, menampilkan pesan kesalahan, dan meminta dosen memasukkan nilai kembali sesuai rentang standar (misal: 0-100 atau A-E).
Pascakondisi Berhasil: Nilai mahasiswa untuk mata kuliah tersebut berhasil tersimpan di sistem.
Pascakondisi Gagal: Nilai tidak tersimpan, dan data nilai lama (jika ada) tidak mengalami perubahan.
