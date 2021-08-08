<a href="https://www.buymeacoffee.com/ziishaned" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee" style="height: 41px !important;width: 174px !important;box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;" ></a>

<p align="center">
    <br/>
    <a href="https://github.com/ziishaned/learn-regex">	
        <img src="https://i.imgur.com/bYwl7Vf.png" alt="Learn Regex">
    </a>
</p>


## Translations:

* [English](README.md)
* [German](translations/README-de.md)
* [Español](translations/README-es.md)
* [Français](translations/README-fr.md)
* [Português do Brasil](translations/README-pt_BR.md)
* [中文版](translations/README-cn.md)
* [日本語](translations/README-ja.md)
* [한국어](translations/README-ko.md)
* [Turkish](translations/README-tr.md)
* [Greek](translations/README-gr.md)
* [Magyar](translations/README-hu.md)
* [Polish](translations/README-pl.md)
* [Русский](translations/README-ru.md)
* [Tiếng Việt](translations/README-vn.md)
* [فارسی](translations/README-fa.md)
* [Indonesia](translations/README-id.md) (WIP)

## Apa itu Regular Expression?

<p>
    <a href="https://gum.co/learn-regex">
        <img src="https://img.shields.io/badge/-Unduh%20PDF%20-0a0a0a.svg?style=flat&colorA=0a0a0a" alt="Unduh PDF">
    </a>
</p>

> Regular Expression adalah sekumpulan karakter atau simbol yang dimana digunakan untuk menemukan suatu pola khusus pada sebuah text.

Regular Expression adalah pola yang dicocokan dengan string subjek dari
kiri ke kanan. Regular Expression digunakan untuk mengganti teks didalam string, 
validasi formulir, meng-ekstrak substring dari string berdasarkan kecocokan pola, 
dan masih banyak lagi. Istilah "regular expression" cukup panjang, jadi kamu biasanya menemukan istilah tersebut disingkat menjadi "regex" atau "regexp". 

Bayangkanlah kamu menulis sebuah aplikasi dan kamu ingin mengatur sebuah peraturan ketika sebuah
pengguna memilih nama pengguna mereka. Kita ingin untuk mengizinkan sebuah nama pengguna mengandung huruf,
angka, garis bawah dan tanda hubung. Kita juga ingin membatasi batas karakter
nama pengguna. jadi itu tidak terlihat buruk. Kita bisa menggunakan Regular Expression tersebut untuk memvalidasi username itu:

<br/><br/>
<p align="center">
  <img src="./img/regexp-en.png" alt="Regular expression">
</p>

Regular Expression diatas bisa menerima string `john_doe`, `jo-hn_doe` dan
`john12_as`. Itu tidak cocok dengan `Jo` karena string itu mengandung huruf 
besar dan juga terlalu pendek.

## Daftar Isi

