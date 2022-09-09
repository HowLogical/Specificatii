# 1. Tipuri de date

Vom considera 3 categorii principale de tipuri de date:  
1. Tipuri de baza (**primitive**)
2. Tipuri complexe (**clase**)
3. Multimi

## 1.1. Tipuri de baza (**primitive**)

Tipurile de baza (sau primtive) sunt tipuri de date pe care le consideram predefinite si indivizibile. Acestea constituie "atomii" din care se pot compune alte tipuri de date mai complexe.  
Tipurile de baza sunt:  
- **text** (sau string)
    - Reprezinta un sir de caractere de lungime variabila.
    - Valorile se delimiteaza de ghilimele.
    - Daca valoarea textului contine ghilimele, acestea vor fi precedate de un backslash (ex.: \\").
    - Daca valoarea textului contine un backslash, acesta va fi precedat de inca un backslash (ex.: \\\\).
    - Exemple de valori:
        - "Contract de comodat"
        - "R/456/2020"
        - "1234"
        - "Napoleon a spus \\"Niciodata nu-ţi întrerupe inamicul cât timp acesta face o greşeală\\"."
        - "http:\\\\\\\\www.google.com" (a se observa dublarea backslash-ului)
- **intreg** (sau int)
    - Reprezinta un numar intreg (pozitiv sau negativ).
    - Exemple de valori: 
        - 1052
        - -5
        - 0
- **real**
    - Reprezinta un numar real (pozitiv sau negativ).
    - Separatorul de zecimale va fi considerat "." (punctul).
    - Exemple de valori:
        - 5
        - -0.025
        - 7.03
- **boolean**
    - Poate lua doar 2 valori: **true** sau **false**.
- **data**
    - Reprezinta o data calendaristica.
    - Se noteaza intre ghilimele (asemanator unui **text**) dar respecta formatul "aaaa-ll-zz", unde aaaa reprezinta cifrele anului, ll reprezinta cifrele lunii si zz reprezinta cifrele zilei.
    - Exemple de valori:
        - "2022-09-09"
        - "2024-01-31"
- **timp**
    - Reprezinta o valoare de timp exprimata in ore, minute, secunde.
    - Se noteaza intre ghilimele (asemanator unui **text**) dar respecta formatul "hh:mm:ss", unde hh reprezinta cifrele orei, mm reprezinta cifrele minutului si ss reprezinta cifrele secundei.
    - Exemple de valori:
        - "00:00:00"
        - "23:01:15"
        - "07:04:13"
- **moment**
    - Reprezinta o valoare de **data** + **timp** exprimata in ani, luni, zile, ore, minute, secunde.
    - Se noteaza intre ghilimele (asemanator unui **text**) dar respecta formatul "aaaa-ll-zz hh:mm:ss", unde aaaa reprezinta cifrele anului, ll reprezinta cifrele lunii si zz reprezinta cifrele zilei, hh reprezinta cifrele orei, mm reprezinta cifrele minutului si ss reprezinta cifrele secundei.
    - Componenta de timp se poate omite si se considera implicit 00:00:00
    - Exemple de valori:
        - "2019-05-31 23:00:59"
        - "2022-09-09" *(se considera "2022-09-09 00:00:00")*
- **id**
    - Reprezinta un identificator unic aleator

## 1.2. Tipuri complexe de date (**clase**)
Tipurile complexe de date (clasele) sunt folosite pentru a reprezenta obiecte ce contin o serie de proprietati si nu pot fi definite print-un singur tip primtiv. Clasele servesc drept "template-uri" pentru crearea de obiecte.  

- O **clasa** este reprezentata de denumirea sa (ex.: `ActIdentitate`).
- Denumirea unei **clase** este **unica** in contextul aplicatiei.
- O **clasa** este alcatuita din **proprietati**.
- O **proprietate** este alcatuita din:  
    1. Denumirea proprietatii
    2. Tipul proprietatii (poate fi oricare din cele 3 categorii de tipuri de date)
- Denumirea unei proprietati este unica in clasa. De exemplu o clasa de tip Persoana nu poate avea o proprietate cu denumirea "varsta" de tip string si alta proprietate tot cu denumirea "varsta" dar de tip intreg.
- Denumirea clasei sau a unei proprietati va putea contine doar litere si cifre (fara spatii sau alte caractere speciale). De asemenea, primul caracter este obligatoriu o litera.
- Denumirea clasei va fi in format [PascalCase](https://wiki.c2.com/?PascalCase) (prima litera mare).
- Denumirea unei proprietati va fi in format [camelCase](https://en.wikipedia.org/wiki/Camel_case) (prima litera mica).

### 1.2.1. Reprezentare ca text
Putem reprezenta o clasa sub forma de text in urmatorul mod:
```javascript
clasa DenumireClasa {
    denumireProprietate1: TipProprietate1
    denumireProprietate2: TipProprietate2
    ...
    denumireProprietateN: TipProprietateN
}
```
- Denumirea clasei este precedata de cuvantul "clasa".
- Proprietatile clasei sunt delimitate de un set de acolade
- O proprietate este scrisa sub forma `denumireProprietate: TipProprietate`
- Fiecare proprietate este scrisa pe un rand nou
- Daca este necesar, se pot adauga comentarii si observatii daca sunt precedate de doua slash-uri (//)

Exemple:
```javascript
clasa ActIdentitate {
    id: id
    cnp: text
    serie: text
    nr: text //Numarul cartii de identitate
    nume: text
    prenume: text
    dataEliberare: data
    dataExpirare: data
}
```
```javascript
clasa Persoana {
    id: id
    nume: text
    prenume: text
    acteIdentitate: ActIdentitate[] //Multimea actelor de identitate ce apartin persoanei
    mama: Persoana
    tata: Persoana 
}
```
*Nota: A se vedea sectiunea 1.3. pentru explicatia notatiei "[]"*

### 1.2.2. Reprezentare sub forma tabelara
Putem reprezenta o clasa sub forma de tabel in urmatorul mod:  

**DenumireClasa**  
|Denumire|Tip|Observatii|
|---|---|---|
|denumireProprietate1|TipProprietate1|Observatie1|
|denumireProprietate2|TipProprietate2|Observatie2|
|...|...|...|
|denumireProprietateN|TipProprietateN|ObservatieN|

**Exemple:**  

**ActIdentitate**  
|Denumire|Tip|Observatii|
|---|---|---|
|id|id||
|cnp|text||
|serie|text||
|nr|text|Numarul cartii de identitate|
|nume|text||
|prenume|text||
|dataEliberare|data||
|dataExpirare|data||

**Persoana**
|Denumire|Tip|Observatii|
|---|---|---|
|id|id||
|nume|text||
|prenume|text||
|acteIdentitate|ActIdentitate[]|Multimea actelor de identitate ce apartin persoanei|
|mama|Persoana||
|tata|Persoana||

*Nota: A se vedea sectiunea 1.3. pentru explicatia notatiei "[]"*

### 1.2.3. Mostenire de clase
- O clasa poate mosteni una sau mai multe clase.
- Clasa mostenita se numeste clasa parinte iar clasa mostenitoare se numeste clasa copil.
- Clasa copil preia toate proprietatile clasei parinte (si a claselor mostenite de clasa parinte daca este cazul)
- Mostenirea nu se poate realiza daca se creeaza un ciclu (de exemplu o clasa A nu poate mosteni o clasa B daca simultan clasa B mosteneste clasa A)
- Mostenirea nu se poate realiza daca exista un conflict de tipuri intre proprietati
- Un obiect de tipul clasei Parinte poate fi substituit cu un obiect de tipul unei clase Copil (a se vedea capitolul "2. Variabile" pentru exemple)
- Notam mostenirea in continuarea denumirei clasei prin cuvantul "mosteneste" urmat de denumirile claselor parinte separate prin virgula.
    ```javascript
    clasa A { }
    clasa B { }
    clasa C mosteneste A, B {

    }
    ```
**Exemplu:**
```javascript
clasa Entitate {
    id: id
}
// Proprietati Entitate:
// id: id


// Clasa Persoana va prelua proprietatea "id" de la Entitate
clasa Persoana mosteneste Entitate {
    nume: text
    prenume: text
}
// Proprietati Persoana:
// id: id
// nume: text
// prenume: text


// Clasa Politist va prelua proprietatile "id", "nume" si "prenume" de la Persoana
clasa Politist mosteneste Persoana {
    nrLegitimatie: text
}
// Proprietati Politist:
// id: id
// nume: text
// prenume: text
// nrLegitimatie: text
```

## 1.3. Multimi
- Multimile se noteaza adaugand 2 paranteze patrate in continuarea denumirii unui tip si reprezinta in sine un tip nou
- Se pot realiza multimi de oricare din cele 3 tipuri principale:
    1. Multimi de primitive
    2. Multimi de tipuri complexe
    3. Multimi de multimi
- Multimile se considera a fi implicit neordonate
- Exemple:
    - **text**[] - reprezinta o multime de texte
    - **real**[] - reprezinta o multime de numere reale
    - **ActIdentitate**[] - reprezinta o multime de acte de identitate
    - **Persoana**[] - reprezinta o multime de persoane
    - **Persoana\[\]**[] - reprezinta o multime de multimi de persoane

# 2. Variabile

### 1.2.4. Obiecte

### 1.2.4. Exemple de valori 
```javascript
//Fie `andra` un obiect de tip Persoana (conform definitiei de la 1.2.2).  
fie andra: Persoana = {
    id: "0b809da0-5933-4785-be89-8e3e6d5e9abd",
    nume: "Stan"
    prenume: "Andra"
    acteIdentitate: [
        {
            id: id
            cnp: text
            serie: text
            nr: text //Numarul cartii de identitate
            nume: text
            prenume: text
            dataEliberare: data
            dataExpirare: data
        }
    ],
    mama: null
    tata: null
}
```

# 3. Functii

## 2.1. Functii de baza