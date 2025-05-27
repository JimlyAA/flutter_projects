# Praktikum Flutter Navigasi

## Tujuan Praktikum

Mempelajari dan mengimplementasikan empat jenis navigasi dalam Flutter, yaitu Named Routes, Navigator 2.0, Nested Navigation, dan Deep Linking, untuk membangun aplikasi mobile dengan alur navigasi yang baik dan fleksibel.

---

## Jenis Navigasi dalam Flutter

### 1. Named Routes
Navigasi berdasarkan nama rute yang sudah didefinisikan di awal. Cocok untuk aplikasi kecil hingga menengah.

- **Contoh pemakaian:**
  ```dart
  Navigator.pushNamed(context, '/detail');
