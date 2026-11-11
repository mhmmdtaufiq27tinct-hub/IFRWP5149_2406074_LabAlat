# Pemetaan skenario ke activity diagram LAB P06

| Diagram | Aktor/swimlane | Alur wajib dan kondisi |
|:--|:--|:--|
| Peminjaman | Peminjam, Sistem | Isi pengajuan → validasi kelengkapan → Periksa Ketersediaan (include) → tersedia: simpan status Menunggu keputusan → pilihan cetak bukti. Tidak tersedia/tidak lengkap: tampilkan kegagalan tanpa pengajuan berhasil. |
| Pengembalian | Petugas, Sistem | Pilih pinjaman → verifikasi status Dipinjam dan jumlah → Periksa Kondisi Peralatan → simpan tanggal/kondisi dan ubah status Selesai. Gagal validasi berhenti tanpa simpan. |
| Keputusan | Petugas, Sistem | Pilih pengajuan → setujui atau tolak → simpan keputusan dan tampilkan hasil. |
| Ketersediaan | Peminjam, Sistem | Masukkan kriteria pencarian → sistem menampilkan ketersediaan atau hasil kosong. |
| Kelola data | Petugas, Sistem | Pilih tambah/ubah/hapus; hapus hanya jika tidak sedang dipinjam dan tidak ada pengajuan aktif. |
| Laporan | Kepala Laboratorium, Sistem | Pilih parameter laporan → sistem menyajikan laporan peminjaman. |
| Cetak bukti | Mahasiswa, Sistem | Terima konfirmasi pengajuan → cetak bila dipilih; jika tidak, alur dasar berakhir sukses. |

Setiap activity diagram menggunakan satu initial node, action yang tersambung, guard lengkap pada decision, dan activity final dengan hasil yang jelas. Swimlane mengikuti pelaku pada skenario P05. Pemeriksaan kelengkapan aksesori adalah unsur proses tambahan P06; jangan mengatribusikannya ke P03–P05. Collaboration tidak menjadi action maupun swimlane.
