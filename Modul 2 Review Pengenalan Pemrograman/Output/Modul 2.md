<h1 align="center">Laporan Praktikum Modul 2</h1>
<p align="center">Balawan Satria Lhaksana Putra Mazzimo - 103112430004</p>


## Dasar Teori
Pemrograman dengan bahasa Go memiliki struktur yang sederhana namun kuat, dengan aturan penulisan yang jelas dan efisien. Setiap program utama harus memiliki package main dan func main() sebagai titik awal eksekusi. Proses pengembangan melibatkan penulisan kode dalam file .go, kompilasi menggunakan go build, dan eksekusi melalui terminal. Go menyediakan berbagai tipe data seperti integer, float, boolean, dan string, serta mendukung deklarasi variabel yang fleksibel. Selain itu, bahasa ini memiliki kontrol alur yang mencakup perulangan for dalam berbagai bentuk dan percabangan dengan if-else serta switch-case untuk pengambilan keputusan.
### Soal Latihan 2A

#### Soal 1

> Telusuri program berikut dengan cara mengkompilasi dan mengeksekusi program. Silakan masukan data yang sesuai sebanyak yang diminta program. Perhatikan keluaran yang diperoleh. Coba terangkan apa sebenarnya yang dilakukan program tersebut?

```go
package main

import "fmt"

func main() {

    var (
        satu, dua, tiga string
        temp string
    )

    fmt.Print("Masukan input string: ")
    fmt.Scanln(&satu)

    fmt.Print("Masukan input string: ")
    fmt.Scanln(&dua)

    fmt.Print("Masukan input string: ")
    fmt.Scanln(&tiga)

    fmt.Println("Output awal = " + satu + " " + dua + " " + tiga)

    temp = satu
    satu = dua
    dua = tiga
    tiga = temp

    fmt.Println("Output akhir = " + satu + " " + dua + " " + tiga)

}
```
Hasil :
![[Screenshot 2025-03-05 232603.png]]
Deskripsi :
- **Mendeklarasikan variabel**  
    Variabel `satu`, `dua`, `tiga`, dan `temp` bertipe string.
- **Menerima input dari pengguna**
    - Input pertama disimpan ke variabel `satu`
    - Input kedua disimpan ke variabel `dua`
    - Input ketiga disimpan ke variabel `tiga`
- **Menampilkan urutan awal input**  
    Program mencetak nilai dari ketiga variabel (`satu`, `dua`, `tiga`) dalam satu baris.
- **Melakukan proses pertukaran nilai (rotasi ke kiri)**
    - Nilai `satu` disimpan sementara di `temp`.
    - Nilai `dua` dipindahkan ke `satu`.
    - Nilai `tiga` dipindahkan ke `dua`.
    - Nilai `temp` (nilai awal `satu`) dipindahkan ke `tiga`.
- **Menampilkan output akhir setelah pertukaran**  
    Program mencetak kembali ketiga variabel setelah pertukaran posisi dilakukan.
#### Soal 2

>Tahun kabisat adalah tahun yang habis dibagi 400 atau habis dibagi 4 tetapi tidak habis dibagi 100. Buatlah sebuah program yang menerima input sebuah bilangan bulat dan memeriksa apakah bilangan tersebut merupakan tahun kabisat (true) atau bukan (false).

```go
package main
 
import (
    "fmt"
)

func main() {

    var tahun int
    fmt.Print("Masukkan tahun: ")
    fmt.Scan(&tahun)
    kabisat := false

    if tahun%400 == 0 {

        kabisat = true

    } else if tahun%100 == 0 {

        kabisat = false

    } else if tahun%4 == 0 {

        kabisat = true

    } else {

        kabisat = false

    }

    fmt.Println("Tahun:", tahun)
    fmt.Println("Kabisat:", kabisat)

}
```
Hasil :
![[Pasted image 20250306025545.png]]
Deskripsi :
Program ini dibuat untuk menentukan apakah sebuah tahun merupakan **tahun kabisat** atau bukan. Program menerima input berupa tahun (bilangan bulat), lalu melakukan proses pengecekan berdasarkan aturan berikut:
- Tahun kabisat adalah tahun yang habis dibagi 400.
- Jika tidak habis dibagi 400, tahun tetap bisa menjadi tahun kabisat jika:
    - Habis dibagi 4.
    - Tidak habis dibagi 100.
