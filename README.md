<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="style.css">
    <title>Test</title>
</head>
<body onload="pozadina()" id="telo" >
 
    <div class="forma">
        <input type="text" placeholder="Ime" id="ime">
        <input type="text" placeholder="Prezime" id="prezime">
        <select name="zemlja" id="zemlja">
            <option value="Srbija" selected>Srbija</option>
            <option value="Nemacka">Nemacka</option>
            <option value="Bugarska">Bugarska</option>
        </select>
        <input type="password" id="lozinka" placeholder="Lozinka">
        <div class="radio">
            <input type="radio" name="prihvata" id="prihvata" checked>
            <p>Prihvatam uslove</p>
            <input type="radio" name="prihvata" id="odbija">
            <p>Ne prihvatam uslove</p>
        </div>
        <button onclick="proveri()">Proveri</button>
        <br>
        <input type="text" placeholder="frekSlova" id="frekslova">
        <button onclick="frekSlova()">Prikazi</button>
        <div class="prikaz">
            <div class="kolona" id="slova">
            </div>
            <div class="kolona" id="brojevi">
            </div>
        </div>
    </div>
 
    <script src="script.js"></script>
</body>
</html>
 
 
 
 
body{
    margin: 0;
    width: 100vw;
    height: 100vh;
 
    display: flex;
    justify-content: center;
    align-items: center;
}
 
.forma{
    width: 50%;
    height: 75%;
    margin: 0;
 
    border-radius: 20rem;
    background-color: white;
    box-shadow: 0px 0px 55px 10px black;
 
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    gap: 1rem;
}
 
.radio{
    display: flex;
    gap: 1rem;
}
 
.pozadina1{
    background-image: url(https://unsplash.it/id/273/1920/1080);
}
.pozadina2{
    background-image: url(https://unsplash.it/id/192/1920/1080);
}
 
.prikaz{
    display: flex;
    margin: 0;
    gap: 1rem;
}
 
.kolona{
    display: flex;
    flex-direction: column;
}
 
.kolona p{
    margin: 0;
}
 
 
 
function pozadina(){
    datum = new Date();
    datumPozadine = new Date("2015-12-31")
 
 
    if (datum < datumPozadine){
        document.getElementById('telo').classList.add('pozadina1');
    }
    else{
        document.getElementById('telo').classList.add('pozadina2');
    }
}
 
 
function proveri(){
 
    let boolIme = false;
    let boolPrezime = false;
    let boolLozinka = false;
 
 
    let ime = document.getElementById('ime').value;
    let prezime = document.getElementById('prezime').value;
    let lozinka = document.getElementById('lozinka').value;
 
    if(ime != '' && ime != null){
        boolIme = true;
    }
 
    if(prezime != '' && prezime != null){
        boolPrezime = true;
    }
 
    if(lozinka != '' && lozinka != null){
        boolLozinka = true;
    }
 
    if(document.getElementById('odbija').checked){
        alert("Niste prihvatili uslove")
    }
 
 
    if(boolLozinka && boolIme && boolPrezime){
        alert("Korektan unos");
    }
    else{
        alert("Los unos");
    }
}
 
 
function frekSlova(){
    let string = document.getElementById("frekslova").value;
    let niz = string.split('');
 
    let el = []
    let brojac = []
 
    for (let i = 0; i < niz.length; i++) {
        if(!el.includes(niz[i])){
            el.push(niz[i]);
        }
    }
 
    for (let i = 0; i < el.length; i++) {
        br = 0;
        for (let j = 0; j < niz.length; j++) {
            if(el[i] == niz[j]){
                br++;
            }
        }
        brojac.push(br)
    }
 
    for (let i = 0; i < el.length; i++) {
        document.getElementById("slova").innerHTML += '<p>' + el[i] + '</p>';
    }
 
    for (let i = 0; i < brojac.length; i++) {
        document.getElementById("brojevi").innerHTML += '<p>' + brojac[i] + '</p>'; 
    }
 
}
