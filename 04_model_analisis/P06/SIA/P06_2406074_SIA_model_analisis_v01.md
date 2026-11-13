# Model analisis activity SIA P06

## Batas model

Produk utama SIA P06 adalah satu activity diagram gabungan **Input Nilai Mata Kuliah sampai Lihat KHS**, berdasarkan SIA-UC08 dan SIA-UC09 pada deskripsi SIA P05. Model menggambarkan penginputan nilai oleh Dosen, pemeriksaan dan pengesahan oleh Admin Akademik, publikasi KHS serta pemberitahuan hasil, lalu akses Mahasiswa untuk melihat KHS. Metadata P06 menetapkan artefak diagram utama bernama `P06_2406074_SIA_activity_v01.drawio` di folder `04_model_analisis/P06/SIA`; dokumen ini mendefinisikan alur analisis yang menjadi acuannya.

Sebagai latihan per use case yang mengikuti struktur LAB, folder `03_latihan_tools/P06/SIA` juga memuat diagram UC07–UC13. Diagram tambahan ini menguraikan skenario P05 masing-masing; tidak mengubah cakupan produk utama gabungan UC08–UC09.

## Aktor dan swimlane

| Swimlane | Tanggung jawab |
|:--|:--|
| Dosen | Memilih mata kuliah yang diampu dan mahasiswa, mengisi nilai, serta melengkapi nilai yang masih kurang. |
| Sistem | Menyediakan daftar/formulir, memeriksa rentang dan kelengkapan nilai, menyimpan nilai, menyiapkan publikasi, menerbitkan KHS, mengirim pemberitahuan, dan menyajikan KHS. |
| Admin Akademik | Memeriksa kelengkapan dan mengesahkan nilai sebelum dipublikasikan. |
| Mahasiswa | Memilih semester dan melihat KHS yang nilai-nilainya sudah dipublikasikan. |

## Alur gabungan UC08–UC09

1. Dosen memilih mata kuliah yang diampu; Sistem menampilkan daftar mahasiswa.
2. Dosen memilih mahasiswa, memasukkan nilai, dan mengirimkannya.
3. Sistem memeriksa apakah nilai berada dalam rentang yang sah. Nilai di luar rentang ditolak dan diberi pesan; nilai yang sah disimpan.
4. Sistem memeriksa kelengkapan nilai. Jika masih ada nilai yang belum lengkap, Dosen melengkapinya dan alur kembali ke pemeriksaan kelengkapan.
5. Setelah lengkap, Admin Akademik memeriksa serta mengesahkan nilai. Sistem mencatat pengesahan dan menyiapkan publikasi.
6. Fork membagi dua pekerjaan yang dapat berjalan paralel: Sistem menerbitkan KHS di portal akademik dan mengirim pemberitahuan hasil studi kepada Mahasiswa. Join menunggu kedua pekerjaan selesai.
7. Mahasiswa memilih semester; Sistem mencari nilai yang sudah dipublikasikan dan menampilkan KHS. Jika belum tersedia, Sistem menyampaikan bahwa KHS belum tersedia.

## Keputusan dan sinkronisasi

| Titik keputusan/sinkronisasi | Guard atau kondisi | Hasil |
|:--|:--|:--|
| Pemeriksaan rentang nilai (UC08) | `[nilai sah]` | Nilai disimpan dan proses berlanjut. |
| Pemeriksaan rentang nilai (UC08) | `[nilai di luar rentang]` | Nilai ditolak; tidak dilanjutkan sebagai nilai tersimpan. |
| Pemeriksaan kelengkapan nilai (UC08) | `[lengkap]` | Diteruskan ke pemeriksaan dan pengesahan Admin Akademik. |
| Pemeriksaan kelengkapan nilai (UC08) | `[belum lengkap]` | Dosen melengkapi nilai; alur bergabung kembali sebelum pengesahan. |
| Fork/join publikasi | Kedua action dimulai setelah persiapan dan pengesahan | Penerbitan KHS dan pemberitahuan berjalan paralel; join menunggu keduanya. |
| Pencarian KHS (UC09) | `[nilai terpublikasi tersedia]` | KHS untuk semester pilihan ditampilkan. |
| Pencarian KHS (UC09) | `[belum ada nilai terpublikasi]` | Sistem memberi informasi KHS belum tersedia. |

## Pemetaan terhadap kebutuhan use case

| Use case | Perilaku yang direalisasikan |
|:--|:--|
| SIA-UC08 Input Nilai Mata Kuliah | Input nilai oleh Dosen, validasi rentang, penyimpanan, pemeriksaan kelengkapan, pengesahan, dan persiapan publikasi. SIA-CO01 adalah realisasi use case, bukan action terpisah. |
| SIA-UC09 Lihat KHS | Pencarian berdasarkan semester dan penampilan hanya nilai yang telah dipublikasikan. SIA-CO02 adalah realisasi use case, bukan action terpisah. |

Diagram tambahan pada `03_latihan_tools/P06/SIA` menguraikan use case P05 UC07–UC13: lihat kalender, input nilai, lihat KHS, kelola data mahasiswa umum, tambah, ubah, dan hapus. UC11–UC13 adalah spesialisasi UC10; diagramnya mengikuti hubungan tersebut.

## Aturan dan batas analisis

- Dosen hanya dapat menginput nilai untuk mata kuliah yang diampunya dan setelah masa perkuliahan berakhir.
- Nilai harus berada pada rentang sah. Penyimpanan nilai tidak dengan sendirinya berarti nilai sudah dipublikasikan.
- Admin Akademik mengesahkan nilai yang lengkap sebelum publikasi.
- KHS hanya menampilkan nilai yang telah dipublikasikan; aktivitas melihat KHS tidak mengubah data nilai.
- Penerbitan KHS dan pemberitahuan mahasiswa merupakan dua action paralel setelah persiapan publikasi, sesuai skenario P05 dan checklist artefak P06.
- Pengubahan nilai setelah publikasi, koreksi nilai, mekanisme notifikasi, dan rincian rentang angka tidak ditetapkan oleh skenario; jangan menambah aturan tersebut pada diagram tanpa kebutuhan eksplisit.
- Pengelolaan data mahasiswa (UC10–UC13) dan kalender akademik (UC07) adalah diagram latihan tambahan P06, bukan bagian alur utama produk P06 gabungan UC08–UC09.
