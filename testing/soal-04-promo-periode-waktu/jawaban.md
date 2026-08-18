PENGUJIAN PROMO BERBASIS PERIODE WAKTU

Promo diskon dua puluh persen untuk kategori minuman berlaku pada tanggal satu sampai tujuh setiap bulan. Sistem menentukan aktif tidaknya promo dengan membandingkan tanggal transaksi terhadap tanggal mulai dan tanggal selesai, dan kedua tanggal tersebut, yaitu tanggal satu dan tanggal tujuh, sama-sama termasuk dalam periode promo.

| Skenario | Tanggal Transaksi | Langkah Pengujian | Hasil yang Diharapkan |
| --- | --- | --- | --- |
| a. Tengah periode promo | 4 Agustus 2026 | Tambah produk minuman ke keranjang, cek harga yang muncul | Diskon 20 persen harus muncul |
| b. Hari terakhir promo | 7 Agustus 2026 | Sama seperti di atas | Diskon 20 persen tetap harus muncul, karena hari terakhir masih termasuk periode promo |
| c. Sehari setelah promo berakhir | 8 Agustus 2026 | Sama seperti di atas | Diskon tidak boleh muncul, harga kembali normal |
| d. Sehari sebelum promo dimulai | 31 Juli 2026 | Sama seperti di atas | Diskon tidak boleh muncul, harga tetap normal |

Poin penting dari pengujian ini terletak pada skenario b dan c, di mana sistem harus konsisten memperlakukan tanggal tujuh sebagai bagian dari promo, namun tanggal delapan sudah berada di luar promo. Dengan begitu, logika pengecekannya harus memastikan tanggal transaksi lebih besar atau sama dengan tanggal mulai, dan lebih kecil atau sama dengan tanggal selesai, bukan menggunakan tanda lebih kecil saja di salah satu sisi, supaya tidak ada satu hari pun yang terlewat atau kelebihan hitung.
