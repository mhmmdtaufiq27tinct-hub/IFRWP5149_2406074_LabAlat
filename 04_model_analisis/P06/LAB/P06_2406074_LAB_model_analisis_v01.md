# Model analisis activity LAB P06

## Batas model

Model P06 menerjemahkan skenario use case LAB P05 dan model kumulatif LAB P04 menjadi tujuh activity diagram pada `03_latihan_tools/P06/LAB`. Diagram mencakup lihat ketersediaan, kelola data peralatan, ajukan peminjaman, cetak bukti, proses keputusan, lihat laporan, dan catat pengembalian. Activity diagram menunjukkan urutan kerja, pembagian tanggung jawab aktor dan sistem, keputusan, serta hasil akhir; diagram tidak menggantikan katalog use case P04.

Sistem menangani data dan status. Penyerahan fisik alat terjadi di luar perangkat lunak. Aturan keputusan tetap merujuk skenario: pengajuan yang berhasil berstatus Menunggu Keputusan, pemeriksaan ketersediaan wajib sebelum penyimpanan, cetak bukti opsional, dan pencatatan pengembalian hanya untuk peminjaman berstatus Dipinjam.

## Swimlane dan tanggung jawab

| Swimlane | Tanggung jawab dalam alur |
|:--|:--|
| Mahasiswa / Peminjam | Meminta informasi ketersediaan, mengirim pengajuan, memilih cetak bukti jika diinginkan, dan terlibat dalam serah-terima fisik sesuai skenario. |
| Petugas Laboratorium | Mengelola data peralatan, menetapkan keputusan pengajuan, dan mencatat pengembalian beserta kondisi alat. |
| Kepala Laboratorium | Meminta dan melihat laporan peminjaman. |
| Sistem | Menampilkan data, memvalidasi pengajuan, memeriksa ketersediaan dan syarat perubahan, menyimpan status, serta menyajikan hasil atau pesan alternatif. |

## Pemetaan activity terhadap use case P04/P05

| Berkas activity | Use case terkait | Alur dan keluaran analisis |
|:--|:--|:--|
| `P06_2406074_activity_lihat_ketersediaan_v01.drawio` | LAB-UC01 | Peminjam meminta ketersediaan; Sistem menampilkan daftar dan status alat, atau pesan jika tidak ada alat tersedia. |
| `P06_2406074_activity_kelola_data_v01.drawio` | LAB-UC02; LAB-UC08–UC10 | Petugas memilih tambah/ubah/hapus. Sistem menampilkan atau memvalidasi data; hapus hanya diteruskan jika alat tidak sedang dipinjam dan tidak memiliki pengajuan aktif. Data yang tidak ditemukan atau tidak valid menghasilkan pesan penolakan. |
| `P06_2406074_activity_peminjaman_v01.drawio` | LAB-UC03–UC04 | Pengajuan melewati pemeriksaan ketersediaan. Jika tersedia dan lengkap, sistem menyimpan pengajuan; jika tidak, pengajuan tidak berhasil. Keputusan Petugas diproses pada UC06. |
| `P06_2406074_activity_cetak_bukti_v01.drawio` | LAB-UC05 | Setelah pengajuan tersimpan, decision [ya, memilih cetak] menuju pencetakan; guard [tidak] mengakhiri alur tanpa mengubah keberhasilan pengajuan. |
| `P06_2406074_activity_keputusan_v01.drawio` | LAB-UC06 | Sistem menampilkan pengajuan Menunggu Keputusan; Petugas menetapkan Setujui atau Tolak. Status pengajuan diperbarui jika masih dapat diproses; selain itu Sistem memberi pesan. |
| `P06_2406074_activity_laporan_v01.drawio` | LAB-UC07 | Kepala Laboratorium memilih periode; Sistem menampilkan laporan untuk periode tersebut atau pesan jika data tidak tersedia. |
| `P06_2406074_activity_pengembalian_v01.drawio` | LAB-UC11–UC12 | Pengembalian melibatkan konfirmasi alat, pemeriksaan kondisi, dan pembaruan status setelah syarat peminjaman terpenuhi. Hasil rusak/tidak lengkap mengarah pada pencatatan kerusakan atau kekurangan. |

## Keputusan dan alur alternatif

- **Pengajuan:** hasil UC04 menentukan cabang tersedia/tidak tersedia. Hanya data yang lengkap dan tersedia disimpan sebagai pengajuan berhasil dengan status Menunggu Keputusan.
- **Cetak bukti:** cabang bersyarat memakai condition yang sama dengan `extend` UC05, yaitu [Mahasiswa memilih cetak]. Tidak memilih cetak tidak membatalkan pengajuan.
- **Kelola data peralatan:** Sistem membedakan operasi tambah, ubah, dan hapus; data yang tidak ditemukan/tidak sah ditolak. Hapus mensyaratkan tidak sedang dipinjam dan tidak memiliki pengajuan aktif.
- **Keputusan:** pengajuan yang sudah tidak dapat diproses tidak ditimpa. Jika masih berstatus Menunggu Keputusan, hasil Setujui/Tolak dicatat.
- **Pengembalian:** hanya pengajuan berstatus Dipinjam yang dapat ditutup. Kondisi Baik, Rusak Ringan, dan Rusak Berat dicatat; kerusakan tidak otomatis menghasilkan denda.

## Konsistensi dan butir peninjauan

Activity dibuat untuk menguraikan LAB-UC01–UC12 dan mempertahankan relasi `include` UC03–UC04 serta `extend` UC05–UC03 dari P04. Status, aktor, guard, dan pascakondisi perlu konsisten dengan deskripsi use case kumulatif P04 dan skenario LAB P05.

Dua detail diagram saat ini perlu dibaca sebagai asumsi proses, bukan kebutuhan baru yang sudah disahkan: diagram pengembalian memuat pemeriksaan kelengkapan aksesori serta tindakan menjadwalkan perbaikan, sedangkan aturan kebutuhan P04 hanya menetapkan pemeriksaan kondisi alat dan belum menetapkan alur aksesori/perbaikan. Diagram pengajuan juga memakai swimlane Mahasiswa, sementara generalisasi P04 memperbolehkan Dosen sebagai Peminjam. Jika diagram hendak diselaraskan penuh, gunakan swimlane Peminjam (Mahasiswa atau Dosen) dan pastikan penyerahan fisik tidak digambarkan sebagai transaksi yang dilakukan sistem.

Perpindahan fisik peralatan, reservasi stok teknis setelah keputusan, serta aturan keterlambatan dan denda tetap di luar batas model kecuali kebutuhan baru ditambahkan secara eksplisit.
