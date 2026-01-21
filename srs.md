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

### **3.1. Interfejs użytkownika (UI)**

Interfejs użytkownika ma formę responsywnej aplikacji webowej. Główny przypadek użycia obejmuje:

* widok kalendarza dostępności zasobu,
* formularz tworzenia rezerwacji,
* listę własnych rezerwacji.
  Makiety interfejsu przygotowane są w narzędziu Figma.

### **3.2. Interfejsy programowe (API)**

* Integracja z uczelnianym systemem uwierzytelniania (SSO).
* Integracja z systemem poczty elektronicznej (powiadomienia).

---
## **4\. Wymagania funkcjonalne**

### **4.1. Rezerwacja zasobu**

**Opis:**
Umożliwia użytkownikowi dokonanie rezerwacji wybranego zasobu.

**Historyjka użytkownika:**

Jako użytkownik, chcę zarezerwować zasób na określony termin, aby móc z niego skorzystać zgodnie z planem.

**Cel biznesowy:**
Usprawnienie zarządzania dostępnością zasobów uczelni.

**Warunki wstępne:**
Użytkownik jest zalogowany w systemie i posiada odpowiednie uprawnienia.

**Warunki końcowe:**
Rezerwacja zostaje zapisana i potwierdzona.

**Kryteria akceptacji:**

* **WF-REZ-01 (Scenariusz główny):**
  * Given: jestem zalogowanym użytkownikiem,
  * And: zasób jest dostępny w wybranym terminie,
  * When: potwierdzam rezerwację,
  * Then: rezerwacja otrzymuje status „Aktywna”.
* **WF-REZ-02 (Scenariusz alternatywny):**
  * Given: zasób jest już zarezerwowany,
  * When: próbuję dokonać rezerwacji,
  * Then: system blokuje operację i wyświetla komunikat.
* **WF-REZ-03 (Scenariusz wyjątkowy):**
  * Given: system utracił połączenie z bazą danych,
  * When: potwierdzam rezerwację,
  * Then: system informuje o błędzie i nie zapisuje rezerwacji.

### **4.2. Anulowanie rezerwacji**

**Historyjka użytkownika:**

Jako użytkownik, chcę anulować rezerwację, aby zwolnić zasób.

**Kryteria akceptacji:**

* **WF-ANUL-01:**
  * Given: posiadam aktywną rezerwację,
  * When: anuluję ją,
  * Then: status rezerwacji zmienia się na „Anulowana”
  * And: zasób staje się ponownie dostępny.

### **4.3. Zarządzanie zasobami (Administrator)**

**Historyjka użytkownika:**

Jako administrator, chcę dodawać i edytować zasoby, aby system odzwierciedlał aktualny stan infrastruktury.

**Kryteria akceptacji:**

* **WF-ADM-01:** Administrator może dodać nowy zasób.
* **WF-ADM-02:** Administrator może zablokować zasób na czas serwisu.
* **WF-ADM-03:** Administrator może edytować status zasobu.

### **4.4. Priorytetyzacja wymagań**

* Must Have: rezerwacja, anulowanie, zarządzanie zasobami.
* Should Have: rezerwacje cykliczne, powiadomienia e-mail.
* Could Have: eksport rezerwacji do kalendarza google.
* Won’t Have: płatności.

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

Analizie poddano systemy Planbook, Booked Scheduler oraz uczelniane rozwiązania wewnętrzne. Zidentyfikowano jako kluczowe przewagi: prostotę UI, widok kalendarza oraz automatyczne wykrywanie konfliktów. Braki konkurencji obejmują skomplikowaną konfigurację i brak rezerwacji cyklicznych.

---
