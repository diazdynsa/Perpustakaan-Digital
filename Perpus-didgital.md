# Perpustakaan-Digital
# class perpustakaan untuk menyimpan informasi buku dan mengelola operasinya
class Perpustakaan:
    def __init__(self):
        # daftar buku disimpan di dictionary ini
        self.buku = {
            "Garis Waktu": {"penulis": "Fiersa Besari", "tersedia": True},
            "Filosofi Teras": {"penulis": "Henry Manampiring", "tersedia": True},
            "Distilasi Alkena": {"penulis": "Wira Nagara", "tersedia": True},
        }

    # method untuk menampilkan daftar buku beserta statusnya
    def tampilkan_buku(self):
        print("\nDaftar Buku:")
        for judul, info in self.buku.items():
            status = "Tersedia" if info["tersedia"] else "Dipinjam"
            print(f"- {judul} ({info['penulis']}) - {status}")

    # method untuk meminjam buku berdasarkan judul
    def pinjam_buku(self, judul):
        if judul in self.buku:
            if self.buku[judul]["tersedia"]:
                self.buku[judul]["tersedia"] = False
                print(f"Anda berhasil meminjam buku '{judul}'.")
            else:
                print(f"Buku '{judul}' sedang dipinjam.")
        else:
            print("Buku tidak ditemukan.")

    # method untuk mengembalikan buku berdasarkan judul
    def kembalikan_buku(self, judul):
        if judul in self.buku:
            if not self.buku[judul]["tersedia"]:
                self.buku[judul]["tersedia"] = True
                print(f"Anda telah mengembalikan buku '{judul}'.")
            else:
                print(f"Buku '{judul}' sudah tersedia di perpustakaan.")
        else:
            print("Buku tidak ditemukan.")

# fungsi utama untuk mengatur menu dan interaksi pengguna
def main():
    # membuat objek Perpustakaan
    perpustakaan = Perpustakaan()
    
    while True:
        # menampilkan menu utama
        print("\nMenu:")
        print("1. Tampilkan daftar buku")
        print("2. Pinjam buku")
        print("3. Kembalikan buku")
        print("4. Keluar")
        pilihan = input("Pilih menu (1-4): ")
        
        # menangani pilihan user/pengguna
        if pilihan == "1":
            perpustakaan.tampilkan_buku()
        elif pilihan == "2":
            judul = input("Masukkan judul buku yang ingin dipinjam: ")
            perpustakaan.pinjam_buku(judul)
        elif pilihan == "3":
            judul = input("Masukkan judul buku yang ingin dikembalikan: ")
            perpustakaan.kembalikan_buku(judul)
        elif pilihan == "4":
            print("Terima kasih telah menggunakan sistem perpustakaan!")
            break
        else:
            print("Pilihan tidak valid. Silakan coba lagi.")

# menjalankan program main/utama
if __name__ == "__main__":
    main()
