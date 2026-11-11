# Periksa setiap diagram dengan checklist berikut sebelum mengunggah ke LMS. Satu unsur yang tidak terpenuhi berarti diagram belum selesai dan harus diperbaiki terlebih dahulu.
## ✓ Tepat satu initial node dan minimal satu activity final node; tidak ada action yang terputus dari alur.
## ✓ Setiap decision mempunyai guard pada semua alur keluarnya; guard saling lepas dan bersama sama menutup semua kemungkinan.
## ✓ Setiap cabang decision kembali melalui merge atau bermuara ke activity final node dengan keadaan akhir yang jelas.
## ✓ Fork selalu berpasangan dengan join; proses paralel disatukan oleh join, bukan oleh merge.
## ✓ Setiap action berada pada swimlane aktor yang melakukannya pada tabel skenario; respon sistem berada pada swimlane Sistem.
## ✓ Setiap action tertelusur ke langkah tabel skenario Pertemuan 5 dan nama action sama dengan bunyi langkah sumbernya.
## ✓ Include digambar sebagai action wajib pada alur utama (Periksa Ketersediaan pada peminjaman; Periksa Kondisi Peralatan pada pengembalian) dan extend digambar sebagai cabang bersyarat dengan condition yang sama, yaitu [ya, memilih cetak].
## ✓ Unsur proses baru Tahap 5, yaitu Periksa kelengkapan aksesori peralatan, diberi keterangan unsur proses baru dan tidak diklaim berasal dari Pertemuan 3, 4, atau 5.
## ✓ Collaboration tidak digambar sebagai action atau sebagai swimlane