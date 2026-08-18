SKEMA TRANSAKSI PENJUALAN DAN PERGERAKAN STOK

Tabel yang dibutuhkan:

| Tabel | Field | Keterangan |
| --- | --- | --- |
| transactions | id, invoice_no, tanggal, kasir_id, total, metode_bayar, status | Data induk satu transaksi penjualan. |
| transaction_items | id, transaction_id, product_id, nama_produk_saat_itu, qty, harga_saat_transaksi, subtotal | Detail barang-barang yang dibeli dalam satu transaksi. |
| products | id, nama, barcode, harga_sekarang, stok | Data master produk yang dipakai sehari-hari, bukan untuk transaksi lama. |

Bagian yang paling penting ada pada kolom harga_saat_transaksi di tabel transaction_items. Kolom ini menyimpan harga barang persis pada saat transaksi itu terjadi, bukan mengambil langsung dari harga_sekarang di tabel products. Jadi harga tersebut seolah-olah difoto pada saat transaksi berlangsung dan disimpan sendiri di transaction_items.

Efeknya, apabila suatu saat harga produk di tabel products diubah, misalnya kecap yang tadinya lima belas ribu naik menjadi tujuh belas ribu, data transaksi lama yang sudah tersimpan tidak ikut berubah, karena data itu tidak lagi bergantung pada harga terbaru dan sudah memiliki nilai sendiri di kolom harga_saat_transaksi.

Mengenai relasinya, satu transaction bisa memiliki banyak transaction_items karena satu transaksi biasanya berisi banyak barang berbeda. Tiap transaction_items tetap terhubung ke satu product lewat product_id, namun ini hanya dipakai sebagai referensi informasi produk terkini, misalnya untuk melihat gambar atau kategori produk, bukan untuk mengambil harga.