#### Soal 3

>Buat program Bola yang menerima input jari-jari suatu bola (bilangan bulat). Tampilkan Volume dan Luas kulit bola. 𝑣𝑜𝑙𝑢𝑚𝑒𝑏𝑜𝑙𝑎 = 4 3 𝜋𝑟 3 dan 𝑙𝑢𝑎𝑠𝑏𝑜𝑙𝑎 = 4𝜋𝑟 2 (π ≈ 3.1415926535).

```go
package main  

import (
    "fmt"
    "math"
)

func main() {

    var jejari float64

    // Input jari-jari dari user

    fmt.Print("Masukkan jejari bola: ")

    fmt.Scan(&jejari)

    // Rumus volume dan luas permukaan bola

    volume := (4.0 / 3.0) * math.Pi * math.Pow(jejari, 3)

    luas := 4 * math.Pi * math.Pow(jejari, 2)

    // Output hasil perhitungan

    fmt.Printf("Bola dengan jejari %.0f memiliki volume %.4f dan luas kulit %.4f\n", jejari, volume, luas)

}
```
Hasil :
![[Pasted image 20250306030130.png]]
Deskripsi :
Program ini bertujuan untuk menghitung **volume** dan **luas permukaan bola** berdasarkan jari-jari (radius) yang dimasukkan oleh pengguna. Formula yang digunakan adalah:
- **Volume bola**: 4/3πr^3
- **Luas permukaan bola**: 4πr^2
Dengan π sekitar 3.1415926535.
#### Soal 4

>Dibaca nilai temperatur dalam derajat Celsius. Nyatakan temperatur tersebut dalam Fahrenheit 𝐶𝑒𝑙𝑠𝑖𝑢𝑠 = (𝐹𝑎ℎ𝑟𝑒𝑛ℎ𝑒𝑖𝑡 − 32) × 5/9 𝑅𝑒𝑎𝑚𝑢𝑟 = 𝐶𝑒𝑙𝑐𝑖𝑢𝑠 × 4/5 𝐾𝑒𝑙𝑣𝑖𝑛 = (𝐹𝑎ℎ𝑟𝑒𝑛ℎ𝑒𝑖𝑡 + 459.67) × 5/9

```go
package main

import (
	"fmt"
)

func main() {
	var celsius float64

	// Input suhu dalam Celsius
	fmt.Print("Masukkan suhu dalam Celsius: ")
	fmt.Scan(&celsius)

	// Konversi ke Reamur, Fahrenheit, dan Kelvin
	reamur := celsius * 4 / 5
	fahrenheit := (celsius * 9 / 5) + 32
	kelvin := celsius + 273.15

	// Output hasil konversi
	fmt.Println("Derajat Reamur:", reamur)
	fmt.Println("Derajat Fahrenheit:", fahrenheit)
	fmt.Println("Derajat Kelvin:", kelvin)
}

```
Hasil :
![[Pasted image 20250306030918.png]]
Deskripsi :
Program ini bertujuan untuk mengubah suhu yang diinputkan dalam satuan derajat **Celsius** menjadi tiga satuan suhu lainnya, yaitu:
1. **Reamur** - Skala suhu yang digunakan di beberapa negara, terutama di Eropa pada masa lalu.
2. **Fahrenheit** - Skala suhu yang umum digunakan di Amerika Serikat.
3. **Kelvin** - Skala suhu standar ilmiah yang digunakan dalam sains dan teknik.
#### Soal 5

