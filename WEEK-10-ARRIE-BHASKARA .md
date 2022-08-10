# Joyfull Jasper Week 10

# Backend Dev

## Authentication, Authorization, Encryption

### Authentication / Autentifikasi

- Sebuah metode untuk memeriksa kebenaran identitas pengakses data secara autentik.
- Proses validasi atau pembuktian identitas terhadap pengguna yang ingin mengakses suatu file, aplikasi, atau sistem tertentu.

### Jenis-Jenis Autentikasi

**1. Single Factor Authentication**

- Jenis autentikasi yang meminta pengguna untuk memasukkan ID pengguna. Kemudian proses autentikasi pun akan berjalan dengan meminta pengguna untuk memasukkan password yang tepat dan sesuai dengan ID pengguna.

**2. Multi Factor Authentication**

- jenis autentikasi yang mewajibkan pengguna untuk memverifikasi tiga jenis identitas, misalnya ID pengguna, sidik jari/wajah, dan beberapa pertanyaan yang berhubungan dengan pengguna.

### Authorization / otorisasi

- Merupakan suatu batasan untuk mengakses bagian menu tertentu pada sistem informasi elektronik, proses ini terjadi setelah proses otentikasi. Yang mana identitas pengguna akan terjamin sebelum daftar akses pengguna dengan mencari entri pada tabel serta database.

### Encryption

- Proses teknis yang mengonversikan informasi menjadi kode rahasia, sehingga mengaburkan data yang Anda kirim, terima, atau simpan.

### Jenis-jenis Enkripsi

**1. Symmetric encryption**
Enkripsi yang terkait atau identik digunakan baik untuk proses enkripsi maupun dekripsi. Dalam beberapa kalangan, kunci yang dibagikan disebut sebagai "rahasia bersama", karena pengirim/sistem yang memantau enkripsi harus membagikan Kunci ini kepada siapa pun yang berwenang mendekripsi pesan.

**2. Asymmetric encryption**
Disebut juga sebagai enkripsi kunci publik, berbagai kunci digunakan untuk proses enkripsi dan dekripsi. Satu kunci dibagikan secara publik dan dapat digunakan oleh siapa pun (maka disebut "enkripsi kunci publik"), sementara yang satu lagi adalah kunci pribadi. Hal ini membuat sistem kunci asimetris menjadi lebih aman daripada algoritme kunci simetris, karena peretas atau penjahat cyber tidak dapat menyalin kunci saat dikirimkan.

### Session VS Cookie VS LocalStorage

![CLS](asset/01-cookies-local-session-storage.jpg)

### Token Based Authentication using JWT

Seperti namanya, JSON Web Token, yang berarti token ini menggunakan JSON (Javascript Object Notation), lalu token ini memungkinkan kita untuk mengirimkan data yang dapat diverifikasi oleh dua pihak atau lebih.

### Components of a JWT

#### Header

- Bagian pertama disebut dengan header. Header berisi informasi tentang algoritma dan jenis token yang digunakan.
- string yang di-encode menggunakan base64. Jadi kita bisa mendapatkan nilai asli dari teks tersebut dengan men-decodenya.

```
{
    "alg":"HS256",
    "typ":"JWT"
}
```

#### Payload

- Payload berisi data yang ingin dikirim melalui token.

```
{"nama":"Bhaskara"}
```

#### Signature

Signature adalah hash gabungan dari header, payload dan sebuah secret key (berupa string random panjang biasanya):

![JWT](asset/01-jwt.jpg)

## Sequelize

- Sequelize adalah ORM (Object Relational Mapping) Node JS yang berbasis promise. Sequelize mendukung sebagian besar relational Database seperti MySQL, PostgresQL, MariaDB, SQLite dan Miscrosoft SQL Server.

- Dengan fitur fitur di Sequelize, kita bisa mengelola dan mengatur data di database kita dengan cepat, dan efisien.

![ORM](asset/01-ORM.jpg)

### Penggunaan Sequelize

#### Instalasi Sequelize

```
npm init -y // utk create project pertama
npm install express mysql2 sequelize dotenv cors
```

Dan terakhir kita instal nodemon utk auto-reload servernya

```
npm install --save-dave nodemon
```

### Seting di Sequelize

**1. Setting Package.json**

```
{
  "name": "32-sequelize",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "dev": "nodemon index.js" // setting nodemon
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "cors": "^2.8.5",
    "dotenv": "^16.0.1",
    "express": "^4.18.1",
    "mysql2": "^2.3.3",
    "sequelize": "^6.21.3"
  },
  "devDependencies": {
    "nodemon": "^2.0.19"
  }
}
```

Hasil dari package.json yang di-create

**2. Setting Database**

- Database yang di pakai adalah MySQL - pastikan user dan password login ke MySQL benar.

- buat folder bernama **Config** dan save file dengan **dbConnection.js**

```
require("dotenv").config();
const { Sequelize } = require("sequelize");

const host = process.env.HOST || "localhost";

const sequelize = new Sequelize({
  database: process.env.DATABASE_NAME || "sekolah",
  username: process.env.DATABASE_USERNAME || "admin123",
  password: process.env.DATABASE_PASSWORD || "admin123",
  dialect: "mysql",
  host,
});

module.exports = sequelize;

```

- create folder models yg berisi file UserModel.js untuk sinkronisasi database pada user

