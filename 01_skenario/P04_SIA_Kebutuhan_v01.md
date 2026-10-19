<!-- Skenario-->

Skenario berikut merupakan bahan latihan yang ditetapkan untuk
jobsheet, bukan hasil pengumpulan kebutuhan laboratorium nyata.
Skenario ini melanjutkan potongan model Pertemuan 3.

Selain mahasiswa, dosen juga meminjam peralatan laboratorium untuk
kegiatan praktikum dan penelitian. Mahasiswa dan dosen sama-sama
dapat melihat ketersediaan peralatan dan mengajukan peminjaman.
Petugas laboratorium mengelola data peralatan: menambah peralatan
baru, mengubah data peralatan, dan menghapus data peralatan yang
tidak lagi dipakai. Setelah peminjaman disetujui dan alat diambil, petugas
mencatat pengembalian peralatan. Pada saat mencatat pengembalian,
petugas memeriksa dan mencatat kondisi peralatan. Dua use case utama
pada potongan model ini, Ajukan Peminjaman dan Catat Pengembalian
Peralatan, ditunjukkan realisasinya oleh collaboration yang bersesuaian.

Seluruh fungsi Pertemuan 3 tetap berlaku dan tetap digambar:
pemeriksaan ketersediaan di dalam pengajuan, pencetakan bukti
pengajuan oleh mahasiswa, proses keputusan peminjaman oleh petugas,
dan laporan peminjaman untuk kepala laboratorium. Diagram Pertemuan
4 adalah diagram Pertemuan 3 yang ditambah, bukan diagram baru yang
menggantikannya.

<!-- Kebutuhan Tugas Pertemuan 4 -->

ID | Kebutuhan tugas
SIA-R07 | Mahasiswa dan Dosen, sebagai Civitas Akademika, dapat melihat
kalender akademik.
SIA-R08 | Dosen dapat menginput nilai mata kuliah yang diampunya.
SIA-R09 | Mahasiswa dapat melihat KHS untuk semester yang nilainya sudah
dipublikasikan.
SIA-R10 | Admin Akademik dapat mengelola data mahasiswa.
SIA-R11 | Pengelolaan data mahasiswa terdiri dari tiga bentuk khusus: tambah,
ubah, dan hapus data mahasiswa.
SIA-R12 | Model menunjukkan collaboration yang merealisasikan Input Nilai Mata
Kuliah dan Lihat KHS.

<!-- Batas dan Asumsi -->

Batas dan asumsi
• Kode kebutuhan dimulai dari SIA-R07 agar SIA-R01 dan SIA-R02
(Pertemuan 2) serta SIA-R03 sampai SIA-R06 (Pertemuan 3) tetap
mempunyai identitas berbeda.
• Pengguna telah terautentikasi dan memiliki hak akses sesuai peran.
• Kalender akademik pada tugas ini adalah agenda resmi institusi (awal
semester, batas KRS, masa ujian, dan sejenisnya); jangan
menyamakannya dengan jadwal kuliah pada Pertemuan 2.
• Nilai hanya dapat diinput oleh dosen pengampu mata kuliah tersebut. Nilai
yang diinput belum terpublikasi sebelum dinyatakan resmi oleh ketentuan
tugas ini: KHS hanya menampilkan nilai yang sudah dipublikasikan.
• Hapus Data Mahasiswa hanya untuk mahasiswa yang tidak memiliki data
akademik aktif. Ketentuan ini fiktif untuk latihan.
• Pengajuan KRS tetap digambar sebagai bagian diagram kumulatif dari
Pertemuan 3. Pembayaran dan perancangan basis data berada di luar
tugas ini.

<!-- Aktor utama dan khusus -->

Aktor | Kedudukan | Tujuan terhadap sistem
Peminjam | Umum (general), baru pada Pertemuan 4 | Peran umum bagi peminjam peralatan. Mewariskan fungsinya kepada Mahasiswa dan Dosen.
Mahasiswa | Khusus dari Peminjam, tetap dari Pertemuan 3 | Melihat ketersediaan dan mengajukan peminjaman (diwarisi dari Peminjam), ditambah mencetak bukti pengajuan sebagai asosiasi khususnya sendiri.
Dosen | Khusus dari Peminjam, baru pada Pertemuan 4 | Melihat ketersediaan dan mengajukan peminjaman (diwarisi dari Peminjam).
Petugas Laboratorium | Tetap dari Pertemuan 3 | Mengelola data peralatan, memproses keputusan peminjaman, dan mencatat pengembalian peralatan.
Kepala Laboratorium | Tetap dari Pertemuan 3 | Melihat laporan peminjaman.

<!-- Katalog Use case -->

ID | Nama use case | Peran dalam model | Sumber kebutuhan
LAB-UC01 | Lihat Ketersediaan Peralatan | Tetap dari Pertemuan 3; fungsi aktor umum Peminjam | LAB-R01, LABR07
LAB-UC02 | Kelola Data Peralatan Tetap dari Pertemuan 3; use case UMUM bagi |LABUC08, LAB-UC09, LABUC10 | LAB-R02, LABR08
LAB-UC03 | Ajukan Peminjaman | Tetap dari Pertemuan 3; fungsi aktor umum
Peminjam; menyertakan
LAB-UC04; direalisasikan
LAB-CO01
LAB-R03, LABR07
LAB-UC04 Periksa Ketersediaan Tetap dari Pertemuan 3;
perilaku yang disertakan
LAB-UC03
LAB-R03
LAB-UC05 Cetak Bukti
Pengajuan
Tetap dari Pertemuan 3;
tambahan bersyarat pada
LAB-UC03 melalui
«extend»
LAB-R04
LAB-UC06 Proses Keputusan
Peminjaman
Tetap dari Pertemuan 3;
fungsi utama petugas
LAB-R05
LAB-UC07 Lihat Laporan
Peminjaman
Tetap dari Pertemuan 3;
fungsi utama kepala
laboratorium
LAB-R06
LAB-UC08 Tambah Data
Peralatan
Baru pada Pertemuan 4;
use case KHUSUS dari
LAB-UC02
LAB-R08
LAB-UC09 Ubah Data Peralatan Baru pada Pertemuan 4;
use case KHUSUS dari
LAB-UC02
LAB-R08
LAB-UC10 Hapus Data Peralatan Baru pada Pertemuan 4; LAB-R08
