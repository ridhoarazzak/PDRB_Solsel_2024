# PDRB Spasial Solok Selatan 2024

Estimasi disagregasi spasial PDRB Kabupaten Solok Selatan ke level 39 nagari, menggunakan metode **dasymetric mapping** berbasis proksi citra satelit — dikerjakan sepenuhnya dengan Google Earth Engine (GEE) dan Python/Colab.

## ⚠️ Penting: ini estimasi, bukan data resmi

BPS hanya merilis PDRB di level **kabupaten** (lihat [Kabupaten Solok Selatan Dalam Angka 2025](https://solokselatankab.bps.go.id/)). Sebaran per-nagari dalam repo ini adalah **hasil model/estimasi**, dipecah dari total resmi tersebut menggunakan tiga proksi spasial:

- Citra cahaya malam hari (VIIRS Nighttime Lights)
- Kepadatan penduduk (HRSL)
- Tutupan lahan (MapBiomas Indonesia)

Total dan struktur sektoral dikunci ke angka resmi BPS (validasi pycnophylactic, drift < 0,15%) — tapi **sebaran per nagarinya tetap perkiraan**, bukan hasil sensus atau survei langsung.

## Metodologi

Kerangka dasar formula bobot alokasi per sektor diadaptasi dari kerangka *dasymetric mapping* yang dibagikan oleh **Firman Afrianto (PT. Sagamartha Ultima)** — lihat metodologi aslinya (skill share, 2025).

Dari kerangka dasar tersebut, notebook ini menambahkan beberapa ekstensi khusus untuk konteks Solok Selatan:

- Migrasi sumber tutupan lahan ke MapBiomas Indonesia
- Revisi formula Sektor Pertambangan & Penggalian: menggabungkan layer *Placer Potential* (indikasi geologi) dengan bonus deteksi perubahan SAR (aktivitas berjalan), tervalidasi terhadap titik PETI yang sudah dikonfirmasi
- Perbaikan kalibrasi populasi: koreksi formula anomali NTL-populasi yang sebelumnya over-koreksi untuk nagari pusat pasar/komersial (populasi kecil + NTL tinggi adalah pola wajar kawasan non-residensial, bukan indikasi data sensus salah)
- Filter reliabilitas untuk GDP per kapita (nagari dengan populasi < 3.000 jiwa atau area > 100 km² ditandai kurang reliable)

## Isi Repo

| File | Deskripsi |
|---|---|
| `PDRB_SolSel_2024_v18_fixed.ipynb` | Notebook utama (Python/GEE), dari alokasi sektor hingga dashboard visualisasi |

## Disclaimer

Model ini masih berstatus **draft**, dikembangkan mandiri tanpa afiliasi institusi. Kritik dan masukan metodologis sangat terbuka — silakan buka issue atau hubungi langsung.

## Terkait

Bagian dari [South Solok Spatial Data Initiative (SSDI)](https://ssdi.vercel.app) — inisiatif geospasial 17 modul untuk 39 nagari di Kabupaten Solok Selatan.
