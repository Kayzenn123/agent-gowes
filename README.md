# GENJOT — 16 Rute Gowes Nusantara

**Live:** https://kayzenn123.github.io/agent-gowes/ · 30 Days of Code, Hari 3 (2026-10-11)

Satu jalan horizontal berisi 16 rute sepeda Indonesia — dari CFD Jakarta sampai sunrise Bromo. Kayuh (scroll) ke kanan, pilih rute, lihat profil elevasi, adu dua rute, simpan favorit, bagikan ke grup gowes.

Dibangun dari template web-starter (AstroWind) — dipakai sebagai pipeline build Astro + SEO + font self-hosting, dengan halaman dan seluruh logika custom.

## Fitur
- Trek horizontal penuh (pinned scroll): 5 panel — hero, daftar rute, detail, adu rute, tas gowes
- 16 kartu rute ala rambu jalan + filter level (santai/sedang/brutal) & wilayah
- **Hover kartu mengubah tema waktu seluruh halaman** (pagi/siang/senja/malam)
- Detail rute: profil elevasi SVG generatif (draw-on), statistik count-up, reveal lingkaran
- Adu 2 rute head-to-head (jarak, elevasi, level) dengan penanda pemenang
- Favorit tersimpan di localStorage (versioned, validasi skema)
- Deep-link `?rute=<id>`, salin ringkasan (clipboard + fallback), unduh JSON/CSV
- Easter egg: tekan `G` 3x → rute rahasia "Tanjakan Cinomati"
- Aksesibilitas: skip link, aria-live, tombol jeda marquee, toggle gerak, keyboard ←/→/Home/End + tombol prev/next, fallback vertikal saat reduced-motion, mode ringan otomatis (≤4 core / Save-Data / FPS<40)

## Tech
Astro 7 + GSAP + ScrollTrigger (dynamic import, hanya saat motion nyala) + 3 font OFL self-host (Metamorphous, Scada, Playwrite ES Deco via Fontsource). 24 ikon SVG monoline digambar tangan. Tanpa gambar raster, tanpa tracker.

## Skor
- Lighthouse (lokal, VM overload load ~10): mobile 51–62 / 91 / 100 / 100, desktop 44 / 91 / 100 / 100 (Performance/Accessibility/Best Practices/SEO). Performance = plafon lingkungan (halaman pin-horizontal minimal pun mentok 39 fps di sini); a11y/BP/SEO ≥ 90.
- qa.js: 0 overflow, 0 console error, tap target ≥44px, 1 h1, lang=id — di 360/390/768/1280.
- Fungsional: 18/18 tes Playwright lolos (filter, favorit + persist, deep-link, compare + error state, easter egg, salin, keyboard nav).
- Gerbang kritik: karakter 9, keunikan 9, kerapian 8. Lihat `CRITIQUE.md`.

## Data
Semua angka rute (jarak/elevasi/waktu) = **estimasi komunitas, bukan data resmi** — dilabeli di UI.

## Jalanin lokal
```bash
npm i && npm run dev   # http://localhost:4321
npm run build          # -> dist/
```
