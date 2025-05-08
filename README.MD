PENCARIAN DATA MAHASISWA

import java.util.Scanner; // Mengimpor kelas Scanner dari library java untuk membaca input pengguna

class Mahasiswa { // Mendefinisikan kelas Mahasiswa yang akan merepresentasikan data mahasiswa.
String nim; // Mendeklarasikan variabel instance untuk menyimpan nim sebagai string
String nama; // Mendeklarasikan variabel instance untuk menyimpan nama sebagai string
String jurusan; // Mendeklarasikan variabel instance untuk menyimpan jurusan sebagai string
double ipk; // Mendeklarasikan variabel instance untuk menyimpan ipk sebagai double

    public Mahasiswa(String nim, String nama, String jurusan, double ipk) { // Konstruktor untuk kelas Mahasiswa yang menginisialisasi semua atribut
        this.nim = nim; // this.nim mengacu pada variabel instance, sedangkan nim adalah parameter
        this.nama = nama; // this.nama mengacu pada variabel instance, sedangkan nama adalah parameter
        this.jurusan = jurusan; // this.jurusan mengacu pada variabel instance, sedangkan jurusan adalah parameter
        this.ipk = ipk; // this.ipk mengacu pada variabel instance, sedangkan ipk adalah parameter
    }

    @Override
    public String toString() { // Mengoverride method toString() untuk memberikan representasi string yang diformat dari objek Mahasiswa
        return String.format("NIM: %s\nNama: %s\nJurusan: %s\nIPK: %.2f", nim, nama, jurusan, ipk); // Format output akan menampilkan semua data mahasiswa dengan layout yang rapi, %.2f untuk menampilkan IPK dengan 2 angka di belakang koma
    }

}

public class PencarianDataMahasiswa { // Mendefinisikan kelas utama yang berisi logika program pencarian
public static void main(String[] args) { // Method main sebagai entry point program
// Data mahasiswa
Mahasiswa[] daftarMahasiswa = { // Membuat array daftarMahasiswa yang berisi 7 objek Mahasiswa, setiap objek diinisialisasi dengan NIM, nama, jurusan, dan IPK
new Mahasiswa("2023001", "Budi Santoso", "Teknik Informatika", 3.75),
new Mahasiswa("2023002", "Andi Wijaya", "Sistem Informasi", 3.50),
new Mahasiswa("2023003", "Dewi Lestari", "Teknik Komputer", 3.90),
new Mahasiswa("2023004", "Rina Maulana", "Teknik Informatika", 3.60),
new Mahasiswa("2023005", "Doni Kusuma", "Manajemen Informatika", 3.25),
new Mahasiswa("2023006", "Sinta Rahma", "Sistem Informasi", 3.85),
new Mahasiswa("2023007", "Rudi Hermawan", "Teknik Komputer", 3.40)
};

        Scanner scanner = new Scanner(System.in); // Membuat objek Scanner untuk membaca input dari keyboard

        System.out.println("=== SISTEM PENCARIAN DATA MAHASISWA ==="); // Menampilkan header program
        System.out.print("Masukkan NIM Mahasiswa yang dicari: "); // memasukkan NIM yang dicari
        String nimCari = scanner.nextLine(); // Membaca input NIM dari pengguna dan menyimpannya di variabel nimCari

        // Lakukan pencarian linear
        Mahasiswa hasilPencarian = cariMahasiswaByNIM(daftarMahasiswa, nimCari); // Memanggil method cariMahasiswaByNIM dengan parameter array mahasiswa dan NIM yang dicari, hasil pencarian disimpan di variabel hasilPencarian

        System.out.println("\nHASIL PENCARIAN:"); // Menampilkan hasil pencarian
        if (hasilPencarian != null) { // jika ditemukan
            System.out.println("Mahasiswa ditemukan!"); // menampilkan pesan mahasiswa ditemukan!
            System.out.println(hasilPencarian); // menampilkan data mahasiswa
        } else { // jika tidak ditemukan
            System.out.println("Mahasiswa dengan NIM " + nimCari + " tidak ditemukan."); // menampilkan pesan mahasiswa dengan nim tersebut tidak ditemukan
        }

        scanner.close(); // Menutup objek Scanner
    }

