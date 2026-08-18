PEMBULATAN UANG KEMBALIAN TUNAI

Total tagihan pada kasus ini adalah Rp 47.630, dan pembeli membayar tunai dengan uang Rp 50.000.

Bagian a, total tagihan setelah dibulatkan. Aturan pembulatannya adalah dibulatkan ke kelipatan seratus rupiah terdekat, di mana sisa di bawah lima puluh dibulatkan ke bawah dan sisa lima puluh ke atas dibulatkan ke atas. Apabila 47.630 dibagi dengan seratus, sisanya adalah tiga puluh. Karena tiga puluh lebih kecil dari lima puluh, maka nominal ini dibulatkan ke bawah, sehingga total tagihan setelah dibulatkan menjadi Rp 47.600.

Bagian b, uang kembalian yang harus diberikan. Karena uang yang diterima adalah Rp 50.000 dan tagihan setelah dibulatkan adalah Rp 47.600, maka kembaliannya adalah 50.000 dikurangi 47.600 sama dengan Rp 2.400.

Bagian c, apabila pembeli yang sama membayar menggunakan QRIS atau metode non tunai lainnya. Karena aturan pembulatan hanya berlaku untuk pembayaran tunai, maka tagihannya tetap Rp 47.630 persis tanpa dibulatkan sama sekali. Selain itu, karena pembayaran diproses langsung melalui sistem atau gateway pembayaran, maka secara otomatis tidak ada uang kembalian, berbeda dengan pembayaran tunai yang membutuhkan uang fisik untuk dikembalikan.

Berikut pseudocode yang menggambarkan logikanya.

    function hitungTagihanTunai(totalTagihan):
        sisa = totalTagihan modulo 100
        jika sisa kurang dari 50:
            totalDibulatkan = totalTagihan dikurangi sisa
        jika tidak:
            totalDibulatkan = totalTagihan dikurangi sisa ditambah 100
        kembalikan totalDibulatkan

    function prosesBayar(totalTagihan, metode, uangDiterima):
        jika metode sama dengan "tunai":
            tagihanFinal = hitungTagihanTunai(totalTagihan)
            kembalian = uangDiterima dikurangi tagihanFinal
            kembalikan {tagihanFinal, kembalian}
        jika tidak:
            tagihanFinal = totalTagihan
            kembalian = 0
            kembalikan {tagihanFinal, kembalian}

    kasus a dan b, tunai:
    prosesBayar(47630, "tunai", 50000) hasilnya tagihanFinal 47600, kembalian 2400

    kasus c, non tunai:
    prosesBayar(47630, "QRIS", 47630) hasilnya tagihanFinal 47630, kembalian 0
