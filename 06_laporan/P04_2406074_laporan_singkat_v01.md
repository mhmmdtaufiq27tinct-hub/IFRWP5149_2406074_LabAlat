# Laporan Singkat Pertemuan 4

**Nama:** Muhammad Taufiq  
**NIM:** 2406074  
**Kelas:** C

## Ringkasan

Model use case kumulatif diperluas untuk kasus LAB dan SIA dengan generalization aktor/use case, relasi realization collaboration, serta kebutuhan baru. Semua fungsi Pertemuan 3 tetap menjadi bagian model.

## LAB

Peminjam menjadi aktor umum bagi Mahasiswa dan Dosen. Mereka mewarisi akses melihat ketersediaan dan mengajukan peminjaman. Mahasiswa tetap memiliki asosiasi khusus untuk mencetak bukti. Petugas dapat mencatat pengembalian; pemeriksaan kondisi peralatan menjadi perilaku wajib. Kelola data peralatan memiliki bentuk khusus tambah, ubah, dan hapus. Collaboration LAB-CO01 dan LAB-CO02 merealisasikan pengajuan dan pencatatan pengembalian.

## SIA

Civitas Akademika menjadi aktor umum bagi Mahasiswa dan Dosen untuk melihat kalender akademik. Admin Akademik menambah, mengubah, atau menghapus data mahasiswa melalui generalization dari Kelola Data Mahasiswa. Dosen pengampu menginput nilai; mahasiswa melihat KHS yang nilainya telah dipublikasikan. Collaboration terkait merealisasikan Input Nilai Mata Kuliah dan Lihat KHS.

## Pemeriksaan

Diagram harus mempertahankan kebutuhan dan relasi P03. Arah generalization menuju induk; include menuju use case yang disertakan; realization menghubungkan collaboration ke use case yang direalisasikan. Penghapusan data dibatasi sesuai aturan skenario. Keterlambatan/denda LAB dan aturan institusi nyata SIA tidak diasumsikan.
