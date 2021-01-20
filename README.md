```
                                                 MIRA SHINTANIA
                                                   312010290
                                                    TI.20.B2

```
# **Package & Module**
## **Module**
Modul merupakan bagian dari program yang berisi fungsi-fungsi yang dibuat pada file terpisah.
Dengan adanya modul-modul yang terpisah, dapat dikelompokkan sesuai dengan fungsinya dan memudahkan dalam mengelola kode program.
Modul dapat dipanggil sesuai dengan kebutuhannya.

### Membuat Module
Untuk menggunakan modul yang telah dibuat cukup menggunakan perintah import Contoh:
```
>>> import example
>>> example.add(4,5.5)
9.5

# import module by renaming it
import math as m
print("The value of pi is"
, m.pi)
```

## **Package**
Package merupakan namespace yang berisi banyak modul dan paket. Package merupakan sebuah direktory yang berisi banyak file-file modul. Setiap package pada Python, harus ada file khusus yang bernama init.py. File tersebut merupakan file kosong, atau bisa juga diisi dengan sesuatu.

### Membuat Package
- Buat sebuah directory (folder), dan tambahkan file kosong dengan nama init.py
- Buat sejumah file kode program python (ekstensi .py) pada folder tersebut yang berisi fungsi-fungsi (modul program)
- Untuk menggunakan package yang telah dibuat cukup menggunakan perintah import
```
import nama_package.nama_module
atau
from nama_package import nama_module
```

### **Package Input Nilai**
```
def input_nama():
    global nama
    nama = input("Masukkan Nama        : ")
    return nama

def input_nim():
    global nim
    nim = input("Masukkan NIM         : ")
    return nim

def input_nilaiTugas():
    global nilaiTugas
    nilaiTugas = int(input("Masukkan Nilai Tugas : "))
    return nilaiTugas

def input_nilaiUts():
    global nilaiUts
    nilaiUts = int(input("Masukkan Nilai UTS   : "))
    return nilaiUts

def input_nilaiUas():
    global nilaiUas
    nilaiUas = int(input("Masukkan Nilai UAS   : "))
    return nilaiUas
```
    
### **Package Daftar Nilai**
```
from view.input_nilai import *

dataMhs = {}

def tambah_data():
    global dataMhs
    nama = input_nama()
    nim = input_nim()
    nilaiTugas = input_nilaiTugas()
    nilaiUts = input_nilaiUas()
    nilaiUas = input_nilaiUas()
    nilaiAkhir = (0.30 * nilaiTugas) + (0.35 * nilaiUts) + (0.35 * nilaiUas)
    dataMhs[nama] = nim, nilaiTugas, nilaiUts, nilaiUas, nilaiAkhir
    print("\nData Berhasil Ditambahkan!")
    return dataMhs

def ubah_data():
    nama = input("Masukkan Nama: ")
    if nama in dataMhs.keys():
        nim           = input_nim()
        nilaiTugas    = input_nilaiTugas()
        nilaiUts      = input_nilaiUts()
        nilaiUas      = input_nilaiUas()
        nilaiAkhir    = (0.30 * nilaiTugas) + (0.35 * nilaiUts) + (0.35 * nilaiUas)
        dataMhs[nama]  = nim, nilaiTugas, nilaiUts, nilaiUas, nilaiAkhir
        print("\nData Berhasil Di Update!")
    else:
        print("Data tidak ditemukan!")

def hapus_data():
    nama = input("Masukkan Nama:  ")
    if nama in dataMhs.keys():
        del dataMhs[nama]
        print("Data",nama,"Telah dihapus!")
    else:
        print("Data Mahasiswa Tidak Ada".format(nama))
 ```
 
 ## **Package View Nilai**
 ```
 from model.daftar_nilai import *

def cetak_daftar_nilai():
    if dataMhs.items():
        print("\n                      DAFTAR NILAI MAHASISWA                    ")
        print("==================================================================")
        print("| No |     Nama     |    NIM    | Tugas |  UTS  |  UAS  |  Akhir |")
        print("==================================================================")
        i = 0
        for x in dataMhs.items():
            i += 1
            print("| {6:2} | {0:12s} | {1:9s} | {2:5} | {3:5} | {4:5} | {5:6} |".format(x[0], x[1][0], x[1][1], x[1][2],
                                                                                        x[1][3], x[1][4], i))
        print("==================================================================")
    else:
        print("\n                      DAFTAR NILAI MAHASISWA                    ")
        print("==================================================================")
        print("| No |     Nama     |    NIM    | Tugas |  UTS  |  UAS  |  Akhir |")
        print("==================================================================")
        print("|                          TIDAK ADA DATA!                       |")
        print("==================================================================")

def cetak_hasil_pencarian():
    nama = input("Masukkan Nama        : ")
    if nama in dataMhs.keys():
        print("\n                   DAFTAR NILAI MAHASISWA                   ")
        print("==============================================================")
        print("|     Nama     |    NIM    | Tugas |  UTS  |  UAS  |  Akhir  |")
        print("==============================================================")
        print("| {0:12s} | {1:9s} | {2:5} | {3:5} | {4:5} | {5:6}  |".format(nama, dataMhs[nama][0], dataMhs[nama][1],
                                                                            dataMhs[nama][2], dataMhs[nama][3],
                                                                            dataMhs[nama][4]))
        print("==============================================================")
    else:
        print("Datanya {0} Tidak Ada ".format(nama))
```
