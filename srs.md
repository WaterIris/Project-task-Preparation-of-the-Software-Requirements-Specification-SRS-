# **Specyfikacja Wymagań Oprogramowania (SRS)**

## **1\. Wstęp**

### **1.1. Cel dokumentu**

Celem niniejszego dokumentu jest przedstawienie kompletnej Specyfikacji Wymagań Oprogramowania (SRS) dla systemu **Pogrzebalia v1.0** – systemu informatycznego wspierającego zarządzanie domem pogrzebowym. Dokument stanowi podstawę do projektowania, implementacji, testów oraz walidacji systemu i jest przeznaczony dla interesariuszy biznesowych, zespołu projektowego oraz prowadzącego zajęcia.

### **1.2. Wizja, zakres i cele produktu**

**Wizja:**
Stworzenie nowoczesnego, empatycznego i bezpiecznego systemu informatycznego, który usprawni obsługę klientów domu pogrzebowego oraz uporządkuje procesy organizacyjne.

**Zakres systemu:**
System umożliwia kompleksowe zarządzanie usługami pogrzebowymi, dokumentacją, personelem, rezerwacjami ceremonii oraz kontaktami z klientami.

**Cele biznesowe i KPIs:**

* Skrócenie czasu obsługi klienta o 30% (średni czas od zgłoszenia do podpisania umowy)
* Zmniejszenie liczby błędów w dokumentacji o 50%
* Możliwość obsługi do 100 aktywnych zleceń miesięcznie

**Poza zakresem:**

* Prowadzenie księgowości pełnej
* Zarządzanie cmentarzem
* Obsługa krematoriów zewnętrznych

### **1.3. Definicje, akronimy i skróty**

* **SRS** – Specyfikacja Wymagań Oprogramowania
* **RODO** – Rozporządzenie o Ochronie Danych Osobowych
* **Klient** – osoba zlecająca usługę pogrzebową
* **Zlecenie** – komplet informacji dotyczących jednej ceremonii

### **1.4. Przegląd dokumentu**

Rozdział 2 opisuje ogólną charakterystykę systemu. Rozdziały 3–5 zawierają wymagania funkcjonalne i niefunkcjonalne. Rozdział 6 opisuje analizę porównawczą rynku.

---

## **2\. Opis ogólny**

### **2.1. Główne funkcje produktu**

* Zarządzanie zleceniami pogrzebowymi
* Rejestracja i obsługa klientów
* Planowanie ceremonii
* Zarządzanie personelem
* Generowanie dokumentów
* Powiadomienia i przypomnienia

### **2.2. Klasy użytkowników**

* **Administrator** – zarządza systemem i użytkownikami
* **Pracownik biura** – obsługa klientów i dokumentów
* **Pracownik terenowy** – wgląd w harmonogram ceremonii

**Persona – Pracownik biura:**
Anna, 38 lat, pracuje w domu pogrzebowym, zależy jej na szybkim i bezbłędnym przygotowaniu dokumentów.

### **2.3. Ograniczenia projektowe i implementacyjne**

**Technologiczne:** aplikacja webowa, baza PostgreSQL
**Organizacyjne:** termin oddania – koniec semestru
**Prawne:** pełna zgodność z RODO

### **2.4. Założenia projektowe**

* Użytkownicy posiadają podstawowe umiejętności obsługi komputera
* System dostępny przez przeglądarkę
* Dostęp do infrastruktury AWS lub Azure Microsoft

---
## **3\. Wymagania dotyczące interfejsów zewnętrznych**

### **3.1. Interfejs użytkownika**

* Stonowana kolorystyka
* Intuicyjna nawigacja
* Responsywny design

### **3.2. Interfejsy programowe**

* Integracja z systemem e-mail
* Integracja z systemem SMS

---

## **4\. Wymagania funkcjonalne**

### **4.1. Zarządzanie zleceniem pogrzebowym**

**Opis:**
Umożliwia rejestrację i obsługę zlecenia pogrzebowego.

**Historyjka użytkownika:**
Jako pracownik biura,chcę dodać nowe zlecenie pogrzebowe,aby móc rozpocząć proces organizacji ceremonii.

**Cel biznesowy:**
Ustandaryzowanie i klasyfikacja obsługi zleceń.

**Warunki wstępne:**
Użytkownik zalogowany jako pracownik biura.

**Warunki końcowe:**
Zlecenie zapisane w systemie.

**Kryteria akceptacji:**

* **WF-ZL-01 (Scenariusz główny)**
  * Given: Jestem zalogowany jako pracownik biura
  * When: Wypełnię formularz i zapiszę
  * Then: Zlecenie zostaje zapisane i otrzymuje unikalny numer
* **WF-ZL-02 (Alternatywny)**
  * Given: Brak wymaganych danych
  * When: Próba zapisu
  * Then: System wyświetla komunikat o błędzie

