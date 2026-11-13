# Deskripsi lengkap use case kumulatif SIA P05

Dokumen ini memuat seluruh 13 use case kumulatif SIA-UC01 sampai SIA-UC13 dari P02 sampai P04. UC01–UC02 berasal dari P02, UC03–UC06 meneruskan model P03, dan UC07–UC13 melengkapi P04. Skenario rinci P05 untuk UC07–UC13 dipertahankan pada bagian masing-masing.

## SIA-UC01 — Lihat Jadwal Kuliah

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | SIA-UC01 — Lihat Jadwal Kuliah |
| Sumber kebutuhan | SIA-R01 (P02) |
| Tujuan | Melihat jadwal kuliah yang tersedia. |
| Aktor utama | Mahasiswa |
| Pemicu | Mahasiswa memilih fungsi Lihat Jadwal Kuliah. |
| Prasyarat | Mahasiswa terautentikasi; informasi jadwal tersedia di sistem. |
| Alur utama | Mahasiswa meminta jadwal; sistem menampilkan jadwal kuliah yang tersedia. |
| Alternatif/pengecualian | Jika jadwal belum tersedia, sistem menyampaikan informasi tersebut. |
| Pascakondisi | Jadwal ditampilkan; tidak ada perubahan data. |

## SIA-UC02 — Kelola Jadwal Kuliah

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | SIA-UC02 — Kelola Jadwal Kuliah |
| Sumber kebutuhan | SIA-R02 (P02) |
| Tujuan | Mengelola informasi jadwal kuliah. |
| Aktor utama | Admin Akademik |
| Pemicu | Admin Akademik memilih fungsi Kelola Jadwal Kuliah. |
| Prasyarat | Admin Akademik terautentikasi dan memiliki hak akses. |
| Alur utama | Admin Akademik memilih jadwal untuk dikelola, sistem menampilkan informasi jadwal, Admin mengirim pengelolaan, lalu sistem menyimpan dan menampilkan hasil. |
| Alternatif/pengecualian | Jika data tidak dapat diproses, sistem menolak penyimpanan dan menyampaikan alasan. |
| Pascakondisi berhasil | Pengelolaan jadwal tersimpan. |
| Pascakondisi gagal | Data jadwal tidak berubah. |

## SIA-UC03 — Ajukan KRS

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | SIA-UC03 — Ajukan KRS |
| Sumber kebutuhan | SIA-R03, SIA-R04, SIA-R05 (P03) |
| Tujuan | Menyimpan pengajuan KRS yang lolos validasi untuk menunggu keputusan Dosen Wali. |
| Aktor utama | Mahasiswa |
| Aktor pendukung | Sistem menjalankan SIA-UC04 Validasi KRS. |
| Pemicu | Mahasiswa memilih Ajukan KRS. |
| Prasyarat | Mahasiswa terautentikasi; data mata kuliah, prasyarat, dan jadwal tersedia. |
| Include | SIA-UC04 Validasi KRS selalu dijalankan sebagai bagian pengajuan. |
| Extension point | Bukti pengajuan tersedia setelah KRS berhasil tersimpan. |
| Pascakondisi berhasil | KRS tersimpan dengan status Menunggu persetujuan Dosen Wali. |
| Pascakondisi gagal | Tidak ada pengajuan baru yang berhasil tersimpan. |

**Alur utama:** Mahasiswa memilih mata kuliah dan mengirim pengajuan. Sistem menjalankan UC04. Jika valid, sistem menyimpan KRS dengan status Menunggu persetujuan Dosen Wali dan menampilkan konfirmasi.

**Alternatif:** Jika validasi gagal, sistem menampilkan alasan dan tidak menyimpan pengajuan berhasil. Setelah pengajuan tersimpan, UC05 dijalankan hanya jika [Mahasiswa memilih unduh]; tanpa pilihan unduh, pengajuan tetap berhasil.

