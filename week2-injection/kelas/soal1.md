# Juice-Shop Write-up: Login Admin

## Overview

Title: Login Admin

Category: SQL Injection

Decribe: Log in with the administrator's user account.

<img width="478" height="177" alt="image" src="https://github.com/user-attachments/assets/c09ba3fe-9045-4720-ad24-7ca28c9b65e8" />

### Alat yang Digunakan

- **Browser:** Berfungsi sebagai media untuk mengakses dan melakukan login ke aplikasi web.
- **Burp Suite:** Dipakai untuk menangkap serta memodifikasi permintaan HTTP dalam rangka melakukan injeksi SQL.

### Resource

## Payload : [Klik](https://github.com/payloadbox/sql-injection-payload-list)

### Metode dan Solusi

#### Langkah-Langkah yang Diambil untuk Menyelesaikan Tantangan

1. **Masuk Halaman Login**
   
   <img width="912" height="769" alt="image" src="https://github.com/user-attachments/assets/7a54fc18-bb37-4e84-a905-0eef49242811" />

2. **Uji SQL Injection pada kolom Email**
   
   Untuk Payload SQL Injection bisa diliat pada link yang tertera sebelumnya

```bash
'--
```

Untuk kolom **Password**, isi dengan sembarang nilai (contoh: WASD).
<img width="641" height="647" alt="image" src="https://github.com/user-attachments/assets/4d74572c-eff8-412d-82a8-96377023f9cf" />

3. **Hasil Login**
   
   Setelah menekan tombol Log in, sistem berhasil mengautentikasi tanpa memverifikasi password asli administrator. Kita berhasil login sebagai admin.
   
<img width="522" height="380" alt="image" src="https://github.com/user-attachments/assets/081a40cc-b78d-4dad-aef5-5721e63f5763" />


---


### Penjelasan Solusi

Serangan **SQL Injection** ini berhasil karena adanya **kelemahan dalam validasi masukan** dan **kurangnya penggunaan _prepared statement_** saat menangani kueri SQL. Kode yang disuntikkan berhasil mengubah struktur logis dari perintah SQL, sehingga melewati proses otentikasi dan masuk sebagai administrator tanpa memerlukan kata sandi yang benar.

