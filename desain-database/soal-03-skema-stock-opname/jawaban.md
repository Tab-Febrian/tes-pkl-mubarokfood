SKEMA STOCK OPNAME (PENCOCOKAN STOK FISIK)

Bagian pertama, riwayat.

Tabel yang dibutuhkan:

| Tabel | Field | Keterangan |
| --- | --- | --- |
| stock_opname_sessions | id, tanggal, gudang_id, dilakukan_oleh, status (draft/approved), disetujui_oleh, tanggal_disetujui | Data induk tiap sesi stock opname. |
| stock_opname_details | id, session_id, product_id, stok_sistem_sebelum, hasil_hitung_fisik, selisih, catatan | Detail tiap produk yang dihitung dalam satu sesi opname. |

Mengenai relasinya, satu stock_opname_sessions bisa memiliki banyak stock_opname_details, dan tiap stock_opname_details terhubung ke satu product. Dengan struktur seperti ini, riwayat tiap sesi opname, yaitu kapan dilakukan, siapa yang melakukan, dan gudang mana yang dihitung, beserta detail selisih di tiap produknya bisa dilihat ulang kapan saja tanpa kehilangan data.

Bagian kedua, update stok.

Begitu status pada stock_opname_sessions diubah dari draft menjadi approved, sistem akan mengambil semua baris di stock_opname_details yang terhubung ke sesi tersebut melalui session_id, kemudian mengambil nilai hasil_hitung_fisik dari tiap baris itu, lalu memperbarui kolom stok pada tabel products yang sudah ada supaya nilainya sama dengan hasil_hitung_fisik dari hasil opname tersebut.

Dengan cara ini, stok gudang otomatis menyesuaikan diri dengan kondisi fisik sebenarnya begitu sesi opname disetujui, tanpa perlu ada yang mengubahnya satu per satu secara manual.