>Tipe karakter sebenarnya hanya apa yang tampak dalam tampilan. Di dalamnya tersimpan dalam bentuk biner 8 bit (byte) atau 32 bit (rune) saja. Buat program ASCII yang akan membaca 5 buat data integer dan mencetaknya dalam format karakter. Kemudian membaca 3 buah data karakter dan mencetak 3 buah karakter setelah karakter tersebut (menurut tabel ASCII) Masukan terdiri dari dua baris. Baris pertama berisi 5 buah data integer. Data integer mempunyai nilai antara 32 s.d. 127. Baris kedua berisi 3 buah karakter yang berdampingan satu dengan yang lain (tanpa dipisahkan spasi). Keluaran juga terdiri dari dua baris. Baris pertama berisi 5 buah representasi karakter dari data yang diberikan, yang berdampingan satu dengan lain, tanpa dipisahkan spasi. Baris kedua berisi 3 buah karakter (juga tidak dipisahkan oleh spasi).

```go
package main

import "fmt"

func main() {

	var kode1, kode2, kode3, kode4, kode5 int
	var huruf1, huruf2, huruf3 rune

	fmt.Scan(&kode1, &kode2, &kode3, &kode4, &kode5)
	fmt.Scanln()
	fmt.Scanf("%c%c%c\n", &huruf1, &huruf2, &huruf3)

	huruf1 += 1
	huruf2 += 1
	huruf3 += 1

	fmt.Printf("%c%c%c%c%c\n", kode1, kode2, kode3, kode4, kode5)
	fmt.Printf("%c%c%c\n", huruf1, huruf2, huruf3)
}
```
Hasil :
![[Pasted image 20250306031623.png]]
Deskripsi :
Program ini merupakan program sederhana dalam bahasa Go yang berfungsi untuk menerima input berupa lima kode ASCII dan tiga karakter. Program kemudian akan:
1. **Membaca lima bilangan bulat** yang merepresentasikan kode ASCII dari karakter tertentu.
2. **Membaca tiga karakter langsung**.
3. **Menggeser (shift) ketiga karakter tersebut** ke karakter selanjutnya dalam urutan ASCII (misalnya, 'a' menjadi 'b', 'B' menjadi 'C', dst.).
4. **Menampilkan karakter yang sesuai dengan lima kode ASCII** yang telah dimasukkan.
5. **Menampilkan tiga karakter hasil pergeseran (incremented characters)**.
### Soal Latihan 2B

#### Soal 1

> Siswa kelas IPA di salah satu sekolah menengah atas di Indonesia sedang mengadakan praktikum kimia. Di setiap percobaan akan menggunakan 4 tabung reaksi, yang mana susunan warna cairan di setiap tabung akan menentukan hasil percobaan. Siswa diminta untuk mencatat hasil percobaan tersebut. Percobaan dikatakan berhasil apabila susunan warna zat cair pada gelas 1 hingga gelas 4 secara berturutan adalah ‘merah’, ‘kuning’, ‘hijau’, dan ‘ungu’ selama 5 kali percobaan berulang. Buatlah sebuah program yang menerima input berupa warna dari ke 4 gelas reaksi sebanyak 5 kali percobaan. Kemudian program akan menampilkan true apabila urutan warna sesuai dengan informasi yang diberikan pada paragraf sebelumnya, dan false untuk urutan warna lainnya.

```go
package main

import "fmt"

func main() {
	var gelas1, gelas2, gelas3, gelas4 string
	var berhasil = true

	for i := 1; i <= 5; i++ {
		fmt.Printf("Percobaan %d: ", i)
		fmt.Scan(&gelas1, &gelas2, &gelas3, &gelas4)

		if !(gelas1 == "merah" && gelas2 == "kuning" && gelas3 == "hijau" && gelas4 == "ungu") {
			berhasil = false
		}
	}

	fmt.Printf("Berhasil: %t\n", berhasil)
}
```
Hasil :
![[Pasted image 20250306032319.png]]
Deskripsi :
Program ini bertujuan untuk mencatat hasil praktikum kimia yang dilakukan siswa. Dalam percobaan ini, setiap sesi terdiri dari 4 tabung reaksi yang masing-masing diisi dengan zat cair berwarna. Warna yang harus muncul secara berurutan agar percobaan dianggap berhasil adalah:
- Gelas 1: **merah**
- Gelas 2: **kuning**
- Gelas 3: **hijau**
- Gelas 4: **ungu**
Program akan meminta pengguna memasukkan 4 warna cairan untuk setiap tabung reaksi selama **5 kali percobaan**. Setelah semua data dimasukkan, program akan memeriksa apakah semua percobaan memiliki urutan warna yang benar. Jika semua percobaan sesuai, program mencetak **`Berhasil: true`**, jika ada satu saja yang tidak sesuai, program mencetak **`Berhasil: false`**.
#### Soal 2

