
---

# Examenoverzicht JavaScript (Deel 1 - 11)

## 1. Basis & Structuur

JavaScript wordt door de browser uitgevoerd om webpagina's interactief te maken. De runtime omgeving is ingebouwd in de browser.

- **Scriptkoppeling**: Plaats de `<script>` tag bij voorkeur net voor de sluitende `</body>` tag om de laadtijd van de pagina niet te vertragen.
    
- **Window Load**: Gebruik altijd een `load` event listener zodat de code pas start als de DOM-tree volledig is opgebouwd.
    
- **Arrow Functions**: De standaard manier om functies te definiëren in deze cursus.
    


```JavaScript
// De standaard opzet van een script
const setup = () => {
    console.log("De DOM is klaar voor gebruik!"); [cite: 182]
};

window.addEventListener("load", setup); [cite: 358, 1110]
```

---

## 2. De DOM-Tree & Navigatie

De **Document Object Model (DOM)** tree is een boomstructuur die de browser opbouwt uit HTML.

- **Nodes**: Elk onderdeel is een 'node'. De bovenste is de **root** (`html`).
    
- **Soorten Nodes**: Er zijn element nodes (tags), text nodes (tekst) en comment nodes.
    
- **Navigatie**: Gebruik properties zoals `firstElementChild`, `lastElementChild` en `nextElementSibling` om tussen elementen te springen.
    


```JavaScript
// Navigeren door de boom
let lijst = document.querySelector("ul");
let eersteItem = lijst.firstElementChild; [cite: 2410]
let tweedeItem = eersteItem.nextElementSibling; [cite: 2411]
let ouder = lijst.parentNode; [cite: 2391]
```

---

## 3. Elementen Selecteren & Manipuleren

Om een element aan te passen, moet je het eerst opvragen via het `document` object.

- **Selecteren**:
    
    - `querySelector(selector)`: Pakt het **eerste** element dat voldoet aan de CSS-selector.
        
    - `querySelectorAll(selector)`: Pakt **alle** elementen in een NodeList.
        
- **Inhoud**:
    
    - `.textContent`: Voor pure tekst (geen HTML verwerking).
        
    - `.innerHTML`: Voor volledige HTML-inhoud; vervangt alle bestaande kinderen.
        
    - `.value`: Alleen voor `<input>` elementen.
        


```JavaScript
// Selecteren en wijzigen
const mijnTitel = document.querySelector("#hoofdtitel"); [cite: 1328]
mijnTitel.textContent = "Nieuwe Tekst"; [cite: 147]

const inputVeld = document.querySelector(".gebruikersnaam");
let naam = inputVeld.value; [cite: 284]

// Attributen aanpassen
const afbeelding = document.querySelector("img");
afbeelding.setAttribute("src", "foto.jpg"); [cite: 1493, 1506]
```

---

## 4. Events (Interactie)

JavaScript reageert op gebeurtenissen via **event listeners**.

- **Event Object**: De listener ontvangt een object (meestal `e` of `event`) met nuttige info.
    
- **Bubbling**: Events "borrelen" omhoog naar ancestors.
    
- **`event.target`**: Het element waarop effectief geklikt is.
    


```JavaScript
const knopKlik = (event) => {
    console.log("Je klikte op: " + event.target.nodeName); [cite: 1567]
    event.preventDefault(); // Stopt standaardgedrag (bijv. link volgen) [cite: 1591]
};

let knop = document.querySelector("#saveBtn");
knop.addEventListener("click", knopKlik); [cite: 1079] // LET OP: Geen haakjes () [cite: 1082]
```

---

## 5. Variabelen, Getallen & Arrays

- **Numbers**: Alle getallen zijn kommagetallen met dubbele precisie. Gebruik `Number.parseInt()` of `Number.parseFloat()` voor conversie.
    
- **Math**: `Math.random()` geeft een getal tussen 0 en 1. Gebruik `Math.floor()` om naar beneden af te ronden naar een geheel getal.
    
- **Arrays**: Dynamische lijsten.
    
    - `push()`: Toevoegen aan het einde.
        
    - `sort()`: Sorteert het array (gebruik een vergelijkingsfunctie!).
        


```JavaScript
// Array sorteren (getallen)
let cijfers = [10, 5, 80, 2];
cijfers.sort((a, b) => a - b); [cite: 1735, 1739]

// Strings vergelijken
let s1 = "appel";
let s2 = "peer";
let resultaat = s1.localeCompare(s2); [cite: 1665, 1668]
```

---

## 6. Objecten & JSON

Objecten bundelen data in properties.

- **Object Literal**: `let student = { naam: "Jan", leeftijd: 20 };`.
    
- **JSON**: Gebruikt voor data-uitwisseling.
    
    - `JSON.stringify(obj)`: Object naar tekst.
        
    - `JSON.parse(str)`: Tekst naar object.
        


```JavaScript
// Object maken
let product = {
    id: 1,
    naam: "Laptop",
    prijs: 999
};

// Opslaan in LocalStorage (vereist string)
localStorage.setItem("productData", JSON.stringify(product)); [cite: 1872]
```

---

## 7. Storage & Error Handling

- **LocalStorage**: Bewaart data permanent in de browser.
    
- **SessionStorage**: Data verdwijnt als het tabblad sluit.
    
- **Try...Catch**: Voorkomt dat het script crasht bij runtime errors.
    


```JavaScript
try {
    let opgeslagenData = localStorage.getItem("productData");
    let data = JSON.parse(opgeslagenData);
} catch (error) {
    console.error("Fout bij het laden van data!"); [cite: 1872]
}
```

---
