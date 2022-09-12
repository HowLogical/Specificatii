# User Interface

# 1. Elemente generale

## 1.1. UIElement
Este clasa de baza pe care o mosteneste orice element de interfata.

**UIElement**
<table>
    <tr>
        <th>Denumire</th>
        <th>Tip</th>
        <th>Observatii</th>
        <th>Valoare implicita</th>
    </tr>
    <tr>
        <td>id</td>
        <td>id!</td>
        <td>Se atribuie automat.</td>
        <td>-</td>
    </tr>
    <tr>
        <td>hidden</td>
        <td>boolean!</td>
        <td>Ascunde/afiseaza elementul si elementele subordonate.</td>
        <td>false</td>
    </tr>
</table>

## 1.2. Sectiune
**Sectiune** mosteneste **UIElement**
<table>
    <tr>
        <th>Denumire</th>
        <th>Tip</th>
        <th>Observatii</th>
        <th>Valoare implicita</th>
    </tr>
</table>

## 1.3. Form
Clasa de baza pe care o mostenesc machetele.

**Form** mosteneste **UIElement**
<table>
    <tr>
        <th>Denumire</th>
        <th>Tip</th>
        <th>Observatii</th>
        <th>Valoare implicita</th>
    </tr>
    <tr>
        <td>disabled</td>
        <td>boolean!</td>
        <td>Daca valoarea este true, toate elementele subordonate vor fi disabled. Altfel se vor considera proprietatile disabled individuale componentelor</td>
        <td>false</td>
    </tr>
</table>

## 1.4. Control
Clasa de baza pe care o mostenesc controalele.

**Control** mosteneste **UIElement**
<table>
    <tr>
        <th>Denumire</th>
        <th>Tip</th>
        <th>Observatii</th>
        <th>Valoare implicita</th>
    </tr>
    <tr>
        <td>name</td>
        <td>text!</td>
        <td>Denumirea campului de date.</td>
        <td></td>
    </tr>
    <tr>
        <td>disabled</td>
        <td>boolean!</td>
        <td>Daca valoarea este true, elementul si elementele subordonate vor fi dezactivate.</td>
        <td>false</td>
    </tr>
</table>

## 1.5. FormControl
Clasa de baza pe care o mostenesc controalele din machete (Form-uri).

**FormControl** mosteneste **UIElement**
<table>
    <tr>
        <th>Denumire</th>
        <th>Tip</th>
        <th>Observatii</th>
        <th>Valoare implicita</th>
    </tr>
    <tr>
        <td>label</td>
        <td>text</td>
        <td>Eticheta afisata, daca este cazul.</td>
        <td>null</td>
    </tr>
    <tr>
        <td>required</td>
        <td>boolean!</td>
        <td>Daca valoarea este true, se va afisa o steluta rosie care indica obligativitatea completarii campului.</td>
        <td>false</td>
    </tr>
</table>

## 1.6. Modal
Ferestre pop-up. Afisarea / ascunderea se controleaza prin proprietatea `hidden`.

**Modal** mosteneste **UIElement**
<table>
    <tr>
        <th>Denumire</th>
        <th>Tip</th>
        <th>Observatii</th>
        <th>Valoare implicita</th>
    </tr>
</table>

# 2. Controale

## 2.1. TextBox
Camp de baza de introducere de texte scurte.

![TextBox](./images/ui/TextBox_01.png)

**TextBox** mosteneste **FormControl**
<table>
    <tr>
        <th>Denumire</th>
        <th>Tip</th>
        <th>Observatii</th>
        <th>Valoare implicita</th>
    </tr>
    <tr>
        <td>value</td>
        <td>text</td>
        <td>Valoarea afisata in camp.</td>
        <td></td>
    </tr>
    <tr>
        <td>maxLength</td>
        <td>intreg</td>
        <td>Lungimea maxima a textului introdus.</td>
        <td>null</td>
    </tr>
</table>

## 2.2. LargeTextBox
Camp de baza de introducere de texte mari, care se pot intinde pe mai multe randuri.

![LargeTextBox](./images/ui/LargeTextBox_01.png)

