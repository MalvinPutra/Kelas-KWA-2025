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
![Uploading Screenshot 2025-09-11 110906.png…]()


### Hasil

* Berhasil login sebagai **Jim** tanpa mengetahui password aslinya.
* Challenge **“Login Jim”** ditandai *Solved*. 
