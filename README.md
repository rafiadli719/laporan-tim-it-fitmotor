# laporan-tim-it-fitmotor

Skill Claude: rapikan catatan mentah tim IT FIT MOTOR menjadi laporan harian ringkas (format WhatsApp) untuk manajemen.

## Pasang lewat Plugins (cara termudah, pakai link GitHub)

1. Buka claude.ai, **Settings → Customize → Plugins → Add → Add marketplace**.
2. Isi URL: `https://github.com/rafiadli719/laporan-tim-it-fitmotor`
3. Klik **Sync**, lalu pasang plugin `laporan-tim-it-fitmotor` dari marketplace `fitmotor-skills`.
4. Di chat baru, tempel catatan kerja hari ini dan minta: "rapikan jadi laporan harian IT".

Di Claude Code: `/plugin marketplace add rafiadli719/laporan-tim-it-fitmotor`, lalu `/plugin install laporan-tim-it-fitmotor@fitmotor-skills`.

## Alternatif: unggah ZIP (Claude chat)

1. Unduh [laporan-tim-it-fitmotor.zip](https://github.com/rafiadli719/laporan-tim-it-fitmotor/raw/main/laporan-tim-it-fitmotor.zip).
2. **Settings → Capabilities** (atau **Customize → Skills**) → **Upload skill** → pilih ZIP, lalu nyalakan skill.

Fitur Skills dan Plugins bisa bergantung pada paket akun; untuk Team/Enterprise, admin mungkin perlu mengaktifkannya.

## Struktur repo

- `.claude-plugin/marketplace.json` dan `.claude-plugin/plugin.json`: agar repo bisa ditambahkan sebagai marketplace.
- `skills/laporan-tim-it-fitmotor/SKILL.md`: isi skill (sumber utama).
- `laporan-tim-it-fitmotor.zip`: harus dibuat ulang setiap `SKILL.md` berubah (isinya folder `laporan-tim-it-fitmotor/` berisi `SKILL.md`).
