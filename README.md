# Pengumpulan-Tugas-PBO-
# Class Produk (Parent Class)
class Produk:

    # Konstruktor untuk menyimpan data produk
    def __init__(self, id_produk, nama, harga, stok):
        self.id_produk = id_produk
        self.nama = nama
        self.harga = harga
        self.stok = stok


# Class Makanan mewarisi class Produk
class Makanan(Produk):

    # Menambahkan atribut tanggal kadaluarsa
    def __init__(self, id_produk, nama, harga, stok, kadaluarsa):
        super().__init__(id_produk, nama, harga, stok)
        self.kadaluarsa = kadaluarsa


# Class Minuman mewarisi class Produk
class Minuman(Produk):

    # Menambahkan atribut ukuran
    def __init__(self, id_produk, nama, harga, stok, ukuran):
        super().__init__(id_produk, nama, harga, stok)
        self.ukuran = ukuran


# Class DetailBelanja untuk menyimpan detail pembelian
class DetailBelanja:

    def __init__(self, produk, jumlah):
        self.produk = produk
        self.jumlah = jumlah
        self.subtotal = produk.harga * jumlah


# Class Transaksi untuk menghitung total pembayaran
class Transaksi:

    def __init__(self, detail_belanja, bayar):

        self.detail_belanja = detail_belanja
        self.total = 0

        # Menghitung total harga
        for item in detail_belanja:
            self.total += item.subtotal

        self.bayar = bayar
        self.kembalian = bayar - self.total

    # Menampilkan struk pembayaran
    def cetak_struk(self):

        print("\nSTRUK PEMBELIAN")

        for item in self.detail_belanja:
            print("Produk   :", item.produk.nama)
            print("Harga    : Rp", item.produk.harga)
            print("Jumlah   :", item.jumlah)
            print("Subtotal : Rp", item.subtotal)
            print("-" * 30)

            print("Total      : Rp", self.total)
            print("Bayar      : Rp", self.bayar)
            print("Kembalian  : Rp", self.kembalian)


# Object Makanan
produk1 = Makanan(1, "Nasi Goreng Spesial", 25000, 20, "2026-06-30")
produk2 = Makanan(2, "Mie Ayam Pangsit", 18000, 15, "2026-05-30")
produk3 = Makanan(3, "Roti Bakar Cokelat", 15000, 10, "2026-05-25")

# Object Minuman
produk4 = Minuman(4, "Es Teh Manis Jumbo", 5000, 50, "Besar")
produk5 = Minuman(5, "Kopi Susu Gula Aren", 12000, 30, "Sedang")
produk6 = Minuman(6, "Jus Alpukat", 15000, 12, "Besar")

# Menyimpan semua produk ke dalam list
daftar_produk = [
    produk1,
    produk2,
    produk3,
    produk4,
    produk5,
    produk6
]

# Menyimpan detail belanja
detail_belanja = []

# Menu pembelian
while True:

    print("\nDAFTAR PRODUK")

    # Menampilkan daftar produk
    for produk in daftar_produk:
        print(f"{produk.id_produk}. {produk.nama} - Rp {produk.harga}")

    # Memilih produk
    pilihan = int(input("\nPilih Produk (1-6): "))

    # Validasi pilihan
    if pilihan < 1 or pilihan > 6:
        print("Pilihan tidak tersedia!")
        continue

    # Memasukkan jumlah pembelian
    jumlah = int(input("Jumlah Item : "))

    # Membuat object DetailBelanja
    produk = daftar_produk[pilihan - 1]
    detail_belanja.append(DetailBelanja(produk, jumlah))

    # Konfirmasi menambah produk
    lagi = input("Tambah produk lagi? (iya/tidak): ").lower()

    if lagi == "tidak":
        break

# Proses pembayaran
bayar = int(input("\nMasukkan Uang Pembayaran : Rp "))

# Membuat object Transaksi
transaksi = Transaksi(detail_belanja, bayar)

# Menampilkan struk pembayaran
transaksi.cetak_struk()
