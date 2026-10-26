# laporan-tim-it-fitmotor

Skill Claude: rapikan catatan mentah tim IT FIT MOTOR menjadi laporan harian ringkas (format WhatsApp) untuk manajemen.

## Pasang di Claude chat (claude.ai atau aplikasi Claude)

1. Unduh file ZIP: [laporan-tim-it-fitmotor.zip](https://github.com/rafiadli719/laporan-tim-it-fitmotor/raw/main/laporan-tim-it-fitmotor.zip)
2. Buka claude.ai, klik nama akun, lalu **Settings → Capabilities** (atau **Customize → Skills**).
3. Pastikan **Code execution / Skills** aktif, lalu klik **Upload skill** dan pilih file ZIP tadi.
4. Nyalakan skill `laporan-tim-it-fitmotor`.
5. Di chat baru, tempel catatan kerja hari ini dan minta: "rapikan jadi laporan harian IT".

Fitur Skills perlu paket berbayar (Pro, Max, Team, atau Enterprise). Untuk Team/Enterprise, admin mungkin perlu mengaktifkannya dulu.

## Pasang di Claude Code (opsional, via terminal)

```bash
git clone https://github.com/rafiadli719/laporan-tim-it-fitmotor.git ~/.claude/skills/laporan-tim-it-fitmotor
```

Restart Claude Code, lalu jalankan `/laporan-tim-it-fitmotor <catatan>`.

## Catatan pemeliharaan

`laporan-tim-it-fitmotor.zip` harus dibuat ulang setiap `SKILL.md` berubah (isinya folder `laporan-tim-it-fitmotor/` berisi `SKILL.md`).