> Suatu pita (string) berisi kumpulan nama-nama bunga yang dipisahkan oleh spasi dan ‘– ‘, contoh pita diilustrasikan seperti berikut ini. Pita: mawar – melati – tulip – teratai – kamboja – anggrek Buatlah sebuah program yang menerima input sebuah bilangan bulat positif (dan tidak nol) N, kemudian program akan meminta input berupa nama bunga secara berulang sebanyak N kali dan nama tersebut disimpan ke dalam pita. (Petunjuk: gunakan operasi penggabungan string dengan operator “+” ). Tampilkan isi pita setelah proses input selesai.

```go
package main

import "fmt"

func main() {
	var bunga, pita string
	var jumlah int

	for {
		fmt.Printf("Bunga %d: ", jumlah+1)
		fmt.Scan(&bunga)

		if bunga == "selesai" {
			break
		}

		if jumlah > 0 {
			pita += " - "
		}
		pita += bunga
		jumlah++
	}

	fmt.Println("Pita:", pita)
	fmt.Println("Jumlah Bunga:", jumlah)
}
```
Hasil :
![[Pasted image 20250306032730.png]]
Deskripsi : 
Program ini adalah program pencatatan jumlah bunga beserta nama-namanya yang dihubungkan dalam satu pita menggunakan bahasa pemrograman **Golang**.
#### Soal 3

> Setiap hari Pak Andi membawa banyak barang belanjaan dari pasar dengan mengendarai sepeda motor. Barang belanjaan tersebut dibawa dalam kantong terpal di kiri-kanan motor. Sepeda motor tidak akan oleng jika selisih berat barang di kedua kantong sisi tidak lebih dari 9 kg. Buatlah program Pak Andi yang menerima input dua buah bilangan real positif yang menyatakan berat total masing-masing isi kantong terpal. Program akan terus meminta input bilangan tersebut hingga salah satu kantong terpal berisi 9 kg atau lebih.

```go
package main

import "fmt"

func main() {
	var kantong1, kantong2, selisih float32
	var oleng bool

	for {
		fmt.Print("Masukkan berat belanjaan di kedua kantong: ")
		fmt.Scan(&kantong1, &kantong2)

		// Berhenti jika berat salah satu kantong negatif
		if kantong1 < 0 || kantong2 < 0 {
			fmt.Println("Proses selesai")
			break
		}

		// Berhenti jika total berat melebihi 150 kg
		if kantong1+kantong2 > 150 {
			fmt.Println("Proses selesai")
			break
		}

		// Hitung selisih berat antara kedua kantong
		if kantong1 > kantong2 {
			selisih = kantong1 - kantong2
		} else {
			selisih = kantong2 - kantong1
		}

		// Tentukan apakah sepeda akan oleng
		oleng = selisih >= 9

		// Tampilkan status oleng
		fmt.Println("Sepeda motor Pak Andi akan oleng:", oleng)
	}
}
```
Hasil :
![[Pasted image 20250306033543.png]]
Deskripsi :
Program ini bertujuan untuk membantu Pak Andi mengevaluasi apakah sepeda motornya akan oleng atau tidak saat membawa barang belanjaan. Barang belanjaan tersebut dibagi ke dalam dua kantong terpal di sisi kiri dan kanan motor. Sepeda motor dianggap berisiko oleng jika selisih berat antara kedua kantong lebih dari atau sama dengan 9 kg.
#### Soal 4
> Diberikan sebuah persamaan sebagai berikut ini. 𝑓(𝑘) = (4𝑘 + 2) 2 (4𝑘 + 1)(4𝑘 + 3) Buatlah sebuah program yang menerima input sebuah bilangan sebagai K, kemudian menghitung dan menampilkan nilai f(K) sesuai persamaan di atas.

