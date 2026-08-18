HAK AKSES USER

Waktu seorang user dengan role Kasir mencoba membuka menu "Riwayat Pembelian & Harga Beli", sistem harus melakukan pengecekan dari awal user itu login sampai permintaannya diterima atau ditolak.

Prosesnya dimulai saat user login dengan username dan password. Setelah data itu divalidasi, sistem mengambil informasi role milik user tersebut, dalam kasus ini Kasir, lalu menyimpannya ke dalam session. Berdasarkan role itu, sistem hanya menampilkan menu-menu yang memang menjadi haknya, sehingga menu Riwayat Pembelian tidak akan muncul di tampilan Kasir karena bukan izinnya.

Namun soal ini juga menyinggung kemungkinan user mencoba mengetik URL menu itu secara langsung di browser, bukan lewat klik menu. Di sinilah bagian penting dari alurnya. Sistem tidak boleh hanya mengandalkan menu yang disembunyikan di tampilan, karena kalau user mengetahui alamat URL-nya, dia tetap bisa mencoba mengaksesnya secara langsung. Oleh karena itu, setiap kali ada permintaan masuk ke halaman tersebut, baik dari klik menu maupun dari URL langsung, sistem wajib melakukan pengecekan ulang role dan izin user di sisi server.

Jika hasil pengecekan menunjukkan bahwa role Kasir tidak memiliki izin untuk melihat riwayat pembelian, maka sistem akan menolak permintaan itu dan menampilkan pesan semacam Akses Ditolak atau kode 403. Sebaliknya, jika user yang login memiliki izin yang sesuai, misalnya role Pembelian, maka sistem akan melanjutkan dan menampilkan halaman yang diminta.

Sebagai gambaran urutan langkahnya secara ringkas, alurnya seperti ini. User login, sistem memvalidasi username dan password, sistem mengambil role dan permission user lalu menyimpannya ke session, user mencoba membuka menu baik lewat klik maupun ketik URL, sistem melakukan pengecekan izin di server, kemudian permintaan ditolak jika tidak sesuai dan diterima jika sesuai.

Berikut potongan pseudocode yang menggambarkan logikanya.

    saat login:
        user = validasiLogin(username, password)
        simpan role dan permission user ke session

    saat user membuka halaman "Riwayat Pembelian & Harga Beli":
        jika permission "lihat_riwayat_pembelian" ada pada user:
            tampilkan halaman
        jika tidak ada:
            tampilkan pesan "Akses Ditolak" atau kode 403

Intinya, menyembunyikan menu di tampilan hanya berfungsi untuk kenyamanan pengguna saja, sedangkan keamanan yang sesungguhnya berada pada pengecekan ulang izin di server setiap kali ada permintaan akses, sehingga sistem tetap aman meskipun user mencoba mengakalinya lewat URL.
