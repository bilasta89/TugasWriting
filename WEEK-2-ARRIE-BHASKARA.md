Joyfull Jasper Week 2
==============

- [Scope di Javascript](#scopeJavascript)
- [Function di Javascript](#function-javascript)
    - [Argumen Function](#argumen-Function)
    - [Default Parameter](#default-parameter)
    - [Function Helper](#function-helper)
    - [Arrow Function](#arrow-function)
- [Objek pada Javascript](#objek-pada-javascript)
- [Mengakses Properti Objek](#mengakses-propert-objek)
    - [Dot Notation](#dot-notation)
    - [Bracket Notation](#bracket-notation)
- [Objek Method](#object-method)
- [Array](#array)
- [Javasricpt Conditional](#javascript-conditional)
- [Perulangan (looping)](#perulangan-looping)
    - [For Loop](#for-loop)
    - [While loop](#while-loop)
    - [Do while loop](#do-while-loop)
- [Javascript HTML Dom](#javascript-html-dom)
    - [Cara Akses Element HTML](#cara-akses-element-html)

## Scope di Javascript
Scope adalah konsep dalam flow data variabel yang enentukan suatu variabel bisa diakses pada scope tertentu atau tidak. Analoginya seperti ini:
Kita semua bisa melihat bintang-bintang dilangit karena bumi bersifat global. Namun jika kita tinggal di Sumatera, kita tidak akan bisa melihat monas yang berada di jakarta. Monas bersifat local yaitu hanya berada di Jakarta. Jenis pada scope adalah :
1. Block scope adalah area yang dicakup oleh scope yang ada di dalam statement if-else atau looping, atau bisa juga kita sebut dengan block statement. 	
2. Global scope : variabel yang kita buat dapat diakses dimanapun dalam suatu file.
3. Local scope : variabel yang dideklarasikan di dalam suatu blok bisa berupa function-scoped atau block-scoped. 

## Function di Javascript
Function adalah sebuah blok kode dalam sebuah grup untuk menyelesaikan 1 task atau 1 fitur. Saat kita membutuhkan fitur tersebut nantinya, kita bisa kembali menggunakannya.

##### Argumen Funtion
Argumen adalah nilai yang digunakan saat memanggil function. Jumlah argumen harus sama dengan jumlah parameternya. Jadi jika di function penambahan ada 2 parameter nilai saat membuat function. Saat memanggil function kita gunakan 2 buah nilai argumen. contoh
```
function tambah (a,b){
    return tambah a+b
}
console.log(5,4) //output : 10
```

##### Default Parameter
Default paramaters digunakan untuk memberikan nilai awal/default pada parameter function. Default parameters bisa digunakan jika kita ingin menjaga function agar tidak error saat dipanggil tanpa argumen
```
Function panggilNama (nama = 'Avanger'){
    return 'Helo' + nama
}
console.log(panggilNama('Kapten')); //output : Hello Kapten
console.log(panggilNama()); //output : Hello Avanger
```
##### Function Helper
Function helper adalah function yang bisa kita gunakan dari funtion yang kita buat sebelumnya. Contoh
```
Function perkalian(angka){
    return angka *(9/5);
}
function getFahrenheit(celcius){
    return perkalian(angka) + 32
}

console.log(getFahrenheit(15)); //output : 15
```
##### Arrow Function
Arrow function adalah cara lain menuliskan function. Ini adalah fitur terbaru yang ada pada ES6 (Javascript Version)
```
const salam = () => {
    return 'Hello World';
}

const tambah = (a,b) => {
    return a+b;
}

```
### Objek pada Javascript
Di JavaScript, objek bisa digambarkan sebagai sesuatu yang memiliki properti dan nilai. Sebagai contoh, manusia. Manusia memiliki nama, pekerjaan, umur, dan lain sebagainya. Nah, kemudian kita tahu bahwa nama orang ini adalah Sarah, pekerjaannya adalah programmer, umurnya 24 tahun, dan lain-lain.
Dalam hal ini, manusia adalah objek. Kemudian nama, pekerjaan, umur adalah properti objek. Terakhir, Sarah adalah nilai dari properti nama, programmer adalah nilai dari properti pekerjaan, dan 24 tahun adalah nilai dari properti umur.
```
let orang = {
  nama: 'sarah',
  umur: 24,
  pekerjaan: 'programmer'
};
console.log(orang)
```
#### Mengakses Properti Objek

Jika kita ingin menggunakan nilai yang terdapat di dalam properti suatu objek, maka kita harus mengakses properti objek tersebut.
##### Dot Notation
```
let orang = {
  nama: 'sarah',
  umur: 24,
  pekerjaan: 'programmer'
};

console.log(orang.nama); // Output: "sarah"
console.log(orang.umur); // Output: 24
console.log(orang.pekerjaan); // Output: "programmer"
```
##### Bracket Notation
```
let orang = {
  nama: 'sarah',
  umur: 24,
  pekerjaan: 'programmer'
};

console.log(orang["nama"]); // Output: "sarah"
console.log(orang['umur']); // Output: 24
console.log(orang["pekerjaan"]); // Output: "programmer"
```
#### Object Method
Tipe data dari nilai sebuah properti itu tidak terbatas kepada string dan number saja. Kita juga bisa memberi nilai berupa sebuah fungsi. Fungsi yang terhubung pada sebuah objek kita sebut dengan istilah method. contohnya
```
let kalkulator = {
  namaOperasi: 'penjumlahan',
  jumlah: function(angka1, angka2) {
    return angka1 + angka2;
  }
};

console.log(kalkulator.jumlah(2, 3)); // Output: 5
```
### Array
Array adalah tipe variabel yang dapat menampung berbagai jenis data dengan tipe yang bermacam-macam, dengan jumlah yang tidak terbatas. Array di JavaScript memiliki ciri khas yaitu data yang ditampung dibungkus dengan sepasang kurung siku [ ]. Contoh 
```
// Menyimpan data di variabel satu-per-satu
let murid1 = 'Andi';
let murid2 = 'Ratna';
let murid3 = 'Juwita';

// Menyimpan lebih dari satu data dalam satu array
let murid = ['Andi', 'Ratna', 'Juwita'];
```
Pada contoh di atas, data yang kita miliki hanya berjumlah 3 buah. Bayangkan jika kita memiliki 1000 data! Pasti capek jika harus membuat 1000 variabel dalam satu waktu
Setiap data di array memiliki nomor index. Nomor index berguna untuk mengakses data suatu array di posisi tertentu. Nomor index di array selalu dimulai dari angka nol 0.

Gambar di bawah ini adalah ilustrasi nomor index di array:

![index array](https://skilvul-assets-01.s3-ap-southeast-1.amazonaws.com/lesson/intro-to-javascript/array-index.png)

#### JavaScript Conditional
Kalau diterjemahkan ke dalam bahasa Indonesia, conditional artinya adalah persyaratan. Lalu, kalau dalam konsep JavaScript, conditional itu kira-kira seperti apa? Di JavaScript ada dua cara menulis perintah conditional, yaitu:
- Menggunakan if, else if dan else.
- Menggunakan switch dan case.

contoh penulisan if, else if dan else

```
if (kondisi1) {
  // masukkan kode yang akan dijalankan di sini apabila kondisi1 tercapai
} else if (kondisi2) {
  // masukkan kode yang akan dijalankan di sini apabila kondisi1 tidak tercapai dan kondisi2 tercapai
} else if (kondisi3) {
  // masukkan kode yang akan dijalankan di sini apabila kondisi1 dan kondisi2 tidak tercapai, dan kondisi3 tercapai
} ... {
} else {
  // masukkan kode yang akan dijalankan di sini apabila semua kondisi di atas TIDAK tercapai
}
```
contoh penulisan switch dan case
```
switch (pernyataan) {
  case kondisi1:
    // keputusan yang dijalankan ketika kondisi1 tercapai
    break;
  case kondisi2:
    // keputusan yang dijalankan ketika kondisi2 tercapai
    break;
  case kondisi3:
    // keputusan yang dijalankan ketika kondisi3 tercapai
    break;
  ...
  default:
    // keputusan yang dijalankan ketika semua kondisi tidak tercapai
}
```
#### Perulangan (Looping)
##### for loop
```
for (pernyataan1; pernyataan2; pernyataan3) {
  // kode yang akan dijalankan ketika pernyataan2 benar (true)
}
```
Penjelasan kode di atas:

    pernyataan1 digunakan untuk menentukan nilai awal berjalannya loop.
    pernyataan2 digunakan untuk mendefinisikan kondisi berjalannya sebuah loop. Apabila nilai kondisinya false, maka loop akan berakhir.
    pernyataan3 digunakan untuk menambah atau mengurangi nilai awal pada pernyataan1 setiap kali loop dijalankan.

contoh penggunaannya
```
Kita akan menampilkan angka 1 sampai dengan 10 di console. 
for (let i = 1; i <= 5; i++) {
  console.log(i);
}

/*
Output:
1
2
3
4
5
*/
```
##### While Loop
```
while (kondisi) {
  // kode yang akan dijalankan ketika kondisi benar (true)
}
```
Penjelasan kode di atas:
- while (kondisi) berarti ketika kondisi yang ditentukan benar (true), maka jalankan semua kode yang ada di dalam { }.

contoh penggunaanya
```
let i = 1;

while (i <= 5) {
  console.log(i);
  i++;
}

/*
Output:
1
2
3
4
5
*/
```
##### Do While Loop
```
do {
  // kode yang akan dijalankan ketika kondisi benar (true)
} while (kondisi);
```
contoh penggunaan
```
let i = 1;

do {
  console.log(i);
  i++;
} while (i <= 5);

/*
Output:
1
2
3
4
5
*/
```
#### JavaScript HTML DOM
DOM adalah singkatan dari Document Object Model. Dengan adanya DOM ini, JavaScript diberi akses untuk membuat HTML menjadi dinamis, seperti:

    Mengubah element HTML pada halaman website.
    Mengubah attribute HTML pada halaman website.
    Mengubah CSS style pada halaman website.
    Menambah dan/atau menghapus element maupun attribute HTML.
    Menambah HTML event (contoh: efek klik pada mouse, hover pada mouse, dan lain-lain) pada halaman website.
    Berinteraksi dengan semua HTML event di website.

**Contoh Penggunaan**
Misalnya kita mempunyai element HTML sebagai berikut:
```
<input id="umur" type="text" value="20" />
```

Untuk mengakses value dari *input* di atas, maka bisa dilakukan dengan cara sebagai berikut:
```
let umur = document.getElementById("umur").value;

console.log(umur); // Output: 20
```
Penjelasan dari code diatas
- *document* adalah akar dari semua objek di sebuah website. Jadi untuk mengakses element HTML apapun di satu website, selalu dimulai dengan objek document ini.
- *getElementById* merupakan method dari objek document.
- *value* merupakan properti dari objek element HTML yang dikembalikan dari method *getElementById* yaitu *input*.

##### Cara Akses Element HTML
**1. getElementById(id)**
*getElementById* untuk mengakses element HTML berdasarkan nilai id-nya.

**2. getElementsByTagName(tag)**
Untuk mengakses element-element HTML berdasarkan jenis tag-nya, kita bisa menggunakan *getElementsByTagName*
contoh :
```
<!-- html -->
<h1 id="title">Hello, World!</h1>
<p>Selamat Datang di Skilvul</p>
<h1 class="subtitle">Mari Belajar JavaScript</h1>

let semuaTagH1 = document.getElementsByTagName("h1");

console.log(semuaTagH1[0]); // Output: <h1 id="title">Hello, World!</h1>
console.log(semuaTagH1[1]); // Output: <h1 class="subtitle">Mari Belajar JavaScript</h1>

```
Penjelasan
- Ketika kita memanggil document.getElementsByTagName("h1"), document sebagai akar objek dari halaman html kita akan mencari semua element *h1* di bawahnya.
- Karena di contoh di atas terdapat 2 *h1*, maka document.getElementsByTagName("h1") akan mengembalikan 2 element *h1*. Untuk mengakses masing-masing element, bisa menggunakan [noIndex], sama seperti cara Array mengakses elementnya.

**3. getElementsByClassName(className)**
Untuk mengakses element-element HTML berdasarkan nilai attribute class-nya, kita bisa menggunakan *getElementsByClassName*
contoh
```
<!-- html -->
<h1 class="header">Hello, World!</h1>
<p>Selamat Datang di Skilvul</p>
<span class="header">Mari Belajar JavaScript</span>

let semuaClassHeader = document.getElementsByClassName("header");

console.log(semuaClassHeader); // Output: HTMLCollection(2) [h1.header, span.header]
console.log(semuaClassHeader[0]); // Output: <h1 class="header">Hello, World!</h1>
console.log(semuaClassHeader[1]); // Output: <span class="header">Mari Belajar JavaScript</span>
```
**4. querySelectorAll(cssSelector)**
Untuk mengakses element-element HTML berdasarkan Selector-nya, kita bisa menggunakan querySelectorAll.
contoh
```
<!-- html -->
<h1 class="header">Hello, World!</h1>
<p id="header2">Selamat Datang di Skilvul</p>
<span class="header">Mari Belajar JavaScript</span>

let h1ClassHeader = document.querySelectorAll('h1.header');

console.log(h1ClassHeader); // Output: NodeList [h1.header]
console.log(h1ClassHeader[0]); // Output: <h1 class="header">Hello, World!</h1>

let idHeader2 = document.querySelectorAll('#header2');

console.log(idHeader2); // Output: NodeList [p#header2]
console.log(idHeader2[0]); // Output: <p id="header2">Selamat Datang di Skilvul</p>
```
Penjelasan kode di atas:

Ketika kita memanggil *document.querySelectorAll("h1.header")*, document sebagai akar objek dari halaman html kita akan mencari semua element *h1* dengan attribute class bernilai header di bawahnya. Begitu juga ketika memanggil *document.querySelectorAll('#header2')*, document akan mencari semua element dengan id bernilai header2 di bawahnya.

