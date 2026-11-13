# Skenario SIA P05

Skenario mengikuti diagram kumulatif P04 dan indeks tugas SIA jobsheet P05. Tabel normal dan alternatif menggunakan penomoran berlanjut; satu baris memuat satu aksi aktor atau respons sistem. Diagram P04 tidak diubah.

## SIA-UC07 — Lihat Kalender Akademik

**Aktor:** Civitas Akademika (berlaku untuk Mahasiswa dan Dosen). **Tujuan:** Melihat agenda resmi akademik. **Deskripsi:** Civitas Akademika meminta kalender dan sistem menampilkan agenda akademik yang tersedia atau informasi bahwa kalender belum tersedia.

| No. | Kegiatan | Respon sistem |
|:--:|:--|:--|
| 1 | Memilih Lihat Kalender Akademik | Mengambil kalender akademik |
| 2 | — | Menampilkan kalender akademik yang tersedia |

**Skenario Alternative**

| No. | Condition | Kegiatan | Respon sistem |
|:--:|:--|:--|:--|
| 3 | Kalender belum tersedia | — | Menampilkan informasi kalender belum tersedia |

**Skenario Akhir:** Kalender ditampilkan bila tersedia; bila belum tersedia, sistem menyampaikan kondisinya. Skenario ditulis satu kali atas nama Civitas Akademika, diwarisi Mahasiswa dan Dosen.

## SIA-UC08 — Input Nilai Mata Kuliah

**Aktor:** Dosen. **Tujuan:** Mencatat nilai mahasiswa pada mata kuliah yang diampu. **Deskripsi:** Dosen pengampu memilih mata kuliah dan mahasiswa, mengirim nilai; sistem menolak nilai di luar rentang sah dan menyimpan nilai yang valid. **Collaboration:** SIA-CO01 merealisasikan UC08, bukan langkah kegiatan. **Prasyarat:** Dosen merupakan pengampu mata kuliah terpilih.

| No. | Kegiatan | Respon sistem |
|:--:|:--|:--|
| 1 | Memilih mata kuliah yang diampu | Menampilkan daftar mahasiswa pada mata kuliah tersebut |
| 2 | Memilih mahasiswa | Menampilkan formulir input nilai |
| 3 | Memasukkan nilai mata kuliah | Menerima isian nilai |
| 4 | Mengirim nilai | Memeriksa apakah nilai berada pada rentang yang sah |
| 5 | — | Menyimpan nilai |
| 6 | — | Memeriksa kelengkapan nilai |
| 7 | Admin Akademik memeriksa dan mengesahkan nilai | Mencatat pengesahan nilai |
| 8 | — | Menyiapkan publikasi hasil studi |
| 9 | — | Menerbitkan KHS pada portal akademik |
| 10 | — | Mengirim pemberitahuan hasil studi kepada mahasiswa |

**Skenario Alternative**

| No. | Condition | Kegiatan | Respon sistem |
|:--:|:--|:--|:--|
| 11 | Nilai di luar rentang sah pada langkah 4 | — | Menolak nilai dan menampilkan pesan nilai di luar rentang |
| 12 | Nilai belum lengkap pada langkah 6 | Dosen melengkapi nilai mata kuliah yang belum lengkap | Menerima nilai yang dilengkapi; alur bergabung kembali sebelum pengesahan langkah 7 |

**Skenario Akhir:** Nilai lengkap dan sah disimpan, disahkan, lalu dipublikasikan dan diberitahukan; nilai di luar rentang ditolak. Cabang nilai belum lengkap kembali ke alur sebelum pengesahan. Skenario ini menjadi sumber alur gabungan P06 bersama SIA-UC09; dua action publikasi setelah persiapan berjalan paralel pada diagram P06.

## SIA-UC09 — Lihat KHS

**Aktor:** Mahasiswa. **Tujuan:** Melihat Kartu Hasil Studi semester terpilih. **Deskripsi:** Mahasiswa memilih semester dan sistem hanya menampilkan nilai yang telah dipublikasikan. **Collaboration:** SIA-CO02 merealisasikan UC09, bukan langkah kegiatan.

| No. | Kegiatan | Respon sistem |
|:--:|:--|:--|
| 1 | Memilih semester | Mencari nilai yang telah dipublikasikan untuk semester tersebut |
| 2 | — | Menampilkan KHS berisi nilai yang telah dipublikasikan |
| 3 | Melihat KHS | — |

**Skenario Alternative**

| No. | Condition | Kegiatan | Respon sistem |
|:--:|:--|:--|:--|
| 4 | Belum ada nilai yang dipublikasikan | — | Menampilkan informasi KHS belum tersedia |

**Skenario Akhir:** KHS semester terpilih ditampilkan jika tersedia; jika belum, sistem menyampaikan bahwa KHS belum tersedia.

## SIA-UC10 — Kelola Data Mahasiswa (use case umum)

