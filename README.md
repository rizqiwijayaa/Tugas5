Berikut ini adalah versi **Markdown lengkap** dari penjelasan kode `PencarianDataMahasiswa.java` yang bisa kamu salin langsung ke file `README.md` di GitHub:

---

## 📘 Penjelasan Kode `PencarianDataMahasiswa.java`

Kode ini merupakan program Java sederhana untuk mencari data mahasiswa berdasarkan NIM menggunakan pencarian linear.

---

### 📄 Struktur Kode

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

### 🔍 Fitur

* Menyimpan data mahasiswa menggunakan array objek.
* Menerapkan pencarian linear berdasarkan NIM.
* Menampilkan hasil pencarian dengan format yang rapi.

---

Kalau kamu ingin saya bantu generate `README.md` lengkap dengan judul proyek, deskripsi, cara menjalankan, dan lain-lain, tinggal beri tahu saja!