## SIA-UC04 — Validasi KRS

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | SIA-UC04 — Validasi KRS |
| Sumber kebutuhan | SIA-R04 (P03) |
| Tujuan | Menentukan apakah pengajuan memenuhi pemeriksaan KRS yang ditetapkan. |
| Aktor utama | Sistem sebagai perilaku yang di-include oleh UC03. |
| Aktor pendukung | Mahasiswa mengirim data pengajuan melalui UC03. |
| Pemicu | UC03 mencapai langkah validasi. |
| Prasyarat | Data pengajuan telah dikirim dan tersedia untuk diperiksa. |
| Alur utama | Sistem memeriksa kelengkapan data, prasyarat mata kuliah, dan benturan jadwal, lalu mengembalikan hasil valid kepada UC03 jika seluruh pemeriksaan lolos. |
| Alternatif/pengecualian | Jika satu atau lebih pemeriksaan gagal, sistem mengembalikan alasan kegagalan kepada UC03. |
| Pascakondisi | Hasil validasi diberikan kepada UC03; UC04 tidak menyimpan pengajuan. |

## SIA-UC05 — Unduh Bukti Pengajuan KRS

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | SIA-UC05 — Unduh Bukti Pengajuan KRS |
| Sumber kebutuhan | SIA-R05 (P03) |
| Tujuan | Memperoleh bukti pengajuan KRS yang telah tersimpan. |
| Aktor utama | Mahasiswa |
| Aktor pendukung | Sistem menyediakan bukti pengajuan. |
| Pemicu | Mahasiswa memilih unduh pada konfirmasi pengajuan. |
| Prasyarat | UC03 berhasil dan bukti pengajuan tersedia. |
| Relasi | `extend` UC03 pada extension point bukti tersedia, dengan kondisi [Mahasiswa memilih unduh]. |
| Alur utama | Mahasiswa memilih Unduh Bukti Pengajuan KRS; sistem menyediakan bukti dari pengajuan yang tersimpan. |
| Alternatif/pengecualian | Jika Mahasiswa tidak memilih unduh, UC05 tidak dijalankan dan pengajuan tetap berhasil. |
| Pascakondisi | Bukti disediakan untuk diunduh; data KRS tidak berubah. |

## SIA-UC06 — Proses Keputusan KRS

| Elemen | Deskripsi |
|:--|:--|
| ID dan nama | SIA-UC06 — Proses Keputusan KRS |
| Sumber kebutuhan | SIA-R06 (P03) |
| Tujuan | Mencatat persetujuan atau penolakan atas KRS yang menunggu keputusan. |
| Aktor utama | Dosen Wali |
| Aktor pendukung | Sistem menyimpan dan menampilkan keputusan. |
| Pemicu | Dosen Wali memilih pengajuan KRS untuk diproses. |
| Prasyarat | Pengajuan KRS tersimpan dan berstatus menunggu keputusan. |
| Alur utama | Dosen Wali memilih pengajuan; sistem menampilkan rincian; Dosen Wali memilih Setujui atau Tolak dan memasukkan catatan; sistem menyimpan keputusan serta catatan, lalu menampilkan hasil. |
| Alternatif/pengecualian | Jika pengajuan tidak lagi menunggu keputusan, sistem menampilkan status terkini dan tidak menimpa keputusan yang sudah ada. |
| Pascakondisi berhasil | Status keputusan dan catatan Dosen Wali tercatat. |
| Pascakondisi gagal | Tidak ada keputusan baru yang tersimpan. |

## SIA-UC07 — Lihat Kalender Akademik

