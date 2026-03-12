<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Undangan Alumni Muria</title>

<style>

body{
margin:0;
font-family:'Segoe UI',sans-serif;
background:#f5f5f5;
text-align:center;
color:#333;
}

/* OPENING */

#opening{
height:100vh;
display:flex;
flex-direction:column;
justify-content:center;
align-items:center;
background:linear-gradient(120deg,#1d2671,#c33764);
color:white;
}

#opening button{
margin-top:20px;
padding:12px 30px;
border:none;
border-radius:30px;
font-size:18px;
cursor:pointer;
}

/* SECTION */

section{
padding:70px 20px;
}

.card{
background:white;
max-width:520px;
margin:auto;
padding:30px;
border-radius:15px;
box-shadow:0 15px 30px rgba(0,0,0,0.1);
}

/* SCROLL ANIMATION */

.fade{
opacity:0;
transform:translateY(40px);
transition:1s;
}

.fade.show{
opacity:1;
transform:translateY(0);
}

/* BUTTON */

.btn{
display:inline-block;
margin-top:15px;
padding:10px 25px;
background:#e91e63;
color:white;
border-radius:30px;
text-decoration:none;
}

/* SLIDER */

.slider{
position:relative;
max-width:500px;
margin:auto;
}

.slide{
display:none;
}

.slide img{
width:100%;
border-radius:10px;
}

.prev,.next{
position:absolute;
top:50%;
transform:translateY(-50%);
font-size:25px;
background:white;
border:none;
cursor:pointer;
padding:10px;
}

.prev{left:5px;}
.next{right:5px;}

/* COUNTDOWN */

#countdown{
font-size:22px;
color:#e91e63;
margin-top:15px;
}

footer{
background:#222;
color:white;
padding:20px;
margin-top:40px;
}

</style>

</head>

<body>

<!-- OPENING -->

<div id="opening">

<h1>The Alumni Reuni</h1>

<p>Kepada Yth.</p>

<h2 id="namaTamu">Tamu Undangan</h2>

<button onclick="buka()">Buka Undangan</button>

</div>

<div id="isi" style="display:none">

<!-- DETAIL ACARA -->

<section class="fade">

<div class="card">

<h2>Detail Acara</h2>

<p><b>Tanggal</b><br>21 Maret 2026</p>

<p><b>Jam</b><br>07:00 WIB</p>

<p><b>Lokasi</b><br>Temboro</p>

<a class="btn" href="https://maps.app.goo.gl/j85ShZEQHMMTrL8P8">
Lihat Lokasi
</a>

</div>

</section>

<!-- COUNTDOWN -->

<section class="fade">

<div class="card">

<h2>Menuju Hari Acara</h2>

<div id="countdown"></div>

</div>

</section>

<!-- GALERI SLIDE -->

<section class="fade">

<div class="card">

<h2>Galeri</h2>

<div class="slider">

<div class="slide">
<img src="foto1.jpg">
</div>

<div class="slide">
<img src="foto2.jpg">
</div>

<div class="slide">
<img src="foto3.jpg">
</div>

<button class="prev" onclick="plusSlide(-1)">❮</button>
<button class="next" onclick="plusSlide(1)">❯</button>

</div>

</div>

</section>

<!-- RSVP WHATSAPP -->

<section class="fade">

<div class="card">

<h2>Konfirmasi Kehadiran</h2>

<input id="nama" placeholder="Nama"><br><br>

<select id="hadir">

<option>Hadir</option>
<option>Tidak Hadir</option>

</select><br><br>

<button class="btn" onclick="kirimWA()">Kirim RSVP</button>

</div>

</section>

<!-- AMPL0P DIGITAL -->

<section class="fade">

<div class="card">

<h2>Amplop Digital</h2>

<p>Muamalat</p>

<p><b>7420024711</b></p>

<p>a.n Ammar</p>

</div>

</section>

<footer>

Terima kasih atas doa dan kehadiran Anda

</footer>

</div>

<script>

/* NAMA TAMU OTOMATIS */

const params=new URLSearchParams(window.location.search);
const tamu=params.get("to");

if(tamu){
document.getElementById("namaTamu").innerText=tamu;
}

/* BUKA UNDANGAN */

function buka(){
document.getElementById("opening").style.display="none";
document.getElementById("isi").style.display="block";
}

/* COUNTDOWN */

var tanggal=new Date("Mar 21, 2026 07:00:00").getTime();

setInterval(function(){

var now=new Date().getTime();
var jarak=tanggal-now;

var h=Math.floor(jarak/(1000*60*60*24));
var j=Math.floor((jarak%(1000*60*60*24))/(1000*60*60));

document.getElementById("countdown").innerHTML=
h+" Hari "+j+" Jam";

},1000);

/* SLIDER */

var slideIndex=0;
showSlide();

function plusSlide(n){
slideIndex+=n;
showSlide();
}

function showSlide(){

var i;
var slides=document.getElementsByClassName("slide");

if(slideIndex>=slides.length){slideIndex=0;}
if(slideIndex<0){slideIndex=slides.length-1;}

for(i=0;i<slides.length;i++){
slides[i].style.display="none";
}

slides[slideIndex].style.display="block";

}

/* RSVP WHATSAPP */

function kirimWA(){

var nama=document.getElementById("nama").value;
var hadir=document.getElementById("hadir").value;

var pesan="Halo, saya "+nama+" konfirmasi kehadiran: "+hadir;

var nomor="628214364168";

window.open("https://wa.me/"+nomor+"?text="+encodeURIComponent(pesan));

}

/* SCROLL ANIMATION */

const fades=document.querySelectorAll('.fade');

window.addEventListener('scroll',()=>{

fades.forEach(el=>{

if(el.getBoundingClientRect().top < window.innerHeight-100){

el.classList.add('show');

}

});

});

</script>

</body>
</html>
