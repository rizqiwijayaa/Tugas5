## Tugas 5
## Studi Case 1 `PencarianDataMahasiswa.java`

Kode ini merupakan program Java sederhana untuk mencari data mahasiswa berdasarkan NIM menggunakan pencarian linear.

---

### Struktur Kode

```java
import java.util.Scanner;
```

Mengimpor kelas `Scanner` untuk membaca input dari pengguna.

---

```java
class Mahasiswa {
    String nim;
    String nama;
    String jurusan;
    double ipk;
```

Mendefinisikan class `Mahasiswa` dengan atribut `nim`, `nama`, `jurusan`, dan `ipk`.

---

```java
    public Mahasiswa(String nim, String nama, String jurusan, double ipk) {
        this.nim = nim;
        this.nama = nama;
        this.jurusan = jurusan;
        this.ipk = ipk;
    }
```

Konstruktor untuk menginisialisasi objek `Mahasiswa`.

---

```java
    @Override
    public String toString() {
        return String.format("NIM: %s\nNama: %s\nJurusan: %s\nIPK: %.2f", nim, nama, jurusan, ipk);
    }
}
```

Method `toString()` untuk menampilkan data mahasiswa dengan format yang rapi saat dicetak.

---

```java
public class PencarianDataMahasiswa {
```

Class utama yang berisi fungsi `main()` dan logika pencarian.

---

```java
    public static void main(String[] args) {
```

Fungsi utama yang dijalankan saat program dimulai.

---

```java
        Mahasiswa[] daftarMahasiswa = {
            new Mahasiswa("2023001", "Budi Santoso", "Teknik Informatika", 3.75),
            new Mahasiswa("2023002", "Andi Wijaya", "Sistem Informasi", 3.50),
            new Mahasiswa("2023003", "Dewi Lestari", "Teknik Komputer", 3.90),
            new Mahasiswa("2023004", "Rina Maulana", "Teknik Informatika", 3.60),
            new Mahasiswa("2023005", "Doni Kusuma", "Manajemen Informatika", 3.25),
            new Mahasiswa("2023006", "Sinta Rahma", "Sistem Informasi", 3.85),
            new Mahasiswa("2023007", "Rudi Hermawan", "Teknik Komputer", 3.40)
        };
```

Array objek `Mahasiswa` sebagai data awal yang akan digunakan untuk pencarian.

---

```java
        Scanner scanner = new Scanner(System.in);
```

Membuat objek `Scanner` untuk membaca input pengguna.

---

```java
        System.out.println("=== SISTEM PENCARIAN DATA MAHASISWA ===");
        System.out.print("Masukkan NIM Mahasiswa yang dicari: ");
        String nimCari = scanner.nextLine();
```

Menampilkan pesan ke pengguna dan meminta input NIM mahasiswa yang ingin dicari.

---

```java
        Mahasiswa hasilPencarian = cariMahasiswaByNIM(daftarMahasiswa, nimCari);
```

Memanggil method `cariMahasiswaByNIM` untuk mencari mahasiswa berdasarkan NIM.

---

```java
        System.out.println("\nHASIL PENCARIAN:");
        if (hasilPencarian != null) {
            System.out.println("Mahasiswa ditemukan!");
            System.out.println(hasilPencarian);
        } else {
            System.out.println("Mahasiswa dengan NIM " + nimCari + " tidak ditemukan.");
        }
```

Menampilkan hasil pencarian. Jika ditemukan, tampilkan detailnya, jika tidak tampilkan pesan kesalahan.

---

```java
        scanner.close();
```

Menutup `Scanner` setelah digunakan.

---

```java
    public static Mahasiswa cariMahasiswaByNIM(Mahasiswa[] daftarMahasiswa, String nim) {
        for (int i = 0; i < daftarMahasiswa.length; i++) {
            if (daftarMahasiswa[i].nim.equals(nim)) {
                return daftarMahasiswa[i];
            }
        }
        return null;
    }
}
```

Method `cariMahasiswaByNIM` melakukan pencarian linear terhadap array `daftarMahasiswa`. Jika NIM cocok ditemukan, objek mahasiswa dikembalikan; jika tidak, `null`.

---

### Fitur

* Menyimpan data mahasiswa menggunakan array objek.
* Menerapkan pencarian linear berdasarkan NIM.
* Menampilkan hasil pencarian dengan format yang rapi.

---

## Studi Case 2 `PencarianProduk.java`

Program ini melakukan pencarian produk berdasarkan **kategori** dan **rentang harga** menggunakan pencarian linear dengan banyak kriteria.

---

### Struktur Kode

```java
import java.util.ArrayList;
import java.util.Scanner;
```

Mengimpor `ArrayList` untuk menyimpan hasil pencarian, dan `Scanner` untuk membaca input dari pengguna.

