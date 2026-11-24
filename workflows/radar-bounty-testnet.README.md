# Radar Bounty & Testnet

Memantau perubahan halaman web tiap pagi, kirim alert ke Telegram kalau ada yang berubah. Dibuat untuk memantau papan bounty dan status testnet, tapi URL-nya bisa diganti apa saja.

> **Sampel gratis** — workflow ini boleh dibagikan bebas.

## Cara kerja

1. **Jadwal Pagi** — jalan tiap hari jam 07:00 WIB.
2. **Daftar URL** — daftar halaman yang dipantau (bawaan: `make.fun/bounties` dan `flop.finance/testnet`). Ganti di node ini.
3. **Pecah URL** — tiap URL diproses satu-satu.
4. **Ambil Halaman** — ambil isi halaman lewat HTTP GET biasa.
5. **Hitung Hash & Bandingkan** — isi halaman di-hash (SHA-256), lalu dibandingkan dengan hash kunjungan sebelumnya yang disimpan di workflow static data.
6. **Ada Perubahan?** — kalau hash beda, lanjut ke pengiriman alert.
7. **Kirim Alert Telegram** — kirim pesan berisi URL, hash baru, dan panjang konten.

Catatan: saat pertama kali dijalankan, workflow cuma mencatat hash awal dan **tidak mengirim alert**. Alert baru muncul kalau ada perubahan di kunjungan berikutnya.

## Yang perlu disiapkan

### 1. Bot Telegram
1. Chat @BotFather di Telegram, kirim `/newbot`, ikuti langkahnya sampai dapat token.
2. Di n8n, buka node **Kirim Alert Telegram** → Credential → Create New → isi token bot kamu.
3. Chat ID: kirim satu pesan ke bot kamu, lalu buka `https://api.telegram.org/bot<TOKEN>/getUpdates` dan cari angka `chat.id`. Isi angka itu ke parameter **Chat ID** di node Telegram (ganti `ISI_CHAT_ID_TELEGRAM_ANDA`).

### 2. Ganti URL yang dipantau
Buka node **Daftar URL**, ubah isi array `urls` dengan halaman yang mau kamu pantau.

## Catatan jujur

- **Halaman berat JavaScript hampir tidak terbaca.** Workflow ini memakai HTTP fetch biasa, jadi halaman yang isinya dimuat penuh oleh JavaScript (mis. dashboard interaktif) kemungkinan besar cuma mengembalikan kerangka kosong. Itu keterbatasan teknis, bukan bug template. Untuk halaman seperti itu, pantau lewat RSS atau API resmi kalau ada.
- Hash membandingkan **seluruh isi halaman**, termasuk hal kecil seperti angka pengunjung atau tanggal. Kalau halaman sering berubah sendiri, alert akan sering masuk. Solusinya: ubah node Code supaya cuma membandingkan bagian tertentu.
- Jadwal memakai zona waktu Asia/Jakarta. Kalau server n8n kamu di zona lain, cek lagi jam jalan di node Schedule Trigger.

## Versi node yang dipakai

- Schedule Trigger `n8n-nodes-base.scheduleTrigger` v1.2
- Set `n8n-nodes-base.set` v3.4
- Split Out `n8n-nodes-base.splitOut` v1
- HTTP Request `n8n-nodes-base.httpRequest` v4.2
- Code `n8n-nodes-base.code` v2
- IF `n8n-nodes-base.if` v2.2
- Telegram `n8n-nodes-base.telegram` v1.2
