# 📐 Praktikum Analisis & Desain Berorientasi Objek

<div align="center">





### Praktikum Analisis dan Desain Berorientasi Objek

**S1 Teknik Informatika — Institut Teknologi Garut**

Repository ini digunakan untuk menyimpan dokumentasi, artefak, latihan, hasil pemodelan UML, serta tugas praktikum **Analisis dan Desain Berorientasi Objek** selama satu periode perkuliahan.

</div>

---

# 📖 About

Praktikum ini berfokus pada penerapan konsep **analisis dan desain berorientasi objek** melalui proses pemodelan sistem menggunakan UML dan kakas pemodelan yang sesuai.

Repository akan dikembangkan secara bertahap mengikuti setiap **pertemuan, tugas, latihan, dan proses pemeriksaan/check** yang diberikan selama praktikum.

> **Current Progress:** Repository saat ini baru berisi pekerjaan **Pertemuan 01**. Bagian untuk pertemuan dan tugas berikutnya akan ditambahkan secara bertahap.

---

# 👤 Student Information

| Information          | Detail                                           |
| -------------------- | ------------------------------------------------ |
| **Nama**             | Jakir Apriyan                                    |
| **NIM**              | 2406004                                          |
| **Program Studi**    | S1 Teknik Informatika                            |
| **Institusi**        | Institut Teknologi Garut                         |
| **Mata Kuliah**      | Praktikum Analisis dan Desain Berorientasi Objek |
| **Kode Mata Kuliah** | IFRWP5149                                        |
| **Semester**         | 5                                                |
| **Tahun Akademik**   | 2026                                             |

---

# 🧰 Tools & Technologies

| Technology             | Description                |
| ---------------------- | -------------------------- |
| UML                    | Bahasa pemodelan sistem    |
| draw.io / diagrams.net | Kakas pemodelan diagram    |
| Markdown               | Dokumentasi                |
| Git                    | Version Control            |
| GitHub                 | Repository dan dokumentasi |

Kakas pemodelan dapat menggunakan draw.io/diagrams.net, Visual Paradigm, StarUML, atau kakas sejenis sesuai kebutuhan praktikum.

---

# 🏫 Case Study

## Sistem Informasi Peminjaman dan Pengembalian Peralatan Laboratorium Kampus

Studi kasus yang digunakan pada praktikum adalah:

**Sistem Informasi Peminjaman dan Pengembalian Peralatan Laboratorium Kampus**

Konteks awal kasus melibatkan beberapa peran:

```text
                    Sistem Informasi
                 Laboratorium Kampus
                         │
          ┌──────────────┼──────────────┐
          │              │              │
          ▼              ▼              ▼
     Mahasiswa       Petugas        Kepala Lab /
     / Peminjam     Laboratorium    Administrator
```

Peran tersebut digunakan sebagai konteks awal untuk latihan pemodelan. Detail aturan bisnis dan kebutuhan sistem akan ditentukan melalui proses analisis pada tahapan praktikum berikutnya.

---

# 📚 Praktikum Progress

Repository ini akan diperbarui mengikuti rangkaian pertemuan praktikum.

| Pertemuan | Materi / Fokus                                        | Status |
| --------- | ----------------------------------------------------- | :----: |
| **01**    | Pengenalan lingkungan praktikum & kakas pemodelan UML |   ✅   |
| **02**    | Akan ditambahkan                                      |    ⏳   |
| **03**    | Akan ditambahkan                                      |    ⏳   |
| **04**    | Akan ditambahkan                                      |    ⏳   |
| **05**    | Akan ditambahkan                                      |    ⏳   |
| **06**    | Akan ditambahkan                                      |    ⏳   |
| **...**   | Akan ditambahkan sesuai jobsheet                      |    ⏳   |

### Status Legend

| Status | Meaning                          |
| ------ | -------------------------------- |
| 🔄     | Sedang dikerjakan / dalam proses |
| ✅      | Selesai                          |
| ⏳      | Belum dikerjakan                 |
| ⚠️     | Memerlukan perbaikan             |

---

# 📝 Pertemuan 01

## Pengenalan Lingkungan Praktikum dan Kakas Pemodelan UML

Pertemuan pertama berfokus pada:

* Menyiapkan workspace praktikum.
* Mengenal kakas pemodelan UML.
* Membuat canvas diagram.
* Menambahkan elemen diagram.
* Menghubungkan elemen dengan connector.
* Memberikan label pada elemen.
* Menyimpan source file.
* Membuka kembali source file.
* Melakukan penyuntingan.
* Mengekspor diagram.
* Mendokumentasikan kegiatan melalui logbook.