---

```java
class Produk {
    String id;
    String nama;
    String kategori;
    double harga;
    int stok;
```

Mendefinisikan class `Produk` dengan atribut `id`, `nama`, `kategori`, `harga`, dan `stok`.

---

```java
    public Produk(String id, String nama, String kategori, double harga, int stok) {
        this.id = id;
        this.nama = nama;
        this.kategori = kategori;
        this.harga = harga;
        this.stok = stok;
    }
```

Konstruktor untuk menginisialisasi objek `Produk`.

---

```java
    @Override
    public String toString() {
        return String.format("%-5s | %-25s | %-15s | Rp %.2f | Stok: %d",
                             id, nama, kategori, harga, stok);
    }
}
```

Method `toString()` untuk menampilkan informasi produk dengan format tabel rapi saat dicetak.

---

```java
public class PencarianProduk {
    public static void main(String[] args) {
```

Class utama dan fungsi `main()` sebagai titik masuk program.

---

```java
        Produk[] daftarProduk = {
            new Produk("P001", "Laptop Asus VivoBook", "Elektronik", 8500000, 10),
            new Produk("P002", "Smartphone Samsung Galaxy", "Elektronik", 5000000, 15),
            new Produk("P003", "Kemeja Formal Pria", "Fashion", 250000, 50),
            new Produk("P004", "Sepatu Lari Nike", "Fashion", 1200000, 25),
            new Produk("P005", "Buku Pemrograman Java", "Buku", 150000, 30),
            new Produk("P006", "Mouse Gaming Logitech", "Elektronik", 350000, 20),
            new Produk("P007", "Novel Bumi Manusia", "Buku", 95000, 40),
            new Produk("P008", "Tas Ransel", "Fashion", 300000, 35)
        };
```

Deklarasi array dari objek `Produk` sebagai data awal toko.

---

```java
        Scanner scanner = new Scanner(System.in);
```

Membuat objek `Scanner` untuk membaca input pengguna dari konsol.

---

```java
        System.out.println("=== SISTEM PENCARIAN PRODUK ===");
        System.out.println("Kategori tersedia: Elektronik, Fashion, Buku");
        System.out.print("Masukkan kategori produk: ");
        String kategoriCari = scanner.nextLine();

        System.out.print("Masukkan harga minimum: Rp ");
        double hargaMin = scanner.nextDouble();

        System.out.print("Masukkan harga maksimum: Rp ");
        double hargaMax = scanner.nextDouble();
```

Menampilkan prompt dan membaca input dari pengguna: kategori produk, harga minimum, dan maksimum.

---

```java
        ArrayList<Produk> hasilPencarian = cariProdukByKriteria(daftarProduk, kategoriCari, hargaMin, hargaMax);
```

Memanggil method `cariProdukByKriteria()` untuk mencari produk berdasarkan kategori dan rentang harga.

---

```java
        System.out.println("\nHASIL PENCARIAN:");
        System.out.println("===============================================================");
        System.out.printf("%-5s | %-25s | %-15s | %-10s | %-10s\n",
                          "ID", "Nama Produk", "Kategori", "Harga", "Stok");
        System.out.println("---------------------------------------------------------------");
```

Menampilkan header hasil pencarian dengan format tabel.

---

```java
        if (hasilPencarian.size() > 0) {
            for (Produk p : hasilPencarian) {
                System.out.println(p);
            }
        } else {
            System.out.println("Tidak ada produk yang sesuai dengan kriteria pencarian.");
        }
        System.out.println("===============================================================");
```

Menampilkan hasil pencarian. Jika ada produk yang cocok, akan dicetak satu per satu. Jika tidak, muncul pesan bahwa tidak ditemukan.

---

```java
        scanner.close();
```

Menutup objek `Scanner`.

---

```java
    public static ArrayList<Produk> cariProdukByKriteria(Produk[] daftarProduk,
                                                         String kategori,
                                                         double hargaMin,
                                                         double hargaMax) {
        ArrayList<Produk> hasilPencarian = new ArrayList<>();

        for (int i = 0; i < daftarProduk.length; i++) {
            Produk produk = daftarProduk[i];

            if (produk.kategori.equalsIgnoreCase(kategori) &&
                produk.harga >= hargaMin &&
                produk.harga <= hargaMax) {
                hasilPencarian.add(produk);
            }
        }

        return hasilPencarian;
    }
}
```

Method `cariProdukByKriteria()` melakukan pencarian linear dengan tiga kriteria:

* Kategori produk harus sama (case-insensitive)
* Harga berada dalam rentang yang ditentukan

Produk yang sesuai ditambahkan ke `ArrayList` hasil dan dikembalikan ke pemanggil.

---

