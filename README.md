Sekä README että .html tiedosto tehty Claude tekoälyllä

# Uusien ohjeiden lisääminen sivustolle

Tämä opas kertoo, miten lisäät uusia PDF-ohjeita STM32 Ohjeet -sivustolle. Prosessi koostuu kahdesta vaiheesta: PDF-tiedoston lisäämisestä oikeaan kansioon ja `index.html`-tiedoston päivittämisestä.

---

## Kansiorakenne

Sivuston tiedostot on järjestetty seuraavasti:

```
STM32-Ohjeet/
├── index.html
├── Näytöt/
│   └── ssd1306-ssd1315/
│       └── ssd1306_ohje.pdf
├── Anturit/
│   └── dht22/
│       └── dht22_ohje.pdf
```

Rakenne on aina kolmitasoinen:
1. **Kategoria** – esim. `Näytöt`, `Anturit`, `Kommunikaatio`
2. **Alakategoria** – esim. `ssd1306-ssd1315`, `dht22`
3. **PDF-tiedosto** – esim. `ssd1306_ohje.pdf`

---

## Vaihe 1 – Lisää PDF-tiedosto oikeaan kansioon

Luo tarvittaessa uusi kansio ja kopioi PDF sinne.

## Vaihe 2 – Päivitä index.html

Avaa `index.html` tekstieditorilla ja etsi `manuals`-muuttuja tiedoston loppupuolelta. Se näyttää tältä:

```javascript
const manuals = {
  "Näytöt": {
    "SSD1306 / SSD1315": [
      { name: "SSD1306 Ohje", file: "Näytöt/ssd1306-ssd1315/ssd1306_ohje.pdf" }
    ]
  }
};
```

### Tapaus A – Lisää ohje olemassa olevaan alakategoriaan

Lisää uusi rivi kyseisen alakategorian listaan:

```javascript
const manuals = {
  "Näytöt": {
    "SSD1306 / SSD1315": [
      { name: "SSD1306 Ohje",      file: "Näytöt/ssd1306-ssd1315/ssd1306_ohje.pdf" },
      { name: "SSD1306 Pikaohje",  file: "Näytöt/ssd1306-ssd1315/ssd1306_pikaohje.pdf" }
    ]
  }
};
```

### Tapaus B – Lisää uusi alakategoria olemassa olevaan kategoriaan

```javascript
const manuals = {
  "Näytöt": {
    "SSD1306 / SSD1315": [
      { name: "SSD1306 Ohje", file: "Näytöt/ssd1306-ssd1315/ssd1306_ohje.pdf" }
    ],
    "ILI9341": [
      { name: "ILI9341 Ohje", file: "Näytöt/ili9341/ili9341_ohje.pdf" }
    ]
  }
};
```

### Tapaus C – Lisää kokonaan uusi kategoria

```javascript
const manuals = {
  "Näytöt": {
    "SSD1306 / SSD1315": [
      { name: "SSD1306 Ohje", file: "Näytöt/ssd1306-ssd1315/ssd1306_ohje.pdf" }
    ]
  },
  "Anturit": {
    "DHT22": [
      { name: "DHT22 Ohje", file: "Anturit/dht22/dht22_ohje.pdf" }
    ]
  }
};
```

---