Pertemuan ini **belum bertujuan menghasilkan model analisis final**. Fokusnya adalah memastikan lingkungan kerja dan kemampuan dasar penggunaan kakas telah siap.

---

# 🧪 Scenario S-ORI-01

### Mahasiswa Membuka Daftar Peralatan dan Melihat Informasi Ketersediaan

Skenario latihan:

```text
        ●
        │
        ▼
┌──────────────────────────────┐
│ Buka daftar peralatan        │
└──────────────────────────────┘
        │
        ▼
┌──────────────────────────────┐
│ Lihat informasi ketersediaan │
└──────────────────────────────┘
        │
        ▼
        ◎
```

Diagram latihan terdiri dari:

| No | Element                      | Description           |
| -: | ---------------------------- | --------------------- |
|  1 | Initial Node                 | Titik awal aktivitas  |
|  2 | Buka daftar peralatan        | Aktivitas pertama     |
|  3 | Lihat informasi ketersediaan | Aktivitas kedua       |
|  4 | Final Node                   | Titik akhir aktivitas |

Total terdapat **empat elemen** dan **tiga alur penghubung berarah**.

Diagram diberi status:

> **Belum divalidasi sebagai model proses.**

Tidak ditambahkan branching, swimlane, approval, autentikasi, maupun detail database karena belum menjadi bagian dari latihan ini.

---

# 📐 Activity Diagram

### Title

```text
Latihan kakas — S-ORI-01
```

### Flow

```text
Initial Node
     │
     ▼
Buka daftar peralatan
     │
     ▼
Lihat informasi ketersediaan
     │
     ▼
Final Node
```

### Diagram Status

```text
┌─────────────────────────────────────┐
│                                     │
│       🟠 BELUM DIVALIDASI           │
│                                     │
│   Latihan penggunaan kakas UML      │
│   bukan model proses final.         │
│                                     │
└─────────────────────────────────────┘
```

---

# 📂 Repository Structure

Struktur repository akan berkembang seiring bertambahnya tugas dan pertemuan.

```text
IFRWP5149_2406004_LabAlat/
│
├── README.md
│
├── 01_dokumentasi/
│   ├── logbook_pertemuan_01.md
│   └── laporan_singkat_pertemuan_01.md
│
├── 02_skenario/
│   └── S-ORI-01_orientasi_kasus_v01.md
│
├── 03_latihan_tools/
│   ├── P01_2406004_latihan_activity_v01.drawio
│   └── P01_2406004_latihan_activity_v01.png
│
├── 04_model_analisis/
│
├── 05_model_desain/
│
└── metadata/
    └── template_metadata_artefak_v01.md
```

> Struktur folder dapat berkembang sesuai kebutuhan jobsheet pada pertemuan berikutnya.

---

# 📦 Pertemuan 01 Artifacts

| Artifact                                  | Description            | Status |
| ----------------------------------------- | ---------------------- | :----: |
| `README.md`                               | Dokumentasi repository |   🔄   |
| `S-ORI-01_orientasi_kasus_v01.md`         | Dokumentasi skenario   |   🔄   |
| `template_metadata_artefak_v01.md`        | Template metadata      |   🔄   |
| `P01_2406004_latihan_activity_v01.drawio` | Source diagram         |   🔄   |
| `P01_2406004_latihan_activity_v01.png`    | Export diagram         |   🔄   |
| `logbook_pertemuan_01.md`                 | Logbook praktikum      |   🔄   |
| `laporan_singkat_pertemuan_01.md`         | Laporan singkat        |   🔄   |

Jobsheet mencantumkan README, dokumentasi skenario, template metadata, source diagram, hasil ekspor, logbook, dan laporan singkat sebagai artefak Pertemuan 1.

---

# 🏷️ File Naming Convention

Format penamaan artefak:

```text
P<dua digit>_<NIM>_<jenis_artefak>_v<dua digit>.<ekstensi>
```

### Example

```text
P01_2406004_latihan_activity_v01.drawio
P01_2406004_latihan_activity_v01.png
```

### Version Rules

* Versi awal menggunakan `v01`.
* Nomor versi dinaikkan apabila isi artefak mengalami perubahan.
* Perubahan versi dicatat pada logbook.
* Source dan export harus menggunakan versi yang konsisten.
* Export harus berasal dari source versi terakhir.