**LargeTextBox** mosteneste **FormControl**
<table>
    <tr>
        <th>Denumire</th>
        <th>Tip</th>
        <th>Observatii</th>
        <th>Valoare implicita</th>
    </tr>
    <tr>
        <td>autoSize</td>
        <td>boolean!</td>
        <td>Campul se redimensioneaza automat pe inaltime in functie de dimensiunile textului</td>
        <td>false</td>
    </tr>
    <tr>
        <td>minRows</td>
        <td>intreg</td>
        <td>Numarul minim de randuri afisate pe inaltime.</td>
        <td>null</td>
    </tr>
    <tr>
        <td>maxRows</td>
        <td>intreg</td>
        <td>Numarul maxim de randuri afisate pe inaltime.</td>
        <td>null</td>
    </tr>
</table>

## 2.3. PasswordBox
Camp de introducere parole. Valorile tastate vor fi afisate mascat.

![PasswordBox](./images/ui/PasswordBox_01.png)

**PasswordBox** mosteneste **TextBox**
<table>
    <tr>
        <th>Denumire</th>
        <th>Tip</th>
        <th>Observatii</th>
        <th>Valoare implicita</th>
    </tr>
</table>

## 2.4. NumberInput
Camp de introducere valori numerice.

![NumberInput](./images/ui/NumberInput_01.png)

**NumberInput** mosteneste **FormControl**
<table>
    <tr>
        <th>Denumire</th>
        <th>Tip</th>
        <th>Observatii</th>
        <th>Valoare implicita</th>
    </tr>
    <tr>
        <td>value</td>
        <td>real</td>
        <td>Valoarea afisata in camp.</td>
        <td></td>
    </tr>
    <tr>
        <td>min</td>
        <td>real</td>
        <td>Valoarea minima ce poate fi introdusa in camp.</td>
        <td>null</td>
    </tr>
    <tr>
        <td>max</td>
        <td>real</td>
        <td>Valoarea maxima ce poate fi introdusa in camp.</td>
        <td>null</td>
    </tr>
    <tr>
        <td>precision</td>
        <td>intreg</td>
        <td>Numarul maxim de zecimale ce poate fi introdus.</td>
        <td>null</td>
    </tr>
    <tr>
        <td>step</td>
        <td>real!</td>
        <td>Pasul cu care se incrementeaza/decrementeaza valoarea campului atunci cand se folosesc sagetelele din dreapta campului.</td>
        <td>1</td>
    </tr>
</table>

## 2.5. CheckBox
Camp de bifa.

![CheckBox](./images/ui/CheckBox_01.png)

**CheckBox** mosteneste **FormControl**
<table>
    <tr>
        <th>Denumire</th>
        <th>Tip</th>
        <th>Observatii</th>
        <th>Valoare implicita</th>
    </tr>
    <tr>
        <td>value</td>
        <td>boolean!</td>
        <td>Daca value este true atunci CheckBox-ul va fi afisat ca fiind bifat, altfel va fi afisat nebifat.</td>
        <td>false</td>
    </tr>
</table>

## 2.6. Radio
Control cu bifare multipla in care o singura optiune poate fi aleasa la oricare moment dat.

![Radio](./images/ui/Radio_01.png)

**Radio** mosteneste **FormControl**
<table>
    <tr>
        <th>Denumire</th>
        <th>Tip</th>
        <th>Observatii</th>
        <th>Valoare implicita</th>
    </tr>
    <tr>
        <td>value</td>
        <td>any</td>
        <td>Valoarea optiunii bifate.</td>
        <td>null</td>
    </tr>
    <tr>
        <td>options</td>
        <td>RadioOption[]</td>
        <td>Optiunile afisate.</td>
        <td>[]</td>
    </tr>
</table>

**RadioOption** mosteneste **Control**
<table>
    <tr>
        <th>Denumire</th>
        <th>Tip</th>
        <th>Observatii</th>
        <th>Valoare implicita</th>
    </tr>
    <tr>
        <td>label</td>
        <td>text</td>
        <td>Eticheta afisata, daca este cazul.</td>
        <td>null</td>
    </tr>
    <tr>
        <td>value</td>
        <td>any</td>
        <td>Valoarea optiunii daca este bifata.</td>
        <td>null</td>
    </tr>
