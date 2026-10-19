# Bank Sampah Sukamaju Sejahtera

Sistem operasional bank sampah + koperasi simpan pinjam + penjualan produk terintegrasi.

## Tech Stack
- **Framework:** Next.js 16 (App Router) + TypeScript
- **Database:** MySQL (via Prisma ORM)
- **UI:** Tailwind CSS 4 + shadcn/ui + Recharts
- **Auth:** JWT-based (mock auth untuk demo)
- **Payment:** Midtrans Snap (opsional)

## Cara Menjalankan di VS Code + Laragon

### 1. Persiapan
- Install [Node.js LTS](https://nodejs.org/)
- Install [Laragon](https://laragon.org/) (sudah termasuk MySQL)
- Install [VS Code](https://code.visualstudio.com/)
- Jalankan Laragon, pastikan MySQL running

### 2. Import Database
1. Buka **phpMyAdmin** di browser: `http://localhost/phpmyadmin`
2. Klik **Import** di menu atas
3. Pilih file `database/database.sql`
4. Klik **Go** (Import)
5. Database `bank_sampah` akan otomatis dibuat dengan semua tabel + sample data

### 3. Setup Project
```bash
# Clone atau extract project ke folder
cd bank-sampah

# Copy environment file
cp .env.example .env
# Atau di Windows: copy .env.example .env

# Edit .env jika perlu (default sudah sesuai dengan Laragon)
# DATABASE_URL="mysql://root:@localhost:3306/bank_sampah"

# Install dependencies
npm install

# Generate Prisma Client
npx prisma generate

# Jalankan development server
npm run dev
```

### 4. Akses Aplikasi
Buka browser: `http://localhost:3000`

### Login Demo
| Role | Email | Password |
|------|-------|----------|
| Admin | admin@gmail.com | password |
| Owner | owner@gmail.com | password |
| Nasabah | mirwan.10522114@mahasiswa.unikom.ac.id | password |

## Fitur Lengkap

### Public Pages
- Landing page dengan stats, galeri kegiatan, edukasi
- Merchandise catalog (online shop)
- Edukasi & konten artikel
- Dokumentasi kegiatan (galeri foto)
- Lacak pesanan
- Login & Register

### Admin Panel (11 Modul)
1. **Dashboard** — Executive dashboard (Bank Sampah, Koperasi, Penjualan)
2. **Teller Wizard** — Layanan satu pintu (nabung + sedekah + koperasi)
3. **Operasional** — Nabung & sedekah sampah + QC
4. **Finansial** — Penarikan saldo & buku kas
5. **Koperasi** — Simpanan, pinjaman, angsuran, kas
6. **Inventaris** — Stok, pengolahan, penjualan mitra
7. **Penjualan Produk** — Toko online & kasir offline (POS)
8. **Laporan** — Laba rugi (Bank Sampah, Koperasi, Penjualan)
9. **Edukasi** — CRUD artikel edukasi
10. **Dokumentasi Kegiatan** — CRUD kegiatan + upload foto
11. **Master Data** — Nasabah, barang, koperasi, manajemen akun

### User Dashboard
- Profile & saldo
- Transaksi nabung & sedekah
- Simpanan koperasi (pokok, wajib, sukarela)
- Pinjaman + jadwal bayar
- Notification bell (transaksi + reminder jatuh tempo)
- Histori poin

### Fitur Tambahan
- Cetak struk semua transaksi (9 jenis)
- Upload gambar produk
- Upload foto dokumentasi kegiatan
- Upload gambar artikel edukasi
- Filter waktu + custom date range di semua tabel
- Responsive design (mobile, tablet, desktop)
- Midtrans payment integration (opsional)

## Struktur Folder
```
bank-sampah/
├── src/
│   ├── app/                    # Next.js App Router
│   │   ├── api/                # API routes (87 endpoints)
│   │   ├── globals.css         # Global styles
│   │   ├── layout.tsx          # Root layout
│   │   └── page.tsx            # Main page (router)
│   ├── components/
│   │   ├── modules/            # Feature components
│   │   └── ui/                 # shadcn/ui components
│   ├── lib/                    # Utilities (db, api, auth, format)
│   └── hooks/                  # Custom hooks
├── prisma/
│   └── schema.prisma           # Prisma schema (MySQL)
├── public/
│   ├── uploads/                # Uploaded images
│   │   ├── products/           # Product images
│   │   ├── kegiatan/           # Activity photos
│   │   └── edukasi/            # Article images
│   └── logo-bank-sampah.png    # Logo
├── database/
│   └── database.sql            # MySQL database dump
├── .env.example                # Environment template
├── package.json
├── tsconfig.json
├── next.config.ts
└── README.md                   # This file
```

## Troubleshooting

### Error: "Can't connect to MySQL"
- Pastikan Laragon running
- Cek port 3306 tidak digunakan aplikasi lain
- Cek `.env` → `DATABASE_URL="mysql://root:@localhost:3306/bank_sampah"`

### Error: "Prisma Client not generated"
```bash
npx prisma generate
```

### Error: "Module not found"
```bash
# Delete node_modules dan install ulang
rm -rf node_modules
npm install
```

### Reset Database
```bash
# Hapus database di phpMyAdmin, lalu import ulang database.sql
# Atau jalankan:
npx prisma db push
```

## License
Private project — Bank Sampah Sukamaju Sejahtera © 2026
