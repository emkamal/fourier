Transformasi Fourier adalah teknik yang digunakan pada banyak hal. Ini adalah penjelasan apa itu transformasi Fourier, dan berbagai kegunaannya. Dan juga bagaimana dia bisa dipakai untuk membuat gambar cantik seperti ini:

<canvas id="self-draw" class="sketch" width=500 height=500></canvas>

Saya akan menjelaskan cara kerja animasi di atas, sekaligus menjelaskan tenatng transformasi Fourier!

Setelah selesai membaca, kamu harusnya sudah bisa
- Memahami apa itu transformasi Fourier
- Mengetahui apa saja kegunaan praktikal dari transformasi Fourier
- Tahu hal tidak penting tapi seru dari kegunaan transformasi Fourier

Kita tidak akan membahas matematika dan persamaannya dulu. Ada beberapa hal menarik di sisi matematikanya, tapi akan lebih baik kalau kita mulai dengan apa sebenarnya transformasi Fourier itu, dan kenapa kamu mau menggunakannya. Kalau kamu mau mendalami lebih lanjut, ada daftar bacaan lanjutan di bagian bawah!

## Jadi apa itu transformasi Fourier?

Sederhananya, transformasi Fourier adalah cara untuk memecah sesuatu ke dalam beberapa gelombang sinus. Seperti biasa, nama metode ini datang dari seseorang yang hidup di masa lalu dengan nama Fourier.

Mari kita mulai dengan contoh sederhana, kemudian pelan-pelan kita lanjut ke contoh yang lebih kompleks. Pertama, mari kita lihat gelombang, pola yang berulang setiap waktu.

Ini contoh gelombang:

<canvas id="combo-sine-wave" class="sketch" width=500 height=300></canvas>

Pola gelombang ini bisa dipecah ke dalam beberapa gelombang sinus. Dalam hal ini kita bisa pecah jadi dua gelombang sinus. Kalau gelombang sinus pertama kita tambahkan dengan gelombang sinus kedua, kita dapat gelombang yang asli.

<canvas id="combo-sine-wave-split" class="sketch" width=500 height=500></canvas>

Transformasi Fourier adalah cara buat kita mengambil gelombang kombinasi, dan mendapat masing-masing gelombang sinus dari sana. Pada contoh ini, kamu bisa membayangkan sendiri di otak kamu, hanya dengan melihat gelombang asal.

Kenapa? Ternyata banyak hal di dunia nyata yang berinteraksi berdasarkan gelombang-gelombang sinus ini. Kita biasa menyebutnya frekuensi gelombang.

Contoh paling jelas adalah suara – ketika kita mendengar suara, kita bukan mendengarkan garis-garis gelombang itu, yang kita dengar adalah frekuensi-frekuensi berbeda dari gelombang sinus yang menjadi komponen dari suara tersebut.

<button id="together-button" class="button">Dengar sinyal utuh</button>

<button id="split-button-1" class="button">dengar frekuensi tinggi</button>

<button id="split-button-2" class="button">Dengar frekuensi rendah</button>

Dengan membagi sinyal tersebut di komputer, kita bisa tahu suara apa yang di dengar oleh seseorang.Kita bisa tahu seberapa tinggi atau rendah sebuah suara, atau kita juga bisa tahu tangga nada dari suara tersebut.

Kita juga bisa menggunakan proses ini pada gelombang yang tidak terlihat seperti terbuat dari gelombang sinus.

Mari kita coba lihat gelombang yang satu ini. Namanya gelombang kotak.

<canvas id="square-wave" class="sketch" width=500 height=300></canvas>

Agak sulit membayangkannya, tapi gelombang kotak ini juga bisa dipecah kedalam gelmabng-gelombang sinus.

<canvas id="square-wave-split" class="sketch" width=500 height=500></canvas>

Kita butuh banyak kali ini – secara teknis, kita butuh gelombang sinus sebanyak tak-hingga agar dapat secara sempurna merepresentasikannya. Semakin kita tambah gelombang sinusnya, polanya akan semakin mendekat gelombang kotak kita tadi.

