# Paket Template n8n Indonesia — v1

Kumpulan 6 workflow n8n siap impor, dibuat untuk pemakaian sehari-hari: memantau peluang, membalas chat otomatis, posting terjadwal, sampai nyimpan ide. Semua panduan ditulis Bahasa Indonesia, tinggal ikuti langkahnya.

## Isi paket

| # | Workflow | Buat apa | Butuh kredensial |
|---|----------|----------|------------------|
| 1 | `radar-bounty-testnet` | Memantau perubahan halaman web (mis. papan bounty & status testnet) tiap pagi, kirim alert ke Telegram kalau ada yang berubah | Bot Telegram |
| 2 | `bot-telegram-ai` | Bot Telegram yang jawab pakai AI, ingat percakapan sebelumnya | Bot Telegram, OpenAI |
| 3 | `auto-post-x-terjadwal` | Posting ke X otomatis 2x sehari, teksnya berputar sendiri | X (Twitter) OAuth2 |
| 4 | `ringkasan-berita-ai-harian` | Baca RSS tiap pagi, diringkas AI, dikirim ke Telegram | OpenAI, Bot Telegram |
| 5 | `pengingat-harian-telegram` | Kirim pengingat ke Telegram 4x sehari (mis. check-in aplikasi) | Bot Telegram |
| 6 | `simpan-ide-ke-sheets` | Terima ide lewat webhook, simpan otomatis ke Google Sheets | Google Sheets OAuth2 |

File workflow ada di folder `workflows/`. Tiap workflow punya panduan sendiri (`<nama>.README.md`) — baca itu dulu sebelum dipakai.

## Cara impor

Lihat **[CARA-IMPORT.md](CARA-IMPORT.md)** — langkahnya cuma beberapa menit per workflow.

## Yang kamu butuhkan

- **n8n** — bisa yang self-hosted Community Edition (gratis, tanpa batas eksekusi) atau trial n8n Cloud 14 hari. Paket ini dibuat dan dites strukturnya untuk **n8n 2.x**.
- **Akun-akun sesuai workflow yang dipakai** — bot Telegram (gratis, dari @BotFather), kunci API OpenAI (berbayar per pemakaian), akses API X, dan akun Google. Tidak semua workflow butuh semuanya; cek tabel di atas.
- **Tidak ada token atau kunci apa pun di dalam paket ini.** Semua kredensial berupa placeholder (contoh: `ISI_TOKEN_BOT_ANDA`) yang kamu isi sendiri di n8n setelah impor.

## Sampel gratis

2 workflow di paket ini adalah **sampel gratis** dan boleh dibagikan bebas:

- `radar-bounty-testnet`
- `pengingat-harian-telegram`

4 workflow lainnya hanya ada di paket lengkap (berbayar). Lisensi lengkapnya ada di file [LICENSE](LICENSE).

## Catatan jujur

- Workflow yang mengambil halaman web (radar) memakai HTTP fetch biasa. Halaman yang isinya dimuat penuh oleh JavaScript bisa jadi hampir tidak terbaca — ini keterbatasan teknis, bukan bug template.
- Bagian tersulit di paket ini adalah akses API X untuk auto-posting. X punya aturan dan antrean persetujuan sendiri; template-nya sudah benar, tapi aksesnya harus kamu urus di X Developer Portal.
- Workflow AI memakai model OpenAI `gpt-4o-mini` sebagai bawaan. Modelnya bisa diganti di node Model — caranya ada di panduan tiap workflow.

---

## English summary (short)

**Indonesian n8n Template Pack v1** — 6 ready-to-import n8n workflows with Indonesian guides: a website-change radar with Telegram alerts, a Telegram AI chatbot (LangChain agent + memory), scheduled X posting, a daily AI news digest from RSS, daily Telegram reminders, and a webhook-to-Google-Sheets idea catcher. Requires n8n 2.x (self-hosted Community Edition or Cloud trial). No credentials are included — all are placeholders you fill in after import. Two workflows (radar-bounty-testnet, pengingat-harian-telegram) are free samples; the full pack is a paid, single-user licensed product (see LICENSE).