</table>

## 2.7. DatePicker
Camp de selectie / tastare date calendaristice.

![DatePicker](./images/ui/DatePicker_01.png)

**DatePicker** mosteneste **FormControl**
<table>
    <tr>
        <th>Denumire</th>
        <th>Tip</th>
        <th>Observatii</th>
        <th>Valoare implicita</th>
    </tr>
    <tr>
        <td>value</td>
        <td>date</td>
        <td>Data afisata in camp.</td>
        <td>null</td>
    </tr>
    <tr>
        <td>format</td>
        <td>string</td>
        <td>Formatul in care se afiseaza data.</td>
        <td>"zz.ll.aaaa"</td>
    </tr>
</table>

## 2.8. Select
Camp de tip lista de selectie.

![Select](./images/ui/Select_01.png)

**Select** mosteneste **FormControl**
<table>
    <tr>
        <th>Denumire</th>
        <th>Tip</th>
        <th>Observatii</th>
        <th>Valoare implicita</th>
    </tr>
    <tr>
        <td>value</td>
        <td>any</td>
        <td>Valoarea optiunii bifate.</td>
        <td>null</td>
    </tr>
    <tr>
        <td>options</td>
        <td>SelectOption[]</td>
        <td>Optiunile afisate in lista de selectie.</td>
        <td>[]</td>
    </tr>
</table>

**SelectOption**
<table>
    <tr>
        <th>Denumire</th>
        <th>Tip</th>
        <th>Observatii</th>
        <th>Valoare implicita</th>
    </tr>
    <tr>
        <td>label</td>
        <td>text!</td>
        <td>Valoarea afisata - de exemplu denumirea din nomenclator.</td>
        <td></td>
    </tr>
    <tr>
        <td>value</td>
        <td>any</td>
        <td>Valoarea selectata - de regula un id</td>
        <td>null</td>
    </tr>
    <tr>
        <td>disabled</td>
        <td>boolean!</td>
        <td>Daca valoarea este true, optiunea va fi afisata in lista de selectie dar nu va putea fi selectata.</td>
        <td>false</td>
    </tr>
</table>

## 2.9. Slider
Camp de tip slider. Valoarea selectata este de tip real.

![Slider](./images/ui/Slider_01.png)

**Slider** mosteneste **FormControl**
<table>
    <tr>
        <th>Denumire</th>
        <th>Tip</th>
        <th>Observatii</th>
        <th>Valoare implicita</th>
    </tr>
    <tr>
        <td>value</td>
        <td>real!</td>
        <td>Valoarea selectata.</td>
        <td></td>
    </tr>
    <tr>
        <td>min</td>
        <td>real!</td>
        <td>Valoarea minima ce poate fi selectata.</td>
        <td>0</td>
    </tr>
    <tr>
        <td>max</td>
        <td>real!</td>
        <td>Valoarea maxima ce poate fi selectata.</td>
        <td>100</td>
    </tr>
    <tr>
        <td>step</td>
        <td>real!</td>
        <td>Pasul cu care se incrementeaza/decrementeaza valoarea campului atunci cand se trage de slider. Valoarea trebuie sa fie > 0 si sa fie divizibila cu (max - min).</td>
        <td>1</td>
    </tr>
    <tr>
        <td>vertical</td>
        <td>boolean!</td>
        <td>Daca este true, slider-ul va fi orientat vertical. Altfel va fi orientat orizontal.</td>
        <td>false</td>
    </tr>
    <tr>
        <td>options</td>
        <td>SliderOption[]</td>
        <td>Label-urile care vor fi afisate pentru fiecare pas, daca este cazul.</td>
        <td>null</td>
    </tr>
</table>

**SliderOption**
<table>
    <tr>
        <th>Denumire</th>
        <th>Tip</th>
        <th>Observatii</th>
        <th>Valoare implicita</th>
    </tr>
    <tr>
        <td>value</td>
        <td>real!</td>
        <td>Valoarea din slider sub care va fi afisat label-ul</td>
        <td></td>
    </tr>
    <tr>
        <td>label</td>
        <td>text!</td>
        <td>Eticheta de sub pas.</td>
        <td></td>
    </tr>
</table>

# 3. Table