    public static Mahasiswa cariMahasiswaByNIM(Mahasiswa[] daftarMahasiswa, String nim) { // Mendefinisikan method static untuk mencari mahasiswa berdasarkan NIM, menerima parameter array mahasiswa dan NIM yang dicari, mengembalikan objek Mahasiswa jika ditemukan, atau null jika tidak ditemukan
        for (int i = 0; i < daftarMahasiswa.length; i++) { // Melakukan iterasi melalui seluruh elemen array daftarMahasiswa
            // Bandingkan NIM mahasiswa saat ini dengan NIM yang dicari
            if (daftarMahasiswa[i].nim.equals(nim)) { // Membandingkan NIM mahasiswa saat ini dengan NIM yang dicari
                return daftarMahasiswa[i]; // Jika cocok, kembalikan objek mahasiswa tersebut
            }
        }
        // Jika tidak ditemukan
        return null; // Jika loop selesai tanpa menemukan NIM yang cocok, kembalikan null
    }

}

PENCARIAN PRODUK

import java.util.ArrayList; // Mengimpor kelas ArrayList untuk menyimpan koleksi objek
import java.util.Scanner; // Mengimpor kelas Scanner untuk input dari pengguna

class Produk { // Mendefinisikan class Produk yang berisi atribut :
String id; // ID produk
String nama; // Nama produk
String kategori; // Kategori produk
double harga; // Harga produk
int stok; // Jumlah stok

    public Produk(String id, String nama, String kategori, double harga, int stok) { // Constructor untuk inisialisasi objek Produk
        this.id = id; // Mengisi atribut id dengan parameter
        this.nama = nama; // Mengisi atribut nama dengan parameter
        this.kategori = kategori; // Mengisi atribut kategori dengan parameter
        this.harga = harga; // Mengisi atribut harga dengan parameter
        this.stok = stok; // Mengisi atribut stok dengan parameter
    }

    @Override // Override method toString untuk representasi string yang lebih baik
    public String toString() {
        return String.format("%-5s | %-25s | %-15s | Rp %.2f | Stok: %d",
                             id, nama, kategori, harga, stok);
    }

}

public class PencarianProduk { // Mendefinisikan kelas utama
public static void main(String[] args) { // Program dijalankan dari method main
// Data produk
Produk[] daftarProduk = { // Membuat array daftarProduk berisi data produk secara statis (langsung diinisialisasi)
new Produk("P001", "Laptop Asus VivoBook", "Elektronik", 8500000, 10),
new Produk("P002", "Smartphone Samsung Galaxy", "Elektronik", 5000000, 15),
new Produk("P003", "Kemeja Formal Pria", "Fashion", 250000, 50),
new Produk("P004", "Sepatu Lari Nike", "Fashion", 1200000, 25),
new Produk("P005", "Buku Pemrograman Java", "Buku", 150000, 30),
new Produk("P006", "Mouse Gaming Logitech", "Elektronik", 350000, 20),
new Produk("P007", "Novel Bumi Manusia", "Buku", 95000, 40),
new Produk("P008", "Tas Ransel", "Fashion", 300000, 35)
};

        Scanner scanner = new Scanner(System.in); // Membuat objek Scanner untuk membaca input dari user

        System.out.println("=== SISTEM PENCARIAN PRODUK ==="); // // Menampilkan header program
        System.out.println("Kategori tersedia: Elektronik, Fashion, Buku"); // Menampilkan kategori
        System.out.print("Masukkan kategori produk: "); // Meminta input kategori dari pengguna
        String kategoriCari = scanner.nextLine(); // Membaca input kategori dari pengguna dan menyimpannya di variabel kategoriCari

        System.out.print("Masukkan harga minimum: Rp "); //  Meminta input harga minimum
        double hargaMin = scanner.nextDouble(); // Membaca input angka desimal dari pengguna dan mewakili harga minimum dalam pencarian produk.

        System.out.print("Masukkan harga maksimum: Rp "); //  Meminta input harga maksimum
        double hargaMax = scanner.nextDouble(); // Membaca input angka desimal dari pengguna dan mewakili harga maksimum dalam pencarian produk.

        // Lakukan pencarian linear multi-kriteria
        ArrayList<Produk> hasilPencarian = cariProdukByKriteria(daftarProduk, kategoriCari, hargaMin, hargaMax); // Memanggil method cariProdukByKriteria untuk mencari produk yang sesuai kriteria

        System.out.println("\nHASIL PENCARIAN:"); // Menampilkan hasil pencarian

        // Menampilkan header tabel hasil pencarian
        System.out.println("===============================================================");
        System.out.printf("%-5s | %-25s | %-15s | %-10s | %-10s\n",
                          "ID", "Nama Produk", "Kategori", "Harga", "Stok");
        System.out.println("---------------------------------------------------------------");

        if (hasilPencarian.size() > 0) { // Mengecek apakah ada hasil pencarian, jika hasil pencarian ada maka
            for (Produk p : hasilPencarian) { // Menampilkan semua produk yang sesuai
                System.out.println(p);  // Memanggil toString() dari Produk
            }
        } else { Jika tidak menemukan hasil pencarian maka
            System.out.println("Tidak ada produk yang sesuai dengan kriteria pencarian."); // Menampilkan pesan Tidak ada produk yang sesuai dengan kriteria pencarian.
        }
        System.out.println("===============================================================");

        scanner.close(); // Menutup scanner
    }