| Elemen | Deskripsi |
|:--|:--|
| Tujuan | Melihat agenda resmi akademik institusi. |
| Aktor utama | Civitas Akademika (Mahasiswa dan Dosen mewarisi akses) |
| Pemicu | Aktor memilih fungsi Lihat Kalender Akademik. |
| Prasyarat | Aktor terautentikasi; informasi kalender tersedia. |
| Alur utama | Aktor meminta kalender akademik; sistem menampilkan agenda yang tersedia. |
| Alur alternatif | Kalender belum tersedia: Menampilkan informasi kalender belum tersedia. |
| Pascakondisi | Kalender ditampilkan tanpa perubahan data. |
| Generalization | Mahasiswa dan Dosen merupakan aktor khusus Civitas Akademika dan mewarisi akses ini. |

### Skenario normal

| No. | Kegiatan aktor | Respons sistem |
|:--:|:--|:--|
| 1 | Memilih Lihat Kalender Akademik | Mengambil dan menampilkan kalender akademik |

### Skenario alternatif

| No. | Kondisi | Respons sistem |
|:--:|:--|:--|
| 2 | Kalender belum tersedia | Menampilkan informasi kalender belum tersedia |

**Skenario akhir:** Kalender ditampilkan bila tersedia; jika belum, sistem menyampaikan kondisinya.

## SIA-UC08 — Input Nilai Mata Kuliah

| Elemen | Deskripsi |
|:--|:--|
| Tujuan | Mencatat nilai mahasiswa pada mata kuliah yang diampu setelah masa perkuliahan berakhir. |
| Aktor utama | Dosen |
| Pemicu | Aktor memilih fungsi Input Nilai Mata Kuliah. |
| Prasyarat | Dosen terautentikasi, merupakan pengampu mata kuliah terpilih, dan masa perkuliahan berakhir. |
| Alur utama | Dosen memilih mata kuliah dan mahasiswa, memasukkan nilai; sistem memeriksa rentang sah, menyimpan nilai, memeriksa kelengkapan, lalu Admin Akademik mengesahkan nilai lengkap. Sistem menyiapkan publikasi, menerbitkan KHS di portal, dan memberitahu mahasiswa. |
| Alur alternatif | Nilai di luar rentang; atau nilai belum lengkap saat pemeriksaan kelengkapan: Menolak nilai di luar rentang; meminta dosen melengkapi nilai yang kurang lalu melanjutkan sebelum pengesahan. |
| Pascakondisi | Nilai sah tersimpan; nilai lengkap disahkan dan dipublikasikan. UC tidak otomatis memublikasikan nilai yang belum lengkap. |
| Aturan | Nilai harus dalam rentang sah. Penyimpanan nilai tidak otomatis memublikasikannya. |
| Collaboration | SIA-CO01 Input Nilai Mata Kuliah merealisasikan use case ini. |

### Skenario normal

| No. | Kegiatan aktor | Respons sistem |
|:--:|:--|:--|
| 1 | Memilih mata kuliah dan mahasiswa, memasukkan lalu mengirim nilai | Menampilkan daftar/formulir, memeriksa rentang, lalu menyimpan nilai sah |

### Skenario alternatif

| No. | Kondisi | Respons sistem |
|:--:|:--|:--|
| 2 | Nilai di luar rentang; atau nilai belum lengkap saat pemeriksaan kelengkapan | Menolak nilai di luar rentang; meminta dosen melengkapi nilai yang kurang lalu melanjutkan sebelum pengesahan |

**Skenario akhir:** Nilai sah dan lengkap tersimpan, disahkan, dipublikasikan dan diberitahukan; nilai tak sah ditolak. Nilai yang belum lengkap dilengkapi sebelum pengesahan.

## SIA-UC09 — Lihat KHS

| Elemen | Deskripsi |
|:--|:--|
| Tujuan | Melihat Kartu Hasil Studi untuk semester yang dipilih dengan nilai yang sudah dipublikasikan. |
| Aktor utama | Mahasiswa |
| Pemicu | Aktor memilih fungsi Lihat KHS. |
| Prasyarat | Mahasiswa terautentikasi; data nilai mungkin tersedia untuk semester terpilih. |
| Alur utama | Mahasiswa memilih semester; sistem mencari dan menampilkan KHS yang berisi nilai terpublikasi. |
| Alur alternatif | Belum ada nilai yang dipublikasikan untuk semester tersebut: Menyampaikan bahwa KHS belum tersedia. |
| Pascakondisi | KHS ditampilkan jika tersedia; tidak ada perubahan data. |
| Aturan | KHS hanya menampilkan nilai yang telah dipublikasikan. |
| Collaboration | SIA-CO02 Lihat KHS merealisasikan use case ini. |

