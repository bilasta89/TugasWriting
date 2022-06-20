# Joyfull Jasper Week 3

# Javascript Lanjutan

## Modules

Modules adalah _reusable code_ yang dapat di export dari suatu file javascript dan di import ke file javascript yang lain. _Reusable code_ disini adalah data yang dapat di gunakan berulang kali. Untuk bisa menghubungkan file antar JavaScript kita bisa menggunakan _export_ dan _import_ sehingga memungkinkan untuk saling menggunakan kode antar module.

### Export

Export digunakan untuk meng-export variabel pada file JavaScript. Penggunaan export diawali dengan kata kunci _export_ kemudian diikuti oleh nama variabel yang ingin di-export atau bisa digunakan di akhir kode kita, dengan nama variabel yang ingin di export.
**Contoh**

```
//greet.js
export default function greet(user) {
  alert(`hi ${user}`);
}

//user.js
const user = {
  no1: "Baharudin",
  no2: "Arrie",
 };

export { user as userNew };
```

### Import

Import diibaratkan sebagai pasangan dari export. Jadi import digunakan untuk menggunakan variabel yang sudah di-export dari module lainnya.

**Contoh**

```
//import.js
import greet from "./greet.js";
import { userNew } from "./user.js";
```

## Rekrusif

Recursive adalah function yang memanggil dirinya sendiri sampai kondisi tertentu. Recursive kebanyakan digunakan untuk case matematika, fisika, kimia, dan yang berhubungan dengan calculation.
**contoh**

```

function countDown(number) {
console.log("number rekursif", number);
let nextNumber = number - 1;

if (nextNumber > 0) {
countDown(nextNumber);
    }
}
countDown(5);

```

## Web Storage

### Local Storage

#### Menyimpan Data

Local storage memiliki karakteristik sebagai berikut:

1. Menyimpan data tanpa tanggal kadaluarsa.
2. Data tidak akan dihapus ketika web browser ditutup dan akan tersedia seterusnya selama kita tidak menghapus data local storage pada web browser.
3. Dapat menyimpan data hingga 5MB.
4. Hanya dapat menyimpan data string.

```
localStorage.setItem('key', value);
```

#### Mengambil Data

Untuk mengambil data yang telah tersimpan pada local storage, kita dapat menggunakan method getItem() yang membutuhkan 1 parameter. Parameter tersebut adalah key dari data yang kita inginkan.

```
localStorage.getItem('key');
```

#### Menghapus Data

Untuk menghapus data yang telah tersimpan pada local storage, kita dapat menggunakan method removeItem() yang membutuhkan 1 parameter. Parameter tersebut adalah key dari data yang ingin kita hapus.

```
// menghapus key tertentu
localStorage.removeItem("key");

// menghapus semua key
localStorage.clear();
```

### Session Storage

Data yang tersimpan pada session storage akan hilang ketika session dari sebuah laman berakhir.

#### Menyimpan data

```
sessionStorage.setItem('key', value);
```

#### Mengambil data

```
sessionStorage.getItem('key');
```

#### Menghapus data

```
/ menghapus session storage satu persatu berdasarkan key
sessionStorage.removeItem('key');

// menghapus seluruh session storage sekaligus
sessionStorage.clear();
```

Contoh Penggunaan Local Storage dalam pembuatan form login.

```
<!--index.html--->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h1>Login</h1>
    username<input type="text" placeholder="enter your username" id="username"/>
    Password<input type="password" placeholder="enter your password" id="password"/>
    <div>
    <button onclick="save()">save your username to local storage</button>
    <script src="./index.js"></script>
</body>
</html>
```

```
//index.js
const save = () => {
    const usernameInput = document.querySelector("#username").value;
    const passInput = document.querySelector("#password").value;
    console.log("button click",usernameInput);

const data = () => {
    username = usernameInput;
    password = passInput;
}

const dataJSON = JSON.stringify(data);//mengubah array menjadi string
console.log(dataJSON);
localStorage.setItem("username",usernameInput);
localStorage.setItem("password",passInput);

}

const get = () => {
    const dataJSON = localStorage.getItem("data");
    console.log(dataJSON);

    const data = JSON.parse(dataJSON);//mengubah string menjadi bentuk array.
    console.log(data);
}
```

## Javascript Asynchronous

JavaScript termasuk ke dalam single-thread language atau synchronous yang artinya hanya dapat mengeksekusi satu perintah pada satu waktu dan harus menunggu satu perintah tersebut selesai sebelum melanjutkan perintah selanjutnya.

