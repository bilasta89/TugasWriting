# Joyfull Jasper Week 5

# React JS

## Introduction React JS

React JS dibuat oleh Tim Engineer Facebook untuk sisi front-end. React JS membuat aplikasi front-end menjadi lebih cepat walaupun harus menghandle berbagai data. Di React JS dapat menerapkan konsep modular dimana dapat membagi 1 tampilan pada website menjadi komponen-komponen kecil

## Instalasi React JS

Download Node js, dianjurkan download versi LTS (Long Term Support)

<https://nodejs.org/en/>

### Penggunaan React JS

Membuat project di React JS

```
npx create-react-app nama_folder
cd nama_folder
npm run start / npm start
```

## Element React JS

### JSX

JSX adalah syntax extension Javascript, dikembangkan untuk digunakan pada React JS, setiap JSX hanya bisa memiliki 1 parent element.
![Contoh double parent](/asset/jsx%20element.jpg)
![Error double parent](/asset/error-jsx.jpg)

### Virtual DOM

- Duplikasi dari real DOM yang sebenarnya,
- Jika kita memiliki 2 komponen UI dalam 1 page, kita dapat mengupdate data pada 1 komponen, maka React JS hanya melakukan render ulang pada komponen tersebut.

### class dan className

![Class di React](/asset/classname%20JS.jpg)

### Curly Braces di JSX

![Curly braces](/asset/curly-braces.jpg)

- ouput : 5

### Variable di JSX

![Variable di JSX](/asset/varible-jsx.jpg)
- Output :
- John Doe
- john doe

### Atribute di JSX

![Atribute di JSX](/asset/atribute-jsx.jpg)
- output

![output](/asset/output.jpg)

### Event di JSX

![Event di JSX](/asset/event-JSX.jpg)

### Conditional di JSX

<https://reactjs.org/docs/conditional-rendering.html>

### .map()

<https://reactjs.org/docs/lists-and-keys.html>

## React Component

- Component adalah salah satu core dari react JS
- Componet membagi UI dalam satuan kecil yang artinya dalam 1 page ada beberapa component yang bisa kita buat
- ada 2 cara untuk membuat component yaitu dengan Function dan Class

### Create Projek component dengan React JS

ekspetasi output :
![ekspetasi output](/asset/ekspetasiOutput.jpg)

- Langkah 1 - Buat Project Baru

```
npx create-react-app nama_folder
cd nama_folder
npm run start / npm start
```

- Langkah 2 - Buat Folder components
  kita akan membuat 3 component yaitu : Course, ProfileImage, StudentDetails
  note : untuk nama Folder, file dan function components HARUS menggunakan huruf besar diawal dan kata selanjutnya
  ![components](/asset/components.jpg)

**Folder StudentDetails**

- StudentDetails.js
  ![student](/asset/studenDetails.jpg)

**Profile image**

- file ProfileImage.js
  ![profile-image](/asset/profile-image.jpg)

**Folder Course**
isi : Course.js dan CourseCard.js
![course](/asset/course.jpg)

**File Apps.js**
![App](/asset/apps-js.jpg)

**Output**
![Output](/asset/output-akhir.jpg)

## State di React JS

- State adalah data yang dimiliki oleh sebuah komponen (statefull component) dan ada kemungkinan datanya dapat berubah.
- Membuat state membutuhkan **useState()**
- useState : fitur yang di gunakan untuk membuat state dalam functional component
  ![useState](/asset/useState1.jpg)

## React Router

proses pemetaan antara sebuah URL ke dalam sebuah halaman yang terdapat konten / UI (User Interface) sesuai dengan URL yang dituju.

- Instalasi Router

```
$ npm install react-router-dom@6
```

- Penggunaan Router

```
import { BrowserRouter } from "react-router-dom";
```

- Untuk Berpindah halaman bisa menggunakan perintah berikut

```
import * as React from "react";
import { Routes, Route, Link } from "react-router-dom";
import "./App.css";

function App() {
  return (
    <div className="App">
      <h1>Welcome to React Router!</h1>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="about" element={<About />} />
      </Routes>
    </div>
  );
}
```

- Info lebih lanjut Router JS
  <https://reactrouter.com/docs/en/v6/getting-started/installation#basic-installation>
