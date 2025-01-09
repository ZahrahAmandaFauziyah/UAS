# UAS


    # Class Data untuk menyimpan data mahasiswa
    class Mahasiswa:
    def _init_(self, nama, nim, kelas, prodi):
        self.nama = nama
        self.nim = nim
        self.kelas = kelas
        self.prodi = prodi

    # Class View untuk menampilkan data mahasiswa dalam bentuk tabel
    class View:
    @staticmethod
    def tampilkan_tabel(data_mahasiswa):
        print("+----------------+------------+-------+----------------+")
        print("|      Nama      |    NIM     | Kelas |      Prodi     |")
        print("+----------------+------------+-------+----------------+")
        for mahasiswa in data_mahasiswa:
            print(f"| {mahasiswa.nama:<14} | {mahasiswa.nim:<10} | {mahasiswa.kelas:<5} | {mahasiswa.prodi:<14} |")
        print("+----------------+------------+-------+----------------+")

    # Class Process untuk mengelola data mahasiswa
    class Process:
    def _init_(self):
        self.data_mahasiswa = []

    def tambah_mahasiswa(self, nama, nim, kelas, prodi):
        mahasiswa = Mahasiswa(nama, nim, kelas, prodi)
        self.data_mahasiswa.append(mahasiswa)
        print("Mahasiswa berhasil ditambahkan!")

    def hapus_mahasiswa(self, nim):
        for mahasiswa in self.data_mahasiswa:
            if mahasiswa.nim == nim:
                self.data_mahasiswa.remove(mahasiswa)
                print(f"Mahasiswa dengan NIM {nim} berhasil dihapus.")
                return
        print(f"Mahasiswa dengan NIM {nim} tidak ditemukan.")

    def ubah_mahasiswa(self, nim, nama_baru=None, kelas_baru=None, prodi_baru=None):
        for mahasiswa in self.data_mahasiswa:
            if mahasiswa.nim == nim:
                if nama_baru:
                    mahasiswa.nama = nama_baru
                if kelas_baru:
                    mahasiswa.kelas = kelas_baru
                if prodi_baru:
                    mahasiswa.prodi = prodi_baru
                print(f"Mahasiswa dengan NIM {nim} berhasil diubah.")
                return
        print(f"Mahasiswa dengan NIM {nim} tidak ditemukan.")

    # Fungsi utama
    if _name_ == "_main_":
    proses = Process()

    while True:
        print("\nMenu:")
        print("1. Tambah Mahasiswa")
        print("2. Tampilkan Data Mahasiswa")
        print("3. Ubah Data Mahasiswa")
        print("4. Hapus Mahasiswa")
        print("5. Keluar")

        pilihan = input("Pilih menu: ")

        if pilihan == "1":
            nama = input("Masukkan nama: ")
            nim = input("Masukkan NIM: ")
            kelas = input("Masukkan kelas: ")
            prodi = input("Masukkan prodi: ")
            proses.tambah_mahasiswa(nama, nim, kelas, prodi)

        elif pilihan == "2":
            View.tampilkan_tabel(proses.data_mahasiswa)

        elif pilihan == "3":
            nim = input("Masukkan NIM mahasiswa yang ingin diubah: ")
            nama_baru = input("Masukkan nama baru (kosongkan jika tidak ingin mengubah): ")
            kelas_baru = input("Masukkan kelas baru (kosongkan jika tidak ingin mengubah): ")
            prodi_baru = input("Masukkan prodi baru (kosongkan jika tidak ingin mengubah): ")
            proses.ubah_mahasiswa(nim, nama_baru or None, kelas_baru or None, prodi_baru or None)

        elif pilihan == "4":
            nim = input("Masukkan NIM mahasiswa yang ingin dihapus: ")
            proses.hapus_mahasiswa(nim)

        elif pilihan == "5":
            print("Keluar dari program.")
            break

        else:
            print("Pilihan tidak valid. Silakan coba lagi.")

            
            PENJELASAN :
            Kode di atas merupakan implementasi sederhana dari sistem pengelolaan data mahasiswa menggunakan konsep Object-Oriented Programming (OOP) dalam Python.
            Berikut adalah penjelasan bagian-bagian dari kode tersebut:

    1. Class Mahasiswa (Data)
    Class ini digunakan untuk merepresentasikan data mahasiswa.

    Atribut:
    nama: Nama mahasiswa.
    nim: Nomor Induk Mahasiswa.
    kelas: Kelas mahasiswa.
    prodi: Program Studi mahasiswa.
    Masalah:
    Konstruktor __init__ memiliki kesalahan penulisan nama metode (_init_ harusnya __init__), sehingga program tidak akan bisa membuat objek mahasiswa.
    
    2. Class View (Presentasi)
    Class ini digunakan untuk menampilkan data mahasiswa dalam format tabel di konsol.

    Fungsi:
    tampilkan_tabel: Fungsi statis (tidak memerlukan instance class) untuk menampilkan data mahasiswa yang disimpan dalam list.
    
    3. Class Process (Pengelolaan Data)
    Class ini bertugas untuk mengelola data mahasiswa (CRUD: Create, Read, Update, Delete).

    Atribut:
    data_mahasiswa: List yang berisi objek-objek mahasiswa.
    Metode:
    __init__: Menginisialisasi atribut data_mahasiswa sebagai list kosong. (Kesalahan: _init_ harusnya __init__.)
    tambah_mahasiswa:
    Menambahkan mahasiswa baru ke dalam list data_mahasiswa.
    Membuat objek mahasiswa menggunakan class Mahasiswa lalu menambahkannya ke list.
    hapus_mahasiswa:
    Menghapus data mahasiswa berdasarkan NIM.
    Jika NIM ditemukan, data akan dihapus dari list; jika tidak, akan ditampilkan pesan error.
    ubah_mahasiswa:
    Mengubah data mahasiswa berdasarkan NIM.
    Bisa mengubah sebagian atau seluruh atribut (nama, kelas, prodi) mahasiswa.
    Jika NIM tidak ditemukan, akan menampilkan pesan error.
    
    4. Fungsi Utama (if __name__ == "__main__":)
    Bagian ini adalah fungsi utama program untuk berinteraksi dengan pengguna. Terdapat menu untuk melakukan berbagai operasi:

    Tambah Mahasiswa:
    Input data mahasiswa (nama, nim, kelas, prodi) dari pengguna dan tambahkan ke list.
    Tampilkan Data Mahasiswa:
    Menampilkan data mahasiswa dalam bentuk tabel dengan bantuan class View.
    Ubah Data Mahasiswa:
    Input NIM mahasiswa yang ingin diubah.
    Input data baru (atau kosongkan jika tidak ingin mengubah atribut tertentu).
    Hapus Mahasiswa:
    Input NIM mahasiswa yang ingin dihapus.
    Hapus data mahasiswa dari list.
    Keluar:
    Mengakhiri program.
    
    5. Masalah dalam Kode
    a. Kesalahan Penulisan Nama Fungsi __init__
    Fungsi __init__ ditulis sebagai _init_ pada class Mahasiswa dan Process.
    Perbaikan: Ganti _init_ dengan __init__.
    b. Kesalahan pada Nama __name__ dan __main__
    Penulisan nama fungsi utama adalah _name_ == "_main_". Seharusnya __name__ == "__main__".
    Perbaikan: Ganti _name_ dengan __name__ dan _main_ dengan __main__.
    c. Penanganan Input Kosong pada Metode ubah_mahasiswa
    Dalam fungsi ubah_mahasiswa, input kosong untuk nama, kelas, atau prodi tidak ditangani dengan baik. Menggunakan nama_baru or None adalah solusi untuk menangani input kosong.
    d. Tidak Ada Validasi untuk Input Ganda
    Tidak ada validasi untuk mencegah duplikasi NIM saat menambah mahasiswa.

  LINK YOUTUBE:
    https://youtu.be/kwH8KFlGTmY?si=_I2t124rlu-RiSIE
