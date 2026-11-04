| Unsur pada tabel skenario Pertemuan 5 | Menjadi pada activity diagram |
|:---:|:---|
| Skenario Normal | Alur utama: rangkaian action dari initial node sampai activity final node |
| Skenario Alternative | Cabang decision dengan guard yang menyatakan syarat cabang tersebut |
| Langkah include (selalu terjadi) | Action wajib pada alur utama, ditempatkan pada urutan langkahnya di dalam skenario, misalnya Periksa Ketersediaan dari LAB-UC04 |
| Langkah extend (bersyarat) | Cabang decision tersendiri dengan condition yang sama dengan condition extend pada diagram Pertemuan 4, misalnya cabang [ya, memilih cetak] menuju Cetak Bukti Pengajuan dari LABUC05 |
| Kolom Kegiatan (aktor) | Action pada swimlane aktor tersebut |
| Kolom Respon sistem | Action pada swimlane Sistem |
| Skenario Akhir | Activity final node; kondisi selesai pada skenario menjadi keadaan akhir alur |
| Dua pemeriksaan yang tidak saling bergantung | Fork dan join: kedua pemeriksaan digambar paralel dan disatukan kembali sebelum keputusan akhir |