### Skenario normal

| No. | Kegiatan aktor | Respons sistem |
|:--:|:--|:--|
| 1 | Memilih semester dan melihat KHS | Mencari lalu menampilkan KHS dengan nilai yang telah dipublikasikan |

### Skenario alternatif

| No. | Kondisi | Respons sistem |
|:--:|:--|:--|
| 2 | Belum ada nilai yang dipublikasikan untuk semester tersebut | Menyampaikan bahwa KHS belum tersedia |

**Skenario akhir:** KHS semester terpilih ditampilkan jika tersedia; bila belum, sistem menyampaikan KHS belum tersedia.

## SIA-UC10 — Kelola Data Mahasiswa (use case umum)

| Elemen | Deskripsi |
|:--|:--|
| Tujuan | Mengelola data mahasiswa melalui operasi tambah, ubah, atau hapus. |
| Aktor utama | Admin Akademik |
| Pemicu | Aktor memilih fungsi Kelola Data Mahasiswa. |
| Prasyarat | Admin Akademik terautentikasi dan memiliki hak akses pengelolaan data mahasiswa. |
| Alur utama | Admin memilih operasi dan data; sistem menampilkan form/data, memvalidasi operasi, menyimpan perubahan valid, dan mengonfirmasi hasil. UC11—UC13 merupakan spesialisasi UC10. |
| Alur alternatif | Data atau operasi tidak valid: Menolak perubahan dan menampilkan alasan. |
| Pascakondisi | Perubahan sesuai operasi khusus tersimpan; jika ditolak, data tidak berubah. |
| Generalization | SIA-UC11 Tambah, SIA-UC12 Ubah, dan SIA-UC13 Hapus Data Mahasiswa adalah spesialisasi use case umum ini. |

### Skenario normal

| No. | Kegiatan aktor | Respons sistem |
|:--:|:--|:--|
| 1 | Memilih operasi; memasukkan atau memilih data; mengonfirmasi | Menampilkan form/data, memvalidasi, menyimpan perubahan dan menampilkan hasil |

### Skenario alternatif

| No. | Kondisi | Respons sistem |
|:--:|:--|:--|
| 2 | Data atau operasi tidak valid | Menolak perubahan dan menampilkan alasan |

**Skenario akhir:** Perubahan tersimpan dan dikonfirmasi atau ditolak tanpa perubahan.

## SIA-UC11 — Tambah Data Mahasiswa (khusus UC10)

| Elemen | Deskripsi |
|:--|:--|
| Tujuan | Menambahkan rekaman mahasiswa baru melalui pengelolaan data mahasiswa. |
| Aktor utama | Admin Akademik (asosiasi diwarisi dari UC10) |
| Pemicu | Aktor memilih fungsi Tambah Data Mahasiswa. |
| Prasyarat | Admin memiliki hak mengelola data mahasiswa; operasi tambah dipilih pada UC10. |
| Alur utama | Mewarisi langkah umum UC10; Admin mengisi dan mengonfirmasi data baru; sistem memvalidasi dan menyimpan rekaman mahasiswa baru. |
| Alur alternatif | Data mahasiswa baru tidak valid: Menolak penambahan dan menampilkan alasan. |
| Pascakondisi | Data mahasiswa baru tersimpan; jika data tidak valid, tidak ada rekaman baru. |
| Generalization | Spesialisasi SIA-UC10; aktor dan alur umum pengelolaan diwarisi. |

