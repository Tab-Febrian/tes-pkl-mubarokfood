SKEMA HAK AKSES (ROLE & PERMISSION)

Skema ini menggunakan konsep Role-Based Access Control, jadi hak akses diatur lewat role, bukan diatur satu-satu per user. Dengan begini, admin bisa menambah role baru atau menambah izin baru cukup lewat data, tanpa perlu mengubah kode program.

Tabel yang dibutuhkan:

| Tabel | Field | Keterangan |
| --- | --- | --- |
| users | id, nama, username, password, role_id | Data akun pengguna. Satu user terikat ke satu role. |
| roles | id, nama_role | Daftar jenis role, misalnya Gudang, Pembelian, Kasir. |
| permissions | id, nama_permission | Daftar izin akses per fitur, misalnya lihat_stok, lihat_expired, catat_pembelian, lihat_harga_beli, proses_transaksi_kasir, ubah_harga_jual. |
| role_permission | id, role_id, permission_id | Tabel penghubung antara role dan permission. |

Mengenai relasinya, satu role bisa memiliki banyak permission, dan satu permission bisa dipakai oleh banyak role, sehingga dibutuhkan tabel penghubung role_permission untuk relasi banyak ke banyak tersebut. Sementara itu, satu user hanya terikat ke satu role lewat kolom role_id pada tabel users.

Cara kerjanya saat user berhasil login adalah sebagai berikut. Sistem mengambil role_id dari user yang login, lalu mengambil semua permission_id yang berkaitan dengan role tersebut lewat tabel role_permission. Daftar permission itulah yang dipakai untuk menentukan menu atau fitur apa saja yang boleh diakses oleh user tersebut.

Apabila suatu saat ada role baru atau ada penambahan izin ke role yang sudah ada, admin cukup menambahkan data baru ke tabel roles, permissions, atau role_permission, tanpa perlu mengubah kode program sama sekali.
