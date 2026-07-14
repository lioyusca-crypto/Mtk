<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Math COC Challenge</title>

<style>
body{
background:#111;
color:white;
font-family:Arial;
display:flex;
justify-content:center;
align-items:center;
min-height:100vh;
}

.box{
background:#222;
padding:25px;
border-radius:20px;
width:90%;
max-width:500px;
text-align:center;
}

.card{
background:#333;
padding:20px;
border-radius:15px;
animation:show .3s;
}

@keyframes show{
from{transform:scale(.8);opacity:0}
to{transform:scale(1);opacity:1}
}

pre{
font-size:25px;
}

input{
padding:12px;
width:80%;
border-radius:10px;
border:0;
}

button{
padding:12px 25px;
border-radius:10px;
border:0;
}

</style>
</head>

<body>

<div class="box">

<div id="namaBox">
<h2>Masukkan Nama</h2>
<input id="nama" placeholder="Nama">
<br><br>
<button onclick="mulai()">Mulai</button>
</div>

<div id="game" style="display:none">

<h1>🧠 Math COC</h1>

<h3 id="nomor"></h3>

<div id="soal"></div>

<br>

<input id="jawab" type="number" placeholder="Jawaban">

<br><br>

<button onclick="cek()">Submit</button>

</div>

</div>


<script>

let soal=[

[
`<pre>
      A B
    + A B
    ------
      B C C
</pre>
Tentukan nilai AB`,
"61"
],

["51² - 39² = ?","1080"],

["Barisan 1,3,5,7,9,... suku ke-20?","39"],

["2x+3y=27 dan x+y=10. Nilai x?","3"],

["Bilangan 3 digit jumlah digit 12. Angka tersebut?","543"],

["1+2+3+...+200 = ?","20100"],

["a+b=15 dan ab=56. Nilai a²+b²?","113"],

["Luas permukaan kubus 294 cm². Volume?","343"],

["Pola 3,8,15,24,35,... suku ke-10?","120"],

["8 orang berjabat tangan satu kali. Total?","28"]

];


let nomor=0;
let nilai=0;
let namaUser="";
let hasilJawaban=[];


function mulai(){

namaUser=document.getElementById("nama").value;

if(namaUser==""){
alert("Isi nama dulu");
return;
}

localStorage.setItem("nama",namaUser);

document.getElementById("namaBox").style.display="none";
document.getElementById("game").style.display="block";

tampil();

}


function tampil(){

document.getElementById("nomor").innerHTML=
"Soal "+(nomor+1)+"/10";

document.getElementById("soal").innerHTML=
"<div class='card'>"+
soal[nomor][0].replace(/\n/g,"<br>")+
"</div>";

}


function cek(){

let jawab=
document.getElementById("jawab").value;


if(jawab==soal[nomor][1]){
nilai++;
}


hasilJawaban.push(
"Nomor "+(nomor+1)+
" | Jawab: "+jawab+
" | Benar: "+soal[nomor][1]
);


nomor++;

document.getElementById("jawab").value="";


if(nomor<10){

tampil();

}else{


let kata;


if(nilai<=3)
kata="bodoh 62 iq ini";

else if(nilai<=6)
kata="iq setara monyet ini 85";

else if(nilai<=9)
kata="gile nyontek ini";

else
kata="Jan make ai anjg";


document.querySelector(".box").innerHTML=

"<h1>🎉 Selesai</h1>"+
"<h2>"+namaUser+"</h2>"+
"<h2>Nilai: "+nilai+"/10</h2>"+
"<p>"+kata+"</p>"+
"<hr>";


}

}

</script>

</body>
</html>