    // Method untuk mencari produk berdasarkan kategori dan rentang harga
    public static ArrayList<Produk> cariProdukByKriteria(Produk[] daftarProduk,
                                                         String kategori,
                                                         double hargaMin,
                                                         double hargaMax) {

        ArrayList<Produk> hasilPencarian = new ArrayList<>(); // Membuat list kosong untuk menampung produk yang cocok

        for (int i = 0; i < daftarProduk.length; i++) { // Loop melalui semua produk dalam array daftarProduk
            Produk produk = daftarProduk[i]; // Mengambil produk pada indeks ke-i dari array

            // Periksa apakah produk memenuhi semua kriteria
            if (produk.kategori.equalsIgnoreCase(kategori) && // Kategori produk sama dengan yang dicari
                produk.harga >= hargaMin && // Harga produk >= harga minimum yang ditentukan
                produk.harga <= hargaMax) { // Harga produk <= harga maksimum yang ditentukan
                hasilPencarian.add(produk); // Jika semua kriteria terpenuhi, tambahkan produk ke ArrayList hasil
            }
        }

        return hasilPencarian; // Mengembalikan ArrayList yang berisi semua produk yang memenuhi kriteria
    }

}

PENCARIAN KATA
import java.util.ArrayList; // Mengimpor kelas ArrayList untuk menyimpan koleksi data
import java.util.Scanner; // Mengimpor kelas Scanner untuk input dari pengguna