### **4.2. Priorytetyzacja wymagań**

* Zarządzanie zleceniem – Wysoki
* Powiadomienia – Średni
* Raporty – Średni

## **5\. Atrybuty Jakościowe**

* Jakość wykonania
  * Wydajność (Performance):
    * WNF-WYD-01: czas odpowiedzi ≤ 1.5 s przy 200 użytkownikach.

  * Dostępność (Availability):
    * WNF-DOST-01: dostępność 99.8% rocznie.

  * Bezpieczeństwo (Security):
    * WNF-BEZ-01: hasła hashowane bcrypt.
    * WNF-BEZ-02: automatyczne wylogowanie po 30 min.

  * Skalowalność (Scalability):
    * WNF-SKAL-01: obsługa 5000 jednoczesnych sesji.

* Jakość projektu
  * Modyfikowalność (Modifiability):
    * WNF-MOD-01: możliwość dodania nowego typu zasobu bez zmiany istniejącego kodu.
  * Przenośność (Portability):
    * WNF-PRZ-01: uruchomienie przez docker-compose up.

### **5.1. Priorytetyzacja atrybutów jakościowych**

1. Wydajność – Must Have
2. Bezpieczeństwo – Must Have
3. Skalowalność – Should Have

## **6\. Odkrywanie i Analiza Wymagań**

### **6.1. Analiza porównawcza**

Proces ten pozwolił na zidentyfikowanie standardów rynkowych oraz nisz, które system Pogrzebalia powinien zagospodarować, aby uzyskać przewagę konkurencyjną.

**Krok 1: Identyfikacja Konkurencji i Wzorców**
W celu uzyskania pełnego obrazu rynku, analizie poddano trzy grupy systemów:
* *Konkurencja bezpośrednia*: Systemy dedykowane branży funeralnej (np. Mementis, Funeral System). Skupiają się na ewidencji zgonów i druku klepsydr.
* *Konkurencja pośrednia*: Systemy klasy ERP dla małych przedsiębiorstw oraz narzędzia ogólne (np. Asana, Excel), powszechnie używane w mniej cyfrowych zakładach.
* *Wzorce funkcjonalne*: Systemy rezerwacji usług medycznych (np. ZnanyLekarz) pod kątem intuicyjnego planowania kalendarza oraz systemy CRM (np. HubSpot) pod kątem budowania relacji z klientem.

**Krok 2: Zdefiniowanie Kryteriów Oceny**
Poniższa tabela przedstawia porównanie systemu Pogrzebalia z obecnymi rozwiązaniami rynkowymi:

|Kryterium Oceny|Konkurencja Bezpośrednia|Systemy Ogólne (ERP/Excel)|Pogrzebalia v1.0|
|---|---|---|---|
|Intuicyjność UX|Niska (archaicze interfejsy)|Zależna od konfiguracji|Wysoka (empatyczny design)|
|Mobilność|Ograniczona (desktop)|Częściowa|Pełna (RWD dla pracowników)|
|Automatyzacja dokumentów|Wysoka|Niska (ręczne wzorce)|Wysoka (generowanie PDF/DOCX)|
|Powiadomienia SMS/E-mail|Rzadko spotykane|Wymaga integracji|Standard (moduł powiadomień)|
|Łatwość wdrożenia|Trudna (wymaga szkoleń)|Średnia|Bardzo łatwa (SaaS/Cloud)|

**Krok 3: Synteza Wyników i Wnioski**
Na podstawie przeprowadzonej analizy wyciągnięto następujące wnioski, które wpłynęły na ostateczny kształt wymagań w niniejszym SRS:
1. Luka w UX: Większość istniejących systemów funeralnych jest przeładowana funkcjami i posiada skomplikowany interfejs. Wniosek: Pogrzebalia musi postawić na "stonowaną kolorystykę" i prostotę, aby zredukować stres pracowników i klientów (wpisane do sekcji 3.1).
2. Brak wsparcia mobilnego: Pracownicy terenowi często nie mają wglądu w aktualny harmonogram. Wniosek: Konieczność zapewnienia pełnej responsywności (wymóg WNF-DOST-01).
3. Potencjał automatyzacji: Największą bolączką branży jest ręczne wypełnianie podobnych formularzy (US, ZUS, kancelaria). Wniosek: Priorytetem systemu staje się moduł automatycznego generowania dokumentów na podstawie danych ze zlecenia (sekcja 4.1).
4. Unikalna wartość: System Pogrzebalia wyróżni się na tle konkurencji nie tylko funkcjonalnością, ale przede wszystkim podejściem "Cloud-first" oraz wbudowanym modułem komunikacji z klientem (SMS/E-mail), co zredukuje liczbę telefonów do biura.

---