```
console.log("antrian 1");
console.log("antrian 2");
console.log("antrian 3");

// output
// antrian 1
// antrian 2
// antrian 3
```

### Asynchronous

Asynchronous yang biasa dikenal juga dengan sebutan non-blocking mengizinkan komputer kita untuk memproses perintah lain sambil menunggu suatu proses lain yang sedang berlangsung. Ini artinya kita bisa melakukan lebih dari 1 proses sekaligus (multi-thread). Untuk mengatasi masalah tersebut, kita dapat menggunakan:

1. Callback
   Callback adalah sebuah function, namun bedanya dengan function pada umumnya adalah pada cara eksekusinya. Jika function pada umumnya dieksekusi secara langsung, sedangkan callback dieksekusi di dalam function lain melalui parameter.

```
const p1 = () => {
  console.log("proses 1");
};

const p2 = () => {
  setTimeout(() => {
    console.log("proses 2");
  }, 5000);
};

const p3 = () => {
  p1();
  p2();
  console.log("proses 3");
};

p3();

// 1000 ms = 1 second
```

2. Promises
   Promise sesuai dengan artinya adalah janji. Pada promise analogi di atas bisa diartikan seperti:

- _Pending_, jika data sedang diproses.
- _Fulfilled_, jika data telah berhasil didapatkan.
- _Rejected_, jika data gagal didapatkan.
  **Contohnya**

```
const condition = true;

let newPromise = new Promise((resolve, reject) => {
  if (condition) {
    // apa yang dilakukan jika promise 'fulfilled'
    resolve("Berhasil");
  } else {
    // apa yang dilakukan jika promise 'rejected'
    reject(new Error("Error Gagal"));
  }
});

newPromise.then((result) => {
  console.log(result); // Output: "Berhasil"
});
```

3. Async / Await.
   Async adalah salah satu fitur baru dari javascript yang digunakan untuk menangani hasil dari sebuah Promise. Sedangkan await berfungsi untuk menunda sebuah kode dijalankan sampai proses asynchronous berhasil.

4. Fetch
   Fetch adalah native web API untuk melakukan HTTP calls dari external network.

```
let listOfFlags = document.getElementById("list-flags");

const getFlags = async () => {
  const url = "https://restcountries.com/v2/all"; //fetch

  const respons = await fetch(url); //async await
  const result = await respons.json();//async await

  result.forEach((item) => {
    listOfFlags.innerHTML +=
    `<div>
        <img src="${item.flags.svg}" alt="" width="100">
        <h3>${item.name}</h3>
      </div>
    `;
  });

  console.log(result);
};

getFlags();
```

## Responsive Web Design (RWD)

RWD bertujuan membuat website kita dapat diakse dalam device apapun, device yang umumnya digunakan adalah laptop/pc, smartphone dan tablet.

## Bootstrap

Bootstrap adalah framework open-source khusus front end yang awalnya dibuat oleh Mark Otto dan Jacob Thornton untuk mempermudah dan mempercepat pengembangan web di front end. Bootstrap memiliki semua jenis HTML dan template desain berbasis CSS untuk berbagai fungsi dan komponen, seperti navigasi, sistem grid, carousel gambar, dan tombol (button).

```
<!doctype html>
<html lang="en">
  <head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">

    <title>Hello, world!</title>
  </head>
  <body>
    <h1>Hello, world!</h1>

    <!-- Optional JavaScript; choose one of the two! -->

    <!-- Option 1: Bootstrap Bundle with Popper -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.bundle.min.js" integrity="sha384-MrcW6ZMFYlzcLA8Nl+NtUVF0sA7MsXsP1UyJoMp4YLEuNSfAP+JcXn/tWtIaxVXM" crossorigin="anonymous"></script>

    <!-- Option 2: Separate Popper and Bootstrap JS -->
    <!--
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.9.2/dist/umd/popper.min.js" integrity="sha384-IQsoLXl5PILFhosVNubq5LC7Qb9DXgDA9i+tQ8Zj3iwWAwPtgFTxbJ8NT4GN1R8p" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.min.js" integrity="sha384-cVKIPhGWiC2Al4u+LWgxfKTRIcfu0JTxR+EQDz/bgldoEyl4H0zUF0QKbrJ0EcQF" crossorigin="anonymous"></script>
    -->
  </body>
```