public class PencarianKata { // Mendefinisikan kelas utama
public static void main(String[] args) { // Program dijalankan dari method main
Scanner scanner = new Scanner(System.in); // Membuat objek Scanner untuk input

        System.out.println("=== SISTEM PENCARIAN KATA ==="); // Menampilkan judul program
        System.out.print("Masukkan teks: "); // Meminta pengguna mengetikkan teks yang akan diproses
        String teks = scanner.nextLine(); // Membaca seluruh baris input sebagai teks

        System.out.print("Masukkan kata yang dicari: "); // Meminta pengguna mengetikkan kata yang ingin dicari dalam teks
        String kataCari = scanner.nextLine(); // Membaca kata yang ingin dicari

        // Lakukan pencarian kata
        ArrayList<Integer> posisiDitemukan = cariKata(teks, kataCari);  // Memanggil fungsi pencarian kata

        System.out.println("\nHASIL PENCARIAN:"); // Menampilkan hasil pencarian
        if (posisiDitemukan.size() > 0) { // Jika ada hasil ditemukan
            System.out.println("Kata '" + kataCari + "' ditemukan sebanyak " +
                               posisiDitemukan.size() + " kali pada posisi:"); // Menampilkan berapa kali kata ditemukan

            for (int i = 0; i < posisiDitemukan.size(); i++) { // Loop untuk menampilkan semua posisi yang ditemukan
                System.out.println("- Indeks ke-" + posisiDitemukan.get(i) +
                                   " (karakter ke-" + (posisiDitemukan.get(i) + 1) + ")"); // Menampilkan semua posisi kemunculan kata berdasarkan indeks karakter dalam string
            }

            // Tampilkan teks dengan highlight kata yang ditemukan
            System.out.println("\nTeks dengan highlight:"); // Menampilkan pesan Teks dengan highlight
            tampilkanTeksHighlight(teks, kataCari, posisiDitemukan); // Memanggil method tampilkanTeksHighlight untuk menampilkan teks dengan kata yang dicari diberi tanda kurung [ ]
        } else { // jika tidak ditemukan
            System.out.println("Kata '" + kataCari + "' tidak ditemukan dalam teks."); // Menampilkan pesan bahwa kata tidak ditemukan dalam teks
        }

        scanner.close(); // Menutup Scanner
    }

    public static ArrayList<Integer> cariKata(String teks, String kata) { // Method untuk mencari posisi kemunculan kata dalam teks
        ArrayList<Integer> posisi = new ArrayList<>(); // menyimpan kata dalam list posisi

        // Konversi ke lowercase untuk pencarian case-insensitive
        String teksLower = teks.toLowerCase(); // Mengubah teks ke huruf kecil agar pencarian tidak sensitif terhadap kapitalisas
        String kataLower = kata.toLowerCase(); // Mengubah kata ke huruf kecil agar pencarian tidak sensitif terhadap kapitalisas

        int panjangKata = kataLower.length(); // Panjang kata yang dicari
        int panjangTeks = teksLower.length();  // Panjang teks

        // Lakukan linear search
        for (int i = 0; i <= panjangTeks - panjangKata; i++) { // Loop dari indeks 0 sampai batas akhir yang memungkinkan kata muat di teks.
            // Periksa apakah substring dari posisi i sampai i+panjangKata sama dengan kata
            String potongan = teksLower.substring(i, i + panjangKata); // Mengambil potongan teks sepanjang kata yang dicari

            if (potongan.equals(kataLower)) { // Jika potongan cocok dengan kata
                posisi.add(i); // Simpan posisi awal kata

                // Optional: Skip ke akhir kata yang ditemukan untuk menghindari overlap
                // i += panjangKata - 1;
            }
        }

        return posisi;  // Kembalikan daftar posisi
    }

    public static void tampilkanTeksHighlight(String teks, String kata, ArrayList<Integer> posisi) { // Method tampilkanTeksHighlight yang berisi teks kata dan posisi pada array
        StringBuilder hasil = new StringBuilder(teks); // Untuk memodifikasi teks

        // Tambahkan marker untuk highlight (dari posisi terjauh dulu untuk menghindari pergeseran indeks)
        for (int i = posisi.size() - 1; i >= 0; i--) {  // Memulai perulangan mundur dari indeks terakhir hingga indeks pertama dalam daftar posisi
            int pos = posisi.get(i); // Mengambil posisi kemunculan kata dari daftar posisi dan menyimpannya dalam variabel pos
            hasil.insert(pos + kata.length(), "]"); // Menyisipkan tanda ] setelah akhir kata yang ditemukan, berdasarkan posisi pos ditambah panjang kata
            hasil.insert(pos, "["); // Menyisipkan tanda [ di awal kata yang ditemukan, tepat di posisi pos
        }

        System.out.println(hasil.toString()); // mencetak teks akhir yang sudah diberi tanda kurung siku [ dan ] untuk menyoroti kata yang ditemukan
    }

}
