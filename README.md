# 📖 PBO UAS - Aplikasi Login, Sign Up, Forgot Password serta CRUD dengan menggunakan JPA (Java Persistence APl)
## 📂 Topik Utama 
Langkah - langkah Login, Sign Up, Forgot Password serta CRUD dengan menggunakan Persistence

## 📜 Daftar Isi 
- [Koneksi Database dengan JPA](https://github.com/fauziaeka/TugasPBO_TM13/tree/main/META-INF)
- [Project Login](https://github.com/fauziaeka/TugasPBO_TM13/tree/main/PBO_TM13)
- [Project Data Mata Kuliah](https://github.com/fauziaeka/TugasPBO_TM13/tree/main/PBO_TM12)

## 📋 Langkah - Langkah

1. Membuat project baru dengan nama “PBO_UAS” dan uncheklist pada create main class  

 

2. Membuat package baru dengan nama “PBO_UAS” 

  

3. Membuat database baru dengan nama “PBO_UAS” yang didalamnya terdapat table “users” dan table “Mahasiswa” 


 
a. Membuat Table users untuk membuat login dan sign up  

 

b. Membuat Table Mahasiswa untuk menyimpan data Mahasiswa  


 
4. Menyambungkan Netbeans dengan PostgreSql 



a. Ketuk ‘Services’, pilih ‘Databases’ kemudian pilih ‘New Connection’ 

 

b. Pilih PostgreSQL 

 

c. Isi kolom database sesuai dengan nama database pada PostgreSQL kemudian isi password  

 

d. Select schema menjadi public 

 

e. Pada kolom input connection akan otomatis terisi, klik finish 

 

f. Klik service maka akan muncul keterangan bahwa koneksi telah berhasil  

 

g. Masukkan library PostgreSQL JDBC Drivers  

 

5. Buat persistence  

a. Buat persistence dengan cara klik kanan pada package, klik new kemudian pilih Entity Classes from Database 

 

b. Pilih database yang akan digunakan 



c. Masukkan password postgresql 



d. Pindahkan table pada sebelah kiri ke sebelah kanan dengan cara klik Add All>> 



e. Setelah tampilan seperti ini klik next  



f. Setelah tampilan Mapping Options, klik Finish 



g. Maka persistence users dan mahasiswa berhasil dibuat  



h. Setelah berhasil dibuat, akan muncul library sebagai berikut  



i. Berikut tampilan persistence.xml yang telah berhasil dibuat 



j. Berikut merupakan source code yang terbentuk  



6. Membuat kelas MahasiswaDB kemudian isi source codenya



7. Membuat frame Login  



a. Klik kanan, pilih ‘New’ kemudian pilih ‘JFrame Form’  

 

b. Beri nama FrameLogin 

 

c. Buat design pada halaman Login 

 

d. Mengisi import class pada frame Login 



e. Mengisi source code pada btnSignUp, agar saat user belum memiliki akun akan diarahkan ke frame SignUp untuk membuat akun terlebih dahulu  



f. Mengisi btnLogin untuk masuk ke dalam frame Data Mahasiswa  



g. Mengisi btnChangePassword yang berfungsi untuk mengarahkan user agar mengubah password apabila lupa password 



 8. Membuat frame SignUp 



a. Klik kanan, pilih ‘New’ kemudian pilih ‘JFrame Form’  

 

b. Beri nama FrameSignUp 

 

c. Buat design pada halaman SignUp 

 

d. Mengisi import class pada frame SignUp 



e. Mengisi source code pada btnSignUp untuk membuat akun baru dengan cara memasukkan nama lengkap, NIP/NIM dan password  



f. Membuat btnDelete untuk menghapus akun 



9. Membuat frame Forgot Password

   

a. Klik kanan, pilih ‘New’ kemudian pilih ‘JFrame Form’ 

 

b. Beri nama FrameForgotPassword  

 

c. Buat design pada frame ForgotPassword  

 

d. Mengisi import class pada frame ForgotPassword 



e. Mengisi source code pada btnForgotPassword yang berfungsi untuk mengubah password apabila user lupa password  



f. Menambahkan btnClear yang berfungsi untuk menghapus password apabila ingin mengubah password akun yang lain 



10. Membuat FrameMahasiswa 

a. Klik kanan, pilih ‘New’ kemudian pilih ‘JFrame Form’ 



b. Beri nama FrameMahasiswa  



c. Buat design pada FrameMahasiswa  



11. Membuat file laporan (Print)



a. Masukkan library untuk menambahkan Jasper Report yang berfungsi untuk mencetak data 



b. Buat class baru untuk design reportnya dengan cara klik kanan pada package “PBO_UAS” kemudian pilih ‘New’ dan pilih ‘Report Wizard’ 



c. Pilih design layout  



d. Sambungkan ke database yang telah disiapkan, klik Next 



e. Masukkan nama database, username dan password kemudian klik next  



f. Pilih query dan ketikkan secara manual ‘select * from Users’ dan ‘select * from Mahasiswa’ atau bisa juga pilih design query jika memiliki banyak table  



g. Masukkan password database, klik OK 



h. Atur group by sesuai dengan table pada database, lalu pindahkan ke sebelah kanan dan klik next



i. Setelah muncul seperti ini, klik next 



j. Jika muncul tampilan seperti ini, maka telah berhasil membuat report baru 



k. Membuat design pada class Jasper Wizard  



12. Membuat CSV (Upload) 



a. Membuat data Mahasiswa pada Ms Excel yang terdiri dari 5 kolom yang berisi NIM, Nama, Alamat, AsalSMA dan NamaOrangTua 



b. Simpan dalam format CSV (Comma Delimited) 



13. Mengisi source code pada FrameMahasiswa agar program dapat berjalan
    

a. Mengisi import class pada FrameMahasiswa  



b. Mengisi source code pada method tampil yang digunakan untuk menampilkan data pada GUI 



c. Mengisi source code pada btnInsert yang berfungsi untuk menambahkan dat. Button ini berfungsi untuk menambahkan data pada ‘DataMahasiswa’ Sebagai user, kita diminta untuk mengisi informasi mengenai NIM, Nama, Alamat, AsalSMA dan NamaOrangTua. Setelah dimasukkan, kita bisa menekan button Insert. Jika berhasil, akan muncul pesan ‘Data berhasil disimpan’ 



d. Mengisi source code pada btnUpdate yang berfungsi untuk memperbarui data. Langkah pertama masukkan NIM yang ingin diubah, kemudian masukkan informasi mengenai Nama, Alamat, AsalSMA dan NamaOrangTua. Jika berhasil, sistem akan mencetak pesan pemberitahuan bahwa ‘Data berhasil diupdate’ 



e. Mengisi source code pada btnDelete yang berfungsi untuk menghapus data pada ‘Data Mahasiswa’ .User bisa memasukkan data yang ingin dihapus atau bisa juga dengan meng-klik data yang ingin dihapus pada kolom list. Kemudian akan muncul pesan konfirmasi apakah user inggin menghapus data atau tidak. Jika ‘iya’ data akan otomatis dihapus dan jika ‘tidak’ maka data akan batal dihapus 



f. Mengisi source code pada btnExit yang berfungsi untuk keluar dari FrameMahasiswa dengan kembali ke frame Login 



g. Mengisi source code pada program tblMahasiswaMouseClicked yang berfungsi untuk menampilkan data dalam bentuk tabel 



h. Mengisi source code pada btnPrint yang berfungsi untuk mencetak file yang bisa disimpan ke dalam bentuk pdf 



i. Mengisi code btnUpload yang berfungsi untuk mengupload file CSV ke dalam program 



j. Mengisi source code pada program bersih() yang berfungsi untuk memastikan bahwa setelah data dimasukkan atau operasi selesai dilakukan, semua input dari user direset untuk memudahkan pengguna dalam memasukkan data yang baru tanpa harus menghapusnya secara manual 



14. Hasil eksekusi insert data



15. Hasil eksekusi update data



16. Hasil eksekusi delete data



17. Hasil eksekusi print data 



18. Hasil eksekusi upload data 

a. Pilih file yang akan diupload 



b. Jika berhasil akan muncul pesan seperti ini 



c. Data berhasil dimasukkan 



19. Hasil eksekusi btnExit  

 

 
