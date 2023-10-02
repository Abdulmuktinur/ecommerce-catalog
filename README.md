# Ecommerce Catalog

Project ini dibuat untuk menyelesaikan program Project-Based Virtual Intern : Front End Developer Core Initiative x Rakamin Academy.

## Soal 
Pada task terakhir VIX Front End Core Initiative ini, kalian diberikan tugas untuk membentuk sebuah interface dari sebuah website Ecommerce. Kalian ditugaskan untuk membuat dua halaman yaitu men’s clothing dan women’s clothing. Pada task ini, kalian akan bekerja dengan tim UI UX dan juga tim Backend, sehingga website yang akan kalian bangun telah memiliki komponen design juga code API nya.

## Tugas
Tugas kalian adalah membentuk tampilan website, dengan ketentuan :
1. Menampilkan data yang didapat dari API https://fakestoreapi.com dengan index merupakan angka
1-20 yang di tiap index-nya memiliki kategori yang berbeda, misalnya
https://fakestoreapi.com/products/1 yang memiliki kategori men’s clothing
2. Produk yang ditampilkan hanya 1, namun akan berubah setiap kali user menekan tombol Next
Product
3. Sediakan loading element/loader yang akan ditampilkan ketika menunggu balasan dari API sehingga
desain tetap UX friendly. Loader bisa berupa spinner
(https://www.w3schools.com/howto/howto_css_loader.asp) atau skeleton
(https://dev.to/devggaurav/build-a-simple-card-skeleton-loader-component-using-html-andcss-3a20)
4. Membentuk tiga halaman website sesuai dengan desain yang telah di sediakan di Figma [berikut ini](https://www.figma.com/file/x1bkO3alpmGQFtysh9Lmn7/Task-5-Ecommerce?node-id=0%3A1)
   
## Struktur Folder
```
📦 ecommerce
├─ node_modules
├─ public
├─ src
│  ├─ assets
│  │  ├─ style
│  │  │  └─ page.css
│  │  └─ image
│  │     ├─ bg-shape.svg
│  │     └─ bg-unavailable-product.svg
│  ├─ components
│  │  └─ ProductDisplay.vue
│  ├─ App.vue
│  └─ main.js
├─ .gitignore
├─ babel.config.js
├─ deploy.sh
├─ jsconfig.json
├─ package-lock.json
├─ package.json
├─ README.md
└─ vue.config.js
```
## Instalasi
```npm install``` -- install npm package

```npm run serve`` -- menjalankan project

```npm run build``` -- membuild project

## Deploy in Github Pages
```
#!/usr/bin/env sh

# abort on errors
set -e

# build
npm run build

# navigate into the build output directory
cd dist

git init
git add -A
git commit -m 'deploy'

git push -f git@github.com:Abdulmuktinur/ecommerce-catalog.git master:deploy

cd -
```

## TODO LIST
- [x] Desktop Version
- [x] Menampilkan 20 Data
- [x] Membuat loading menunggu balasan dari API
- [x] Menampilkan data berdasarkan kategori men's clothing dan women's clothing
- [ ] Responsive to mobile
- [ ] login page
- [ ] home page
- [ ] Keranjang