<canvas id="square-wave-build-up" class="sketch" width=500 height=500></canvas>
<input id="square-wave-build-up-slider" type="range" min="0" max="1" value="0" step="any" >

<button id="square-wave-button" class="button">Dengar suara gelombangnya</button>

*Geser slider di atas untuk mengatur jumlah gelombang sinusnya.*

Secara visual, kamu akan tahu bahwa yang paling berpengaruh sebenarnya adalah beberapa gelombang sinus pertama. Dengan slider berada di tengah, kita secara umum sudah mendapat bentuk gelombang yang kita inginkan, walaupun tidak halus. Kita cuma butuh sisa gelombang sinus lainnya untuk menghaluskan gelombangnya.

Ketika kamu mendengar gelombangnya, suaranya akan semakin rendah, karena kita menghapus frekuensi-frekuensi yang tinggi.

Proses ini berlaku sama untuk setiap garis yang berulang. Silakan coba gambar sinyalmu sendiri!

<div class="multi-container">
<div class="sketch" >
    <canvas id="wave-draw" class="sketch-child" width=500 height=300></canvas>
    <p id="wave-draw-instruction" class="instruction wave-instruction">Gambar disini!</p>
</div>
<canvas id="wave-draw-split" class="sketch" width=500 height=500></canvas>
</div>
<input id="wave-draw-slider" type="range" min="0" max="1" value="1" step="any">
<button id="wave-draw-button" class="button">Dengar Sinyal</button>

*Geser slider untuk melihat bagaimana penambahan gelombang sinus membuatnya semakin dekat ke gambar kamu*

Lagi-lagi, disamping masalah ketidakhalusan, gelombangnya sudah cukup mirip hanya dengan setengah dari gelombang-gelombang sinus tersebut.

Kita bisa memanfaatkan fenomena ini. Dengan menggunakan transformasi Fourier, kita bisa mengambil bagian yang penting dari sebuah sinyal suara, dan hanya menyimpan gelombang sinus secukupnya agar kita bisa mendapatkan suara yang sudah cukup mirip.

Biasanya, di komputer kita menyimpan gelombang sebagai daftar titik-titik.

<canvas id="wave-samples" class="sketch" width=500 height=500></canvas>

alih-alih, kita bisa menyimpannya dalam bentuk beberapa gelombang sinus. Lalu kita kompres suaranya dengan mengabaikan frekuensi-frekuensi yang kecil. Hasil akhirnya pasti berbeda, tapi akan terdengar sama di telinga manusia.

<canvas id="wave-frequencies" class="sketch" width=500 height=500></canvas>

Pada dasarnya inilah yang dilakukan MP3, tapi mereka lebih cerdas dalam hal memilih frekuensi mana yang disimpan dan mana yang dibuang.

Jadi dalam hal ini kita bisa menggunakan transformasi Fourier untuk memahami properti dasar dari sebuah gelombang,  dan kita bisa menggunakannya untuk hal berguna seperti kompresi data.

Ok, sekarang mari kita gali lebih dalam tentang transformasi Fourier. Bagian selanjutnya ini terlihat keren, tapi juga akan membuat kamu lebih paham lagi tentang transformasi Fourier. Tapi intinya keren deh.

## Episiklus

Di awal, disebutkan bahwa transformasi Fourier memecah sesuatu ke dalam beberapa gelombang sinus. Menariknya, gelombang sinus yang dihasilkan disini bukan gelombang sinus biasa, mereka adalah gelombang sinus 3 dimensi. Kamu bisa menyebutnya "sinusoid kompleks". Atau cukup "spiral".

<canvas id="complex-sinusoid" class="sketch" width=500 height=500></canvas>

Kalau kita lihat dari samping, mereka terlihat seperti gelombang sinus. Tapi dari depan, mereka terlihat seperti lingkaran.