```
const { Sequelize, DataTypes } = require("sequelize");
const sequelize = require("../config/dbConnection");

const UserModel = sequelize.define(
  "user",
  {
    name: {
      type: DataTypes.STRING,
    },
    email: DataTypes.STRING,
    birth_date: DataTypes.DATE,

  },
  {
    timestamps: true,
    createdAt: false,
    updatedAt: false,
  }
);

module.exports = UserModel;

```

**3. Eksekusi Program**
buat file index.js untuk mengeksekusi konesi databasenya

```
const express = require("express");
const app = express();

const sequelize = require("./config/dbConnection");
const UserModel = require("./models/UserModel");
const router = require("./routes");

const PORT = process.env.PORT || 8000;

app.use(express.json());

async function testConnection() {
  try {
    await sequelize.authenticate();
    console.log("sukses");

    await UserModel.sync({ alter: true });
  } catch (error) {
    console.log("error", error);
  }
}

testConnection();

app.use(router);

app.listen(PORT, () => {
  console.log("tes koneksi port", PORT);
});

```

**4. Buat Controler**
buat folder controller lalu buat file UserController.js untuk membedakan antara user dan modelnya.

```
const UserModel = require("../models/UserModel");

module.exports = {
  getAllUser: async (req, res) => {
    const users = await UserModel.findAll();

    res.json({
      message: "sukses ambil data",
      data: users,
    });
  },
};
```

**5. Buat Rute**
Buat folder Route yang isinya index.js, untuk menampung rute-rute aplikasi yang ingin di buat

```
const express = require("express");
const router = express.Router();

router.get("/", (req, res) => {
  res.json({
    message: "sekolah app",
  });
});

// route untuk user
router.use("/user", userRouter);

module.exports = router;

```

## MongoDB

- MongoDB adalah salah satu produk database noSQL Open Source yang menggunakan struktur data JSON untuk menyimpan datanya.
- MongoDB sering dipakai untuk aplikasi berbasis Cloud, Grid Computing, atau Big Data.

### Instalasi MongoDB

https://docs.mongodb.com/manual/administration/install-community/

### MongoDB GUI Tools

untuk menggunakan MongoDB, kita bisa menggunakan MongoDB Compass UI untuk mengexplore DB yang ingin kita buat.

https://www.mongodb.com/products/compass

### MongoDB Atlas

Selain menggunakan Mongo compass, kita juga bisa menggunakan management tool / admin UI versi cloudnya. kita bisa menggunakan MongoDB atlas.

https://www.mongodb.com/cloud/atlas

## Mongoose

- Library yang bisa dibilang sebagai Object Modelling MongoDB untuk NodeJS.
- Mongoose bisa digunakan untuk mengelola hubungan antara data, menyediakan validasi.
- digunakan untuk menerjemahkan antara objek dalam kode dan representasi Objek tersebut di MongoDB.

https://mongoosejs.com/docs/index.html

### Connect NodeJS and MongoDB

- Install dotenv untuk menampung variabel environment database. Dan juga install MongoDB

```
npm install dotenv
npm install mongodb
```

- Buat satu file .env untuk menyimpan variabel database

```
DATABASE_MONGODBATLAS = mongodb+srv://skilvul:skilvul123@cluster0.t7ybq.mongodb.net/?retryWrites=true&w=majority
```

- Membuat file untuk membuat koneksi, dan interaksi dengan database langsung.

```
require("dotenv").config();

const mongoose = require("mongoose");

const url = process.env.DATABASE_MONGODBATLAS || "localhost";

const dbConnection = mongoose.connect(url);

module.exports = dbConnection;
```

### Penggunaan Mongoose

**1 Instalasi**
Pastikan NodeJS dan MongoDB juga sudah terinstall.

```
npm install mongoose
```

**2 Buat Koneksi**

- Buat file koneksinya dengan folder **config** yang berisi file **dbConnection.js**

```
require("dotenv").config();

const mongoose = require("mongoose");

const url = process.env.DATABASE_MONGODBATLAS || "localhost";

const dbConnection = mongoose.connect(url);

module.exports = dbConnection;
```

- Membuat koneksi dengan menggunakan MongoDB database, yang diletakkan di .env

```
DATABASE_MONGODBATLAS = mongodb+srv://skilvul:skilvul123@cluster0.t7ybq.mongodb.net/?retryWrites=true&w=majority

```

**3 Definisikan Schema DB**
dari code dibawah ini kita dapat mendefinisikan Skema dan tipe data untuk setiap field yang akan digunakan.

```
const mongoose = require("mongoose");

// buat schema models

const UserSchema = new mongoose.Schema({
  name: {
    type: String,
    require: true,
  },
  email: {
    type: String,
  },
  telephoneNumber: {
    type: String,
  },
});

const UserModel = mongoose.model("user", UserSchema);

module.exports = UserModel;
```

## Deploy aplikasi backend di HEROKU

- Register / sign up terlebih dahulu di website heroku

https://www.heroku.com/

- pastikan code aplikasi yang kita sudah di upload pada repostory github kita. kemudian repostory nya kita konesikan

![deploy](asset/01-heroku.jpg)

- Pilih enable automatic deploys untuk memproses deploy otomatis apabila codingan kita ada perubahan.
- Pilih branch untuk memilih branch mana yang ingin kita deploy

![deploy](asset/02-heroku.jpg)

- pilih menu more -> view logs untuk melihat status deploy aplikasi

![deploy](asset/03-heroku.jpg)

- jika sudah sukses terdeploy, kita open app untuk melihat aplikasi yang sudah terdeploy

![deploy](asset/04-heroku.jpg)
