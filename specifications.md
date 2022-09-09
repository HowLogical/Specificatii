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
clasa [DenumireClasa] {
    [denumireProprietate1]: [TipProprietate1]
    [denumireProprietate2]: [TipProprietate2]
    ...
    [denumireProprietateN]: [TipProprietateN]
}
```
- Denumirea clasei este precedata de cuvantul "clasa".
- Proprietatile clasei sunt delimitate de un set de acolade
- O proprietate este scrisa sub forma `[denumireProprietate]: [TipProprietate]`
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

**[DenumireClasa]**  
|Denumire|Tip|Observatii|
|---|---|---|
|[denumireProprietate1]|[TipProprietate1]|[Observatie1]|
|[denumireProprietate2]|[TipProprietate2]|[Observatie2]|
|...|...|...|
|[denumireProprietateN]|[TipProprietateN]|[ObservatieN]|

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
- Ordinea implicita a elementelor este ordinea inserarii in multime (primul element inserat este primul din lista)
- Exemple de tipuri de multimi:
    - **text**[] - reprezinta o multime de texte
    - **real**[] - reprezinta o multime de numere reale
    - **ActIdentitate**[] - reprezinta o multime de acte de identitate
    - **Persoana**[] - reprezinta o multime de persoane
    - **Persoana\[\]**[] - reprezinta o multime de multimi de persoane
- Valorile concrete ale unei multimi vor fi ilustrate in paranteze patrate (de exemplu in cazul variabilelor)
- Exemple de valori de multimi:
    ```javascript
    [1, 2, 3, 4]     //-> Multime de tip intreg[]
    [1, 2.2, 3.0, 4] //-> Multime de tip real[]
    ["Exemplu", "de", "multime"] //-> Multime de tip text[]
    [
        [1, 0, 0],
        [0, 1, 0],
        [0, 0, 1]
    ]   //-> Multime de tip intreg[][] (matrice)
    ```

## 1.4. Valoarea null
- Implicit orice tip din cele 3 categorii principale poate lua valoarea **null**.
- Pentru a specifica o proprietate sau o variabila care nu poate lua valoarea **null** putem adauga un "!" dupa tip.
- Exemple:
    ```javascript
    clasa TipStrada {
        denumire: text! //Un obiect de tip TipStrada nu poate exista fara denumire
        abreviere: text
    }
    ```
     ```javascript
    clasa Profesor {
        // ...
    }

    clasa Elev {
        diriginte: Profesor! //Un obiect de tip Elev nu poate exista fara sa aiba asociat un diriginte de tip Profesor
    }
    ```

# 2. Variabile
- O variabila reprezinta un simbol prin care se face trimitere la o valoare de un anumit tip.
- Le putem folosi pentru a reprezenta valori temporare atunci cand descriem algoritmi.
- Declaram variabilele prin cuvantul "fie".
- Conventional putem declara o variabila folosind sintaxa
    ```javascript
    fie [denumireVariabila]: [TipVariabila] = [valoareInitiala]
    ```
- Denumirea unei variabile va fi in format [camelCase](https://en.wikipedia.org/wiki/Camel_case) (prima litera mica).
- Ulterior putem modifica valoarea variabilei folosind sintaxa
    ```javascript
    [denumireVariabila] = [valoare]
    ```
- Exemple:
    ```javascript
    fie x: intreg = 10  //x = 10
    x = x * x           //x = 100
    x = x - 5           //x = 95

    fie y: real = x + 20.5  //y = 115.5

    fie z: real = x + y     //z = 210.5
    ```

    ```javascript
    fie ani: intreg[] = [2019, 2020, 2021]
    //-> ani = [2019, 2020, 2021]

    ani = ani + [2022, 2023] //Se adauga elementele 2022 si 2023 in multimea ani
    //-> ani = [2019, 2020, 2021, 2022, 2023]

    ani = ani - [2020, 2023] //Din multimea ani se sterg elementele 2020 si 2023
    //-> ani = [2019, 2021, 2022]

    ani = []    //multimea este golita
    //-> ani = []
    ```

     ```javascript
    clasa Telefon {
        producator: text
        model: text
        serie: intreg
    }

    fie telefonPrincipal: Telefon = {
        producator: "Samsung"
        model: "A13"
        serie: 1005
    }

    fie telefonRezerva: Telefon = {
        producator: "Apple"
        model: "iPhone 11"
        serie: 6001
    }

    fie telefoaneleMele: Telefon[] = [telefonPrincipal, telefonRezerva]
    ```

# 3. Obiecte
- Obiectele reprezinta valori concrete ale claselor.
- Putem accesa valorile proprietatilor unui obiect folosind notatia
```javascript
[referintaObiect].[denumireProprietate]
```
- Exemplu:
```javascript
//Fie `andra` un obiect de tip Persoana (conform definitiei de la 1.2.2).  
fie andra: Persoana = {
    id: "0b809da0-5933-4785-be89-8e3e6d5e9abd",
    nume: "Stan"
    prenume: "Andra"
    acteIdentitate: [
        {
            id: "20bf705f-7e49-4b1b-aee1-335eb02e3164"
            cnp: "6010308015164"
            serie: "RK"
            nr: "000123"
            nume: "Stan"
            prenume: "Andra"
            dataEliberare: "2020-02-31"
            dataExpirare: "2028-02-30"
        },
        {
            id: "2de91a68-7ea9-4968-bc1b-f4e4266393a6"
            cnp: "6010308015164"
            serie: "RR"
            nr: "000567"
            nume: "Chirita" //Numele de dinainte de casatorie
            prenume: "Andra"
            dataEliberare: "2014-03-08"
            dataExpirare: "2020-03-08"
        }
    ],
    mama: null
    tata: null
}

