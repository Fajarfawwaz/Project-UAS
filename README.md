# BIODATA
## NAMA : FAJAR FAWWAZ ATALLAH
## NIM : 312410357
## KELAS : TI.24.A4
# ![400326530-e3b5a3e9-75ba-4812-bab2-8284ebbbb8cd](https://github.com/user-attachments/assets/6091c2d7-6db9-48e3-9f1a-00421c2385b4)
Program ini adalah aplikasi sederhana untuk sistem mengelola jual beli kasur berbasis terminal. Program ini dibuat dengan pendekatan modular dan menggunakan prinsip OOP (Object-Oriented Programming). Program ini memungkinkan pengguna menambahkan jumlah kasur yang otomatis mengubah harga total sesuai dengan jumlah kasur yang di input
```PYTHON
class Mattress:
    def __init__(self, quantity):
        self.quantity = quantity
        self.price_per_unit = 5000

    def total_price(self):
        return self.quantity * self.price_per_unit


class View:
    @staticmethod
    def display_table(customer_name, date, quantity, total_price):
        print("\n+-------------------------------------------------+")
        print("|                     Hasil                       |")
        print("+-------------------------------------------------+")
        print(f"| Nama Pelanggan: {customer_name}                  |")
        print(f"| Tanggal: {date}                                 |")
        print(f"| Jumlah Kasur: {quantity}                        |")
        print(f"| Total Harga: Rp{total_price}                    |")
        print("+-------------------------------------------------+")


class Process:
    @staticmethod
    def validate_input(input_value):
        try:
            quantity = int(input_value)
            if quantity < 1:
                raise ValueError("Jumlah kasur tidak boleh kurang dari 1.")
            return quantity
        except ValueError as e:
            print(e)
            return None

    @staticmethod
    def validate_date(input_date):
        from datetime import datetime
        try:
            date_obj = datetime.strptime(input_date, "%m/%Y")
            return date_obj.strftime("%B %Y")  # Mengembalikan dalam format Bulan Tahun
        except ValueError:
            print("Format tanggal tidak valid. Gunakan MM/YYYY.")
            return None


def main():
    # Input dari pengguna
    customer_name = input("Masukkan nama pelanggan: ")
    user_input = input("Masukkan jumlah kasur: ")
    date_input = input("Masukkan tanggal (bulan/tahun - MM/YYYY): ")
    
    # Validasi input
    quantity = Process.validate_input(user_input)
    if quantity is None:
        return  # Menghentikan program jika input tidak valid

    date = Process.validate_date(date_input)
    if date is None:
        return  # Menghentikan program jika input tanggal tidak valid

    # Proses data
    mattress = Mattress(quantity)
    total_price = mattress.total_price()

    # Tampilkan hasil
    View.display_table(customer_name, date, quantity, total_price)


if __name__ == "__main__":
    main()
```
Kode Di atas merupakan program yang mensimulasikan pemesanan kasur, dimana pengguna dapat memasukan nama pelanggan, jumlah kasur yang ingin di pesan, dan tanggal pemesanan, program ini menghitung total harga dan menampilkan hasilnya dalam format yang terstruktur, berikut adalah penjelasan lebih rinci mengenai setiap bagian bagian dari kode codingan di atas : 

## 1. KELAS MATTRESS
```PYTHON
_init__(self, quantity):
        self.quantity = quantity
        self.price_per_unit = 5000

    def total_price(self):
        return self.quantity * self.price_per_unit
```
Konsuktor ini di gunakan untuk menginisialisasi objek mattress, parameter quantity adalah jumlah kasur, di berikan saat objek matrees di buat, Atribut  price_per_unit di atur menjadi 5000 ( harga per unit kasur ) , total price(self) metode ini menghitung total harga kasur berdasrkan quantity, dan harga per unit, Total harga dikembalikan sebagai hasil dari perkalian quantity dan price_per_unit
## 2. KELAS VIEW
```PYTHON
def display_table(customer_name, date, quantity, total_price):
        print("\n+-------------------------------------------------+")
        print("|                     Hasil                       |")
        print("+-------------------------------------------------+")
        print(f"| Nama Pelanggan: {customer_name}                  |")
        print(f"| Tanggal: {date}                                 |")
        print(f"| Jumlah Kasur: {quantity}                        |")
        print(f"| Total Harga: Rp{total_price}                    |")
        print("+-------------------------------------------------+")
```
ini adalah metode statis yang menampilkan hasil pemesanan dalam bentuk tabel, menampilkan informasi nama pelanggan, jumlah kasur yang di pesan, dan total harga kasur yang di beli, format tabel dibuat menggunakan karakter khusus ( misalnya +,|, dan spasi ) untuk memberikan tampilan yang terstruktur dan mudah untuk di baca
## 3. KELAS PROCCES
```python
def validate_input(input_value):
        try:
            quantity = int(input_value)
            if quantity < 1:
                raise ValueError("Jumlah kasur tidak boleh kurang dari 1.")
            return quantity
        except ValueError as e:
            print(e)
            return None

    @staticmethod
    def validate_date(input_date):
        from datetime import datetime
        try:
            date_obj = datetime.strptime(input_date, "%m/%Y")
            return date_obj.strftime("%B %Y")  # Mengembalikan dalam format Bulan Tahun
        except ValueError:
            print("Format tanggal tidak valid. Gunakan MM/YYYY.")
            return None
```
metode statis ini memvalidasi input untuk jumlah kasur, yang di masukan oleh pengguna, pertama, mencoba mengkonversi nilai input ke dalam bentuk integer, jika berhasil, akan memeriksa apakah jumlah kasur yang di beli lebih dari atau sama dengan satu, jika valid akan mengembalikan nilai quantity, jika tidak valid, mencetak pesan eror yang dan mengembalikan none. 
## 4. FUNGSI MAIN : 
```PYTHON
 # Input dari pengguna
    customer_name = input("Masukkan nama pelanggan: ")
    user_input = input("Masukkan jumlah kasur: ")
    date_input = input("Masukkan tanggal (bulan/tahun - MM/YYYY): ")
    
    # Validasi input
    quantity = Process.validate_input(user_input)
    if quantity is None:
        return  # Menghentikan program jika input tidak valid

    date = Process.validate_date(date_input)
    if date is None:
        return  # Menghentikan program jika input tanggal tidak valid

    # Proses data
    mattress = Mattress(quantity)
    total_price = mattress.total_price()

    # Tampilkan hasil
    View.display_table(customer_name, date, quantity, total_price)
```
fungsi utama ini berfungsi sebagai penghubung antara input pengguna, pemrosesan data, dan tampilan hasil, sehingga apabila sudah di isi akan menghasilkan tampilan informasi pemesanan dalam format tabel yang terstruktur. 
