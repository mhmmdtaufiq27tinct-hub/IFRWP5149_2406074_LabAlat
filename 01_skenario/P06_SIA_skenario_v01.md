# Skenario SIA P06

| Elemen | Deskripsi |
|:--|:--|
| ID artefak | SIA-P06-ACTIVITY |
| Judul | Skenario activity diagram Input Nilai Mata Kuliah sampai Lihat KHS |
| Pertemuan | 06 |
| Sumber | SIA-UC08 dan SIA-UC09 pada deskripsi SIA P05; jobsheet revisi Pertemuan 6 |
| Jenis/status | Skenario activity diagram / draf |
| Kakas | draw.io; Markdown untuk telaah |
| Swimlane | Dosen, Sistem, Admin Akademik, Mahasiswa |
| Asumsi | Mata kuliah diampu Dosen; masa perkuliahan berakhir; nilai sah berada dalam rentang yang ditetapkan; Admin Akademik mengesahkan nilai lengkap sebelum publikasi |
| Pemeriksaan | Decision lengkap/belum lengkap dengan merge; nilai di luar rentang ditolak; publikasi dan pemberitahuan berjalan paralel melalui fork/join; satu initial dan satu activity final |

## Cakupan skenario

Skenario utama P06 menggabungkan SIA-UC08 Input Nilai Mata Kuliah dengan SIA-UC09 Lihat KHS. Dosen menginput nilai untuk mata kuliah yang diampu. Sistem memeriksa rentang dan kelengkapan nilai. Admin Akademik memeriksa serta mengesahkan nilai yang lengkap. Setelah pengesahan, Sistem menyiapkan publikasi, lalu menerbitkan KHS dan mengirim pemberitahuan kepada Mahasiswa secara paralel. Setelah kedua proses selesai, Mahasiswa dapat memilih semester dan melihat KHS yang memuat nilai terpublikasi.

SIA-CO01 dan SIA-CO02 adalah realisasi UC08 dan UC09, bukan langkah kegiatan aktor atau sistem. Use case kalender dan kelola data mahasiswa (UC07, UC10–UC13) tidak masuk ke alur gabungan utama P06.

## Skenario Normal

| No. | Kegiatan | Respon sistem |
|:--:|:--|:--|
| 1 | Dosen memilih mata kuliah yang diampu | Menampilkan daftar mahasiswa pada mata kuliah tersebut |
| 2 | Dosen memilih mahasiswa | Menampilkan formulir input nilai |
| 3 | Dosen memasukkan nilai mata kuliah | Menerima isian nilai |
| 4 | Dosen mengirim nilai | Memeriksa apakah nilai berada pada rentang yang sah |
| 5 | – | Menyimpan nilai yang sah |
| 6 | – | Memeriksa kelengkapan nilai mata kuliah |
| 7 | Admin Akademik memeriksa dan mengesahkan nilai yang lengkap | Mencatat pengesahan nilai |
| 8 | – | Menyiapkan publikasi hasil studi |
| 9 | – | Menerbitkan KHS pada portal akademik (berjalan paralel setelah fork) |
| 10 | – | Mengirim pemberitahuan hasil studi kepada Mahasiswa (berjalan paralel setelah fork) |
| 11 | Mahasiswa memilih semester | Mencari nilai yang telah dipublikasikan untuk semester tersebut |
| 12 | – | Menampilkan KHS yang berisi nilai terpublikasi |
| 13 | Mahasiswa melihat KHS | – |

Langkah 9 dan 10 tidak bergantung satu sama lain. Keduanya dimulai setelah persiapan publikasi pada langkah 8 dan bergabung kembali pada join sebelum Mahasiswa melanjutkan ke langkah 11.

## Skenario Alternative

| No. | Condition | Kegiatan | Respon sistem |
|:--:|:--|:--|:--|
| 14 | Nilai di luar rentang sah pada langkah 4 | – | Menolak nilai dan menampilkan pesan bahwa nilai di luar rentang; nilai tersebut tidak diteruskan ke proses penyimpanan dan publikasi |
| 15 | Nilai belum lengkap pada pemeriksaan langkah 6 | Dosen melengkapi nilai mata kuliah yang belum lengkap | Menerima nilai yang dilengkapi; alur kembali ke pemeriksaan kelengkapan langkah 6, lalu bergabung kembali sebelum pengesahan langkah 7 |
| 16 | Belum ada nilai yang dipublikasikan untuk semester yang dipilih pada langkah 11 | – | Menampilkan informasi bahwa KHS belum tersedia; alur berakhir tanpa perubahan data |

## Skenario Akhir

Skenario berhasil jika nilai berada pada rentang sah, seluruh nilai lengkap, Admin Akademik mengesahkan nilai, Sistem menyelesaikan publikasi KHS dan pemberitahuan, lalu Mahasiswa melihat KHS semester pilihannya. Publikasi KHS dan pemberitahuan sama-sama harus selesai sebelum alur berlanjut setelah join. Jika nilai di luar rentang, nilai ditolak. Jika nilai belum lengkap, Dosen melengkapinya sebelum pengesahan. Jika belum ada nilai terpublikasi untuk semester yang dipilih, Sistem menyampaikan bahwa KHS belum tersedia.

## Pemetaan unsur skenario ke activity diagram

| Unsur skenario | Representasi pada activity diagram |
|:--|:--|
| Skenario normal | Rangkaian action dari initial node sampai activity final node. |
| Skenario alternatif | Decision dengan guard yang sesuai kondisi alternatif; cabang penolakan berakhir tanpa publikasi. |
| Nilai lengkap/belum lengkap | Decision dengan guard `[lengkap]` dan `[belum lengkap]`; cabang belum lengkap menuju action Dosen melengkapi nilai, lalu merge kembali sebelum pengesahan. |
| Nilai sah/tidak sah | Decision hasil pemeriksaan rentang; guard `[sah]` menuju penyimpanan dan `[di luar rentang]` menuju penolakan. |
| Publikasi dan pemberitahuan | Fork setelah Sistem menyiapkan publikasi; action penerbitan KHS dan pengiriman pemberitahuan berjalan paralel; join menunggu kedua action selesai. |
| Aktor dan respons | Action Dosen, Admin Akademik, dan Mahasiswa ditempatkan di swimlane peran masing-masing; pemeriksaan, penyimpanan, publikasi, notifikasi, dan penampilan KHS berada di swimlane Sistem. |
| Skenario akhir | Activity final dicapai setelah hasil alur normal atau setelah sistem menyampaikan hasil cabang alternatif. |

## Batas dan aturan

- Dosen hanya menginput nilai mata kuliah yang diampunya setelah masa perkuliahan berakhir.
- Nilai harus berada pada rentang yang sah. Batas angka tidak ditentukan dalam skenario, sehingga tidak ditambahkan di sini.
- Nilai yang tersimpan belum otomatis dipublikasikan; pengesahan Admin Akademik mendahului persiapan publikasi.
- KHS hanya menampilkan nilai yang telah dipublikasikan.
- Pengubahan nilai setelah publikasi, koreksi nilai, mekanisme teknis pemberitahuan, dan penanganan kegagalan portal berada di luar cakupan skenario ini.