<canvas id="complex-sinusoid-turn" class="sketch" width=500 height=500></canvas>

Sejauh ini kita masih hanya bermain-main dengan gelombang sinus 2 dimensi. Saat kita melakukan transformasi Fourier pada gelombang 2D, bagian kompleksnya tereliminasi sehingga kita hanya mendapat gelombang sinus sederhana.

Tapi kita bisa menggunakan gelombang sinus 3D untuk membuat sesuatu yang menarik seperti ini:

<canvas id="peace-epicycles" class="sketch" width=500 height=500></canvas>

Ada apa disini?

Kita bisa melihat gambarnya sebagai sebuah bentuk 3 dimensi karena dia bergerak seiring waktu. Kalau kamu membayangkan tangannya digambar oleh seseorang, ketiga dimensinya merepresentasikan ujung pensil si penggambar pada momen tersebut. Dimensi x dan y menunjukkan posisi, dan lalu dimensi ketiga adalah waktu pada momen tersebut.

<canvas id="peace-3d" class="sketch" width=500 height=500></canvas>

Sekarang kita punya pola 3 dimensi, kita tidak bisa lagi menggunakan gelombang sinus 2 dimensi biasa untuk merepresentasikannya. Tidak peduli berapa banyak pun gelombang sinus 2 dimensi yang kita tambahkan, kita tidak akan bisa mendapatkan sesuatu dengan 3 dimensi. Jadi kita butuh hal lain.

Yang bisa kita gunakan adalah gelombang sinus spiral 3 dimensi yang kita sebutkan sebelumnya. Jika kita tambahkan banyak gelombang sinus spiral 3 dimensi, kita bisa mendapatkan sesuatu yang terlihat seperti pola 3 dimensi kita.

Ingat, gelombang-gelombang ini terlihat seperti lingkaran ketika kita melihatnya dari arah depan. Nama pola dimana sebuah lingkarang bergerak di sekitar lingkaran lainnya adalah episiklus.

<canvas id="peace-build-up" class="sketch" width=500 height=500></canvas>
<input id="peace-build-up-slider" type="range" min="0" max="1" value="1" step="any">

*Geser slider diatas untuk mengatur jumlah lingkaran yang ada.*

Seperti sebelumnya, kita bisa mendapatkan pola yang sudah mendekati pola yang kita inginkan hanya dengan beberapa lingkaran. Karena bentuk ini adalah bentuk yang cukup sederhana, lingkaran-lingkaran terakhir berfungsi untuk menajamkan gars-garisnya.

Semua ini bisa digunakan untuk gambar apapun, beneran! Silakan coba sendiri.

<div class="multi-container">
<div class="sketch" >
    <canvas id="draw-zone" class="sketch-child" width=500 height=500></canvas>
    <p id="draw-zone-instruction" class="instruction">Gambar disini!</p>
    <button id="draw-zone-undo-button" class="button embedded-button">Undo</button>
</div>
<canvas id="circle-zone" class="sketch" width=500 height=500></canvas>
</div>
<input id="circle-zone-slider" type="range" min="0" max="1" value="1" step="any">

*Pakai slider untuk mengatur jumlah lingkaran yang dipakai untuk memggambar*

Lagi-lagi, kita bisa lihat bahwa untuk kebanyakan bentuk, kita bisa membuat yang cukup mirip hanya dengan jumlah lingkaran yang sedikit, alih-alih harus menyimpang semua titik.

Bisakah kita menggunakan ini pada data riil? Tentu bisa! Tapi untuk ini kita sudah punya format data yang bernama SVG, yang mungkin bisa lebih efisies untuk bentuk gambar yang pada umumnya kita buat. Jadi untuk saat ini, teknik menggambar dengan transformasi Fourier ini hanya untuk lucu-lucuan saja.

<canvas id="fourier-title" class="sketch" width=500 height=300></canvas>

Tapi ada lagi loh tipe data visual lain yang menggunakan tranformasi Fourier.

