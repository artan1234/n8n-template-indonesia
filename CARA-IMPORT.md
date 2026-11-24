# Cara Impor Workflow ke n8n

Panduan ini buat semua workflow di paket ini. Sekali paham, impor workflow berikutnya tinggal ulang langkah yang sama.

## Langkah-langkah

### 1. Buka n8n kamu
Buka alamat n8n kamu (mis. `http://localhost:5678` kalau self-host di laptop, atau alamat Cloud kamu). Login seperti biasa.

### 2. Buat workflow baru dari file
1. Di halaman Workflows, klik tombol **⋯ (titik tiga)** di kanan atas, lalu pilih **Import from File**.
   - Di sebagian versi, caranya: buka workflow kosong, klik **⋯** di kanan atas editor, lalu **Import from File**.
2. Pilih file `.json` workflow yang mau diimpor dari folder `workflows/` paket ini.
3. Workflow langsung muncul di editor, lengkap dengan semua node dan panahnya.

### 3. Hubungkan kredensial
Node yang butuh login (Telegram, OpenAI, X, Google Sheets) akan ditandai peringatan karena kredensialnya masih kosong. Untuk tiap node itu:

1. Klik node-nya.
2. Di bagian **Credential**, klik **Create New** (atau pilih kredensial yang sudah ada).
3. Isi datanya sesuai panduan di file `<nama-workflow>.README.md` — di sana dijelaskan cara dapat token/kunci dari tiap layanan.
4. Klik **Save**.

Nama kredensial di dalam file template sengaja ditulis jelas, contoh: `Telegram Bot — ISI TOKEN`. Itu cuma penanda, bukan kredensial beneran.

### 4. Sesuaikan isinya
Sebelum diaktifkan, cek dan ubah yang perlu diubah:

- **Chat ID Telegram** — ganti `ISI_CHAT_ID_TELEGRAM_ANDA` dengan chat ID kamu (caranya ada di panduan tiap workflow).
- **Daftar URL / feed RSS / teks postingan** — ganti dengan punyamu sendiri di node Set / RSS / Code.
- **Jadwal** — node Schedule Trigger sudah disetel (mis. jam 07:00 WIB). Klik node-nya kalau mau ubah jam.

### 5. Tes dulu, baru aktifkan
1. Klik **Execute Workflow** (tombol ▶ di bawah editor) buat jalanin sekali secara manual. Perhatikan: ada node yang error atau tidak?
2. Kalau ada yang merah, baca pesan error-nya — biasanya karena kredensial belum diisi atau chat ID masih placeholder.
3. Kalau sudah hijau semua, aktifkan workflow dengan tombol **Active** (toggle di kanan atas). Workflow terjadwal baru akan jalan otomatis kalau sudah aktif.

## Kalau impor gagal

- **"Workflow could not be imported"** — pastikan file JSON-nya tidak kamu edit manual dan tidak rusak. Coba unduh ulang dari paket aslinya.
- **Node hilang / "unknown node type"** — n8n kamu mungkin versinya lebih lama dari 2.x. Update n8n dulu, lalu impor ulang.
- **Node LangChain tidak muncul** — node AI (Agent, OpenAI Chat Model, Memory) butuh n8n versi yang mendukung LangChain. Di n8n 2.x sudah bawaan.

## Catatan

- Workflow yang diimpor dalam keadaan **tidak aktif** (Active: off). Sengaja begitu, supaya kamu bisa cek dan isi kredensial dulu sebelum dia jalan sendiri.
- Impor tidak menimpa workflow lain. Kalau impor file yang sama dua kali, n8n akan membuat salinan baru.
