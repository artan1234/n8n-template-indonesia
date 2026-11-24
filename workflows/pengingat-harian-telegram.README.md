# Pengingat Harian Telegram

Kirim pengingat ke Telegram 4x sehari — jam 08:00, 12:00, 16:00, dan 20:00 WIB — dengan teks yang beda tiap jam. Tidak pakai AI, jadi tidak ada biaya tambahan apa pun.

> **Sampel gratis** — workflow ini boleh dibagikan bebas.

## Cara kerja

1. **Jadwal Pengingat** — jalan tiap hari jam 08:00, 12:00, 16:00, dan 20:00 WIB.
2. **Pilih Pengingat** — pilih teks pengingat sesuai jam saat itu.
3. **Kirim Pengingat** — kirim ke Telegram kamu.

Contoh bawaan: pengingat check-in aplikasi harian (MEC, Zoi, dan sejenisnya). Ganti sesukamu.

## Yang perlu disiapkan

### 1. Bot Telegram
1. Chat @BotFather di Telegram, kirim `/newbot`, ikuti langkahnya sampai dapat token.
2. Di n8n, buka node **Kirim Pengingat** → Credential → Create New → isi token bot kamu.
3. Chat ID: kirim satu pesan ke bot kamu, lalu buka `https://api.telegram.org/bot<TOKEN>/getUpdates` dan cari angka `chat.id`. Isi angka itu ke parameter **Chat ID** (ganti `ISI_CHAT_ID_TELEGRAM_ANDA`).

### 2. Ganti teks pengingat
Buka node **Pilih Pengingat**, ubah isi daftarnya. Kuncinya adalah jam (8, 12, 16, 20). Contoh: pengingat minum obat, jadwal belajar, atau to-do harian.

### 3. Ubah jam
Buka node **Jadwal Pengingat**, ubah cron expression-nya. Contoh: `0 7,13,19 * * *` = jam 07:00, 13:00, dan 19:00. Ingat: kalau jam di jadwal berubah, kunci di node **Pilih Pengingat** harus disesuaikan juga.

## Versi node yang dipakai

- Schedule Trigger `n8n-nodes-base.scheduleTrigger` v1.2
- Set `n8n-nodes-base.set` v3.4
- Telegram `n8n-nodes-base.telegram` v1.2