- [Basic Matchers](#1-basic-matchers)
- [Meta Characters](#2-meta-characters)
  - [The Full Stop](#21-the-full-stops)
  - [Character Sets](#22-character-sets)
    - [Negated Character Sets](#221-negated-character-sets)
  - [Repetitions](#23-repetitions)
    - [The Star](#231-the-star)
    - [The Plus](#232-the-plus)
    - [The Question Mark](#233-the-question-mark)
  - [Braces](#24-braces)
  - [Capturing Groups](#25-capturing-groups)
      - [Non-Capturing Groups](#251-non-capturing-groups)
  - [Alternation](#26-alternation)
  - [Escaping Special Characters](#27-escaping-special-characters)
  - [Anchors](#28-anchors)
    - [The Caret](#281-the-caret)
    - [The Dollar Sign](#282-the-dollar-sign)
- [Shorthand Character Sets](#3-shorthand-character-sets)
- [Lookarounds](#4-lookarounds)
  - [Positive Lookahead](#41-positive-lookahead)
  - [Negative Lookahead](#42-negative-lookahead)
  - [Positive Lookbehind](#43-positive-lookbehind)
  - [Negative Lookbehind](#44-negative-lookbehind)
- [Flags](#5-flags)
  - [Case Insensitive](#51-case-insensitive)
  - [Global Search](#52-global-search)
  - [Multiline](#53-multiline)
- [Greedy vs Lazy Matching](#6-greedy-vs-lazy-matching)

## 1. Basic Matchers

Regular Expression hanya sebuah pola dari karakter yang kita gunakan untuk melakukan
pencarian di sebuah teks.  Sebagai contoh, Regular Expression `the` maksudnya : huruf
`t`, diikuti huruf `h`, diikuti huruf `e`.

<pre>
"the" => The fat cat sat on <a href="#learn-regex"><strong>the</strong></a> mat.
</pre>

[Test the regular expression](https://regex101.com/r/dmRygT/1)

Regular Expression `123` cocok dengan string `123`. Regular Expression
cocok dengan string input dengan membandingkan setiap karakter dalam Regular Expression
untuk setiap karakter dalam string input, satu setelah lainnya. Regular
expression biasanya case-sensitive sehingga regular expression `The` tidak
akan cocok dengan string `the`.

<pre>
"The" => <a href="#learn-regex"><strong>The</strong></a> fat cat sat on the mat.
</pre>

[Test the regular expression](https://regex101.com/r/1paXsy/1)

## 2. Meta Characters

Karakter meta adalah blok bangunan regular expression.  Karakter
meta tidak berdiri sendiri tetapi sebaliknya ditafsirkan dalam
beberapa cara khusus. Beberapa karakter meta memiliki arti khusus dan ditulis di dalam tanda
kurung siku. Karakter meta adalah sebagai berikut:

|Meta character|Deskripsi|
|:----:|----|
|.|Titik cocok dengan karakter tunggal apapun kecuali jeda baris.|
|[ ]|Character class. Mencocokkan dengan karakter apa pun yang ada di antara tanda kurung siku.|
|[^ ]|Negated character class. Mencocokkan dengan karakter apapun yang tidak berada di antara tanda kurung siku|
|*|Mencocokkan 0 atau lebih pengulangan dari simbol sebelumnya.|
|+|Mencocokkan 1 atau lebih pengulangan simbol sebelumnya.|
|?|Membuat simbol sebelumnya opsional.|
|{n,m}|Braces. Mencocokkan setidaknya "n" tapi tidak lebih dari "m" pengulangan dari simbol sebelumnya.|
|(xyz)|Character group. Mencocokkan karakter xyz dengan urutan yang tepat.|
|&#124;|Alternasi. Mencocokkan dengan karakter sebelumnya atau karakter setelah simbol.|
|&#92;|Lolos karakter berikutnya. Ini mengizinkan kamu untuk mencocokkan karakter dengan <code>[ ] ( ) { } . * + ? ^ $ \ &#124;</code>|
|^|Mencocokkan dengan input awal.|
|$|Mencocokkan dengan input akhir.|

## 2.1 The Full Stop

The full stop `.` is the simplest example of a meta character. The meta character `.`
matches any single character. It will not match return or newline characters.
For example, the regular expression `.ar` means: any character, followed by the
letter `a`, followed by the letter `r`.

<pre>
".ar" => The <a href="#learn-regex"><strong>car</strong></a> <a href="#learn-regex"><strong>par</strong></a>ked in the <a href="#learn-regex"><strong>gar</strong></a>age.
</pre>

[Test the regular expression](https://regex101.com/r/xc9GkU/1)

## 2.2 Character Sets

Character set (set karakter) juga disebut dengan character class. kurung siku digunakan
untuk menentukan character set. Gunakan tanda kurang didalam character set untuk menentukan
jangkauan karakter. Urutan dari jangkauan karakter didalam kurung siku tidak berpengaruh.
Misalnya, regular expression `[Tt]he` berarti: sebuah huruf besar `T` atau sebuah huruf kecil
`t`, diikuti dengan huruf `h`, diikuti dengan huruf `e`.

<pre>
"[Tt]he" => <a href="#learn-regex"><strong>The</strong></a> car parked in <a href="#learn-regex"><strong>the</strong></a> garage.
</pre>

[Test the regular expression](https://regex101.com/r/2ITLQ4/1)

Sebuah titik didalam suatu character set, bagaimanapun, benar-benar berarti sebuah titik.
Regular expression `ar[.]` berarti: sebuah huruf kecil `a`, diikuti dengan huruf `r`, diikuti
dengan sebuah karakter titik `.`.

<pre>
"ar[.]" => A garage is a good place to park a c<a href="#learn-regex"><strong>ar.</strong></a>
</pre>

[Test the regular expression](https://regex101.com/r/wL3xtE/1)

### 2.2.1 Negated Character Sets

Secara umum, tanda sisipan mewakili awal dari string, tapi ketika itu ditulis setalah kurung
siku buka, itu membalik set karakternya. Misalnya, regular expression `[^c]ar` berarti:
karakter apapun kecuali `c`, diikuti dengan karakter `a`, diikuti dengan huruf `r`.

<pre>
"[^c]ar" => The car <a href="#learn-regex"><strong>par</strong></a>ked in the <a href="#learn-regex"><strong>gar</strong></a>age.
</pre>

[Test the regular expression](https://regex101.com/r/nNNlq3/1)

## 2.3 Repetitions

Karakter meta `+`, `*` atau `?` digunakan untuk menentukan berapa kali subpola dapat
terjadi. Karakter meta tersebut bertindak berbeda pada berbagai situasi.

### 2.3.1 The Star

Simbol bintang `*` cocok dengan 0 atau lebih pengulangan dari karakter sebelumnya. Regular
expression `a*` berarti: 0 atau lebih pengulangan dari huruf kecil `a`. Tapi jika itu muncul
setelah sebuah character set atau class itu akan menemukan pengulangan dari seluruh set
karakter tersebut. Misalnya, regular expression `[a-z]*` berarti: sejumlah huruf kecil
dalam satu baris.

<pre>
"[a-z]*" => T<a href="#learn-regex"><strong>he</strong></a> <a href="#learn-regex"><strong>car</strong></a> <a href="#learn-regex"><strong>parked</strong></a> <a href="#learn-regex"><strong>in</strong></a> <a href="#learn-regex"><strong>the</strong></a> <a href="#learn-regex"><strong>garage</strong></a> #21.
</pre>

[Test the regular expression](https://regex101.com/r/7m8me5/1)

Simbol bintang `*` bisa digunakan dengan karakter meta `.` untuk mencocokkan karakter apapun
pada string `.*`. Simbol `*` bisa digunakan dengan karakter whitespace `\s` untuk mencocokkan
string dari karakter whitespace. Misalnya, regular expression `\s*cat\s*` berarti: 0 atau
lebih spasi, diikuti dengan huruf kecil `c`, diikuti dengan huruf kecil `a`, diikuti dengan
huruf kecil `t`, diikuti dengan 0 atau lebih spasi.

<pre>
"\s*cat\s*" => The fat<a href="#learn-regex"><strong> cat </strong></a>sat on the con<a href="#learn-regex"><strong>cat</strong></a>enation.
</pre>

[Test the regular expression](https://regex101.com/r/gGrwuz/1)

### 2.3.2 The Plus

Simbol tambah `+` cocok dengan 1 atau lebih pengulangan dari karakter sebelumnya. Misalnya,
regular expression `c.+t` berarti: sebuah huruf kecil `c`, diikuti dengan setidaknya satu
karakter, diikuti dengan sebuah huruf kecil `t`. Itu perlu diklarifikasi bahwa `t` adalah
`t` terakhir dari kalimat tersebut.

<pre>
"c.+t" => The fat <a href="#learn-regex"><strong>cat sat on the mat</strong></a>.
</pre>

[Test the regular expression](https://regex101.com/r/Dzf9Aa/1)

### 2.3.3 The Question Mark

Di regular expression, karakter meta `?` membuat karakter sebelumnya menjadi opsional.
Simbol in cocok dengan 0 atau 1 instansi dari karakter sebelumnya. Misalnya, regular
expression `[T]?he` berarti: huruf besar opsional `T`, diikuti dengan huruf kecil `h`,
diikuti dengan huruf kecil `e`.

<pre>
"[T]he" => <a href="#learn-regex"><strong>The</strong></a> car is parked in the garage.
</pre>

[Test the regular expression](https://regex101.com/r/cIg9zm/1)

<pre>
"[T]?he" => <a href="#learn-regex"><strong>The</strong></a> car is parked in t<a href="#learn-regex"><strong>he</strong></a> garage.
</pre>

[Test the regular expression](https://regex101.com/r/kPpO2x/1)

## 2.4 Braces

Di regular expression, braces juga disebut quantifier (pembilang) digunakan untuk
menentukan berapa kali sebuah karakter atau kelompok karakter dapat diulang. Misalnya,
regular expression `[0-9]{2,3}` berarti: cocok dengan setidaknya angka 2 digit, tapi
tidak lebih dari 3, mulai dari 0 sampai 9.

<pre>
"[0-9]{2,3}" => Angkanya adalah 9.<a href="#learn-regex"><strong>999</strong></a>7 tapi kita membulatkannya menjadi <a href="#learn-regex"><strong>10</strong></a>.0.
</pre>

[Test the regular expression](https://regex101.com/r/juM86s/1)

Kita dapat mengosongkan angka kedua. Misalnya, regular expression `[0-9]{2,}` berarti:
Cocok dengan 2 atau lebih digit. Jika kita juga menghapus tanda koma, regular expression
`[0-9]{3}` berarti: cocok dengan tepat 3 digit.

<pre>
"[0-9]{2,}" => Angkanya adalah 9.<a href="#learn-regex"><strong>9997</strong></a> tapi kita membulatkannya menjadi <a href="#learn-regex"><strong>10</strong></a>.0.
</pre>

[Test the regular expression](https://regex101.com/r/Gdy4w5/1)

<pre>
"[0-9]{3}" => Angkanya adalah 9.<a href="#learn-regex"><strong>999</strong></a>7 tapi kita membulatkannya menjadi 10.0.
</pre>

[Test the regular expression](https://regex101.com/r/Sivu30/1)

## 2.5 Capturing Groups

Suatu capturing group (kelompok penangkap) adalah sebuah kelompok dari subpola yang
ditulis di dalam kurung `(...)`. Seperti pembahasan sebelumnya, di regular expression,
jika kita menaruh sebuah quantifier (pembilang) setelah sebuah karakter, itu akan mengulangi
karakter pendahulunya. Tapi jika kita menaruh sebuah quantifier setelah sebuah capturing
group, itu mengulangi seluruh capturing group. Misalnya, regular expression `(ab)*`
cocok dengan 0 atau lebih pengulangan dari karakter "ab". Kita juga bisa menggunakan
karakter alternation `|`  di dalam sebuah capturing group. Misalnya, regular expression
`(c|g|p)ar` berarti: sebuah huruf kecil `c`, `g` atau `p`, diikuti dengan `a`, diikuti
dengan `r`.

<pre>
"(c|g|p)ar" => The <a href="#learn-regex"><strong>car</strong></a> is <a href="#learn-regex"><strong>par</strong></a>ked in the <a href="#learn-regex"><strong>gar</strong></a>age.
</pre>

[Test the regular expression](https://regex101.com/r/tUxrBG/1)

Perhatikan bahwa capturing group tidak hanya mencocokkan, tetapi juga menangkap
karakter-karakter untuk digunakan dalam bahasa induk. Bahasa induknya bisa Python atau
JavaScript atau hampir semua bahasa yang mengimplementasikan regular expressions dalam 
sebuah function definition.

### 2.5.1 Non-Capturing Groups

Suatu non-capturing group adalah sebuah capturing group yang mencocokkan karakter tapi 
tidak menangkapnya. Sebuah non-capturing group dilambangkan dengan sebuah `?` diikuti 
dengan sebuah `:` di dalam tanda kurung `(...)`. Misalnya, regular expression `(?:c|g|p)ar`
mirip dengan `(c|g|p)ar` karena mencocokkan karakter yang sama tapi tidak akan membuat
sebuah capture group.

<pre>
"(?:c|g|p)ar" => The <a href="#learn-regex"><strong>car</strong></a> is <a href="#learn-regex"><strong>par</strong></a>ked in the <a href="#learn-regex"><strong>gar</strong></a>age.
</pre>

[Test the regular expression](https://regex101.com/r/Rm7Me8/1)

Non-capturing group bisa berguna ketika digunakan pada function find-and-replace atau 
ketika dicampur dengan capturing group untuk menjaga gambaran saat memproduksi jenis output
lainnya. Lihat juga [4. Lookaround](#4-lookaround).

## 2.6 Alternation

Pada sebuah regular expression, tanda garis vertikal `|` digunakan untuk menetapkan
alternation. Alternation itu seperti pernyataan OR diantara banyak expression. Sekarang,
kamu mungkin berpikir bahwa set karakter and alternation bekerja dengan cara yang sama. 
Tapi perbedaan terbesarnya diantara set karakter dan alternation adalah set karakter
bekerja pada character level tapi alternation bekerja pada expression level. Misalnya,
regular expression `(T|t)he|car` berarti: salah satu (sebuah huruf besar `T` atau sebuah
huruf kecil `t`, diikuti dengan sebuah huruf kecil `h`, diikuti dengan sebuah huruf kecil
`e`) ATAU (sebuah huruf kecil `c`, diikuti dengan sebuah huruf kecil `a`, diikuti dengan 
sebuah huruf kecil `r`). Perhatikan bahwa kita menambahkan tanda kurung untuk penegasan,
untuk menunjukkan bahwa salah satu expression di dalam kurung dapat dipenuhi dan itu
akan cocok.

<pre>
"(T|t)he|car" => <a href="#learn-regex"><strong>The</strong></a> <a href="#learn-regex"><strong>car</strong></a> is parked in <a href="#learn-regex"><strong>the</strong></a> garage.
</pre>

[Test the regular expression](https://regex101.com/r/fBXyX0/1)

## 2.7 Escaping Special Characters

Sebuah backslash `\` digunakan pada regular expression untuk meng-escape karakter berikutnya.
Ini membolehkan kita untuk memasukkan karakter spesial seperti `{ } [ ] / \ + * . $ ^ | ?`
sebagai karakter yang dicocokkan. Untuk menggunakan salah satu dari karakter spesial itu
sebagai karakter yang dicocokkan, awali dengan tanda `\`.

Misalnya, regular expression `.` digunakan untuk mencocokkan karakter apapun kecuali baris
baru. Sekarang, untuk mencocokkan `.` pada string yang di-input, regular expression 
`(f|c|m)at\.?` berarti: sebuah huruf kecil `f`, `c` atau `m`, diikuti dengan sebuah huruf
kecil `a`, diikuti dengan sebuah huruf kecil `t`, opsionalnya diikuti sebuah karakter `.`.

<pre>
"(f|c|m)at\.?" => The <a href="#learn-regex"><strong>fat</strong></a> <a href="#learn-regex"><strong>cat</strong></a> sat on the <a href="#learn-regex"><strong>mat.</strong></a>
</pre>

[Test the regular expression](https://regex101.com/r/DOc5Nu/1)

## 2.8 Anchors

Di regular expression, Kita menggunakan anchor untuk mengecek jika simbol yang cocok adalah
simbol awal atau simbol akhir pada string yang di-input. Anchor ada dua jenis yaitu: jenis
pertama adalah tanda sisipan `^` yang memeriksa jika karakter yang cocok adalah karakter 
pertama dari string yang di-input dan jenis kedua adalah tanda dolar `$` yang mana memeriksa
jika karakter yang cocok adalah karakter terakhir dari string yang di-input.

### 2.8.1 The Caret

Tanda sisipan `^` digunakan untuk memeriksa jika karakter yang cocok adalah karakter pertama
dari string yang di-input. Jika kita menggunakan regular expression berikut `^a` (artinya 'a'
harus menjadi karakter awal) dari string `abc`, itu akan cocok dengan `a`. Tapi jika kita
menggunakan regular expression `^b` pada string diatas, itu tidak akan cocok dengan apapun.
Karena pada string `abc`, karakter "b" bukan karakter awal. Mari lihat regular expression 
lainnya `^(T|t)he` yang berarti: sebuah huruf besar `T` atau sebuah huruf keci `t` harus
menjadi karakter pertama pada string-nya, diikuti sebuah huruf kecil `h`, diikuti sebuah huruf
kecil `e`.

<pre>
"(T|t)he" => <a href="#learn-regex"><strong>The</strong></a> car is parked in <a href="#learn-regex"><strong>the</strong></a> garage.
</pre>

[Test the regular expression](https://regex101.com/r/5ljjgB/1)

<pre>
"^(T|t)he" => <a href="#learn-regex"><strong>The</strong></a> car is parked in the garage.
</pre>

[Test the regular expression](https://regex101.com/r/jXrKne/1)

### 2.8.2 The Dollar Sign

Tanda dolar `$` digunakan untuk memeriksa jika karakter yang cocok adalah karakter terakhir
dari string yang di-input. Misalnya, regular expression `(at\.)$` berarti: sebuah huruf
kecil `a`, diikuti dengan sebuah huruf kecil `t`, diikuti dengan sebuah tanda `.` dan
yang cocok harus berada di akhir string-nya.

<pre>
"(at\.)" => The fat c<a href="#learn-regex"><strong>at.</strong></a> s<a href="#learn-regex"><strong>at.</strong></a> on the m<a href="#learn-regex"><strong>at.</strong></a>
</pre>

[Test the regular expression](https://regex101.com/r/y4Au4D/1)

<pre>
"(at\.)$" => The fat cat. sat. on the m<a href="#learn-regex"><strong>at.</strong></a>
</pre>

[Test the regular expression](https://regex101.com/r/t0AkOd/1)

##  3. Shorthand Character Sets

Ada sejumlah singkatan nyaman untuk sekumpulan karakter yang biasa digunakan
pada regular expression:

|Singkatan|Keterangan|
|:----:|----|
|.|Karakter apapun kecuali baris baru|
|\w|Karakter huruf dan angka: `[a-zA-Z0-9_]`|
|\W|Karakter selain huruf dan angka: `[^\w]`|
|\d|Karakter angka: `[0-9]`|
|\D|Karakter selain angka: `[^\d]`|
|\s|karakter whitespace (spasi, tab, enter, dll): `[\t\n\f\r\p{Z}]`|
|\S|karakter selain whitespace: `[^\s]`|

## 4. Lookarounds

Lookbehind (melihat ke belakang) dan lookahead (melihat ke depan) juga disebut
lookaround (melihat sekitar) merupakan jenis tertentu dari ***non-capturing groups***
(digunakan untuk mencocokkan sebuah pola tapi tanpa memasukkan pola tersebut pada
daftar yang cocok). Lookarounds digunakan ketika suatu pola harus didahului atau
diikuti oleh pola yang lain. Misalnya, bayangkan kita ingin mendapatkan semua angka
yang didahului oleh karakter `$` dari string `$4.44 and $10.88`. Kita akan menggunakan
regular expression berikut `(?<=\$)[0-9\.]*` yang berarti: dapatkan semua angka yang
mengandung karakter `.` dan didahului oleh karakter `$`. Ini adalah lookaround yang 
biasa digunakan pada regular expressions:

|Simbol|Keterangan|
|:----:|----|
|?=|Lookahead Positif|
|?!|Lookahead Negatif|
|?<=|Lookbehind Positif|
|?<!|Lookbehind Negatif|

### 4.1 Positive Lookahead

Lookahead positif menegaskan bahwa bagian pertama dari expression harus diikuti
dengan lookahead expression. Hasil pencocokkan hanya mengandung text yang cocok dengan
bagian pertama dari expression. Untuk menetapkan sebuah lookahead positif, digunakanlah
tanda kurung. Di dalam tanda kurung itu, sebuah tanda tanya dengan sebuah tanda sama
dengan digunakan seperti ini: `(?=...)`. Lookahead expressions ditulis setelah tanda
sama dengan didalam tanda kurung. Misalnya, regular expression `(T|t)he(?=\sfat)` berarti:
cocok dengan sebuah huruf kecil `t` atau sebuah huruf besar `T`, diikuti dengan huruf `h`, 
diikuti dengan huruf `e`. Di dalam kurung kita menetapkan sebuah lookahead positif yang
memberi tahu mesin regular expression untuk mencocokkan `The` atau `the` hanya jika itu
diikuti dengan kata `fat`.

<pre>
"(T|t)he(?=\sfat)" => <a href="#learn-regex"><strong>The</strong></a> fat cat sat on the mat.
</pre>

[Test the regular expression](https://regex101.com/r/IDDARt/1)

### 4.2 Negative Lookahead

Lookahead negatif digunakan ketika kita ingin mendapatkan semua kecocokkan yang tidak diikuti
oleh pola tertentu dari string yang di-input. Lookahead negatif ditulis dengan cara yang sama
seperti lookahead postif. Satu-satunya perbedaan adalah, daripada menggunakan tanda sama 
dengan `=`, kita menggunakan sebuah tanda seru `!` untuk menunjukkan negasi, yaitu: `(?!...)`.
Mari simak regular expression berikut `(T|t)he(?!\sfat)` yang berarti: dapatkan semua kata
`The` atau `the` yang tidak diikuti karakter spasi dan kata `fat` dari string yang di-input.

<pre>
"(T|t)he(?!\sfat)" => The fat cat sat on <a href="#learn-regex"><strong>the</strong></a> mat.
</pre>

[Test the regular expression](https://regex101.com/r/V32Npg/1)

### 4.3 Positive Lookbehind

Lookbehind positif digunakan untuk mendapatkan semua kecocokkan yang didahului oleh suatu pola
tertentu. Lookbehind positif ditulis seperti ini: `(?<=...)`. Misalnya, regular expression
`(?<=(T|t)he\s)(fat|mat)` berarti: dapatkan semua kata `fat` atau `mat` yang muncul setelah
kata `The` atau `the` dari string yang di-input.

<pre>
"(?<=(T|t)he\s)(fat|mat)" => The <a href="#learn-regex"><strong>fat</strong></a> cat sat on the <a href="#learn-regex"><strong>mat</strong></a>.
</pre>

[Test the regular expression](https://regex101.com/r/avH165/1)

### 4.4 Negative Lookbehind

Lookbehind negatif digunakan untuk mendapatkan semua kecocokkan yang tidak didahului oleh
suatu pola tertentu. Lookbehind negatif ditulis seperti ini: `(?<!...)`. Misalnya, regular
expression `(?<!(T|t)he\s)(cat)` berarti: dapatkan semua kata `cat` yang bukan setelah kata
`The` atau `the` dari string yang di-input.

<pre>
"(?&lt;!(T|t)he\s)(cat)" => The cat sat on <a href="#learn-regex"><strong>cat</strong></a>.
</pre>

[Test the regular expression](https://regex101.com/r/8Efx5G/1)

## 5. Flags

Flag juga disebut modifier karena itu mengubah output dari sebuah regular
expression. Flag bisa digunakan pada berbagai urutan dan combinasi, dan 
merupakan bagian yang tidak terpisahkan dari RegExp.

|Flag|Keterangan|
|:----:|----|
|i|Case insensitive: Pencocokkan akan menyamakan huruf besar dan huruf kecil.|
|g|Global Search: Mencocokkan semuanya, bukan hanya yang pertama.|
|m|Multiline: Anchor karakter bekerja pada tiap baris.|

### 5.1 Case Insensitive

Modifier `i` digunakan untuk melakukan pencocokkan case-insensitive (huruf kecil
dan huruf besar diperlakukan setara). Misalnya, regular expression `/The/gi`
berarti: sebuah huruf besar `T`, diikuti dengan sebuah huruf kecil `h`, diikuti
dengan sebuah `e`. Dan pada akhir dari regular expression flag `i` memberi tahu
mesin regular expression untuk mengabaikan besar kecilnya huruf. Seperti yang 
bisa kamu lihat, kita juga menetapkan flag `g` karena kita ingin mencari pola pada
seluruh string yang di-input.

<pre>
"The" => <a href="#learn-regex"><strong>The</strong></a> fat cat sat on the mat.
</pre>

[Test the regular expression](https://regex101.com/r/dpQyf9/1)

<pre>
"/The/gi" => <a href="#learn-regex"><strong>The</strong></a> fat cat sat on <a href="#learn-regex"><strong>the</strong></a> mat.
</pre>

[Test the regular expression](https://regex101.com/r/ahfiuh/1)

### 5.2 Global Search

Modifier `g` digunakan untuk melakukan pencocokkan secara global (menemukan semua yang cocok daripada
berhenti setelah kecocokkan pertama). Misalnya, regular expression `/.(at)/g`
berarti: karakter apapun kecuali baris baru, diikuti dengan sebuah huruf kecil `a`,
diikuti dengan sebuah huruf kecil `t`. Karena kita menetapkan flag `g` pada akhir dari
regular expression, regex-nya sekarang akan menemukan semua kecocokkan pada string yang di-input, 
bukan hanya yang pertama (yang merupakan tindakan default).

<pre>
"/.(at)/" => The <a href="#learn-regex"><strong>fat</strong></a> cat sat on the mat.
</pre>

[Test the regular expression](https://regex101.com/r/jnk6gM/1)

<pre>
"/.(at)/g" => The <a href="#learn-regex"><strong>fat</strong></a> <a href="#learn-regex"><strong>cat</strong></a> <a href="#learn-regex"><strong>sat</strong></a> on the <a href="#learn-regex"><strong>mat</strong></a>.
</pre>

[Test the regular expression](https://regex101.com/r/dO1nef/1)

### 5.3 Multiline

Modifier `m` digunakan untuk melakukan pencocokkan banyak baris. Seperti yang telah kita bahas sebelumnya,
anchors `(^, $)` digunakan untuk memeriksa jika suatu pola berada di awal dari input atau di akhir. Tapi
jika kita ingin anchors-nya bekerja pada setiap baris, kita menggunakan flag `m`. Misalnya, regular
expression `/at(.)?$/gm` berarti: sebuah huruf kecil `a`, diikuti sebuah huruf kecil `t` dan,
opsionalnya apapun kecuali baris baru. Dan karena flag `m`, mesin regular expression sekarang 
mencocokkan pola yang berada di akhir dari setiap baris pada suatu string.

<pre>
"/.at(.)?$/" => The fat
                cat sat
                on the <a href="#learn-regex"><strong>mat.</strong></a>
</pre>

[Test the regular expression](https://regex101.com/r/hoGMkP/1)

<pre>
"/.at(.)?$/gm" => The <a href="#learn-regex"><strong>fat</strong></a>
                  cat <a href="#learn-regex"><strong>sat</strong></a>
                  on the <a href="#learn-regex"><strong>mat.</strong></a>
</pre>

[Test the regular expression](https://regex101.com/r/E88WE2/1)

## 6. Greedy vs Lazy Matching
Secara default, sebuah regex akan melakukan greedy match, yang berarti pencocokkan akan dilakukan
sepanjang mungkin. Kita bisa menggunakan `?` untuk melakukan lazy match, yang berarti pencocokkan harus
dilakukan sesingkat mungkin

<pre>
"/(.*at)/" => <a href="#learn-regex"><strong>The fat cat sat on the mat</strong></a>. </pre>


[Test the regular expression](https://regex101.com/r/AyAdgJ/1)

<pre>
"/(.*?at)/" => <a href="#learn-regex"><strong>The fat</strong></a> cat sat on the mat. </pre>


[Test the regular expression](https://regex101.com/r/AyAdgJ/2)


## Contribution

* Open a pull request with improvements
* Discuss ideas in issues
* Spread the word
* Reach out with any feedback [![Twitter URL](https://img.shields.io/twitter/url/https/twitter.com/ziishaned.svg?style=social&label=Follow%20%40ziishaned)](https://twitter.com/ziishaned)

## License

MIT &copy; [Zeeshan Ahmad](https://twitter.com/ziishaned)