## JPEGs

Did you know Fourier transforms can also be used on images? In fact, we use it all the time, because that's how JPEGs work! We're applying the same principles to images – splitting up something into a bunch of sine waves, and then only storing the important ones.

Now we're dealing with images, we need a different type of sine wave. We need to have something that no matter what image we have, we can add up a bunch of these sine waves to get back to our original image.

To do that, each of our sine waves will be images too. Instead of a wave that's a line, we now have images with black and white sections. To represent the size of a wave, each image will have more or less contrast.

We can also use these to represent color in the same way, but let's start with black-and-white images for now. To represent colorless images, we need some horizontal wave images,

<img id="img-y-component" src="img/components-4-0.png" class="sketch sketch-small">

Along with some vertical wave images.

<img id="img-x-component" src="img/components-0-4.png" class="sketch sketch-small">

By themselves, just horizontal and vertical images aren't enough to represent the types of images we get. We also need some extra ones that you get by multiplying the two together.

<div class="multi-container">
<img id="img-mult-x-component" src="img/components-0-4.png" class="sketch sketch-mult">
<div class="maths">×</div>
<img id="img-mult-y-component" src="img/components-4-0.png" class="sketch sketch-mult">
<div class="maths">=</div>
<img id="img-x-y-component" src="img/components-4-4.png" class="sketch sketch-mult">
</div>

For an 8x8 image, here are all the images we need.

<div class="img-component-container">
    <img src="img/components-0-0.png" class="img-component">
    <img src="img/components-0-1.png" class="img-component">
    <img src="img/components-0-2.png" class="img-component">
    <img src="img/components-0-3.png" class="img-component">
    <img src="img/components-0-4.png" class="img-component">
    <img src="img/components-0-5.png" class="img-component">
    <img src="img/components-0-6.png" class="img-component">
    <img src="img/components-0-7.png" class="img-component">
    <img src="img/components-1-0.png" class="img-component">
    <img src="img/components-1-1.png" class="img-component">
    <img src="img/components-1-2.png" class="img-component">
    <img src="img/components-1-3.png" class="img-component">
    <img src="img/components-1-4.png" class="img-component">
    <img src="img/components-1-5.png" class="img-component">
    <img src="img/components-1-6.png" class="img-component">
    <img src="img/components-1-7.png" class="img-component">
    <img src="img/components-2-0.png" class="img-component">
    <img src="img/components-2-1.png" class="img-component">
    <img src="img/components-2-2.png" class="img-component">
    <img src="img/components-2-3.png" class="img-component">
    <img src="img/components-2-4.png" class="img-component">
    <img src="img/components-2-5.png" class="img-component">
    <img src="img/components-2-6.png" class="img-component">
    <img src="img/components-2-7.png" class="img-component">
    <img src="img/components-3-0.png" class="img-component">
    <img src="img/components-3-1.png" class="img-component">
    <img src="img/components-3-2.png" class="img-component">
    <img src="img/components-3-3.png" class="img-component">
    <img src="img/components-3-4.png" class="img-component">
    <img src="img/components-3-5.png" class="img-component">
    <img src="img/components-3-6.png" class="img-component">
    <img src="img/components-3-7.png" class="img-component">
    <img src="img/components-4-0.png" class="img-component">
    <img src="img/components-4-1.png" class="img-component">
    <img src="img/components-4-2.png" class="img-component">
    <img src="img/components-4-3.png" class="img-component">
    <img src="img/components-4-4.png" class="img-component">
    <img src="img/components-4-5.png" class="img-component">
    <img src="img/components-4-6.png" class="img-component">
    <img src="img/components-4-7.png" class="img-component">
    <img src="img/components-5-0.png" class="img-component">
    <img src="img/components-5-1.png" class="img-component">
    <img src="img/components-5-2.png" class="img-component">
    <img src="img/components-5-3.png" class="img-component">
    <img src="img/components-5-4.png" class="img-component">
    <img src="img/components-5-5.png" class="img-component">
    <img src="img/components-5-6.png" class="img-component">
    <img src="img/components-5-7.png" class="img-component">
    <img src="img/components-6-0.png" class="img-component">
    <img src="img/components-6-1.png" class="img-component">
    <img src="img/components-6-2.png" class="img-component">
    <img src="img/components-6-3.png" class="img-component">
    <img src="img/components-6-4.png" class="img-component">
    <img src="img/components-6-5.png" class="img-component">
    <img src="img/components-6-6.png" class="img-component">
    <img src="img/components-6-7.png" class="img-component">
    <img src="img/components-7-0.png" class="img-component">
    <img src="img/components-7-1.png" class="img-component">
    <img src="img/components-7-2.png" class="img-component">
    <img src="img/components-7-3.png" class="img-component">
    <img src="img/components-7-4.png" class="img-component">
    <img src="img/components-7-5.png" class="img-component">
    <img src="img/components-7-6.png" class="img-component">
    <img src="img/components-7-7.png" class="img-component">