### Skenario normal

| No. | Kegiatan aktor | Respons sistem |
|:--:|:--|:--|
| 1 | Memilih tambah pada UC10, mengisi data dan mengonfirmasi penambahan | Menampilkan form tambah, memvalidasi, menyimpan rekaman baru dan mengonfirmasi |

### Skenario alternatif

| No. | Kondisi | Respons sistem |
|:--:|:--|:--|
| 2 | Data mahasiswa baru tidak valid | Menolak penambahan dan menampilkan alasan |

**Skenario akhir:** Data baru tersimpan atau penambahan ditolak beserta alasannya.

## SIA-UC12 — Ubah Data Mahasiswa (khusus UC10)

| Elemen | Deskripsi |
|:--|:--|
| Tujuan | Memperbarui data mahasiswa yang dipilih. |
| Aktor utama | Admin Akademik (asosiasi diwarisi dari UC10) |
| Pemicu | Aktor memilih fungsi Ubah Data Mahasiswa. |
| Prasyarat | Admin memiliki hak akses; data mahasiswa yang dipilih tersedia; operasi ubah dipilih pada UC10. |
| Alur utama | Mewarisi langkah umum UC10; Admin memperbarui dan mengonfirmasi data; sistem memvalidasi dan menyimpan perubahan. |
| Alur alternatif | Data perubahan tidak valid: Menolak perubahan dan menampilkan alasan. |
| Pascakondisi | Perubahan tersimpan; jika tidak valid, data lama tetap utuh. |
| Generalization | Spesialisasi SIA-UC10; aktor dan alur umum pengelolaan diwarisi. |

### Skenario normal

| No. | Kegiatan aktor | Respons sistem |
|:--:|:--|:--|
| 1 | Memilih data, mengubah isian dan mengonfirmasi perubahan | Menampilkan data terpilih, memvalidasi, menyimpan dan mengonfirmasi perubahan |

### Skenario alternatif

| No. | Kondisi | Respons sistem |
|:--:|:--|:--|
| 2 | Data perubahan tidak valid | Menolak perubahan dan menampilkan alasan |

**Skenario akhir:** Data mahasiswa diperbarui atau data lama dipertahankan tanpa perubahan.

## SIA-UC13 — Hapus Data Mahasiswa (khusus UC10)

| Elemen | Deskripsi |
|:--|:--|
| Tujuan | Menghapus data mahasiswa yang memenuhi syarat. |
| Aktor utama | Admin Akademik (asosiasi diwarisi dari UC10) |
| Pemicu | Aktor memilih fungsi Hapus Data Mahasiswa. |
| Prasyarat | Admin memiliki hak akses; data mahasiswa terpilih tersedia; data tidak memiliki data akademik aktif. |
| Alur utama | Mewarisi langkah umum UC10; Admin memilih data dan mengonfirmasi; sistem memeriksa data akademik aktif lalu menghapus data jika memenuhi syarat. |
| Alur alternatif | Mahasiswa memiliki data akademik aktif: Menolak penghapusan dan menyampaikan alasan. |
| Pascakondisi | Data mahasiswa terhapus; jika memiliki data akademik aktif, data tetap ada. |
| Generalization | Spesialisasi SIA-UC10; aktor dan alur umum pengelolaan diwarisi. |

### Skenario normal

| No. | Kegiatan aktor | Respons sistem |
|:--:|:--|:--|
| 1 | Memilih data dan mengonfirmasi penghapusan | Memeriksa data akademik aktif, menghapus data yang memenuhi syarat dan mengonfirmasi |

### Skenario alternatif

| No. | Kondisi | Respons sistem |
|:--:|:--|:--|
| 2 | Mahasiswa memiliki data akademik aktif | Menolak penghapusan dan menyampaikan alasan |

**Skenario akhir:** Data terhapus hanya jika tidak memiliki data akademik aktif; selain itu, penghapusan ditolak.
