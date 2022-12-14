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
- Denumirea clasei sau a unei proprietati va putea contine doar litere, cifre si underscore-uri (fara spatii sau alte caractere speciale). De asemenea, primul caracter este obligatoriu o litera.
- Denumirea clasei va fi in format [PascalCase](https://wiki.c2.com/?PascalCase) (prima litera mare).
- Denumirea unei proprietati va fi in format [camelCase](https://en.wikipedia.org/wiki/Camel_case) (prima litera mica).

### 1.2.1. Reprezentare ca text
Putem reprezenta o clasa sub forma de text in urmatorul mod:
```javascript
clasa <DenumireClasa> {
    <denumireProprietate1>: <TipProprietate1>
    <denumireProprietate2>: <TipProprietate2>
    ...
    <denumireProprietateN>: <TipProprietateN>
}
```
- Denumirea clasei este precedata de cuvantul "clasa".
- Proprietatile clasei sunt delimitate de un set de acolade
- O proprietate este scrisa sub forma `<denumireProprietate>: <TipProprietate>`
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

**\<DenumireClasa\>**  
|Proprietate|Tip|Observatii|
|---|---|---|
|\<denumireProprietate1\>|\<TipProprietate1\>|\<Observatie1\>|
|\<denumireProprietate2\>|\<TipProprietate2\>|\<Observatie2\>|
|...|...|...|
|\<denumireProprietateN\>|\<TipProprietateN\>|\<ObservatieN\>|

**Exemple:**  

**ActIdentitate**  
|Proprietate|Tip|Observatii|
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
|Proprietate|Tip|Observatii|
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
- Elementul unei multimi de la o pozitie (index) `i` se poate accesa prin sintaxa:
    ```javascript
    <referintaMultime>[i]
    ```
    Nota: primul element din multime va avea indexul `0` iar ultimul element va avea indexul `n - 1`, unde `n` este numarul total de elemente din multime.
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
- Exemple de accesare si modificare de elemente:
    ```javascript
    fie ani: intreg[] = [2020, 2021, 2022]
    fie primulElement: intreg = ani[0] //-> primulElement = 2020
    fie ultimulElement: intreg = ani[2] //-> ultimulElement = 2022

    //Acesare element in functie de index variabil:
    fie index: intreg = 1
    fie element: intreg = ani[index] //-> element = 2021
    
    index = index + 1
    element = ani[index] //-> element = 2022

    //Accesare element prin limbaj liber
    element = primul element din multimea ani > 2020 //-> element = 2021

    //Modificare element:
    ani[index] = 2025 //-> ani = [2020, 2021, 2022]
    element = ani[index] //-> element = 2025
    ```
    *Nota: A se vedea capitolul `2. Variabile` pentru explicatii referitoare la sintaxa folosita mai sus*


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
- Un obiect poate fi declarat prin sintaxa
    ```javascript
    (<TipObiect>) {
        <denumireProprietate1>: <valoare1>
        <denumireProprietate2>: <valoare2>
        ...
        <denumireProprietateN>: <valoareN>
    }
    ```
- Obiectele reprezinta valori concrete ale claselor. Echivalent, clasele reprezinta template-uri dupa care sunt create obiectele. De exemplu, daca avem o clasa numita Masina:
    ```javascript
    clasa Masina {
        marca: text
        model: text
        culoare: text
    }
    ```
    Exemple de obiecte de tipul Masina ar putea fi:  

    ```javascript
    fie fordFocusNegru: Masina = (Masina) {
        marca: "Ford"
        model: "Focus"
        culoare: "negru"
    }

    fie fordFocusRosu: Masina = (Masina) {
        marca: "Ford"
        model: "Focus"
        culoare: "rosu"
    }

    //Daca nu se specifica tipul inainte de declararea obiectului, se considera a fi tipul de baza al variabilei, multimii sau proprietatii
    fie daciaLoganAlbastra: Masina = {
        marca: "Dacia"
        model: "Logan"
        culoare: "albastru"
    }
    ```
- Putem reprezenta un obiect si sub forma tabelara astfel:  
  
    **fie** daciaLoganAlbastra: **Masina**
    |Proprietate|Valoare|Observatii|
    |---|---|---|
    |marca|"Dacia"||
    |model|"Logan"||
    |culoare|"albastru"||

- Daca nu se specifica tipul inainte de declararea obiectului, se considera a fi tipul de baza al variabilei, multimii sau proprietatii. In cazul in care tipul obiectului este o subclasa a tipului de baza, trebuie specificat obligatoriu. De exemplu:
    ```javascript
    clasa Excavator mosteneste Masina {
        volumCupa: real
    }

    clasa Tanc mosteneste Masina {
        calibruTunCm: real
    }

    fie vehicule: Masina[] = {
        (Tanc) {
            marca: "Krupp"
            model: "Panzer IV"
            culoare: "gri"
            calibruTunCm: 7.5
        },
        (Excavator) {
            marca: "Komatsu"
            model: " PC170LC-10"
            culoare: "gablen"
            volumCupa: 110.75
        },
        (Tanc) {
            marca: "Vauxhall Motors"
            model: "Churchill Mark V"
            culoare: "crem"
            calibruTunCm: 9.5
        },
        {
            marca: "Dacia"
            model: "Logan"
            culoare: "albastru"
        },
    }
    ```
- Putem accesa valorile proprietatilor unui obiect folosind notatia
    ```javascript
    <referintaObiect>.<denumireProprietate>
    ```
- Exemplu:
    ```javascript
    //Fie `andra` un obiect de tip Persoana (conform definitiei de la 1.2.2).  
    fie andra: Persoana = (Persoana) {
        id: "0b809da0-5933-4785-be89-8e3e6d5e9abd",
        nume: "Stan"
        prenume: "Andra"
        acteIdentitate: [
            (ActIdentitate) {
                id: "20bf705f-7e49-4b1b-aee1-335eb02e3164"
                cnp: "6010308015164"
                serie: "RK"
                nr: "000123"
                nume: "Stan"
                prenume: "Andra"
                dataEliberare: "2020-02-31"
                dataExpirare: "2028-02-30"
            },
            (ActIdentitate) {
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
    fie <denumireVariabila>: <TipVariabila>[] = <<referintaMultime> | <valoareMultime>> ordonata <"crescator" | "descrescator">
    ```
- Pentru multimi de obiecte:
    ```javascript
    fie <denumireVariabila>: <TipVariabila>[] = <<referintaMultime> | <valoareMultime>> ordonata dupa <proprietate1> <"crescator" | "descrescator">, <proprietate2> <"crescator" | "descrescator">, ..., <proprietateN> <"crescator" | "descrescator">
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
pentru fiecare <denumireVariabilaElement> din <referintaMultime>:
    //...instructiuni
```
Putem accesa si numarul elementului (indexul), folosind sintaxa:
```javascript
pentru fiecare <denumireVariabilaElement>, index <denumireVariabilaIndex> din <referintaMultime>:
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

        //Adauga un rand nou doar daca nu suntem pe ultimul element
        daca n < lungime(adreseOrdonate) - 1
            adresaLucrare = adresaLucrare + RAND_NOU

//variabila adresaLucrare va lua valoarea:
//"1. Aleea Alexandru numarul 101A
//2. Bulevardul Ferdinand numarul 12
//3. Strada Marin Preda numarul 201"
```

# 6. Functii
- Functiile ne ofera o metoda de a reprezenta un algoritm intr-un mod reutilizabil.
- O functie este alcatuita din:
    1. Denumirea functiei
    2. 0 sau mai multi parametri
    3. Tipul rezultatului
    4. Algoritmul care prelucreaza parametrii si returneaza rezultatul
- O functie are sintaxa:
    ```javascript
    functie <denumireFunctie>(<denumireParametru1>: <TipParametru1>, ..., <denumireParametruN>: <TipParametruN>): <TipRezultat> {
        //...algoritm
    }
    ```
- O functie se apeleaza prin sintaxa:
    ```javascript
    <denumireFunctie>(<parametru1>, ..., <parametruN>)
    ```
- In cadrul algoritmului, se va folosi cuvantul `returneaza` pentru a indica valoarea returnata de functie.
- Functia se opreste din executie in momentul parcurgerii instructiunii `returneaza`
- Daca functia nu returneaza valori se poate omite tipul returnat si folosirea cuvantului `returneaza`
- Pot exista mai multe functii cu aceeasi denumire dar cu parametri diferiti.
- Nu pot exista mai multe functii cu aceeasi denumire dar cu tip rezultat diferit
- Exemple:
    ```javascript
    functie patrat(x: intreg): intreg {
        returneaza x * x
    }

    functie adunare(a: intreg, b: intreg): intreg {
        returneaza a + b
    }

    fie rezultat: intreg = patrat(5) //-> rezultat = 25

    //Compunere functii
    rezultat = adunare(patrat(6), 2) //-> rezultat = 38
    ```
    ```javascript

    functie filtrarePare(elemente: intreg[]): intreg[] {
        fie rezultat: intreg[] = []

        pentru fiecare element din elemente
            daca element par
                rezultat = rezultat + [element]

        returneaza rezultat
    }

    fie numere: intreg[] = [1, 2, 3, 4, 5, 6]

    fie pare: intreg[] = filtrarePare(numere)
    //-> pare = [2, 4, 6]

    ```

## 6.1. Functii predefinite

Pentru comoditate vom predefini urmatoarele functii utilizate comun:

### 6.1.1. Functii generale
In aceasta sectiune tipul `any` va reprezenta orice tip, indiferent de categoria sa.

**lungime**
```javascript
lungime(multime: any[]): intreg {
    returneaza numarul de elemente din multime
}

lungime(str: text): intreg {
    returneaza numarul de caractere din str
}

//Exemple:
fie l: intreg
l = lungime([]) //l = 0
l = lungime([5, 6, 1]) //l = 3
l = lungime("Decebal, regele Daciei") //l = 22
```

### 6.1.2. Functii predefinite pentru numere

**radical**
```javascript
radical(x: real): real {
    returneaza radicalul lui x
}

radical(x: real, ordin: intreg): real {
    returneaza radicalul de ordin n a lui x
}

//Exemple:
fie rez: real
rez = radical(25)           //rez = 5
rez = radical(radical(49))  //rez = 2.6457513...
rez = radical(64, 3)        //rez = 4
```

### 6.1.3. Functii predefinite pentru texte

**ltrim, rtrim, trim**
```javascript
//Left trim
ltrim(str: text): text {
    returneaza textul 'str' fara spatii la inceput
}

//Right trim
rtrim(str: text): text {
    returneaza textul 'str' fara spatii la sfarist
}

//Trim
trim(str: text): text {
    //returneaza textul 'str' fara spatii la inceput si sfarist
    returneaza ltrim(rtrim(str))
}

//Exemple:
fie rez: text
rez = ltrim("  Hey  ")      //-> rez = "Hey  "
rez = rtrim("  Salut  ")    //-> rez = "  Salut"
rez = trim("  Exemplu  ")   //-> rez = "Exemplu"
```

**char**
```javascript
char(str: text, pozitie: intreg): text {
    returneaza caracterul de la pozitia <pozitie> din text
}
//Nota: primul caracter are pozitia 0

fie rez: text
rez = char("Analiza", 0)    //rez = "A"
rez = char("Test", 2)       //rez = "s"
```

**substring**
```javascript
substring(str: text, pozitieStart: intreg, pozitieFinal: text): text {
    returneaza textul din str incepand cu pozitieStart (inclusiv) pana la pozitieFinal (exclusiv)
}

substring(str: text, pozitieStart: intreg): text {
    //returneaza textul din str incepand cu pozitieStart (inclusiv) pana la final
    returneaza substring(text, pozitieStart, lungime(text))
}

fie rez: text
rez = substring("aroma", 1) //-> rez = "roma"
rez = substring("Analizare", 3, 7) //-> rez = "liza"
```

**replaceText**
```javascript
replaceText(txt: text, textCautat: text, textulNou: text): text {
    returneaza un nou text in care fiecare aparitie a lui <textCautat> din txt este inlocuita cu <textulNou>
}

fie rez: text
rez = replaceText("mere prune nectarine", " ", ",") //-> rez = "mere,prune,nectarine"
```

### 6.1.4. Functii predefinite pentru date

**zi, luna, an**
```javascript
zi(data: data): intreg {
    returneaza numarul zilei din luna pentru parametrul data
}

luna(data: data): intreg {
    returneaza numarul lunii din an pentru parametrul data
}

anul(data: data): intreg {
    returneaza anul parametrului data
}

fie data: data = "2022-09-30"
fie rez: intreg
rez = zi(data)      //-> rez = 30
rez = luna(data)    //-> rez = 9
rez = an(data)      //-> rez = 2022
```

**ultimaZiDin, primaZiDin**
```javascript
ultimaZiDin(data: data, din: text): data {
    daca din = "luna"
        returneaza ultima zi a lunii in care se incadreaza parametrul data
    daca din = "an"
        returneaza ultima zi a anului in care se incadreaza parametrul data
}

fie data: data = "2022-09-15"

fie rez: data = ultimaZiDin(data, "luna") //-> rez = "2022-09-31"
rez = ultimaZiDin(data, "an") //-> rez = "2022-12-31"
```
```javascript
primaZiDin(data: data, din: text): data {
    daca din = "luna"
        returneaza prima zi a lunii in care se incadreaza parametrul data
    daca din = "an"
        returneaza prima zi a anului in care se incadreaza parametrul data
}

fie data: data = "2022-09-17"

fie rez: data = primaZiDin(data, "luna") //-> rez = "2022-09-01"
rez = primaZiDin(data, "an") //-> rez = "2022-01-01"
```


# 7. Module
*TODO*

# 8. Tipuri generice

*TODO*