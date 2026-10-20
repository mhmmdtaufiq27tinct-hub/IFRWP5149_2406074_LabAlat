___
| Elemen | LAB-UC01 — Lihat Jadwal Kuliah |
|:---:|:---|
| Tujuan | Memasktikan Jadwal Kuliah Terkini |
| Aktor utama | Mahasiswa |
| Sumber kebutuhan | SIA-R01 |
| Pemicu | Mahasiswa memilih Lihat jadwal Kuliah |
| Prasyarat | KRS yang Mahasiswa ajukan telah divalidasi oleh Dosen Wali |
| Pascakondisi berhasil | Mahasiswa dapat melihat jadwal kuliah |
| Pascakondisi gagal | Mahasiswa belum mengisi KRS atau KRS yang diajukan belum divalidasi oleh Dosen wali |
| Include | - |
| Extension point | KRS disetujui, pada langkah 6 |
| Extend | LAB-UC05 jika [mahasiswa memilih Lihat Jadwal Kuliah] |
___
| Elemen | LAB-UC02 — Ajukan KRS |
|:---:|:---|
| Tujuan | Untuk dapat mengikuti perkuliahan |
| Aktor utama | Mahasiswa |
| Sumber kebutuhan | SIA-R03 |
| Pemicu | Mahasiswa memilih fungsi Ajukan KRS |
| Prasyarat | Prasyarat mata kuliah terpenuhi; jadwal kuliah tidak bentrok |
| Pascakondisi berhasil | Pengajuan KRS menunggu Sistem untuk divalidasi sebagai pengajuan |
| Pascakondisi gagal | Tidak ada pengajuan KRS yang berhasil |
| Include | - |
| Extension point | - |
| Extend | - |
___
| Elemen | LAB-UC03 — Validasi KRS sebagai pengajuan |
|:---:|:---|
| Tujuan | Memvalidasi KRS yang diajukan Mahasiswa |
| Aktor utama | Mahasiswa |
| Sumber kebutuhan | SIA-R03 dan SIA-R04 |
| Pemicu | Mahasiswa memilih fungsi Ajukan KRS |
| Prasyarat | Mahasiswa telah mengajukan KRS; prasyarat mata kuliah terpenuhi; jadwal kuliah tidak bentrok |
| Pascakondisi berhasil | Pengajuan tersimpan dengan nomor dan status Menunggu keputusan |
| Pascakondisi gagal | Tidak ada pengajuan baru yang berhasil tersimpan |
| Include | LAB-UC04 — Periksa prasyarat mata-kuliah, dan jadwal yang bentrok |
| Extension point | - |
| Extend | - |
___
| Elemen | LAB-UC04 — Unduh bukti pengajuan |
|:---:|:---|
| Tujuan | Menyimpan bukti pengajuan secara offline |
| Aktor utama | Mahasiswa |
| Sumber kebutuhan | SIA-R05 |
| Pemicu | Mahasiswa memilih fungsi Unduh Bukti Pengajuan |
| Prasyarat | Mahasiswa telah mengajukan KRS; prasyarat mata kuliah terpenuhi; jadwal kuliah tidak bentrok |
| Pascakondisi berhasil | Dokumen bukti pengajuan KRS terunduh dan tersimpan di penyimpanan lokal |
| Pascakondisi gagal | KRS belum diajukan; KRS belum tersimpan di sistem |
| Include | - |
| Extension point | Bukti pengajuan tersedia, pada langkah 6 |
| Extend | LAB-UC03 jika [mahasiswa memilih Unduh Bukti Pengajuan] |
___
| Elemen | LAB-UC05 — Persetujuan atau Penolakan KRS |
|:---:|:---|
| Tujuan | Memvalidasi KRS yang diajukan Mahasiswa. |
| Aktor utama | Dosen Wali |
| Sumber kebutuhan | SIA-R06 |
| Pemicu | Mahasiswa memilih fungsi Ajukan KRS |
| Prasyarat | Mahasiswa telah mengajukan KRS; prasyarat mata kuliah terpenuhi; jadwal kuliah tidak bentrok; Sistem sudah menyimpan perajuan |
| Pascakondisi berhasil | Mahasiswa dapat mengikuti dan melihat jadwal kuliah; Admin Akademik dapat mengelola Jadwal Kuliah. |
| Pascakondisi gagal | Tidak ada pengajuan baru yang berhasil tersimpan |
| Include | - |
| Extension point | KRS disetujui; KRS diajukan untuk disetujui atau ditolak, pada langkah 6 |
| Extend | SIA-UC04 jika [mahasiswa memilih Lihat Jadwal Kuliah] ; SIA-UC06 jika [Admin Akademik memilih Kelola Jadwal Kuliah ] ; SIA-UC0 jika [Mahasiswa memilih Ajukan KRS ] |
___
| Elemen | LAB-UC06 — Kelola Jadwal Kuliah |
|:---:|:---|
| Tujuan | Mengelola Jadwal Kuliah Mahasiswa. |
| Aktor utama | Admin Akademik |
| Sumber kebutuhan | SIA-R02 |
| Pemicu | Admin Akademik memilih fungsi kelola Jadwal Kuliah |
| Prasyarat | Mahasiswa telah mengajukan KRS; KRS telah disetujui |
| Pascakondisi berhasil | Admin Akademik dapat mengelola Jadwal Kuliah. |
| Pascakondisi gagal | Admin Akademik tidak dapat mengelola Jadwal Kuliah. |
| Include | - |
| Extension point | KRS disetujui; KRS diajukan untuk disetujui atau ditolak, pada langkah 6 |
| Extend | SIA-UC06 jika [Admin Akademik memilih Kelola Jadwal Kuliah ] |