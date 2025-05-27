# Praktikum Flutter Navigasi
Jimly Asidiq Anwar - 4522210018

## Tujuan Praktikum
Tujuan dari praktikum ini adalah untuk memahami dan mengimplementasikan berbagai jenis navigasi yang tersedia dalam pengembangan aplikasi Flutter.

## 1. Navigation
Navigasi di Flutter dipakai untuk pindah dari satu halaman ke halaman lain, misalnya dari Home ke Detail atau About. Di kode ini, cara pindah halamannya ada dua: yang pertama pakai `MaterialPageRoute` (langsung), dan yang kedua pakai nama rute dengan `Navigator.pushNamed()`. Beberapa widget yang dipakai buat navigasi ini adalah `MaterialApp` untuk daftar rute, `ElevatedButton` buat tombolnya, dan `Navigator` buat proses pindah halamannya.

### Widget dan Fungsi yang Digunakan
| Widget/Fungsi                                | Fungsi                                                              |
| -------------------------------------------- | ------------------------------------------------------------------- |
| `MaterialApp`                                | Menyediakan struktur utama aplikasi dan tempat mendefinisikan route |
| `Navigator.push`                             | Navigasi manual ke halaman lain menggunakan `MaterialPageRoute`     |
| `Navigator.pushNamed`                        | Navigasi otomatis berdasarkan nama route yang sudah didefinisikan   |
| `Navigator.pop`                              | Kembali ke layar sebelumnya (back)                                  |
| `Scaffold`                                   | Struktur dasar setiap layar: ada `appBar`, `body`, dll              |
| `AppBar`                                     | Menampilkan bar atas dengan judul                                   |
| `ElevatedButton`                             | Tombol untuk aksi navigasi                                          |
| `ModalRoute.of(context)?.settings.arguments` | Mengambil argumen dari route saat navigasi                          |


### Screenshots
![Screenshot_20250527_194655](https://github.com/user-attachments/assets/17cb4355-9359-46a9-b166-7d0416e98ad2)
![Screenshot_20250527_194721](https://github.com/user-attachments/assets/705dadbf-49f0-40bc-8464-058abeb3f1e6)

## 2. Navigation 2.0
Aplikasi ini pakai sistem navigasi yang otomatis pindah halaman berdasarkan kondisi, bukan pakai push atau pop manual.

Waktu kita pilih item di halaman utama (Home), aplikasi langsung menampilkan halaman detail. Kalau tombol Back ditekan, balik lagi ke Home.

### Widget dan Fungsi yang Digunakan
| Widget             | Fungsi                                                                 |
| ------------------ | ---------------------------------------------------------------------- |
| `Navigator`        | Mengelola tumpukan halaman (`pages`) dan menangani navigasi.           |
| `MaterialPage`     | Mewakili satu halaman dalam navigator. Digunakan dalam daftar `pages`. |
| `Scaffold`         | Struktur dasar tampilan tiap layar (ada `AppBar`, `body`, dll).        |
| `ListView.builder` | Menampilkan daftar item secara dinamis di `HomeScreen`.                |
| `ListTile`         | Menampilkan satu item dalam daftar dengan `onTap`.                     |
| `ElevatedButton`   | Tombol aksi untuk kembali ke `HomeScreen`.                             |

### Screenshots
![Screenshot_20250527_195314](https://github.com/user-attachments/assets/7dbafdc5-6367-42a3-b347-c0352f87d225)
![Screenshot_20250527_195325](https://github.com/user-attachments/assets/1cc94c39-3f6c-4471-8467-9ce455ec6a4c)

## 3. Nested Navigation
Aplikasi ini menggunakan nested navigation atau navigator bersarang, yaitu teknik di mana satu Navigator ditanamkan di dalam halaman lain untuk mengelola alur layar secara lokal (terisolasi dari navigator utama).

### Widget dan Fungsi yang Digunakan
| Widget / Kelas              | Fungsi                                                                |
| --------------------------- | --------------------------------------------------------------------- |
| `Navigator`                 | Membuat navigator bersarang (di `SetupFlowScreen`)                    |
| `GlobalKey<NavigatorState>` | Mengontrol navigator nested (`_navigatorKey`)                         |
| `MaterialPageRoute`         | Menentukan rute berpindah halaman utama (`HomeScreen` -> `SetupFlow`) |
| `Navigator.pushNamed`       | Navigasi antar halaman di dalam navigator nested                      |
| `Navigator.pop`             | Kembali ke layar sebelumnya (baik nested maupun utama)                |
| `onGenerateRoute`           | Membangun halaman berdasarkan `settings.name` di navigator nested     |

### Screenshots
![Screenshot_20250527_195737](https://github.com/user-attachments/assets/cef89ee5-f678-462d-ba69-290f0e516870)
![Screenshot_20250527_195800](https://github.com/user-attachments/assets/45ec18bc-1d14-4ea1-82db-0802cc22fa2d)

## 4. Deep Link Navigation
Navigasi ini menggunakan pendekatan Router API (Declarative Navigation) dengan kombinasi Router, RouterDelegate, dan RouteInformationParser. Ini cocok untuk mendukung deep linking (misalnya akses langsung ke /detail/1 atau /settings dari URL).

### Widget dan Fungsi yang Digunakan
| Widget/Kelas                        | Fungsi                                                                                        |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `Router` (via `MaterialApp.router`) | Komponen utama untuk navigasi deklaratif.                                                     |
| `AppRouterDelegate`                 | Mengatur logika navigasi dan tampilan berdasarkan state (`_selectedItemId`, `_showSettings`). |
| `AppRouteInformationParser`         | Menerjemahkan URL menjadi state aplikasi (`RoutePath`) dan sebaliknya.                        |
| `RoutePath`                         | Model yang merepresentasikan path seperti home, detail, dan settings.                         |
| `Navigator`                         | Menampilkan stack halaman (`MaterialPage`) berdasarkan state.                                 |
| `MaterialPage`                      | Membungkus setiap halaman agar bisa dikelola oleh Navigator.                                  |
| `onPopPage`                         | Menangani tombol back.                                                                        |
| `ListTile` + `onTap`                | Untuk navigasi ke halaman detail item.                                                        |
| `IconButton`                        | Untuk membuka halaman Settings dari Home.                                                     |

### Screenshots
![Screenshot_20250527_200216](https://github.com/user-attachments/assets/72de7797-e377-40d8-b9b0-26cac7cf5975)
![Screenshot_20250527_200226](https://github.com/user-attachments/assets/cfaf9f4b-9b33-4900-80eb-6b80fc3170e5)

## Cara Menjalankan Aplikasi di Android Studio

Berikut langkah-langkah untuk menjalankan aplikasi Flutter di Android Studio:

1. **Buka Android Studio**  
   Jalankan Android Studio di komputermu.

2. **Buka Proyek Flutter**  
   Klik `File > Open`, lalu pilih folder Flutter_projects.

3. **Pastikan Emulator atau Perangkat Fisik Tersambung**  
   - Jalankan emulator dari Android Studio, atau  
   - Hubungkan HP Android ke laptop dan aktifkan *USB debugging*.

4. **Jalankan Aplikasi**  
   Tekan tombol `Run` (ikon ▶️ hijau di toolbar), atau gunakan shortcut:
   - Windows/Linux: `Shift + F10`
   - macOS: `Control + R`

5. **Selesai!**  
   Aplikasi akan terinstal dan dijalankan pada emulator atau perangkat yang dipilih.

---