</div>

If we take the images, adjust their contrast to the right amount, and then add them up we can create any image.

Let's start with this letter 'A'. It's pretty small, but we need it to be small otherwise we'll end up with too many other images.

<img src="img/a.png" class="sketch sketch-letter">

As we add more and more of these images, we end up with something that becomes closer and closer to the actual image. But I think you'll see the pattern here, as we get a reasonable approximation with just a few of them.

<div class="hidden-preload">
    <img src="img/img-buildup-0-0.png">
    <img src="img/img-buildup-0-1.png">
    <img src="img/img-buildup-0-2.png">
    <img src="img/img-buildup-0-3.png">
    <img src="img/img-buildup-0-4.png">
    <img src="img/img-buildup-0-5.png">
    <img src="img/img-buildup-0-6.png">
    <img src="img/img-buildup-0-7.png">
    <img src="img/img-buildup-1-0.png">
    <img src="img/img-buildup-1-1.png">
    <img src="img/img-buildup-1-2.png">
    <img src="img/img-buildup-1-3.png">
    <img src="img/img-buildup-1-4.png">
    <img src="img/img-buildup-1-5.png">
    <img src="img/img-buildup-1-6.png">
    <img src="img/img-buildup-1-7.png">
    <img src="img/img-buildup-2-0.png">
    <img src="img/img-buildup-2-1.png">
    <img src="img/img-buildup-2-2.png">
    <img src="img/img-buildup-2-3.png">
    <img src="img/img-buildup-2-4.png">
    <img src="img/img-buildup-2-5.png">
    <img src="img/img-buildup-2-6.png">
    <img src="img/img-buildup-2-7.png">
    <img src="img/img-buildup-3-0.png">
    <img src="img/img-buildup-3-1.png">
    <img src="img/img-buildup-3-2.png">
    <img src="img/img-buildup-3-3.png">
    <img src="img/img-buildup-3-4.png">
    <img src="img/img-buildup-3-5.png">
    <img src="img/img-buildup-3-6.png">
    <img src="img/img-buildup-3-7.png">
    <img src="img/img-buildup-4-0.png">
    <img src="img/img-buildup-4-1.png">
    <img src="img/img-buildup-4-2.png">
    <img src="img/img-buildup-4-3.png">
    <img src="img/img-buildup-4-4.png">
    <img src="img/img-buildup-4-5.png">
    <img src="img/img-buildup-4-6.png">
    <img src="img/img-buildup-4-7.png">
    <img src="img/img-buildup-5-0.png">
    <img src="img/img-buildup-5-1.png">
    <img src="img/img-buildup-5-2.png">
    <img src="img/img-buildup-5-3.png">
    <img src="img/img-buildup-5-4.png">
    <img src="img/img-buildup-5-5.png">
    <img src="img/img-buildup-5-6.png">
    <img src="img/img-buildup-5-7.png">
    <img src="img/img-buildup-6-0.png">
    <img src="img/img-buildup-6-1.png">
    <img src="img/img-buildup-6-2.png">
    <img src="img/img-buildup-6-3.png">
    <img src="img/img-buildup-6-4.png">
    <img src="img/img-buildup-6-5.png">
    <img src="img/img-buildup-6-6.png">
    <img src="img/img-buildup-6-7.png">
    <img src="img/img-buildup-7-0.png">
    <img src="img/img-buildup-7-1.png">
    <img src="img/img-buildup-7-2.png">
    <img src="img/img-buildup-7-3.png">
    <img src="img/img-buildup-7-4.png">
    <img src="img/img-buildup-7-5.png">
    <img src="img/img-buildup-7-6.png">
    <img src="img/img-buildup-7-7.png">
