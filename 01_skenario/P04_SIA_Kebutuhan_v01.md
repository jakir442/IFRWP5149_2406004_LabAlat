| ID      |                                          Kebutuhan tugas 
-----------------------------------------------------------------------------------------------------------------
| SIA-R07 | Mahasiswa dan Dosen, sebagai Civitas Akademika, dapat melihat kalender akademik.                    
| SIA-R08 | Dosen dapat menginput nilai mata kuliah yang diampunya.                                             
| SIA-R09 | Mahasiswa dapat melihat KHS untuk semester yang nilainya sudah dipublikasikan.                      
| SIA-R10 | Admin Akademik dapat mengelola data mahasiswa.                                                      
| SIA-R11 | Pengelolaan data mahasiswa terdiri dari tiga bentuk khusus: tambah, ubah, dan hapus data mahasiswa. 
| SIA-R12 | Model menunjukkan collaboration yang menghubungkan Input Nilai Mata Kuliah dan Lihat KHS.           
----------------------------------------------------------------------------------------------------------------


        Sumber         |    Hubungan        | Tujuan
-------------------------------------------------------
Civitas Akademika      | Asosiasi	    | SIA-R07
Dosen	               | Asosiasi	    | SIA-R08
Mahasiswa	       | Asosiasi	    | SIA-R09
Admin Akademik	       | Asosiasi	    | SIA-R10
Tambah Data Mahasiswa  | Generalization     | SIA-R10
Ubah Data Mahasiswa    | Generalization	    | SIA-R10
Hapus Data Mahasiswa   | Generalization	    | SIA-R10
Mahasiswa	       | Generalization	    | Civitas Akademika
Dosen	               | Generalization     | Civitas Akademika
SIA-R08	               | Realization	    | SIA-R09