---

# 📝 Metadata

Setiap artefak praktikum menggunakan informasi metadata seperti:

```text
ID artefak :
Judul :
Pertemuan :
Sumber skenario :
Jenis/status :
Kakas :
Pembuat :
Versi dan tanggal :
Asumsi/pertanyaan :
Pemeriksaan :
Riwayat revisi :
```

Metadata digunakan untuk membantu identifikasi, pelacakan versi, pemeriksaan, dan riwayat perubahan artefak.

---

# ✅ Quality & Validation Checklist

Checklist berikut digunakan untuk memeriksa kualitas pekerjaan **Pertemuan 01**.

## 📁 Workspace

* [ ] Folder induk menggunakan NIM dan nama kasus yang benar.
* [ ] README menjelaskan identitas, kakas, dan status latihan.
* [ ] Logbook tersedia dan dapat dibaca.
* [ ] Template metadata tersedia dan dapat dibaca.

## 📐 Diagram

* [ ] Diagram memiliki empat elemen latihan.
* [ ] Diagram memiliki tiga alur penghubung.
* [ ] Label diagram dapat terbaca.
* [ ] Diagram diberi status belum divalidasi.
* [ ] Tidak ada aturan bisnis tambahan yang diklaim sebagai fakta.

## 💾 Source & Export

* [ ] Source file dapat dibuka kembali.
* [ ] Source file dapat disunting.
* [ ] Gambar ekspor sesuai dengan versi terakhir source.
* [ ] Nama source dan export konsisten.
* [ ] Nomor versi source dan export konsisten.

## 📦 Submission

* [ ] Arsip pengumpulan dapat dibuka.
* [ ] Tidak terdapat kredensial.
* [ ] Tidak terdapat data pribadi nyata.

Checklist ini mengikuti standar kualitas dan validasi yang ditetapkan dalam Jobsheet Pertemuan 1.

---

# 📊 Pertemuan 01 Progress

| Component         | Status |
| ----------------- | :----: |
| Workspace         |   🔄   |
| README            |   🔄   |
| Scenario S-ORI-01 |   🔄   |
| Metadata Template |   🔄   |
| Activity Diagram  |   🔄   |
| Source File       |   🔄   |
| Export File       |   🔄   |
| Logbook           |   🔄   |
| Short Report      |   🔄   |
| Validation        |    ⏳   |

> Status akan diubah menjadi `✅` setelah komponen benar-benar selesai dan diperiksa.

---

# 📈 Overall Repository Progress

```text
Praktikum Analisis & Desain Berorientasi Objek

Pertemuan 01  ████████████████████  In Progress
Pertemuan 02  ░░░░░░░░░░░░░░░░░░░░  Coming Soon
Pertemuan 03  ░░░░░░░░░░░░░░░░░░░░  Coming Soon
Pertemuan 04  ░░░░░░░░░░░░░░░░░░░░  Coming Soon
   ...        ░░░░░░░░░░░░░░░░░░░░  Coming Soon
```

Repository ini akan diperbarui setiap kali terdapat jobsheet, tugas, latihan, atau pemeriksaan baru.

---

# 📋 Revision History

| Version | Date           | Description                      |
| ------- | -------------- | -------------------------------- |
| `v01`   | September 2026 | Initial repository documentation |
| `v02`   | —              | —                                |
| `v03`   | —              | —                                |

---

# 📚 References

* Jobsheet Praktikum Analisis dan Desain Berorientasi Objek — Pertemuan 1.
* Dokumentasi kakas pemodelan UML.
* OMG UML 2.5.1.

---

# 👨‍💻 Developer

<div align="center">

### Jakir Apriyan

**2406004**

S1 Teknik Informatika
Institut Teknologi Garut

---

**Praktikum Analisis dan Desain Berorientasi Objek**

IFRWP5149

</div>

---

# ⭐ Repository

Repository ini dibuat sebagai dokumentasi proses pembelajaran dan pengerjaan praktikum **Analisis dan Desain Berorientasi Objek**.

Setiap pertemuan akan ditambahkan secara bertahap sehingga repository tetap terstruktur, terdokumentasi, dan mudah diperiksa.

---

<div align="center">

### 📐 Analisis & Desain Berorientasi Objek

**Institut Teknologi Garut · S1 Teknik Informatika · 2026**

Built with UML, draw.io & GitHub

</div>