```go
package main

import (
	"fmt"
	"math"
)

func main() {
	var k int

	fmt.Print("Nilai K: ")
	fmt.Scan(&k)

	result := 1.0

	for i := 0; i < k; i++ {
		numerator := math.Pow(float64(4*i+2), 2)
		denominator := float64((4*i + 1) * (4*i + 3))

		result *= numerator / denominator
	}

	fmt.Printf("Hasil dari operasi fungsi = %.10f\n", result)
}
```
Hasil : 
![[Pasted image 20250306033916.png]]
Deskripsi
Program ini meminta pengguna memasukkan sebuah bilangan bulat positif K, yang menunjukkan jumlah iterasi perhitungan. Pada setiap iterasi, program menghitung pecahan matematis menggunakan rumus tertentu, lalu mengalikan hasilnya secara berurutan (cumulative product). Proses ini terus berulang hingga K kali, kemudian hasil akhir ditampilkan dengan presisi 10 angka di belakang koma.

### Soal Latihan 2C

#### Soal 1

> PT POS membutuhkan aplikasi perhitungan biaya kirim berdasarkan berat parsel. Maka, buatlah program BiayaPos untuk menghitung biaya pengiriman tersebut dengan ketentuan sebagai berikut! Dari berat parsel (dalam gram), harus dihitung total berat dalam kg dan sisanya (dalam gram). Biaya jasa pengiriman adalah Rp. 10.000,- per kg. Jika sisa berat tidak kurang dari 500 gram, maka tambahan biaya kirim hanya Rp. 5,- per gram saja. Tetapi jika kurang dari 500 gram, maka tambahan biaya akan dibebankan sebesar Rp. 15,- per gram. Sisa berat (yang kurang dari 1kg) digratiskan biayanya apabila total berat ternyata lebih dari 10kg.

```go
package main

import (
	"fmt"
)

func main() {
	var beratParsel int

	fmt.Print("Berat parsel (gram): ")
	fmt.Scan(&beratParsel)

	kg := beratParsel / 1000
	gr := beratParsel % 1000

	biayaKg := kg * 10000
	var biayaGr int

	if gr >= 500 {
		biayaGr = gr * 5
	} else {
		if kg >= 10 {
			biayaGr = gr * 5
		} else {
			biayaGr = gr * 15
		}
	}

	totalBiaya := biayaKg + biayaGr

	fmt.Printf("Detail berat: %d kg + %d gr\n", kg, gr)
	fmt.Printf("Detail biaya: Rp. %d + Rp. %d\n", biayaKg, biayaGr)
	fmt.Printf("Total biaya: Rp. %d\n", totalBiaya)
}
```
Hasil :
![[Pasted image 20250306101156.png]]
Deskripsi :
Program BiayaPos adalah aplikasi berbasis Go yang digunakan untuk menghitung biaya pengiriman paket berdasarkan beratnya. Pengguna diminta memasukkan berat parsel dalam satuan gram. Program kemudian menghitung total biaya kirim sesuai dengan ketentuan yang berlaku di PT POS, yaitu:
- **Biaya per kilogram:** Rp. 10.000,-.
- **Biaya sisa berat (kurang dari 1 kg):**
    - Jika sisa berat **500 gram atau lebih**, dikenakan biaya Rp. 5 per gram.
    - Jika sisa berat **kurang dari 500 gram**:
        - Jika total berat **kurang dari 10 kg**, biaya Rp. 15 per gram.
        - Jika total berat **10 kg atau lebih**, biaya Rp. 5 per gram.
Program akan menampilkan:
- Detail berat dalam kg dan gram.
- Detail biaya untuk berat kg dan gram.
- Total biaya yang harus dibayar.
#### Soal 2

> Jawablah pertanyaan-pertanyaan berikut: 
> a. Jika nam diberikan adalah 80.1, apa keluaran dari program tersebut? Apakah eksekusi program tersebut sesuai spesifikasi soal? 
> b. Apa saja kesalahan dari program tersebut? Mengapa demikian? Jelaskan alur program seharusnya! 
> c. Perbaiki program tersebut! Ujilah dengan masukan: 93.5; 70.6; dan 49.5. Seharusnya keluaran yang diperoleh adalah ‘A’, ‘B’, dan ‘D’.

