# Tailwind CSS basic learning

- [Tailwind CSS basic learning](#tailwind-css-basic-learning)
  - [Installation](#installation)
  - [Folder Directories](#folder-directories)
  - [Extention for VS code Studio](#extention-for-vs-code-studio)
  - [Use NPM for auto script `--watch`](#use-npm-for-auto-script---watch)
  - [Tailwind Utility](#tailwind-utility)
  - [Spacing](#spacing)
    - [Margin](#margin)
    - [Padding](#padding)
    - [Space Between](#space-between)
  - [Sizing](#sizing)
    - [Width](#width)
    - [Height](#height)
    - [Max min Height and Width](#max-min-height-and-width)
  - [Typography](#typography)
    - [Font Family](#font-family)
    - [Text Color](#text-color)
  - [Background](#background)
    - [background Attachment](#background-attachment)
    - [Background Size](#background-size)
    - [background Repeat](#background-repeat)
    - [Background Position](#background-position)
    - [Images](#images)
  - [Border](#border)
    - [Divide](#divide)
    - [Outline](#outline)
    - [Ring](#ring)
  - [Effect](#effect)
    - [Box Shadow](#box-shadow)
    - [Box Shadow Color](#box-shadow-color)
    - [Opacity](#opacity)
    - [Mix Blend Mode](#mix-blend-mode)
  - [Filter](#filter)
    - [Blur](#blur)
    - [Backdrop blur](#backdrop-blur)
  - [PseudoClass](#pseudoclass)
    - [Group styling Pseudoclass](#group-styling-pseudoclass)
    - [after: Pseudoclass](#after-pseudoclass)
    - [invalid: Pseudo](#invalid-pseudo)
  - [Dark Mode](#dark-mode)
  - [Transform](#transform)
    - [Scale](#scale)
    - [Rotate](#rotate)
  - [Transition](#transition)
  - [Layouting](#layouting)
    - [Container](#container)
    - [Float](#float)
    - [position](#position)
    - [Column](#column)
  - [Responsive Design](#responsive-design)
  - [Flex](#flex)
    - [Display Flex](#display-flex)
  - [Grid](#grid)

## Installation

for basic intallation you can visit at [Tailwindcss.com](https://tailwindcss.com). but in this documentation i use tutorial from youtube [Dave Gray](https://www.youtube.com/watch?v=lCxcTsOHrjo&list=PPSV). maybe soon i will update documentation from other resource.
for easiest way, i use `Live Server` extention from Visual Studio Code, and enable `Full Reload`. and you can install `tailwindconfog.js` use this command. If you use **Node ver.16 up** you ***should not have to install*** `postcss` and `autoprefixer`. just `npm install tailwindcss` its automatically install all dependancies like `postcss` and `autoprefixer`.

```bash
npx tailwindcss init
```

after that you can make directory `build` and `src` in root directory. this is folder structure is

```html
_root
|__/build
|____/index.html
|__/src
|____/input.css
|__tailwindcss.config.json
```

on `tailwind.config.js` file set the content setting

```javascript
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    './build/*.html'
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

and on `./src/input.css` add this code

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

and for compile tailwind css you can use this command

```bash
npx tailwindcss -i ./src/input.css -o ./build/css/style.css
```

and if you want to compile during writing a code you can use

```bash
npx tailwindcss -i ./src/input.css -o ./build/css/style.css --watch
```

## Folder Directories

```html
_root
|__/build
|____/index.html
|__/src
|____/input.css
|__tailwindcss.config.json
```

## Extention for VS code Studio

- `Live Server` for browser
- `Tailwind CSS Intellisense` for tailwind css type class
- `inline fold` for folding class, it make easier to maintain tailwind code
- `prettier-plugin tailwind` for resturctured tailwind code

you can isntall with npm

```npm
npm install --save-dev prettier
```

and then make a file `.prettierrc` and paste this code

```json
{
  "semi": false,
  "singleQuote": true,
  "trailingComma": "es5",
  "arrowParens": "avoid",
  "printWidth": 80
}
```

and integration with VS code with isntall plugin `Prettier - Code Formatter`. for manual formatter you can run

```npm
npx prettier --write <file or folder>"
```

example

```npm
npx prettier --write "./build/*.html
```

## Use NPM for auto script `--watch`

you can use NPM for automated compile, if you always type `npx tailwindcss` its too wasted times for using auto compile. you can NPM to manage it

```npm
npm init -y
```

now you can setting in `package.json` file this code

```json
"scripts": {
    "watch": "npx tailwindcss -i ./src/input.css -o ./build/css/style.css --watch"
  },
```

if you run `npm run watch` this also run script in `watch`

## Tailwind Utility

try to documentated utility tailwind

## Spacing

spacing in tailwind it is `margin` `padding` `spaceBetween`

### Margin

Margin is a jarak from element to outer element

- `mx` margin untuk sumbu x, secara horizontal atau kanan dan kiri
- `my` margin untuk sumbu y, secara vertikal atau atas bawah
- `m-auto` untuk membuat element ke tengah, digunakan ketika parent nya mempunyai display `flex`.
- `mx-auto` untuk membuat element berada di tengah, tetapi hanya untuk element yang displaynya `block`

satuan dalam `margin` `padding` `spaceBetween` `m-1` sama dengan 0,25 rem atau 4px

```css
m-1 = 0.25rem = 4px
m-4 = 1 rem = 16px
```

for more information about spacing you can see at [Tailwind CSS Spacing Costumization](https://tailwindcss.com/customizing-spacing)

### Padding

padding it is almost same with [Margin](#margin), bedanya padding tidak memiliki **nilai - dan auto**. pada saat kita menambahkan padding, otomatis kita akan menambahkan lebar pada element nya

### Space Between

`space between` depends on `flex`. it mean if you use `spacebetween` you should declare `flex`.

- `space-x` will add `margin-left` and `margin-right`
- `space-y` will add `margin-top` and `margin-bottom`

## Sizing

sizing in tailwind is `width and height`

### Width

untuk width hitungannya sama dengan [Margin](#margin), untuk `w-4` berarti `1rem`. `w-px` berarti `1px`

### Height

hal yang sama juga berlaku untuk height

### Max min Height and Width

`max-width or height` it a maximal with ukurannya. misal untuk `max-w-xs` berarti `max-width : 20rem` maka lebar maksimalnya hanya 20 rem atau 320px

## Typography

for more visit [TailwindCSS.com](https://tailwindcss.com)

### Font Family

untuk mengubah jenis font di tailwind kita bisa melakukannya dengan mengubah `tailwind.config.js` :

```javascript
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ['./build/*.html'],
  theme: {
    extend: {
      fontFamily : {

      }
    },
  },
  plugins: [],
}
```

### Text Color

jika mau menambahkan gradient ke text, bisa menggunakan `<span>` untuk kemudian menambahkan class `bg-gradient bg-clip-text text-transparent`

## Background

Tips : jika ingin mengambil gambar dari source unsplash bisa menggunakan link `https://source.unsplash.com/dimensi?kategori`

### background Attachment

untuk membuat background gambar bergerak ketika di scroll atau yang lain dengan catatan gambarnya di attach pada `div` menggunakan `style` dan pada saat menggunakan `background-image : url()` langsung saja di masukan link nya tanpa harus menggunakan tanda petik, atributnya ada.

- `bg-scroll` hanya di scroll tulisannya atau content di dalamnya saja
- `bg-local` akan di scroll bersamaan dengan gambar
- `bg-fix` jika kita scroll di dalam content maka hanya tulisan di dalam contentnya saja, jika di luar content maka akan menimbulkan efek parallax. *pada saat menggunakan background attachment overflow nya harus* `auto`

### Background Size

bagaimana cara kita mengatur ukuran background terhadap pembungkusnya atau parent nya

- `bg-auto` size otomatis
- `bg-cover` size memenuhi konten
- `bg-contain` size hanya memenuhi salah satunya saja, jika tingginya sudah memenuhi maka cukup. tanpa melakukan crop atau yang lainnya.

### background Repeat

untuk mengulang gambar, jika konten gambar tidak terpenuhi. jika anda menggunakan `bg-cover` anda tidak harus menggunakan `bg-repeat`

- `bg-repeat` untuk mengulang gambar
- `bg-no-repeat` untuk tidak melakukan perulangan gambar

### Background Position

untuk mengatur posisi gambar yang kontennya tidak terpenuhi, bisa geser ke atas bawah kiri kanan.

### Images

untuk mengatur gambar kamu bisa menggunakan `object-cover` untuk gambar jika `scretch` atau melebar. dan gunakan `object-top` untuk mengambil gambar posisi atas

## Border

untuk membuat garis pada suatu element seperti border-radius

### Divide

untuk membuat garis pembatas element, aslinya dari border, tetapi tailwind membuat element tersendiri untuk memudahkan.

### Outline

garis boder yang biasanya di buat untuk tombol.

### Ring

bayangan dari shadow nya / mock shadow dari border

## Effect

### Box Shadow

Kita bisa memberikan bayangan ke sebuah element

- `shadow-md`
- `shadow-xl`
- `shadow-lg`

### Box Shadow Color

untuk memberikan warna ke box-shadow

### Opacity

untuk menambahkan transparansi pada elemen kita

### Mix Blend Mode

menambahkan dan mencampurkan gambar background dengan foreground(gambar di depannya)

## Filter

### Blur

memberikan blur ke suatu object

### Backdrop blur

membuat blur element di depan background untuk `glassmorpishm`

## PseudoClass

untuk pseudoclass lebih lengkapnya bisa di lihat di halaman website [Pseudoclass](https://tailwindcss.com/docs/hover-focus-and-other-states)

- `hover` keadaan suatu element ketika kursor berada di dekatnya
- `active` keadaan suatu element ketika kursor melakukan aksi terhadapnya, misal di klik
- `focus`

### Group styling Pseudoclass

Ketika kita ingin membuat hover dalam satu `div group` kita tidak bisa untuk memberikan hover satu-satu ke masing masing `element` dalam `div`, untuk itu kita bisa melakukan

- delarasikan kelas `group` pada `parent` komponennya
- dan `group-hover:` untuk element yang ingin di beri `pseudoclass`

`pseudoclass` nya bisa berupa `focus hover active`

### after: Pseudoclass

digunakan untuk memberikan content pada element seperti menambahkan `*` untuk required pada email

### invalid: Pseudo

untuk menambahkan style ketika keadaan invalid (error)

## Dark Mode

untuk membuat dark mode dari tailwind, cukup dengan mendeklarasikan kelas `dark:` dan buat setting di `tailwind.config.js`

```javascript
/** @type {import('tailwindcss').Config} */
module.exports = {
  darkMode:'class',
  content: ['./build/*.html'],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

lalu pada tag `<html>` beri class `dark`

```html
<html class="dark">
</html>
```

pada saat membuat button darkmode menggunakan checkbox selalu pastikan pada label dan `id` pada input mempunyai nama yang sama, agak ketika `checkbox` di `hidden` tidak hilang. lihat di [WPU](https://www.youtube.com/watch?v=LR5ewsc0y58&list=PPSV) menit ke `28.00`

## Transform

ketika kita menggunakan pseudo `hover` kita tidak bisa menambahkan 2 jenis transform yang berbeda pada satu element yang sama

### Scale

untuk mengubah skala element. `scale-0` itu normal, `scale-50` menjadi lebih kecil

### Rotate

untuk memutar element

## Transition

jika kita ingin membuat transisi dari elemen, yang keluar dari elemennya , gunakan group untuk menghindari patah-patah

```html
<div class="w-40 h-40 mx-auto bg-amber-400 rounded-md shadow-lg group">
  <div class="w-40 h-40 mx-auto bg-pink-400 rounded-md shadow-lg group-hover:rotate-180 transition origin-top-left"></div>
</div>
```

## Layouting

### Container

secara default `container` di tailwind memiliki dua `break-points`

- ketika `@media` ***lebih dari*** `639px` maka lebar maksimal nya adalah `640px`
- ketika `@media` ***lebih dari*** `767px` maka lebar maksimal nya adalah `768px`
- ketika `@media` ***lebih dari*** `1023px` maka lebar maksimal nya adalah `1024px`
- ketika `@media` ***lebih dari*** `1279px` maka lebar maksimal nya adalah `1280px`

### Float

Float digunakan ketika kita ingin sebuah gambar di kelilingi oleh tulisan, kita bisa menggunakan `float-left` `float-right`

### position

- `absolute` ketika `child` komponen kita beri `position absolute`, maka dia akan keluar dari `parent` nya. maka dari itu `parent` nya harus diberi posisi non-static(tidak boleh `static`)
- `fixed` untuk membuat komponen berada di viewport nya, paling atas. dan akan fix di atas walaupun kursor kita scroll ke bawah

setelah position nya di declarasikan di dalam `class` kita bisa atur posisinya menggunakan `top` `right` `bottom` `left`

### Column

gunakan keyword `columns` dan `- jumlahnya` misal `columns-3`

## Responsive Design

`**tips**` pada saat membuat button menggunakan `<a></a>` pastikan untuk mengubah `display` nya menjadi `inline-block` agar bisa di berikan `padding`. ketika membuat `Responsive Design` perhatikan hal-hal berikut:

- selalu awali dengan tampilan `mobile` untuk memberikan nilai awal
- Berikan `max-width` awal ketika elemen ingin terlihat di `breakpoint` handphone atau ketika ingin terlihat di seluruh `breakpoint`.
- untuk mempermudah, berikan `background` disetiap `breakpoint` untuk mengetahui titik dimana `breakpoint` berubah.

```html
<div class="max-w-md sm:bg-sky-200 md:bg-red-200 xl:bg-yellow-200 lg:bg-lime-200"></div>
```

- jika ingin memberikan `max-width` di keadaan tertentu maka kembalikan nilai awal di `breakpoint` terdekat dengan nilai yang ingin kita ubah. misal kita ingin di breakpoint awal dan breakpoint md tidak berubah, hanya ingin berubah ketika di sm maka bisa di lakukan hal berikut:

```html
<div class="max-w-md sm:max-w-full md:max-w-md"></div>
```

- secara default tailwind itu membuat design untuk `mobile first design` jadi diutamakan untuk `mobile design` terlebih dahulu
- berikan css dari `breakpoint handphone` lalu`sm` `md` `xl` **satu persatu**

## Flex

### Display Flex

 memberikan `display flex` pada komponen, akan memberikan komponen `behavior flex` atau sifat flex.

- `flex-1` digunakan untuk menambahkan `grow 1 shrink 1`
- jika menambahkan `flex` pada komponen maka prilakunya akan menjadi `flex-items`
- `flex-wrap` untuk membuat element tidak memenuhi containernya, dan langsung turun mengisi ruang di bawahnya
- `flex-grow` seberapa banyak element flex berkembang terhadap containernya. nilai `0` tidak bertumbuh. `1` bertumbuh
- `flex-shrink` seberapa banyak element flex menyusut terhadap containernya. nilai `0` tidak menyusut. `1` menyusut
- `flex-basis` menetapkan ukuran awal sebelum element bertumbuh
- ketika memberi parent display `flex` kita bisa memberikan `self-center` pada child komponen untuk memindahkan komponen ke tengah

## Grid

- jika kita ingin memberikan ukuran fix pada element kita bisa menggunakan `aspect-ratio`
- untuk membuat kolom layout lebih mudah menggunakan `grid` dan nanti tinggal menambahkan `behavior-grid` nya
- `grid-cols` untuk membuat column
- `col-start` untuk membuat element mulai dari column tertentu
- `row-start` untuk membuat element mulai dari row tertentu
- untuk mengubah posisi element di dalam grid, lebih baik menggunakan flex
