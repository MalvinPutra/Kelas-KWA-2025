## Write-up: Login Jim (OWASP Juice Shop)

### Langkah Pengerjaan

1. **Akses halaman login** Juice Shop → `/#/login`.
2. Di kolom **Email**, masukkan payload:

   ```
   jim@juice-sh.op'--
   ```

   Di kolom **Password**, isi bebas (contoh: `12345`).
3. Klik tombol **Login**.
4. Karena query SQL dipotong dengan `'--`, password tidak lagi divalidasi.

<img width="667" height="685" alt="Screenshot 2025-09-11 110906" src="https://github.com/user-attachments/assets/98f68a47-5c78-4797-ab21-fc78a26fcfd6" />



### Hasil

* Berhasil login sebagai **Jim** tanpa mengetahui password aslinya.
* Challenge **“Login Jim”** ditandai *Solved*. 