### Fitur

* Menyimpan dan menampilkan data produk dalam bentuk array.
* Menerapkan pencarian dengan banyak kriteria (kategori dan harga).
* Menampilkan hasil pencarian dalam format tabel rapi.

---

## Studi Case 3 `PencarianKata.java`

Program ini memungkinkan pengguna untuk mencari sebuah kata dalam sebuah teks dan menampilkan semua posisi kemunculannya, termasuk versi teks dengan **highlight** menggunakan tanda kurung `[` dan `]`.

---

### Struktur Kode

```java
import java.util.ArrayList;
import java.util.Scanner;
```

Mengimpor kelas `ArrayList` untuk menyimpan posisi kemunculan kata dan `Scanner` untuk membaca input pengguna.

---

```java
public class PencarianKata {
    public static void main(String[] args) {
```

Mendeklarasikan class utama dan method `main()` sebagai titik masuk program.

---

```java
        Scanner scanner = new Scanner(System.in);
```

Membuat objek `Scanner` untuk menerima input dari pengguna melalui terminal.

---

```java
        System.out.println("=== SISTEM PENCARIAN KATA ===");
        System.out.print("Masukkan teks: ");
        String teks = scanner.nextLine();

        System.out.print("Masukkan kata yang dicari: ");
        String kataCari = scanner.nextLine();
```

Menampilkan prompt dan membaca teks serta kata yang ingin dicari.

---

```java
        ArrayList<Integer> posisiDitemukan = cariKata(teks, kataCari);
```

Memanggil fungsi `cariKata()` untuk mencari semua posisi kata yang ditemukan dalam teks.

---

```java
        System.out.println("\nHASIL PENCARIAN:");
        if (posisiDitemukan.size() > 0) {
            System.out.println("Kata '" + kataCari + "' ditemukan sebanyak " +
                               posisiDitemukan.size() + " kali pada posisi:");
```

Jika kata ditemukan, tampilkan jumlah dan daftar posisi kemunculannya.

---

```java
            for (int i = 0; i < posisiDitemukan.size(); i++) {
                System.out.println("- Indeks ke-" + posisiDitemukan.get(i) +
                                   " (karakter ke-" + (posisiDitemukan.get(i) + 1) + ")");
            }
```

Menampilkan indeks kemunculan kata (baik berbasis 0 maupun nomor karakter yang biasa digunakan pengguna).

---

```java
            System.out.println("\nTeks dengan highlight:");
            tampilkanTeksHighlight(teks, kataCari, posisiDitemukan);
        } else {
            System.out.println("Kata '" + kataCari + "' tidak ditemukan dalam teks.");
        }
```

Menampilkan versi teks yang di-*highlight* jika kata ditemukan, atau pesan kegagalan jika tidak.

---

```java
        scanner.close();
```

Menutup `Scanner` untuk membebaskan resource.

---

### Fungsi Pencarian Kata

```java
    public static ArrayList<Integer> cariKata(String teks, String kata) {
        ArrayList<Integer> posisi = new ArrayList<>();
```

Fungsi `cariKata()` mengembalikan daftar indeks di mana kata ditemukan dalam teks.

---

```java
        String teksLower = teks.toLowerCase();
        String kataLower = kata.toLowerCase();
```

Melakukan pencarian tidak peka huruf besar/kecil dengan mengubah teks dan kata ke lowercase.

---

```java
        for (int i = 0; i <= panjangTeks - panjangKata; i++) {
            String potongan = teksLower.substring(i, i + panjangKata);

            if (potongan.equals(kataLower)) {
                posisi.add(i);
            }
        }
```

Melakukan pencarian linear dengan memeriksa setiap substring dalam teks.

---

### Fungsi Highlight Teks

```java
    public static void tampilkanTeksHighlight(String teks, String kata, ArrayList<Integer> posisi) {
        StringBuilder hasil = new StringBuilder(teks);
```

Fungsi `tampilkanTeksHighlight()` menyisipkan tanda `[` dan `]` untuk menyorot kata yang ditemukan.

---

```java
        for (int i = posisi.size() - 1; i >= 0; i--) {
            int pos = posisi.get(i);
            hasil.insert(pos + kata.length(), "]");
            hasil.insert(pos, "[");
        }
```

Melakukan penyisipan secara mundur agar indeks tidak bergeser saat teks dimodifikasi.

---

```java
        System.out.println(hasil.toString());
    }
}
```

Mencetak hasil akhir dari teks yang sudah diberi penanda highlight.

---

### Fitur

* Mencari semua kemunculan kata dalam sebuah teks (tidak peka huruf kapital).
* Menampilkan posisi indeks dari tiap kemunculan kata.
* Menyediakan versi teks yang menyorot semua kata yang ditemukan.

---
