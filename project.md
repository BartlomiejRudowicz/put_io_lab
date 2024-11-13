# System aukcyjny

## Wprowadzenie

Specyfikacja wymagań funkcjonalnych w ramach informatyzacji procesu sprzedaży produktów w oparciu o mechanizm aukcyjny. 

## Procesy biznesowe

---
<a id="bc1"></a>
### BC1: Sprzedaż aukcyjna 

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2)

**Opis:** Proces biznesowy opisujący sprzedaż za pomocą mechanizmu aukcyjnego.

**Scenariusz główny:**
1. [Sprzedający](#ac1) wystawia produkt na aukcję. ([UC1](#uc1))
2. [Kupujący](#ac2) oferuje kwotę za produkt wyższą od aktualnie najwyższej oferty. ([BR1](#br1), [UC2](#uc2))
3. [Kupujący](#ac2) wygrywa aukcję ([BR2](#br2), [UC3](#uc3))
4. [Kupujący](#ac2) przekazuje należność Sprzedającemu. ([UC4](#uc4))
5. [Sprzedający](#ac1) przekazuje produkt Kupującemu. ([UC5](#uc5))

**Scenariusze alternatywne:** 

2.A. Oferta Kupującego została przebita, a [Kupujący](#ac2) pragnie przebić aktualnie najwyższą ofertę.
* 2.A.1. Przejdź do kroku 2.

3.A. Czas aukcji upłynął i [Kupujący](#ac2) przegrał aukcję. ([BR2](#br2))
* 3.A.1. Koniec przypadku użycia.

## Aktorzy

<a id="ac1"></a>
### AC1: Sprzedający

Osoba oferująca towar na aukcji.

<a id="ac2"></a>
### AC2: Kupujący

Osoba chcąca zakupić produkt na aukcji.

## Przypadki użycia poziomu użytkownika

### Aktorzy i ich cele

[Sprzedający](#ac1):
* [UC1](#uc1): Wystawienie produktu na aukcję
* [UC5](#uc5): Potwierdzenie dostawy

[Kupujący](#ac2)
* [UC2](#uc2): Złożenie oferty
* [UC3](#uc3): Rozstrzygnięcie aukcji
* [UC4](#uc4): Realizacja płatności

---
<a id="uc1"></a>
### UC1: Wystawienie produktu na aukcję

**Aktorzy:** [Sprzedający](#ac1)

**Scenariusz główny:**
1. [Sprzedający](#ac1) zgłasza do systemu chęć wystawienia produktu na aukcję.
2. System prosi o podanie danych produktu i ceny wywoławczej.
3. [Sprzedający](#ac1) podaje dane produktu oraz cenę wywoławczą.
4. System weryfikuje poprawność danych.
5. System informuje o pomyślnym wystawieniu produktu na aukcję.

**Scenariusze alternatywne:** 

4.A. Podano niepoprawne lub niekompletne dane produktu.
* 4.A.1. System informuje o błędnie podanych danych.
* 4.A.2. Przejdź do kroku 2.

---

<a id="uc2"></a>
### UC2: Złożenie oferty

**Aktorzy:** [Kupujący](#ac2)

**Scenariusz główny:**
1. [Kupujący](#ac2) wybiera aukcję, w której chce złożyć ofertę.
2. System wyświetla szczegóły aukcji i aktualną najwyższą ofertę.
3. [Kupujący](#ac2) wprowadza kwotę oferty.
4. System weryfikuje zgodność oferty z [BR1](#br1).
5. System rejestruje nową ofertę i informuje o jej przyjęciu.

**Scenariusze alternatywne:** 

4.A. Oferowana kwota jest za niska
* 4.A.1. System informuje o zbyt niskiej kwocie.
* 4.A.2. Przejdź do kroku 3.

4.B. Aukcja została zakończona
* 4.B.1. System informuje o zakończeniu aukcji.
* 4.B.2. Koniec przypadku użycia.

---

<a id="uc3"></a>
### UC3: Rozstrzygnięcie aukcji

**Aktorzy:** [Kupujący](#ac2)

**Scenariusz główny:**
1. System wykrywa zakończenie czasu aukcji.
2. System identyfikuje najwyższą ofertę zgodnie z [BR2](#br2).
3. System oznacza aukcję jako zakończoną.
4. System oznacza zwycięską ofertę.
5. System powiadamia zwycięzcę i sprzedającego o rozstrzygnięciu.

**Scenariusze alternatywne:** 

2.A. Brak ofert w aukcji
* 2.A.1. System oznacza aukcję jako nierozstrzygniętą.
* 2.A.2. System powiadamia sprzedającego.
* 2.A.3. Koniec przypadku użycia.

---

<a id="uc4"></a>
### UC4: Realizacja płatności

**Aktorzy:** [Kupujący](#ac2)

**Scenariusz główny:**
1. [Kupujący](#ac2) wybiera wygraną aukcję.
2. System wyświetla szczegóły płatności.
3. [Kupujący](#ac2) realizuje płatność.
4. System weryfikuje otrzymanie płatności.
5. System aktualizuje status aukcji.
6. System powiadamia sprzedającego o otrzymaniu płatności.

**Scenariusze alternatywne:** 

4.A. Błąd płatności
* 4.A.1. System informuje o błędzie.
* 4.A.2. Przejdź do kroku 3.

---

<a id="uc5"></a>
### UC5: Potwierdzenie dostawy

**Aktorzy:** [Sprzedający](#ac1)

**Scenariusz główny:**
1. [Sprzedający](#ac1) wybiera opłaconą aukcję.
2. System wyświetla szczegóły aukcji.
3. [Sprzedający](#ac1) potwierdza przekazanie produktu.
4. System aktualizuje status aukcji i produktu.
5. System powiadamia kupującego.

**Scenariusze alternatywne:** 

1.A. Aukcja nie została opłacona
* 1.A.1. System informuje o braku płatności.
* 1.A.2. Koniec przypadku użycia.

## Obiekty biznesowe

### BO1: Aukcja

Aukcja jest formą zawierania transakcji kupna-sprzedaży, w której Sprzedający określa cenę wywoławczą produktu, natomiast Kupujący mogą oferować własną ofertę zakupu każdorazowo proponując kwotę wyższą od aktualnie oferowanej kwoty. Aukcja kończy się po upływie określonego czasu. Jeśli złożona została co najmniej jedna oferta zakupy produkt nabywa ten Kupujący, który zaproponował najwyższą kwotę. 

### BO2: Produkt

Fizyczny lub cyfrowy obiekt, który ma zostać sprzedany w ramach aukcji.

### BO3: Oferta

Propozycja zakupu produktu złożona przez Kupującego w ramach aukcji, zawierająca oferowaną kwotę.

### BO4: Płatność

Potwierdzenie przekazania należności przez Kupującego Sprzedającemu za wylicytowany produkt.

## Reguły biznesowe

<a id="br1"></a>
### BR1: Złożenie oferty

Złożenie oferty wymaga zaproponowania kwoty wyższej niż aktualnie oferowana o minimum 1,00 PLN.

<a id="br2"></a>
### BR2: Rozstrzygnięcie aukcji

Aukcję wygrywa ten z [Kupujący](#ac2)ch, który w momencie jej zakończenia (upłynięcia czasu) złożył najwyższą ofertę.

## Macierz CRUDL

| Przypadek użycia                   | Aukcja | Produkt | Oferta | Płatność |
|-----------------------------------|---------|---------|---------|-----------|
| UC1: Wystawienie produktu         | C       | C       |         |           |
| UC2: Złożenie oferty              | R       | R       | C       |           |
| UC3: Rozstrzygnięcie aukcji       | U       | R       | U       |           |
| UC4: Realizacja płatności         | U       | R       | R       | C         |
| UC5: Potwierdzenie dostawy        | U       | U       | R       | R         |