##### Kode Awal
```go
package main
import “fmt”
func main() {
 var nam float64
 var nmk string
 fmt.Print(“Nilai akhir mata kuliah: “)
 fmt.Scanln(&nam)
 if nam > 80 {
 nam = “A”
 }
 if nam > 72.5 {
 nam = “AB”
 }
 if nam > 65 {
 nam = “B”
 }
 if nam > 57.5 {
 nam = “BC”
 }
 if nam > 50 {
 nam = “C”
 }
 if nam > 40 {
 nam = “D”
 } else if nam <= 40 {
 nam = “E”
 }
 fmt.Println(“Nilai mata kuliah: “, nmk)
}
```

##### Kode Setelah Perbaikan
```go
package main

import "fmt"

func main() {
	var nam float64
	var nmk string

	fmt.Print("Nilai akhir mata kuliah: ")
	fmt.Scanln(&nam)

	if nam > 80 {
		nmk = "A"
	} else if nam > 72.5 {
		nmk = "AB"
	} else if nam > 65 {
		nmk = "B"
	} else if nam > 57.5 {
		nmk = "BC"
	} else if nam > 50 {
		nmk = "C"
	} else if nam > 40 {
		nmk = "D"
	} else {
		nmk = "E"
	}

	fmt.Println("Nilai mata kuliah:", nmk)
}
```
Jawab : 
a. Program eror
b. Kesalahannya yaitu : 
	1. Logika Kontrol Program Salah
		- Program menggunakan serangkaian **if** terpisah, bukan **if-else if**.
		- Akibatnya, lebih dari satu kondisi bisa terpenuhi dan nilai **nmk** akan ditimpa beberapa kali.
	2. Struktur klasifikasi rentang nilai tidak sesuai aturan grading standar.
		- Biasanya, jika nilai sudah cocok dengan rentang tertentu, program seharusnya **berhenti memeriksa kondisi lain**.
		- Dengan struktur sekarang, program terus memeriksa semua kondisi meskipun kondisi pertama sudah sesuai.
	3. **Alur program yang benar :**
		- Program meminta input nilai akhir.
		- Program memeriksa nilai tersebut secara berurutan menggunakan **if-else if**, dari nilai tertinggi ke terendah.
		- Ketika kondisi cocok, program menetapkan NMK dan berhenti memeriksa kondisi lainnya.
c. Hasil sudah sesuai ketika program sudah diperbaiki :
![[Pasted image 20250306103423.png]]

#### Soal 3

> Sebuah bilangan bulat b memiliki faktor bilangan f > 0 jika f habis membagi b. Contoh: 2 merupakan faktor dari bilangan 6 karena 6 habis dibagi 2. Buatlah program yang menerima input sebuah bilangan bulat b dan b > 1. Program harus dapat mencari dan menampilkan semua faktor dari bilangan tersebut!
> Bilangan bulat b > 0 merupakan bilangan prima p jika dan hanya jika memiliki persis dua faktor bilangan saja, yaitu 1 dan dirinya sendiri. Lanjutkan program sebelumnya. Setelah menerima masukan sebuah bilangan bulat b > 0. Program tersebut mencari dan menampilkan semua faktor bilangan tersebut. Kemudian, program menentukan apakah b merupakan bilangan prima.

```go
package main

import "fmt"

func main() {
	var bilangan, jumlahFaktor int
	var prima bool

	fmt.Print("Bilangan: ")
	fmt.Scan(&bilangan)

	fmt.Print("Faktor: ")
	for i := 1; i <= bilangan; i++ {
		if bilangan%i == 0 {
			fmt.Print(i, " ")
			jumlahFaktor++
		}
	}
	fmt.Println()

	prima = jumlahFaktor == 2
	fmt.Println("Prima:", prima)
}
```
Hasil :
![[Pasted image 20250306105141.png]]
Deskripsikan :
Program ini berfungsi untuk:
1. Menerima input sebuah bilangan bulat positif `bilangan` dari pengguna.
2. Menampilkan semua faktor dari bilangan tersebut.
3. Menentukan apakah bilangan tersebut merupakan **bilangan prima** atau bukan.