fie numeComplet: text = andra.nume + " " + andra.prenume
//-> Valoarea variabilei numeComplet va fi "Stan Andra"
```

# 4. Ordonare multimi
Daca dorim sa specificam ca o variabila ia valoarea unei multimi ordonate, putem folosi sintaxa:
- Pentru multimi de valori primitive:
    ```javascript
    fie [denumireVariabila]: [TipVariabila][] = [[referintaMultime] | [valoareMultime]] ordonata ["crescator" | "descrescator"]
    ```
- Pentru multimi de obiecte:
    ```javascript
    fie [denumireVariabila]: [TipVariabila][] = [[referintaMultime] | [valoareMultime]] ordonata dupa [proprietate1] ["crescator" | "descrescator"], [proprietate2] ["crescator" | "descrescator"], ..., [proprietateN] ["crescator" | "descrescator"]
    ```
**Exemple**:
```javascript
fie ani: intreg[] = [2023, 2019, 2015, 2022]
//-> ani = [2023, 2019, 2015, 2022]

fie aniOrdonatiCrescator = ani ordonata crescator
//-> aniOrdonatiCrescator = [2015, 2019, 2022, 2023]

fie aniOrdonatiDescrescator = ani ordonata descrescator
//-> aniOrdonatiDescrescator = [2023, 2022, 2019, 2015]

fie nume: text[] = ["Bianca", "Ana", "Camelia"] ordonata descrescator
//-> nume = ["Camelia", "Bianca", "Ana"]

fie numeOrdonateCrescator: text[] = nume ordonata crescator
//-> numeOrdonateCrescator = ["Ana", "Bianca", "Camelia"]
```

```javascript
clasa Masina {
    producator: text
    dataFabricatie: data
}

fie masini: Masina[] = [
    {
        producator: "Ford"
        dataFabricatie: "2020-01-01"
    },
    {
        producator: "Dacia"
        dataFabricatie: "2020-01-01"
    },
    {
        producator: "Renault"
        dataFabricatie: "2022-05-29"
    }
]

fie masiniRecente: Masina[] = masini ordonata dupa dataFabricatie descrescator, producator crescator
//-> masiniRecente = [
// {
//     producator: "Renault"
//     dataFabricatie: "2022-05-29"
// },
// {
//     producator: "Dacia"
//     dataFabricatie: "2020-01-01"
// },
// {
//     producator: "Ford"
//     dataFabricatie: "2020-01-01"
// }
//]
//
// Primul element va fi masina produsa de Renault deoarece primul criteriu de ordonare este dataFabricatiei in ordine descrescatoare iar masina Renault este produsa intr-un an mai recent decat celelalte 2.
// Masinile produse de Dacia respectiv Ford sunt produse in aceeasi data, asadar ordinea va fi determinata de al doilea criteriu de ordonare (denumirea producatorului in ordine crescatoare). Dacia va fi afisata inaintea lui Ford doarece D este inaintea lui F in alfabet.
```

# 5. Parcurgere elemente multimi
Putem parcurge elementele unei multimi, unul cate unul, folosind sintaxa:
```javascript
pentru fiecare [denumireVariabilaElement] din [referintaMultime]:
    //...instructiuni
```
Putem accesa si numarul elementului (indexul), folosind sintaxa:
```javascript
pentru fiecare [denumireVariabilaElement], index [denumireVariabilaIndex] din [referintaMultime]:
    //...instructiuni
```
Indexul este o variabila de numar intreg iar primul element al unei multimi va avea indexul 0.

**Exemple:**
```javascript
fie valori: intreg[] = [1, 2, 3, 4, 5]
fie sumaNrPare: intreg = 0

pentru fiecare x din valori:
    daca x par
        sumaNrPare = sumaNrPare + x

//sumaNrPare = 2 + 4 = 6
```
```javascript
clasa Adresa {
    tipStrada: text
    strada: text
    numar: text
}

fie adrese: Adresa[] = [
    {
        tipStrada: "Aleea"
        strada: "Alexandru"
        numar: "101A"
    },
    {
        tipStrada: "Strada"
        strada: "Marin Preda"
        numar: "201"
    },
    {
        tipStrada: "Bulevardul"
        strada: "Ferdinand"
        numar: "12"
    }
]

fie adreseOrdonate: Adresa[] = adrese ordonata dupa tipStrada crescator, strada crescator, numar crescator

fie adresaLucrare: text = ""

pentru fiecare adresa, index n din adreseOrdonate
        adresaLucrare = adresaLucrare + (n + 1) ". " + adresa.tipStrada + " " + adresa.strada + " numarul " + adresa.numar

        //Nu adauga un rand nou dupa ultima adresa
        daca n < lungime(adreseOrdonate) - 1
            adresaLucrare = adresaLucrare + RAND_NOU

//variabila adresaLucrare va lua valoarea:
//"1. Aleea Alexandru numarul 101A
//2. Bulevardul Ferdinand numarul 12
//3. Strada Marin Preda numarul 201"
```

# 6. Functii

## 2.1. Functii de baza