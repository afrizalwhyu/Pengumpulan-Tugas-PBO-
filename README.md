# Pengumpulan-Tugas-PBO-
# Class Produk
class Produk:

    def __init__(self, id_produk, nama, harga, stok):
        self.id_produk = id_produk
        self.nama = nama
        self.harga = harga
        self.stok = stok

    def tampilkan_produk(self):
        print(f"{self.nama} | Harga: Rp {self.harga} | Stok: {self.stok}")


# Inheritance Class Makanan
class Makanan(Produk):

    def __init__(self, id_produk, nama, harga, stok, tanggal_kadaluarsa):

        super().__init__(id_produk, nama, harga, stok)

        self.tanggal_kadaluarsa = tanggal_kadaluarsa

    def info_makanan(self):

        print(f"Makanan : {self.nama}")
        print(f"Harga : Rp {self.harga}")
        print(f"Stok : {self.stok}")
        print(f"Kadaluarsa : {self.tanggal_kadaluarsa}")
        print("-"*33)


# Inheritance Class Minuman
class Minuman(Produk):

    def __init__(self, id_produk, nama, harga, stok, ukuran):

        super().__init__(id_produk, nama, harga, stok)

        self.ukuran = ukuran

    def info_minuman(self):

        print(f"Minuman : {self.nama}")
        print(f"Harga : Rp {self.harga}")
        print(f"Stok : {self.stok}")
        print(f"Ukuran : {self.ukuran}")
        print("-"*33)


# Class Detail Belanja
class DetailBelanja:

    def __init__(self, produk, jumlah):

        self.produk = produk
        self.jumlah = jumlah
        self.subtotal = produk.harga * jumlah

    def tampilkan_detail(self):

        print(f"Produk : {self.produk.nama}")
        print(f"Jumlah : {self.jumlah}")
        print(f"Subtotal : Rp {self.subtotal}")


# Class Transaksi
class Transaksi:

    def __init__(self, detail_belanja, bayar):

        self.detail_belanja = detail_belanja
        self.total_harga = 0

        for item in detail_belanja:
            self.total_harga += item.subtotal

        self.bayar = bayar
        self.kembalian = bayar - self.total_harga

    def tampilkan_transaksi(self):

        print("\n===== DETAIL BELANJA =====")

        for item in self.detail_belanja:
            item.tampilkan_detail()

        print("\n===== TRANSAKSI =====")
        print(f"Total Harga : Rp {self.total_harga}")
        print(f"Bayar : Rp {self.bayar}")
        print(f"Kembalian : Rp {self.kembalian}")


# Object Makanan
produk1 = Makanan(1, "Nasi Goreng Spesial", 25000, 20, "2026-06-30")

produk2 = Makanan(2, "Mie Ayam Pangsit", 18000, 15, "2026-05-30")

produk3 = Makanan(3, "Roti Bakar Cokelat", 15000, 10, "2026-05-25")


# Object Minuman
produk4 = Minuman(4, "Es Teh Manis Jumbo", 5000, 50, "Besar")

produk5 = Minuman(5, "Kopi Susu Gula Aren", 12000, 30, "Sedang")

produk6 = Minuman(6, "Jus Alpukat", 15000, 12, "Besar")


# Output Produk
print("===== DATA PRODUK =====")

produk1.info_makanan()
produk2.info_makanan()
produk3.info_makanan()

produk4.info_minuman()
produk5.info_minuman()
produk6.info_minuman()


# Detail Belanja
detail1 = DetailBelanja(produk2, 2)

detail2 = DetailBelanja(produk4, 3)

detail3 = DetailBelanja(produk5, 1)


# Object Transaksi
transaksi1 = Transaksi(
    [detail1, detail2, detail3],
    100000)


# Output Transaksi
transaksi1.tampilkan_transaksi()
