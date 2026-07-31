# SRA-karta

Karta över Sveriges SRA-föreningar, med en cirkel på 100 km radie runt varje förening. Det gör
det lätt att se vilka delar av landet som ligger inom rimligt avstånd från en förening, och var
upptagningsområdena överlappar.

Elva föreningar finns med, från Bodens Sportskytteklubb i norr till P 7 Skif i söder.

## Använda kartan

Öppna `index.html` i valfri webbläsare. Det finns inget bygge, inga beroenden att installera
och ingen server — Leaflet ligger inbäddat direkt i filen, vilket är varför den är ca 165 kB.

**Kartrutorna hämtas däremot över nätet** från OpenStreetMap. Utan internet ritas markörerna och
cirklarna ut på rätt plats, men bakgrundskartan blir tom.

Repot är publikt men har ingen GitHub Pages-publicering påslagen. Vill du ha kartan på en
webbadress i stället för som lokal fil räcker det att slå på Pages för `master`-grenen.

## Uppdatera föreningslistan

Allt som är handskrivet ligger i arrayen `foreningar` nära slutet av `index.html`:

```js
var foreningar = [
  { namn: 'S:t Eskils Skyttar', lat: 59.3717, lng: 16.5098 },
  …
];
```

Lägg till, ta bort eller rätta poster där — namn plus koordinater i decimalgrader. Resten av
filen ovanför är det inbäddade Leaflet-biblioteket i minifierad form.

**Kör aldrig filen genom en formaterare eller minifierare.** Den skulle skriva om det inbäddade
biblioteket, och diffen blir omöjlig att granska. Redigera bara arrayen och den korta koden runt
kartan.

Vill du ändra radien är det `radius: 100000` (meter) i `L.circle`-anropet strax under listan.

## Attribution

Kartrutor © [OpenStreetMap](https://www.openstreetmap.org/copyright)s bidragsgivare, renderade
med [Leaflet](https://leafletjs.com). Attributionen visas i kartans nedre högra hörn.