</div>
<div id="letter-buildup" class="multi-container">
<img id="letter-buildup-letter" src="img/img-buildup-0-0.png" class="sketch sketch-letter">
<div id="letter-buildup-components" class="img-component-container">
    <img src="img/img-components-0-0.png" class="img-component">
    <img src="img/img-components-0-1.png" class="img-component">
    <img src="img/img-components-0-2.png" class="img-component">
    <img src="img/img-components-0-3.png" class="img-component">
    <img src="img/img-components-0-4.png" class="img-component">
    <img src="img/img-components-0-5.png" class="img-component">
    <img src="img/img-components-0-6.png" class="img-component">
    <img src="img/img-components-0-7.png" class="img-component">
    <img src="img/img-components-1-0.png" class="img-component">
    <img src="img/img-components-1-1.png" class="img-component">
    <img src="img/img-components-1-2.png" class="img-component">
    <img src="img/img-components-1-3.png" class="img-component">
    <img src="img/img-components-1-4.png" class="img-component">
    <img src="img/img-components-1-5.png" class="img-component">
    <img src="img/img-components-1-6.png" class="img-component">
    <img src="img/img-components-1-7.png" class="img-component">
    <img src="img/img-components-2-0.png" class="img-component">
    <img src="img/img-components-2-1.png" class="img-component">
    <img src="img/img-components-2-2.png" class="img-component">
    <img src="img/img-components-2-3.png" class="img-component">
    <img src="img/img-components-2-4.png" class="img-component">
    <img src="img/img-components-2-5.png" class="img-component">
    <img src="img/img-components-2-6.png" class="img-component">
    <img src="img/img-components-2-7.png" class="img-component">
    <img src="img/img-components-3-0.png" class="img-component">
    <img src="img/img-components-3-1.png" class="img-component">
    <img src="img/img-components-3-2.png" class="img-component">
    <img src="img/img-components-3-3.png" class="img-component">
    <img src="img/img-components-3-4.png" class="img-component">
    <img src="img/img-components-3-5.png" class="img-component">
    <img src="img/img-components-3-6.png" class="img-component">
    <img src="img/img-components-3-7.png" class="img-component">
    <img src="img/img-components-4-0.png" class="img-component">
    <img src="img/img-components-4-1.png" class="img-component">
    <img src="img/img-components-4-2.png" class="img-component">
    <img src="img/img-components-4-3.png" class="img-component">
    <img src="img/img-components-4-4.png" class="img-component">
    <img src="img/img-components-4-5.png" class="img-component">
    <img src="img/img-components-4-6.png" class="img-component">
    <img src="img/img-components-4-7.png" class="img-component">
    <img src="img/img-components-5-0.png" class="img-component">
    <img src="img/img-components-5-1.png" class="img-component">
    <img src="img/img-components-5-2.png" class="img-component">
    <img src="img/img-components-5-3.png" class="img-component">
    <img src="img/img-components-5-4.png" class="img-component">
    <img src="img/img-components-5-5.png" class="img-component">
    <img src="img/img-components-5-6.png" class="img-component">
    <img src="img/img-components-5-7.png" class="img-component">
    <img src="img/img-components-6-0.png" class="img-component">
    <img src="img/img-components-6-1.png" class="img-component">
    <img src="img/img-components-6-2.png" class="img-component">
    <img src="img/img-components-6-3.png" class="img-component">
    <img src="img/img-components-6-4.png" class="img-component">
    <img src="img/img-components-6-5.png" class="img-component">
    <img src="img/img-components-6-6.png" class="img-component">
    <img src="img/img-components-6-7.png" class="img-component">
    <img src="img/img-components-7-0.png" class="img-component">
    <img src="img/img-components-7-1.png" class="img-component">
    <img src="img/img-components-7-2.png" class="img-component">
    <img src="img/img-components-7-3.png" class="img-component">
    <img src="img/img-components-7-4.png" class="img-component">
    <img src="img/img-components-7-5.png" class="img-component">
    <img src="img/img-components-7-6.png" class="img-component">
    <img src="img/img-components-7-7.png" class="img-component">
