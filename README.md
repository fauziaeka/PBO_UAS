# 📖 PBO UAS - Aplikasi Login, Sign Up, Forgot Password serta CRUD dengan menggunakan JPA (Java Persistence APl)

## 📂 Topik Utama 
Langkah - langkah Login, Sign Up, Forgot Password serta CRUD dengan menggunakan Persistence

## 📋 Langkah - Langkah

1. Membuat project baru dengan nama “PBO_UAS” dan uncheklist pada create main class  

 ![image](https://github.com/user-attachments/assets/5f20b230-9d5e-4d04-a2ca-e3a1711ffcf3)

2. Membuat package baru dengan nama “PBO_UAS” 

  ![image](https://github.com/user-attachments/assets/ba5b4a50-9f88-45bc-8c30-b5e012047c42)

  ![image](https://github.com/user-attachments/assets/e4a1ed8c-636b-47cf-bf57-d77a70cf3fe6)

3. Membuat database baru dengan nama “PBO_UAS” yang didalamnya terdapat table “users” dan table “Mahasiswa” 

 ![image](https://github.com/user-attachments/assets/63e9f9b5-0e78-49e2-aa84-5600f4ca0a32)

 ![image](https://github.com/user-attachments/assets/2cda482b-000d-4900-9c7d-79de16afab57)

a. Membuat Table users untuk membuat login dan sign up  
 
![image](https://github.com/user-attachments/assets/21441d77-b5f1-49cf-93c4-d94fee82f945)

![image](https://github.com/user-attachments/assets/8a01520f-2216-4196-906f-e95ee712cdad)

b. Membuat Table Mahasiswa untuk menyimpan data Mahasiswa  

![image](https://github.com/user-attachments/assets/31a86bc8-ebfc-45b2-a0a3-3937e35b5c25)

![image](https://github.com/user-attachments/assets/bd5516e8-c46c-47d9-9f10-b7ce3e9be788)
 
4. Menyambungkan Netbeans dengan PostgreSql 

a. Ketuk ‘Services’, pilih ‘Databases’ kemudian pilih ‘New Connection’ 

![image](https://github.com/user-attachments/assets/b3911698-47bf-4d5c-b860-d648eb249edc)
 
b. Pilih PostgreSQL 

![image](https://github.com/user-attachments/assets/9e91e701-fdac-46f3-96a8-26083973e9c2)

c. Isi kolom database sesuai dengan nama database pada PostgreSQL kemudian isi password  

 ![image](https://github.com/user-attachments/assets/fe249a22-3870-4d25-8f1b-4444cc138467)

d. Select schema menjadi public 

![image](https://github.com/user-attachments/assets/5f675c9e-ed3e-4f4a-864a-a67827a2e5ca)

e. Pada kolom input connection akan otomatis terisi, klik finish 

![image](https://github.com/user-attachments/assets/5ee088ec-fa1a-4860-9702-4fedab100a30)

f. Klik service maka akan muncul keterangan bahwa koneksi telah berhasil  

![image](https://github.com/user-attachments/assets/67ee5b86-5083-4cea-ada2-ae5765174a31)

g. Masukkan library PostgreSQL JDBC Drivers  

![image](https://github.com/user-attachments/assets/65d365a3-f698-4179-bb17-5c2b3f74c1d4)

![image](https://github.com/user-attachments/assets/f8f7b2cf-4c44-47d1-a6de-18fc2e7f8fe8)

5. Buat persistence  

a. Buat persistence dengan cara klik kanan pada package, klik new kemudian pilih Entity Classes from Database 

![image](https://github.com/user-attachments/assets/05256c59-b97a-4f85-b5a8-99e6496d8416)

b. Pilih database yang akan digunakan 

![image](https://github.com/user-attachments/assets/56085268-45f6-4299-8343-eac22074cdf1)

c. Masukkan password postgresql 

![image](https://github.com/user-attachments/assets/03bfc007-4523-409f-8759-698f67ddf0e4)

d. Pindahkan table pada sebelah kiri ke sebelah kanan dengan cara klik Add All>> 

![image](https://github.com/user-attachments/assets/c3d35fdc-6ce2-4fc8-baf0-be88fd33d67b)

![image](https://github.com/user-attachments/assets/6af57846-6daa-4d01-974b-d8ddaab366fd)

e. Setelah tampilan seperti ini klik next  

![image](https://github.com/user-attachments/assets/bd99296e-4292-4c83-87e1-3ac22298a7c4)

f. Setelah tampilan Mapping Options, klik Finish 

![image](https://github.com/user-attachments/assets/c279d475-190f-468b-be81-7fe24b964c1f)

g. Setelah berhasil dibuat, akan muncul library sebagai berikut  

![image](https://github.com/user-attachments/assets/85537e6f-fdbd-4bc8-bbba-437ef40c41d6)

h. Berikut tampilan persistence.xml yang telah berhasil dibuat 

![image](https://github.com/user-attachments/assets/e7f2fc17-2559-4028-a25a-d0f36cc570eb)

i. Berikut merupakan source code yang terbentuk  

![image](https://github.com/user-attachments/assets/3678287e-5aa2-4451-b0de-974f09e1e0c9)

6. Membuat kelas MahasiswaDB kemudian isi source codenya

![image](https://github.com/user-attachments/assets/89e8067f-b03e-4b2d-a649-fdc45cc33d16)

![image](https://github.com/user-attachments/assets/c845c4f3-b21e-478c-89c6-c857e80db862)

```
package pbo_uas;

import java.sql.ResultSet;
import java.sql.ResultSetMetaData;
import java.util.Vector;
import javax.swing.table.DefaultTableModel;
import javax.swing.table.TableModel;

/**
 *
 * @author win 10
 */
public class MahasiswaDB {

    public static TableModel resultSetToTableModel(ResultSet rs) {
        try {
            ResultSetMetaData metaData = rs.getMetaData();
            int numberOfColumns = metaData.getColumnCount();
            Vector columnNames = new Vector();

            // Get the column names
            for (int column = 0; column < numberOfColumns; column++) {
                columnNames.addElement(metaData.getColumnLabel(column + 1));
            }

            // Get all rows.
            Vector rows = new Vector();

            while (rs.next()) {
                Vector newRow = new Vector();

                for (int i = 1; i <= numberOfColumns; i++) {
                    newRow.addElement(rs.getObject(i));
                }

                rows.addElement(newRow);
            }

            return new DefaultTableModel(rows, columnNames);
        } catch (Exception e) {
            e.printStackTrace();

            return null;
        }
    }
}
```

7. Membuat frame Login  

a. Klik kanan, pilih ‘New’ kemudian pilih ‘JFrame Form’  

![image](https://github.com/user-attachments/assets/0c7919c5-0eef-4562-af04-5d3149ae1fb4)

b. Beri nama FrameLogin 

![image](https://github.com/user-attachments/assets/79eeb32a-1f0a-4c17-b788-c78e7a9fbaec)

c. Buat design pada halaman Login 

![image](https://github.com/user-attachments/assets/848ab4f1-d4f4-49aa-81bf-3e4c680ca15e)

d. Mengisi import class pada frame Login 

```
package pbo_uas;

import javax.persistence.EntityManager;
import javax.persistence.EntityManagerFactory;
import javax.persistence.Persistence;
import javax.swing.JOptionPane;
```
e. Mengisi source code pada btnSignUp, agar saat user belum memiliki akun akan diarahkan ke frame SignUp untuk membuat akun terlebih dahulu  

```
 private void btnSignUpActionPerformed(java.awt.event.ActionEvent evt) {                                          
        // TODO add your handling code here:
        FrameSignUp SignUpFrame = new FrameSignUp();
        SignUpFrame.setVisible(true);
        this.dispose();
    }          
```

f. Mengisi btnLogin untuk masuk ke dalam frame Data Mahasiswa  

```
private void btnLoginActionPerformed(java.awt.event.ActionEvent evt) {                                         
        // TODO add your handling code here:
        String nim = tfusername.getText();
        String password = new String(tfpw.getPassword());
        if (nim.isEmpty() || password.isEmpty()) {
            JOptionPane.showMessageDialog(null, "Isi Terlebih Dahulu");
            return;
        }
        EntityManagerFactory emf = Persistence.createEntityManagerFactory("PBO_UASPU");
        EntityManager em = emf.createEntityManager();
        try {
            em.getTransaction().begin();
            Users user = em.find(Users.class, nim);
            if (user == null) {
                JOptionPane.showMessageDialog(null, "Username tidak ditemukan");
            } else {
                if (user.getPassword().equals(password)) {
                    JOptionPane.showMessageDialog(null, "BERHASIL LOGIN!!");
                    FrameMahasiswa m = new FrameMahasiswa();
                    m.setVisible(true);
                    this.dispose();
                } else {
                    JOptionPane.showMessageDialog(null, "Username atau Password salah!");
                }
            }
            em.getTransaction().commit();
        } catch (Exception e) {
            JOptionPane.showMessageDialog(null, "Terjadi kesalahan: " + e.getMessage());
            if (em.getTransaction().isActive()) {
                em.getTransaction().rollback();
            }
        } finally {
            em.close();
            emf.close();
        }
    }       
```

g. Mengisi btnChangePassword yang berfungsi untuk mengarahkan user agar mengubah password apabila lupa password 

```
 private void btnChangePasswordActionPerformed(java.awt.event.ActionEvent evt) {                                                  
        // TODO add your handling code here:
        FrameForgotPassword ForgotPasswordFrame = new FrameForgotPassword();
        ForgotPasswordFrame.setVisible(true);
        this.dispose();
    }
```

 8. Membuat frame SignUp 

a. Klik kanan, pilih ‘New’ kemudian pilih ‘JFrame Form’  

![image](https://github.com/user-attachments/assets/e9ca0ecc-c4ef-472b-b9b3-1b3462c52f6f)

b. Beri nama FrameSignUp 

![image](https://github.com/user-attachments/assets/fa8fafcf-0908-4ae5-9fea-655a76904baf)

c. Buat design pada halaman SignUp 

 ![image](https://github.com/user-attachments/assets/929ab85b-078e-4c3a-b35e-d5491761dc5a)

d. Mengisi import class pada frame SignUp 

```
package pbo_uas;

import javax.persistence.EntityManager;
import javax.persistence.EntityManagerFactory;
import javax.persistence.Persistence;
import javax.swing.JOptionPane;
```
e. Mengisi source code pada btnSignUp untuk membuat akun baru dengan cara memasukkan nama lengkap, NIP/NIM dan password  

```
private void btnSignUpActionPerformed(java.awt.event.ActionEvent evt) {                                          
        // TODO add your handling code here:
        if (tfnama.getText().isEmpty() || tfusername.getText().isEmpty() || tfpw.getText().isEmpty()) {
        JOptionPane.showMessageDialog(null, "Nama, NIM, dan Password harus diisi!");
    } else {
        String nama = tfnama.getText();
        String nim = tfusername.getText();
        String password = tfpw.getText();

        if (password.length() < 8) {
            JOptionPane.showMessageDialog(null, "Password minimal harus terdiri dari 8 karakter!");
            return;
        }

        EntityManagerFactory emf = Persistence.createEntityManagerFactory("PBO_UASPU");
        EntityManager em = emf.createEntityManager();

        try {
            em.getTransaction().begin();
            Users existingUser = em.find(Users.class, nim);
            if (existingUser != null) {
                JOptionPane.showMessageDialog(null, "NIM sudah digunakan, silakan pilih yang lain!");
                clear();
            } else {
                Users newUser = new Users();
                newUser.setFullName(nama);
                newUser.setNim(nim);
                newUser.setPassword(password);
                em.persist(newUser);
                em.getTransaction().commit();
                JOptionPane.showMessageDialog(null, "Akun berhasil dibuat!");
                clear();
                FrameLogin loginFrame = new FrameLogin();
                loginFrame.setVisible(true);
                this.dispose();
            }
        } catch (Exception e) {
            if (em.getTransaction().isActive()) {
                em.getTransaction().rollback();
            }
            JOptionPane.showMessageDialog(null, "Terjadi kesalahan: " + e.getMessage());
        } finally {
            em.close();
            emf.close();
        }
    }
    }                  
```

f. Membuat btnDelete untuk menghapus akun 

```
 private void btnDeleteActionPerformed(java.awt.event.ActionEvent evt) {                                          
        // TODO add your handling code here:
        if (tfusername.getText().isEmpty()) {
            JOptionPane.showMessageDialog(null, "NIM harus diisi untuk menghapus akun!");
        } else {
            String nim = tfusername.getText();
            EntityManagerFactory emf = Persistence.createEntityManagerFactory("PBO_UASPU");
            EntityManager em = emf.createEntityManager();
            try {
                em.getTransaction().begin();
                Users user = em.find(Users.class, nim);
                if (user == null) {
                    JOptionPane.showMessageDialog(null, "NIM tidak ditemukan. Tidak ada yang dihapus.");
                } else {
                    int confirm = JOptionPane.showConfirmDialog(null, "Apakah Anda yakin ingin menghapus akun ini?",
                            "Konfirmasi Hapus", JOptionPane.YES_NO_OPTION);
                    if (confirm == JOptionPane.YES_OPTION) {
                        em.remove(user);
                        em.getTransaction().commit();
                        JOptionPane.showMessageDialog(null, "Akun berhasil dihapus!");
                        clear();
                    } else {
                        JOptionPane.showMessageDialog(null, "Penghapusan akun dibatalkan.");
                        em.getTransaction().rollback();
                    }
                }
            } catch (Exception e) {
                if (em.getTransaction().isActive()) {
                    em.getTransaction().rollback();
                }
                JOptionPane.showMessageDialog(null, "Terjadi kesalahan: " + e.getMessage());
            } finally {
                em.close();
                emf.close();
            }
        }
    }                
```

9. Membuat frame Forgot Password

a. Klik kanan, pilih ‘New’ kemudian pilih ‘JFrame Form’ 

 ![image](https://github.com/user-attachments/assets/07afcbb9-118f-449b-8131-1218e2a42937)

b. Beri nama FrameForgotPassword  

 ![image](https://github.com/user-attachments/assets/8d49f21c-4c10-41a6-a68d-3a4c57ec55f3)

c. Buat design pada frame ForgotPassword  

 ![image](https://github.com/user-attachments/assets/fbb54627-2041-4973-9890-973af8590fb7)

d. Mengisi import class pada frame ForgotPassword 

 ```
package pbo_uas;

import javax.swing.*;
import javax.persistence.EntityManager;
import javax.persistence.EntityManagerFactory;
import javax.persistence.Persistence;
```

e. Mengisi source code pada btnForgotPassword yang berfungsi untuk mengubah password apabila user lupa password  

```
private void btnForgotPasswordActionPerformed(java.awt.event.ActionEvent evt) {                                                  
        // TODO add your handling code here:
        String usernameInput = tfnim.getText();
    char[] newPasswordCharArray = tfpwbaru.getPassword();  // Get the new password as a char[]
    char[] confirmPasswordCharArray = tfkonfirmasi.getPassword();  // Get the confirmation password as a char[]

    // Convert char[] to String for comparison
    String newPasswordInput = new String(newPasswordCharArray);
    String confirmPasswordInput = new String(confirmPasswordCharArray);

    // Check if any input fields are empty
    if (usernameInput.isEmpty() || newPasswordInput.isEmpty() || confirmPasswordInput.isEmpty()) {
        JOptionPane.showMessageDialog(null, "Semua kolom harus diisi");
        return;
    }

    // Check if the new password matches the confirmation password
    if (!newPasswordInput.equals(confirmPasswordInput)) {
        JOptionPane.showMessageDialog(null, "Password baru dan konfirmasi password tidak cocok");
        return;
    }

    // Setup EntityManager for database operations
    EntityManagerFactory emf = Persistence.createEntityManagerFactory("PBO_UASPU");
    EntityManager em = emf.createEntityManager();

    try {
        // Begin transaction
        em.getTransaction().begin();

        // Try to find the user in the database
        Users userEntity = em.find(Users.class, usernameInput);

        // If the user does not exist
        if (userEntity == null) {
            JOptionPane.showMessageDialog(null, "Username tidak ditemukan");
        } else {
            // Set the new password and commit the transaction
            userEntity.setPassword(newPasswordInput);
            em.getTransaction().commit();

            // Inform the user about the success
            JOptionPane.showMessageDialog(null, "Password berhasil diperbarui");

            // Proceed to login screen and close the current frame
            FrameLogin loginScreen = new FrameLogin();
            loginScreen.setVisible(true);
            this.dispose();
        }
    } catch (Exception e) {
        // Handle any errors and rollback the transaction in case of an exception
        if (em.getTransaction().isActive()) {
            em.getTransaction().rollback();
        }
        
        // Log the error and show an appropriate message
        e.printStackTrace();
        JOptionPane.showMessageDialog(null, "Terjadi kesalahan saat memperbarui password.");
    } finally {
        // Close the EntityManager and EntityManagerFactory resources
        em.close();
        emf.close();
    }
    }                    
```

f. Menambahkan btnClear yang berfungsi untuk menghapus password apabila ingin mengubah password akun yang lain 

```
 private void btnClearActionPerformed(java.awt.event.ActionEvent evt) {                                         
        // TODO add your handling code here:
        tfnim.setText(" ");
        tfpwbaru.setText(" ");
        tfkonfirmasi.setText(" ");
        tfpwbaru.setEditable(true);
    }       
```


10. Membuat FrameMahasiswa 

a. Klik kanan, pilih ‘New’ kemudian pilih ‘JFrame Form’ 

![image](https://github.com/user-attachments/assets/ad252aba-5059-452b-9eb5-28aaa4fdaae8)

b. Beri nama FrameMahasiswa  

![image](https://github.com/user-attachments/assets/21609e66-2db5-4efa-8a52-4a1c42f961a7)

c. Buat design pada FrameMahasiswa  

![image](https://github.com/user-attachments/assets/966f1c05-891c-4b1a-99a3-e2ab0078e662)


11. Membuat file laporan (Print)

a. Masukkan library untuk menambahkan Jasper Report yang berfungsi untuk mencetak data 

![image](https://github.com/user-attachments/assets/3f3f8131-76e5-4907-8abf-e01030ae420a)

b. Buat class baru untuk design reportnya dengan cara klik kanan pada package “PBO_UAS” kemudian pilih ‘New’ dan pilih ‘Report Wizard’ 

![image](https://github.com/user-attachments/assets/b7f536dc-8744-464c-882b-89fafa997e0b)

c. Pilih design layout  

![image](https://github.com/user-attachments/assets/eef0ab55-4085-4595-beea-a4fb07363f55)

d. Beri nama pada layout 

![image](https://github.com/user-attachments/assets/985003c8-2524-4e78-9e2a-e606a7b501ec)

e. Pilih database JDBC Connection

![image](https://github.com/user-attachments/assets/e6e62065-104c-4faa-b045-7970892964f7)

f. Pilih query dan ketikkan secara manual ‘select * from Mahasiswa’ atau bisa juga pilih design query jika memiliki banyak table  

![image](https://github.com/user-attachments/assets/dbe4842c-74c9-4947-b519-77891d235ed4)

g. Masukkan password database, klik OK 

![image](https://github.com/user-attachments/assets/a28e93d1-f8f4-4461-8c0e-261f50520dc1)

h. Atur group by sesuai dengan table pada database, lalu pindahkan ke sebelah kanan dan klik next

![image](https://github.com/user-attachments/assets/8f15ddba-fe3a-47e4-8ce1-b7dc08c9fa74)

![image](https://github.com/user-attachments/assets/2cb3c82e-0a4c-4ae2-a25b-79f64fc15bf4)


i. Setelah muncul seperti ini, klik next 

![image](https://github.com/user-attachments/assets/805d8a66-60ed-4583-b8d6-9f07044cf686)

j. Jika muncul tampilan seperti ini, maka telah berhasil membuat report baru 

![image](https://github.com/user-attachments/assets/d6a99c02-d5a0-4324-a39e-afe54a44b36a)

k. Membuat design pada class Jasper Wizard  

![image](https://github.com/user-attachments/assets/1ae5f2ba-524e-45dc-8613-22ddc1e3c6c0)

12. Membuat CSV (Upload) 

a. Membuat data Mahasiswa pada Ms Excel yang terdiri dari 5 kolom yang berisi NIM, Nama, Alamat, AsalSMA dan NamaOrangTua 

 ![image](https://github.com/user-attachments/assets/7060fd67-6bc4-4306-b272-cf82839a6a63)

b. Simpan dalam format CSV (Comma Delimited) 

 ![image](https://github.com/user-attachments/assets/9c9c527b-067f-467d-9487-b1c167039ab6)

13. Mengisi source code pada FrameMahasiswa agar program dapat berjalan
    
a. Mengisi import class pada FrameMahasiswa  

```
package pbo_uas;

import java.awt.HeadlessException;
import java.io.BufferedReader;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.util.logging.Level;
import java.util.logging.Logger;
import javax.swing.JOptionPane;
import javax.swing.table.TableModel;
import javax.swing.table.DefaultTableModel;
import pbo_uas.MahasiswaDB;
import net.sf.jasperreports.engine.JasperReport;
import net.sf.jasperreports.engine.*;
import net.sf.jasperreports.view.JasperViewer;
import net.sf.jasperreports.engine.util.JRLoader;
import java.sql.Connection;
import java.util.List;
import javax.persistence.EntityManager;
import javax.persistence.EntityManagerFactory;
import javax.persistence.EntityTransaction;
import javax.persistence.Persistence;
import javax.persistence.Query;
import javax.swing.JFileChooser;
import javax.swing.JScrollPane;
import javax.swing.filechooser.FileSystemView;
import net.sf.jasperreports.engine.JasperFillManager;
import net.sf.jasperreports.engine.JasperPrint;
import pbo_uas.FrameLogin;
```

b. Mengisi source code pada method tampil yang digunakan untuk menampilkan data pada GUI 

```

    public void tampil() {
        EntityManagerFactory emf = Persistence.createEntityManagerFactory("PBO_UASPU");
        EntityManager em = emf.createEntityManager();

        try {
            Query query = em.createNamedQuery("Mahasiswa.findAll");
            List<Mahasiswa> hasil = query.getResultList();

            DefaultTableModel tbMahasiswa = new DefaultTableModel(new String[]{"NIM", "Nama", "Alamat", "Asal SMA", "Nama Orang Tua"}, 0);

            for (Mahasiswa data : hasil) {
                Object[] baris = new Object[5];
                baris[0] = data.getNim();
                baris[1] = data.getNama();
                baris[2] = data.getAlamat();
                baris[3] = data.getAsalsma();
                baris[4] = data.getNamaorangtua();
                tbMahasiswa.addRow(baris);
            }

            tblMahasiswa.setModel(tbMahasiswa);

        } catch (Exception e) {
            JOptionPane.showMessageDialog(this, "Terjadi kesalahan: " + e.getMessage());
        } finally {
            em.close();
        }
    }
```
c. Mengisi source code pada btnInsert yang berfungsi untuk menambahkan dat. Button ini berfungsi untuk menambahkan data pada ‘DataMahasiswa’ Sebagai user, kita diminta untuk mengisi informasi mengenai NIM, Nama, Alamat, AsalSMA dan NamaOrangTua. Setelah dimasukkan, kita bisa menekan button Insert. Jika berhasil, akan muncul pesan ‘Data berhasil disimpan’ 

```
private void btnInsertActionPerformed(java.awt.event.ActionEvent evt) {                                          
        // TODO add your handling code here:                                        
        String nim = tfNIM.getText();
        String nama = tfNama.getText();
        String alamat = tfAlamat.getText();
        String asalsma = tfAsalSMA.getText();
        String namaorangtua = tfNamaOrangTua.getText();

        EntityManagerFactory emf = Persistence.createEntityManagerFactory("PBO_UASPU");
        EntityManager em = emf.createEntityManager();
        EntityTransaction transaction = em.getTransaction();

        try {
            transaction.begin();

            Mahasiswa mahasiswa = new Mahasiswa();
            mahasiswa.setNim(nim);
            mahasiswa.setNama(nama);
            mahasiswa.setAlamat(alamat);
            mahasiswa.setAsalsma(asalsma);
            mahasiswa.setNamaorangtua(namaorangtua);

            em.persist(mahasiswa);

            transaction.commit();

            JOptionPane.showMessageDialog(null, "Data berhasil disimpan");

        } catch (HeadlessException e) {
            if (transaction.isActive()) {
                transaction.rollback();
            }
            JOptionPane.showMessageDialog(null, "Terjadi kesalahan: " + e.getMessage());
        } finally {
            em.close();
        }

        bersih();
        tampil();
    }                    
```

d. Mengisi source code pada btnUpdate yang berfungsi untuk memperbarui data. Langkah pertama masukkan NIM yang ingin diubah, kemudian masukkan informasi mengenai Nama, Alamat, AsalSMA dan NamaOrangTua. Jika berhasil, sistem akan mencetak pesan pemberitahuan bahwa ‘Data berhasil diupdate’ 

```
private void btnUpdateActionPerformed(java.awt.event.ActionEvent evt) {                                          
        // TODO add your handling code here:                                         
        String nim, nama, alamat, asalsma, namaorangtua;

        if (tfNIM.getText().isEmpty()) {
            JOptionPane.showMessageDialog(null, "NIM harus diisi");
            return;
        }
        if (tfNama.getText().isEmpty()) {
            JOptionPane.showMessageDialog(null, "Nama harus diisi");
            return;
        }
        if (tfAlamat.getText().isEmpty()) {
            JOptionPane.showMessageDialog(null, "Alamat harus diisi");
            return;
        }
        if (tfAsalSMA.getText().isEmpty()) {
            JOptionPane.showMessageDialog(null, "Asal SMA harus diisi");
            return;
        }
        if (tfNamaOrangTua.getText().isEmpty()) {
            JOptionPane.showMessageDialog(null, "Nama Orang Tua harus diisi");
            return;
        }

        EntityManagerFactory emf = Persistence.createEntityManagerFactory("PBO_UASPU");
        EntityManager em = emf.createEntityManager();
        EntityTransaction transaction = em.getTransaction();

        try {
            transaction.begin();

            nim = tfNIM.getText();
            nama = tfNama.getText();
            alamat = tfAlamat.getText();
            asalsma = tfAsalSMA.getText();
            namaorangtua = tfNamaOrangTua.getText();

            Mahasiswa mahasiswa = em.find(Mahasiswa.class, nim);

            if (mahasiswa != null) {
                mahasiswa.setNama(nama);
                mahasiswa.setAlamat(alamat);
                mahasiswa.setAsalsma(asalsma);
                mahasiswa.setNamaorangtua(namaorangtua);

                em.merge(mahasiswa);
                transaction.commit();

                JOptionPane.showMessageDialog(null, "Data berhasil diupdate");
                bersih();
            } else {
                JOptionPane.showMessageDialog(null, "Data tidak ditemukan");
            }

        } catch (Exception ex) {
            JOptionPane.showMessageDialog(null, "Terjadi kesalahan: " + ex.getMessage());
            if (transaction.isActive()) {
                transaction.rollback();
            }
        } finally {
            em.close();
        }

        tampil();
    }             
```

e. Mengisi source code pada btnDelete yang berfungsi untuk menghapus data pada ‘Data Mahasiswa’ .User bisa memasukkan data yang ingin dihapus atau bisa juga dengan meng-klik data yang ingin dihapus pada kolom list. Kemudian akan muncul pesan konfirmasi apakah user inggin menghapus data atau tidak. Jika ‘iya’ data akan otomatis dihapus dan jika ‘tidak’ maka data akan batal dihapus 

```
  private void btnDeleteActionPerformed(java.awt.event.ActionEvent evt) {                                          
        // TODO add your handling code here:                                         
        String nim = tfNIM.getText();

        if (nim.isEmpty()) {
            JOptionPane.showMessageDialog(null, "NIM tidak boleh kosong!", "Error", JOptionPane.ERROR_MESSAGE);
            return;
        }

        EntityManagerFactory emf = Persistence.createEntityManagerFactory("PBO_UASPU");
        EntityManager em = emf.createEntityManager();
        EntityTransaction transaction = em.getTransaction();

        try {
            int jawab = JOptionPane.showConfirmDialog(null, "Apakah Anda yakin ingin menghapus Mahasiswa dengan NIM: " + nim + "?", "Konfirmasi Penghapusan", JOptionPane.YES_NO_OPTION);

            if (jawab == JOptionPane.YES_OPTION) {
                transaction.begin();

                Mahasiswa mahasiswa = em.find(Mahasiswa.class, nim);

                if (mahasiswa != null) {
                    em.remove(mahasiswa);
                    transaction.commit();
                    JOptionPane.showMessageDialog(null, "Data berhasil dihapus");
                } else {
                    JOptionPane.showMessageDialog(null, "Data tidak ditemukan untuk NIM: " + nim);
                }
            } else {
                JOptionPane.showMessageDialog(this, "Penghapusan dibatalkan");
            }

        } catch (Exception ex) {
            if (transaction.isActive()) {
                transaction.rollback();
            }
            JOptionPane.showMessageDialog(null, "Terjadi kesalahan: " + ex.getMessage(), "Error", JOptionPane.ERROR_MESSAGE);
        } finally {
            em.close();
        }

        tampil();
        bersih();
    }                                         

    private void btnCetakActionPerformed(java.awt.event.ActionEvent evt) {                                         
        // TODO add your handling code here:
        try {
            if (conn == null || conn.isClosed()) {
                conn = DriverManager.getConnection("jdbc:postgresql://localhost:5432/PBO_UAS", "postgres", "1234");
            }

            String path = "src/pbo_uas/mahasiswa1.jasper";
            JasperReport report = (JasperReport) JRLoader.loadObjectFromFile(path);

            if (conn != null) {
                JasperPrint jprint = JasperFillManager.fillReport(report, null, conn);
                JasperViewer jviewer = new JasperViewer(jprint, false);
                jviewer.setDefaultCloseOperation(JasperViewer.DISPOSE_ON_CLOSE);
                jviewer.setVisible(true);
            } else {
                JOptionPane.showMessageDialog(null, "Koneksi database tidak tersedia.");
            }
        } catch (SQLException e) {
            e.printStackTrace();
            JOptionPane.showMessageDialog(null, "Koneksi database gagal: " + e.getMessage());
        } catch (JRException e) {
            e.printStackTrace();
            JOptionPane.showMessageDialog(null, "Gagal mencetak laporan: " + e.getMessage());
        }
        tampil();
    }               
```

f. Mengisi source code pada btnLogout yang berfungsi untuk keluar dari FrameMahasiswa dengan kembali ke frame Login 

```
private void btnLogoutActionPerformed(java.awt.event.ActionEvent evt) {                                          
        // TODO add your handling code here:
        FrameLogin LoginFrame = new FrameLogin();
        LoginFrame.setVisible(true);
        this.dispose();
    } 
```

g. Mengisi source code pada program tblMahasiswaMouseClicked yang berfungsi untuk menampilkan data dalam bentuk tabel 

```
  private void tblMahasiswaMouseClicked(java.awt.event.MouseEvent evt) {                                          
        // TODO add your handling code here:
        int row = tblMahasiswa.getSelectedRow();
        tfNIM.setText(tblMahasiswa.getValueAt(row, 0).toString());
        tfNama.setText(tblMahasiswa.getValueAt(row, 1).toString());
        tfAlamat.setText(tblMahasiswa.getValueAt(row, 2).toString());
        tfAsalSMA.setText(tblMahasiswa.getValueAt(row, 3).toString());
        tfNamaOrangTua.setText(tblMahasiswa.getValueAt(row, 4).toString());
        tampil();
    }     
```

h. Mengisi source code pada btnPrint yang berfungsi untuk mencetak file yang bisa disimpan ke dalam bentuk pdf 

```
    private void btnCetakActionPerformed(java.awt.event.ActionEvent evt) {                                         
        // TODO add your handling code here:
        try {
            if (conn == null || conn.isClosed()) {
                conn = DriverManager.getConnection("jdbc:postgresql://localhost:5432/PBO_UAS", "postgres", "1234");
            }

            String path = "src/pbo_uas/mahasiswa1.jasper";
            JasperReport report = (JasperReport) JRLoader.loadObjectFromFile(path);

            if (conn != null) {
                JasperPrint jprint = JasperFillManager.fillReport(report, null, conn);
                JasperViewer jviewer = new JasperViewer(jprint, false);
                jviewer.setDefaultCloseOperation(JasperViewer.DISPOSE_ON_CLOSE);
                jviewer.setVisible(true);
            } else {
                JOptionPane.showMessageDialog(null, "Koneksi database tidak tersedia.");
            }
        } catch (SQLException e) {
            e.printStackTrace();
            JOptionPane.showMessageDialog(null, "Koneksi database gagal: " + e.getMessage());
        } catch (JRException e) {
            e.printStackTrace();
            JOptionPane.showMessageDialog(null, "Gagal mencetak laporan: " + e.getMessage());
        }
        tampil();
    }
```

i. Mengisi code btnUpload yang berfungsi untuk mengupload file CSV ke dalam program 

```
 private void btnUploadActionPerformed(java.awt.event.ActionEvent evt) {                                          
        // TODO add your handling code here:
        JFileChooser jfc = new JFileChooser(FileSystemView.getFileSystemView().getHomeDirectory());
        int returnValue = jfc.showOpenDialog(null);
        if (returnValue == JFileChooser.APPROVE_OPTION) {
            File filePilihan = jfc.getSelectedFile();
            System.out.println("File yang dipilih : " + filePilihan.getAbsolutePath());

            EntityManagerFactory emf = null;
            EntityManager em = null;
            EntityTransaction transaction = null;
            BufferedReader br = null;

            try {
                emf = Persistence.createEntityManagerFactory("PBO_UASPU");
                em = emf.createEntityManager();
                transaction = em.getTransaction();
                br = new BufferedReader(new FileReader(filePilihan));
                String baris;
                String pemisah = ";";

                while ((baris = br.readLine()) != null) {
                    String[] mahasiswaData = baris.split(pemisah);

                    if (mahasiswaData.length >= 5) {
                        String nim = mahasiswaData[0];
                        String nama = mahasiswaData[1];
                        String alamat = mahasiswaData[2];
                        String asalsma = mahasiswaData[3];
                        String namaorangtua = mahasiswaData[4];

                        if (!nim.isEmpty() && !nama.isEmpty() && !alamat.isEmpty() && !asalsma.isEmpty() && !namaorangtua.isEmpty()) {
                            try {
                                transaction.begin();

                                Mahasiswa mahasiswa = new Mahasiswa();
                                mahasiswa.setNim(nim);
                                mahasiswa.setNama(nama);
                                mahasiswa.setAlamat(alamat);
                                mahasiswa.setAsalsma(asalsma);
                                mahasiswa.setNamaorangtua(namaorangtua);

                                em.persist(mahasiswa);

                                transaction.commit();
                                JOptionPane.showMessageDialog(null, "Input Data Berhasil!");
                            } catch (Exception e) {
                                if (transaction.isActive()) {
                                    transaction.rollback();
                                }
                                JOptionPane.showMessageDialog(null, "Input Data Gagal: " + e.getMessage());
                            }
                        }
                    } else {
                        System.out.println("Baris tidak memiliki cukup kolom: " + baris);
                    }
                }
            } catch (FileNotFoundException ex) {
                Logger.getLogger(MahasiswaDB.class.getName()).log(Level.SEVERE, null, ex);
            } catch (IOException ex) {
                Logger.getLogger(MahasiswaDB.class.getName()).log(Level.SEVERE, null, ex);
            } finally {
                try {
                    if (br != null) {
                        br.close();
                    }
                    if (em != null) {
                        em.close();
                    }
                    if (emf != null) {
                        emf.close();
                    }
                } catch (IOException e) {
                    JOptionPane.showMessageDialog(null, "Gagal menutup file: " + e.getMessage());
                } catch (Exception e) {
                    JOptionPane.showMessageDialog(null, "Terjadi kesalahan saat menutup EntityManager: " + e.getMessage());
                }
            }
        }
        tampil();
    }                       
```

j. Mengisi source code pada program bersih() yang berfungsi untuk memastikan bahwa setelah data dimasukkan atau operasi selesai dilakukan, semua input dari user direset untuk memudahkan pengguna dalam memasukkan data yang baru tanpa harus menghapusnya secara manual 

```
 private void bersih() {
        tfNIM.setText("");
        tfNama.setText("");
        tfAlamat.setText("");
        tfAsalSMA.setText("");
        tfNamaOrangTua.setText("");
        tampil();
    }
```

14.	Hasil eksekusi frame Sign Up terdapat 2 versi :

 1. Versi Salah dimana cek karakter password kurang dari 8 karakter 

    a.	Pada halaman Login klik “Sign up” jika user belum memiliki akun

    ![image](https://github.com/user-attachments/assets/6e9b9807-75da-4ddc-8fb7-1fa69f316e98)

    b.	Setelah itu, user akan diarahkan untuk membuat akun baru dengan mengisi username, email, full name dan password yang akan tersimpan pada table “users” pada database “pbo_uas”. Unchecklist pada 'show password' apabila ingin mengetahui isi password 

    ![image](https://github.com/user-attachments/assets/b61f442a-a57a-434e-879e-5fccbc36146c)

    ![image](https://github.com/user-attachments/assets/465c926d-c1c4-485f-851b-72ac12aed471)

    c.	Karena password kurang dari 8 karakter maka  akan muncul tampilan sebagai berikut

    ![image](https://github.com/user-attachments/assets/48e1a071-8845-41fa-884c-142cc4d69b8b)

  2. Versi Benar dimana user memasukkan 8 atau lebih dari 8 karakter password

     a. mengisi username, email, full name dan password yang akan tersimpan pada table “users” pada database “pbo_uas”. Unchecklist pada 'show password' apabila ingin mengetahui isi password

     ![image](https://github.com/user-attachments/assets/2ef71a43-2906-41eb-939f-b6700413f938)

     ![image](https://github.com/user-attachments/assets/9757606a-cf59-4781-bba7-40fc5cfd368c)

     b. Jika password memiliki 8 atau lebih dari 8 karakter maka berhasil membuat akun dan akan diarahkan ke menu Login

     ![image](https://github.com/user-attachments/assets/0b2893e9-e3fd-42c7-aa9e-e8be63091028)

16. Hasil eksekusi frame Change Password

    a.	Pada halaman Login, pilih Change password

    ![image](https://github.com/user-attachments/assets/6e9b9807-75da-4ddc-8fb7-1fa69f316e98)

    b.	Masukkan NIP/NIM, password baru serta konfirmasi ulang password, kemudian klik ok

    ![image](https://github.com/user-attachments/assets/5ef64e32-1414-4249-b7ce-ead8e9d21a4e)

    ![image](https://github.com/user-attachments/assets/20720a74-d365-4da8-b7bf-029e34fa5ad2)

    c.	Jika berhasil akan muncul pesan sebagai berikut, kemudian kita akan diarahkan untuk kembali ke halaman Login

    ![image](https://github.com/user-attachments/assets/62996c23-bb2b-4c49-831c-73275c88b0ee)

18. Hasil eksekusi frame Login
   
    a.	Masukkan username dan password yang telah kita buat sebelumnya

    ![image](https://github.com/user-attachments/assets/ac1c1fc8-5035-407e-9aaf-e4321e0002d5)

    b.	Klik Login, maka akan muncul tampilan sebagai berikut

    ![image](https://github.com/user-attachments/assets/c6f741a7-ae9b-42bd-a405-7c4657683076)

    c.	Klik OK, maka user akan diarahkan untuk masuk ke dalam frame “DATA MAHASISWA”

     ![image](https://github.com/user-attachments/assets/d554bc58-4694-4f2b-abae-2ef0343fd9ac)

    ![image](https://github.com/user-attachments/assets/73d30887-e4c4-43a4-a199-94b11a823067)

20. Hasil eksekusi insert data

![image](https://github.com/user-attachments/assets/c4ec927f-89ae-43dd-abab-e6d381485ec3)

21. Hasil eksekusi update data

![image](https://github.com/user-attachments/assets/f71648ff-93c9-4672-bea6-a263e58b598f)

22. Hasil eksekusi delete data

![image](https://github.com/user-attachments/assets/5acaab10-380b-41bd-869b-4e47c4000a52)

![image](https://github.com/user-attachments/assets/07070e6f-e05b-43c1-a579-92bfb53507ab)

23. Hasil eksekusi print data 

![image](https://github.com/user-attachments/assets/1438076e-4399-450b-822c-4e45a7ec5486)

24. Hasil eksekusi upload data 

a. Pilih file yang akan diupload 

![image](https://github.com/user-attachments/assets/be40b3e9-9e3a-4e07-bec5-de9a4e2f4799)

b. Jika berhasil akan muncul pesan seperti ini 

![image](https://github.com/user-attachments/assets/7efe4efd-e15f-459f-84cd-4c061d9215b3)

c. Data berhasil dimasukkan 

![image](https://github.com/user-attachments/assets/ca0d119e-b66d-47e5-866a-814758d85b2d)

22. Hasil eksekusi btnLogout, user akan diarahkan untuk kembali ke Frame Login

    ![image](https://github.com/user-attachments/assets/4f80705f-3020-41db-afe3-8452f9fbf088)


 

 
