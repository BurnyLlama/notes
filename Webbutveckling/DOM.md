---
title: "DOM (Document Object Model)"
keywords:
  - DOM
  - Document Object Model
...

# Vad är DOM?
DOM står för _Document Object Model_. DOM kan modifieras med hjälp av Javascript.

# Omorganisera kod
Tack vare DOM, så går det att separera koden till tre "delar":
1. Struktur (HTML)
2. Stil/design (CSS)
3. Funktion (Javascript)
Detta med hjälp av externa filer som kan laddas in via något av följande:
```html
<head>
    ...
    <link type="text/css" rel="stylesheet" href="./path/to/file.css">
    <script defer type="text/javascript" src="./path/to/script.js"></script>
    ...
</head>
```
`<link>` används för _style sheets_, alltså CSS. Medan `<script>` används för Javascript.

## Exempel på filstruktur
```
Project
|- scripts
|  |- script.js
|- style
|  |- styles.css
|- html
   |- index.html
```

# Struktur på DOM
DOM skapar en struktur som är som en hierarki, eller _familj_, med de olika elementen. Man kan säga att det är organiserade som "lådor".
```
,-------------------------------------,
| html                                |
| ,---------------------------------, |
| | head                            | |
| | ,-----------------------------, | |
| | | title                       | | |
| | '-----------------------------' | |
| | ,-----------------------------, | |
| | | link                        | | |
| | '-----------------------------' | |
| '---------------------------------' |
| ,---------------------------------, |
| | body                            | |
| | ,-----------------------------, | |
| | | h1                          | | |
| | '-----------------------------' | |
| | ,-----------------------------, | |
| | | p                           | | |
| | '-----------------------------' | |
| '---------------------------------' |
'-------------------------------------'
```

# Modifiera ett DOM-element
För att ändra ett element måste man först hitta element, det finns flera sätt för det:
```js
document.querySelector("selector")    // Hitta ett element med CSS-selector
document.querySelectorAll("selector") // Hitta alla element med CSS-selector

document.getElementById("id")  // Hitta ett element via ett ID
document.getElementsById("id") // Hitta alla element via ett ID

document.getElementByTagName("id")  // Hitta ett element via dess tag
document.getElementsByTagName("id") // Hitta alla element via dess tag
```

## Exempel 1
HTML:
```html
<p class="change-me">Hello world!</p>
```
Förväntat resultat:
> Hello world!

Med Javascript:
```js
const element = document.querySelector(".change-me")
element.innerText = "Bye bye world!"
```
Nytt förväntat resultat:
> Bye bye world!

## Exempel 2
HTML:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Change DOM</title>
    <script src="./main.js" defer></script>
</head>
<body>
    <p id="my-paragraph" style="color: red">Roses are red, violets are blue,</p>
    <h1 id="my-h1" style="background-color: pink">But no flower is as beautiful as you</h1>
    <button id="my-button">OK</button>
</body>
</html>
```
Javascript:
```js
const myButton = document.querySelector("#my-button")
const myH1     = document.querySelector("#my-h1")

myButton.addEventListener(
    "click",
    () => myH1.innerText = "Unexpected error on line 32."
)
```
Förväntat resultat:
![4de1f0d1fe3858d5af13dffff6658e56.png](4de1f0d1fe3858d5af13dffff6658e56.png)
Förväntat resultat när knappen ("OK") trycks:
![92dfe7e89eede024bb12d849116210e2.png](92dfe7e89eede024bb12d849116210e2.png)