</div>
</div>

For actual JPEG images there are just a few extra details.

The image gets broken up into 8x8 chunks, and each chunk gets split up separately. We use a set of frequencies to determine how light or dark each pixel is, and then another two sets for the color, one for red-green, and another for blue-yellow. The number of frequencies that we use for each chunk determines the quality of the JPEG.

Here's a real JPEG image, zoomed in so we can see the details. When we play with the quality levels we can see this process happen.

<div id="jpeg-example" class="sketch">
    <img src="img/cat.png" class="sketch-child clear-pixels">
</div>

## Conclusion

So let's recap:

- Fourier transforms are things that let us take something and split it up into its frequencies.
- The frequencies tell us about some fundamental properties of the data we have
- And can compress data by only storing the important frequencies
- And we can also use them to make cool looking animations with a bunch of circles

This is just scratching the surface into some applications. The Fourier transform is an extremely powerful tool, because splitting things up into frequencies is so fundamental. They're used in a lot of fields, including circuit design, mobile phone signals, magnetic resonance imaging (MRI), and quantum physics!

## Questions for the curious

I skipped most of the math stuff here, but if you're interested in the underlying principles of how it works, here are some questions you can use to guide your research:

- How do you mathematically represent a Fourier transform?
- What's the difference between a continuous time Fourier transform and a discrete time Fourier transform?
- How do you computationally do a Fourier transform?
- How do you do a Fourier transform of a whole song? (Rather than just a single note.)

## Further 'reading'

To learn more, some really good resources you can check out are:

[An Interactive Guide To The Fourier Transform](https://betterexplained.com/articles/an-interactive-guide-to-the-fourier-transform/)  
A great article that digs more into the mathematics of what happens.

[But what is the Fourier Transform? A visual introduction.](https://www.youtube.com/watch?v=spUNpyF58BY)  
A great Youtube video by 3Blue1Brown, also explaining the maths of Fourier transforms from an audio perspective.

[A Tale of Math & Art: Creating the Fourier Series Harmonic Circles Visualization](https://alex.miller.im/posts/fourier-series-spinning-circles-visualization/)  
Another article explaining how you can use epicycles to draw a path, explained from a linear algebra perspective.

[Fourier transform (Wikipedia)](https://en.wikipedia.org/wiki/Fourier_transform)  
And of course, the Wikipedia article is pretty good too.

## The author

<canvas id="its-meee" class="sketch" width=500 height=500></canvas>

I'm Jez! Full time I work at a [search company](https://www.google.com/) in the Bay Area, and in my spare time I like making games and interactive code things like this!

This webpage is open-source, you can check out the code on [GitHub](https://github.com/Jezzamonn/fourier)! If you have any feedback or want to ask any questions, feel free to email me at <span id="email-text">fourier [at] jezzamon [dot] com</span>, or shoot me a tweet on [Twitter](https://twitter.com/jezzamonn).

If you want to see more of my work, check out my [homepage](/), and if you want to see what I'm making next, you can follow my Twitter account, [@jezzamonn](https://twitter.com/jezzamonn)!
