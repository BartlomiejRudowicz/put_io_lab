# System aukcyjny

## Wprowadzenie

Specyfikacja wymagań funkcjonalnych w ramach informatyzacji procesu sprzedaży produktów w oparciu o mechanizm aukcyjny. 

## Procesy biznesowe

---
<a id="bc1"></a>
### BC1: Sprzedaż aukcyjna 

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2)

**Opis:** Proces biznesowy opisujący sprzedaż za pomocą mechanizmu aukcyjnego. |

**Scenariusz główny:**
1. [Sprzedający](#ac1) wystawia produkt na aukcję. ([UC1](#uc1))
2. [Kupujący](#ac2) oferuje kwotę za produkt wyższą od aktualnie najwyższej oferty. ([BR1](#br1), [UC2](#uc2))
3. [Kupujący](#ac2) wygrywa aukcję ([BR2](#br2), [UC2](#uc2))
4. [Kupujący](#ac2) przekazuje należność Sprzedającemu(#ac1). ([UC2](#uc2))
5. [Sprzedający](#ac1) przekazuje produkt Kupującemu(#ac2). ([UC3](#uc3))

**Scenariusze alternatywne:** 

2.A. Oferta Kupującego została przebita, a [Kupujący](#ac2) pragnie przebić aktualnie najwyższą ofertę.
* 2.A.1. Przejdź do kroku 2.

3.A. Czas aukcji upłynął i [Kupujący](#ac2) przegrał aukcję. ([BR2](#br2))
* 3.A.1. Koniec przypadku użycia.

---

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
* UC1: Wystawienie produktu na aukcji
* UC2: Zamknięcie aukcji
* UC3: Weryfikacja ofert

[Kupujący](#ac2)
* UC4: Składanie oferty na aukcję
* UC5: Wycofanie oferty

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
### UC2: Zamknięcie aukcji

**Aktorzy:** [Sprzedający](#ac1)

**Scenariusz główny:**
1. Sprzedający inicjuje zakończenie aukcji dla swojego produktu.
2. System sprawdza, czy minął czas aukcji lub jeśli sprzedający chce zakończyć wcześniej.
3. System identyfikuje najwyższą ofertę.
4. Aukcja zostaje zakończona i informacja trafia do sprzedającego oraz kupującego z najwyższą ofertą.

**Scenariusze alternatywne:** 

1.A: Sprzedający anuluje aukcję bez wybrania oferty.


<a id="uc3"></a>
### UC3: Weryfikacja ofert

**Aktorzy:** [Sprzedający](#ac1)

**Scenariusz główny:**
1. Sprzedający przegląda listę ofert dla swojego produktu.
2. System wyświetla szczegóły każdej oferty (kwota, kupujący).
3. Sprzedający wybiera ofertę do dalszego rozważenia lub może zatwierdzić najwyższą ofertę przed czasem zakończenia aukcji.

**Scenariusze alternatywne:** 
1.A: Sprzedający usuwa ofertę, jeśli nie spełnia kryteriów aukcji.


<a id="uc4"></a>
### UC4: Składanie oferty na aukcję

**Aktorzy:** [Kupujący](#ac2)

**Scenariusz główny:**
1. Kupujący wybiera aukcję i określa kwotę swojej oferty.
2. System weryfikuje, czy kwota jest wyższa niż aktualna oferta.
3. System akceptuje ofertę i aktualizuje informacje na stronie aukcji.

**Scenariusze alternatywne:**
2.A: Kwota jest zbyt niska i system odrzuca ofertę.


<a id="uc5"></a>
### UC5: Wycofanie oferty

**Aktorzy:** [Kupujący](#ac2)

**Scenariusz główny:**
1. Kupujący wybiera opcję wycofania oferty.
2. System weryfikuje, czy zasady aukcji pozwalają na wycofanie.
3. System usuwa ofertę i aktualizuje informacje.

**Scenariusze alternatywne:**
2.A: System odrzuca wycofanie oferty ze względu na regulamin aukcji.

---

## Obiewkty biznesowe (inaczje obiekty dziedzinowe lub informatycjne)

### BO1: Aukcja

Aukcja jest formą zawierania transakcji kupna-sprzedaży, w której Sprzedający określa cenę wywoławczą produktu, natomiast Kupujący mogą oferować własną ofertę zakupu każdorazowo proponując kwotę wyższą od aktualnie oferowanej kwoty. Aukcja kończy się po upływie określonego czasu. Jeśli złożona została co najmniej jedna oferta zakupy produkt nabywa ten Kupujący, który zaproponował najwyższą kwotę. 

### BO2: Produkt

Fizyczny lub cyfrowy obiekt, który ma zostać sprzedany w ramach aukcji.

## Reguły biznesowe

<a id="br1"></a>
### BR1: Złożenie oferty

Złożenie oferty wymaga zaproponowania kwoty wyższej niż aktualnie oferowana o minimum 1,00 PLN.


<a id="br2"></a>
### BR2: Rozstrzygnięcie aukcji

Aukcję wygrywa ten z [Kupujący](#ac2)ch, który w momencie jej zakończenia (upłynięcia czasu) złożył najwyższą ofertę.

## Macierz CRUDL


| Przypadek użycia | Produkt | Aukcja | Oferta |
|------------------|---------|--------|--------|
| UC1              |   C     |   R    |        |
| UC2              |         |   U/D  |   R    |
| UC3              |         |        |   R    |
| UC4              |         |        |   C    |
| UC5              |         |        |   D    |