**Aktor:** Admin Akademik. **Tujuan:** Mengelola data mahasiswa melalui operasi tambah, ubah, atau hapus. **Deskripsi:** Admin memilih operasi dan data; sistem memvalidasi lalu menyimpan perubahan yang valid. UC11, UC12, dan UC13 mewarisi alur umum ini serta menetapkan hasil khusus.

| No. | Kegiatan | Respon sistem |
|:--:|:--|:--|
| 1 | Memilih operasi kelola data mahasiswa | Menampilkan form atau data sesuai operasi |
| 2 | Memasukkan atau memilih data mahasiswa | Memvalidasi data dan operasi |
| 3 | Mengonfirmasi operasi | Menyimpan perubahan yang valid |
| 4 | — | Menampilkan konfirmasi hasil pengelolaan |

**Skenario Alternative**

| No. | Condition | Kegiatan | Respon sistem |
|:--:|:--|:--|:--|
| 5 | Data atau operasi tidak valid | — | Menolak perubahan dan menampilkan alasan |

**Skenario Akhir:** Perubahan tersimpan dan dikonfirmasi, atau ditolak beserta alasannya. Langkah umum 1–4 dirujuk use case khusus UC11–UC13.

## SIA-UC11 — Tambah Data Mahasiswa (khusus UC10)

**Aktor:** Admin Akademik. **Tujuan:** Menyimpan data mahasiswa baru. **Deskripsi:** Mewarisi langkah umum SIA-UC10; perilaku pembeda adalah menyimpan rekaman mahasiswa baru.

| No. | Kegiatan | Respon sistem |
|:--:|:--|:--|
| 1–2 | Merujuk SIA-UC10 langkah umum 1–2 | Menampilkan form tambah dan memvalidasi data mahasiswa baru |
| 3 | Mengonfirmasi penambahan data baru | Menyimpan data mahasiswa baru |
| 4 | — | Menampilkan konfirmasi data tersimpan |

**Skenario Alternative**

| No. | Condition | Kegiatan | Respon sistem |
|:--:|:--|:--|:--|
| 5 | Data mahasiswa baru tidak valid | — | Menolak penambahan dan menampilkan alasan |

**Skenario Akhir:** Data mahasiswa baru tersimpan, atau penambahan ditolak beserta alasannya. Langkah umum dirujuk dari UC10; langkah 3–4 menyatakan perilaku pembeda UC11.

## SIA-UC12 — Ubah Data Mahasiswa (khusus UC10)

**Aktor:** Admin Akademik. **Tujuan:** Memperbarui data mahasiswa yang dipilih. **Deskripsi:** Mewarisi langkah umum SIA-UC10; perilaku pembeda adalah menyimpan perubahan pada data mahasiswa terpilih.

| No. | Kegiatan | Respon sistem |
|:--:|:--|:--|
| 1–2 | Merujuk SIA-UC10 langkah umum 1–2 | Menampilkan data mahasiswa terpilih dan memvalidasi perubahan |
| 3 | Mengonfirmasi perubahan data | Memperbarui data mahasiswa terpilih |
| 4 | — | Menampilkan konfirmasi data berhasil diubah |

**Skenario Alternative**

| No. | Condition | Kegiatan | Respon sistem |
|:--:|:--|:--|:--|
| 5 | Data perubahan tidak valid | — | Menolak perubahan dan menampilkan alasan |

**Skenario Akhir:** Data mahasiswa berubah, atau perubahan ditolak beserta alasannya. Langkah umum dirujuk dari UC10; langkah 3–4 menyatakan perilaku pembeda UC12.

## SIA-UC13 — Hapus Data Mahasiswa (khusus UC10)

**Aktor:** Admin Akademik. **Tujuan:** Menghapus data mahasiswa yang memenuhi syarat. **Deskripsi:** Mewarisi langkah umum SIA-UC10; data hanya dapat dihapus jika mahasiswa tidak memiliki data akademik aktif.

| No. | Kegiatan | Respon sistem |
|:--:|:--|:--|
| 1–2 | Merujuk SIA-UC10 langkah umum 1–2 | Menampilkan data mahasiswa terpilih dan memeriksa data akademik aktif |
| 3 | Mengonfirmasi penghapusan | Menghapus data mahasiswa jika tidak memiliki data akademik aktif |
| 4 | — | Menampilkan konfirmasi data mahasiswa terhapus |

**Skenario Alternative**

| No. | Condition | Kegiatan | Respon sistem |
|:--:|:--|:--|:--|
| 5 | Mahasiswa memiliki data akademik aktif | — | Menolak penghapusan dan menampilkan alasan |

**Skenario Akhir:** Data dihapus hanya jika tidak memiliki data akademik aktif; jika syarat gagal, penghapusan ditolak. Langkah umum dirujuk dari UC10; langkah 3–4 menyatakan perilaku pembeda UC13.
