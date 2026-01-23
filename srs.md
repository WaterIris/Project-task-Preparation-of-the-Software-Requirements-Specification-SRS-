# Zarządzanie Projektem Informatycznym

## Jakub Kaleciński, Jakub Koch, Mateusz Tutaj

# **Specyfikacja Wymagań Oprogramowania (SRS)**

## **1\. Wstęp**

### **1.1. Cel dokumentu**

Celem niniejszego dokumentu jest przedstawienie kompletnej Specyfikacji Wymagań Oprogramowania (SRS) dla systemu **Pogrzebalia v1.0** – systemu informatycznego wspierającego zarządzanie domem pogrzebowym. Dokument stanowi podstawę do projektowania, implementacji, testów oraz walidacji systemu i jest przeznaczony dla interesariuszy biznesowych, zespołu projektowego oraz prowadzącego zajęcia.

### **1.2. Wizja, zakres i cele produktu**

**Wizja:**  
Stworzenie nowoczesnego i bezpiecznego systemu informatycznego, który usprawni i automatyzuje obsługę klientów domu pogrzebowego oraz uporządkuje procesy organizacyjne.

**Zakres systemu:**  
System umożliwia kompleksowe zarządzanie usługami pogrzebowymi, dokumentacją, personelem, rezerwacjami ceremonii oraz kontaktami z klientami.

**Cele biznesowe i KPIs:**

* Skrócenie czasu obsługi klienta do ≤15 minut.  
* Zmniejszenie liczby błędów w dokumentacji o 50% i całkowita eliminacja braków w dokumentacji.  
* Wyeliminowanie błędów logistycznych w procesie rezerwacji terminów.  
* Możliwość obsługi do 100 aktywnych zleceń miesięcznie.  
* Zmniejszenie liczby obowiązków pracownika poprzez automatyzacja komunikacji z klientami, powiadomienia: sms, mail i telefonicznie.  
* Automatyczna kalkulacja kwoty usługi.

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

### **2.3. Ograniczenia projektowe i implementacyjne**

**Technologiczne:** aplikacja webowa, baza PostgreSQL  
**Organizacyjne:** termin oddania – koniec semestru  
**Prawne:** pełna zgodność z RODO

### **2.4. Założenia projektowe**

* Użytkownicy posiadają podstawowe umiejętności obsługi komputera  
* System dostępny przez przeglądarkę, możliwość łatwego eksportu danych do formatów csv i aplikacji kalendarzowych.  
* Dostęp do infrastruktury AWS lub Azure Microsoft  
* Kontakt z podwykonawcami i ustalone stawki lub możliwość szybkiej ewaluacji kwoty zlecenia

## **3\. Wymagania dotyczące interfejsów zewnętrznych**

### **3.1. Interfejs użytkownika**

* Stonowana kolorystyka  
* Intuicyjna nawigacja  
* Responsywny design  
* Walidacja danych  
* Gotowe schematy formularzy

### **3.2. Interfejsy programowe**

* Integracja z systemem e-mail  
* Integracja z systemem SMS

## **4\. Wymagania funkcjonalne**

### **4.1. Zarządzanie zleceniem pogrzebowym**

**Opis:**  
Umożliwia rejestrację i obsługę zlecenia pogrzebowego.

**Historyjka użytkownika:**  
Jako pracownik biura,chcę dodać nowe zlecenie pogrzebowe, aby móc rozpocząć proces organizacji ceremonii.

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


### **4.2 Planowanie logistyki przewozu zwłok**

**Opis:**  
 System umożliwia planowanie, rejestrowanie i monitorowanie transportu zwłok pomiędzy kluczowymi lokalizacjami (kostnica, krematorium, kaplica, cmentarz) w ramach zlecenia pogrzebowego.

**Historyjka użytkownika:**  
 Jako pracownik biura  
 chcę zaplanować transport zwłok pomiędzy wskazanymi lokalizacjami  
 aby zapewnić terminową i bezkonfliktową realizację ceremonii.

**Kryteria akceptacji:**

* WF-LOG-01  
   Given: Istnieje aktywne zlecenie pogrzebowe  
   When: Wybiorę lokalizację i termin transportu  
   Then: Transport zostaje zapisany i widoczny w harmonogramie

* WF-LOG-02  
   Given: Istnieje konflikt terminów  
   When: Próba zapisu transportu  
   Then: System informuje o konflikcie

**Priorytet:** Wysoki

### **4.3 Uzgadnianie procesów cmentarnych**

**Opis:**  
System umożliwia ewidencję czynności formalnych związanych z pochówkiem na cmentarzu.

**Historyjka użytkownika:**  
 Jako pracownik biura  
 chcę zarejestrować informacje o wykupie miejsca i kopaniu grobu  
 aby mieć pewność, że wszystkie formalności zostały dopełnione.

**Kryteria akceptacji:**

* WF-CEM-01  
   Given: Istnieje aktywne zlecenie  
   When: Uzupełnię dane dotyczące miejsca pochówku  
   Then: Informacje zostają zapisane w systemie

**Priorytet:** Średni

### **4.4 Generowanie raportów z procesu**

**Opis:**  
 System umożliwia generowanie raportów podsumowujących realizację zleceń pogrzebowych.

**Historyjka użytkownika:**  
 Jako administrator  
 chcę wygenerować raport z realizowanych zleceń  
 aby analizować efektywność i obciążenie pracą.

**Kryteria akceptacji:**

* WF-RAP-01  
   Given: Istnieją zakończone zlecenia  
   When: Wybiorę zakres raportu  
   Then: System generuje raport w formatach PDF i CSV

**Priorytet:** Średni

# **5\. Atrybuty jakościowe**

## **5.1. Jakość wykonania**

### **Wydajność**

* **WNF-WYD-01**  
   Czas odpowiedzi systemu dla operacji tworzenia, edycji i przeglądania zleceń  
   nie przekracza **2 sekund** przy **100 jednoczesnych użytkownikach**.

* **WNF-WYD-02**  
   Generowanie raportów dla maksymalnie **500 zleceń** trwa nie dłużej niż **5 sekund**.

### **Dostępność**

* **WNF-DOST-01**  
  System jest dostępny na poziomie **99,5% w skali roku**, z wyłączeniem planowanych prac serwisowych.

* **WNF-DOST-02**  
  Planowane przerwy w dostępności systemu są komunikowane użytkownikom z co najmniej **24-godzinnym wyprzedzeniem**.

### **Niezawodność**

* **WNF-NIEZ-01**  
  Operacje zapisu danych są realizowane w sposób transakcyjny, uniemożliwiający częściowy zapis danych.

* **WNF-NIEZ-02**  
  System wykonuje automatyczne kopie zapasowe danych nie rzadziej niż raz na **24 godziny**.

### **Bezpieczeństwo**

* **WNF-BEZ-01**  
  Hasła użytkowników oraz są przechowywane w postaci zahashowanej przy użyciu algorytmu **bcrypt**.

* **WNF-BEZ-02**  
  Dostęp do funkcji systemu oraz danych jest kontrolowany na podstawie ról użytkowników.

* **WNF-BEZ-03**  
  Dane klientów przechowywane są w postaci zaszyfrowanej.

* **WNF-BEZ-04**  
  Sesja użytkownika wygasa automatycznie po **30 minutach** braku aktywności.

### **Użyteczność**

* **WNF-UZY-01**  
  Kluczowe funkcje systemu są dostępne z poziomu interfejsu użytkownika w maksymalnie **3 krokach**.

* **WNF-UZY-02**  
  System prezentuje jednoznaczne i czytelne komunikaty o błędach oraz ostrzeżeniach.

## **5.2. Jakość projektu**

### **Modyfikowalność**

* **WNF-MOD-01**  
   Dodanie nowego typu usługi nie wymaga modyfikacji istniejących modułów systemu.

* **WNF-MOD-02**  
   Logika generowania raportów jest wydzielona od logiki obsługi zleceń.

### **Skalowalność**

* **WNF-SKA-01**  
  System umożliwia obsługę wielu oddziałów w ramach jednej instancji aplikacji.

* **WNF-SKA-02**  
  System zachowuje stabilność działania przy wzroście liczby zleceń do **1000**.

### **Testowalność**

* **WNF-TES-01**  
  Logika biznesowa systemu jest możliwa do walidacji dla automatycznych scenariuszy testowych .

### **Przenośność**

* **WNF-POR-01**  
   System może zostać uruchomiony w różnych środowiskach (lokalne, serwerowe, chmurowe) bez modyfikacji kodu źródłowego.

## **5.3. Priorytetyzacja wymagań**

| Priorytet | Atrybut Jakościowy | Kod Wymagania | Uzasadnienie biznesowe |
| :---- | :---- | :---- | :---- |
| **Krytyczny** | **Bezpieczeństwo** | WNF-BEZ-01, 02 | Ochrona danych osobowych (RODO) i wrażliwych informacji o zmarłych jest fundamentem prawnym działania systemu. |
| **Krytyczny** | **Niezawodność** | WNF-NIEZ-01 | Każdy błąd w zapisie (np. dublowanie rezerwacji kaplicy) skutkuje katastrofą wizerunkową i logistyczną. |
| **Wysoki** | **Użyteczność** | WNF-UZY-01, 02 | Pracownik musi obsłużyć klienta w żałobie sprawnie i z empatią; system nie może go rozpraszać skomplikowaną obsługą. |
| **Wysoki** | **Dostępność** | WNF-DOST-01 | Usługi pogrzebowe są świadczone 24/7. Brak dostępu do grafiku transportów paraliżuje pracę terenową. |
| **Średni** | **Wydajność** | WNF-WYD-01 | Kluczowa dla realizacji celu biznesowego (obsługa \< 15 min), ale mniej istotna niż bezpieczeństwo danych. |
| **Średni** | **Modyfikowalność** | WNF-MOD-01 | Pozwala na szybkie dostosowanie oferty (np. nowe typy ceremonii) bez kosztownej przebudowy całego kodu. |
| **Niski** | **Skalowalność** | WNF-SKA-01 | Istotna w kontekście rozwoju firmy (nowe oddziały), ale nie wpływa na bieżącą, poprawną realizację zlecenia. |

## **6\. Odkrywanie i Analiza Wymagań**

### **6.1. Analiza Porównawcza**

Proces ten pozwolił na zidentyfikowanie standardów rynkowych oraz nisz, które system Pogrzebalia v1.0 może wypełnić, aby zyskać przewagę konkurencyjną.

#### **Krok 1: Identyfikacja Konkurencji i Wzorców**

* **Konkurencja bezpośrednia:** Specjalistyczne oprogramowanie dla branży funeralnej.  
* **Konkurencja pośrednia:** Ogólne systemy do zarządzania projektami i logistyką (np. *Trello*, *Monday.com*) oraz systemy CRM wykorzystywane przez mniejsze zakłady.  
* **Wzorce funkcjonalne:** Systemy rezerwacji medycznej (np. *ZnanyLekarz*) pod kątem precyzyjnego zarządzania kalendarzem i powiadomień SMS/E-mail.

#### **Krok 2: Definicja Kryteriów Oceny (Tabela Porównawcza)**

| Kryterium Oceny | Tradycyjne metody (Excel/Papier) | Systemy Konkurencyjne (Legacy) | Pogrzebalia v1.0 (Cele) |
| :---- | :---- | :---- | :---- |
| **Mobilność** | Brak | Ograniczona (aplikacje desktopowe) | Pełna (Cloud, Responsywność) |
| **Automatyzacja komunikacji** | Manualna (telefon/SMS) | Podstawowa (tylko e-mail) | Wielokanałowa (SMS, Mail, Push) |
| **Integracja Logistyki** | Brak (osobne notesy) | Częściowa | Pełna (Harmonogram przewozu zwłok) |
| **Szybkość wyceny** | Wolna (liczenie ręczne) | Średnia (wymaga konfiguracji) | Natychmiastowa (Automatyczny kalkulator) |
| **Zgodność z RODO** | Niska (trudność w usuwaniu danych) | Średnia | Wysoka (Privacy by design) |

#### **Krok 3: Synteza Wyników i Wnioski dla SRS**

1. **Gdzie konkurencja zawodzi?** Większość systemów rynkowych jest przeładowana funkcjami księgowymi, co czyni je mało intuicyjnymi. **Pogrzebalia v1.0** stawia na prostotę (Zasada 3 kroków \- WNF-UZY-01).  
2. **Unikalna wartość (USP):** Automatyczna kalkulacja kosztów zlecenia w czasie rzeczywistym podczas rozmowy z klientem oraz zintegrowany moduł logistyki transportu, który w innych systemach często jest osobnym, płatnym modułem.  
3. **Wnioski dla projektu:**  
   * Należy położyć nacisk na moduł powiadomień (WF-ZL-01), ponieważ automatyzacja kontaktu z rodziną zmarłego jest najbardziej pożądaną funkcją przez właścicieli domów pogrzebowych.  
   * Wymagany jest eksport do kalendarzy zewnętrznych (Google/Outlook), co ułatwi pracę pracownikom terenowym bez konieczności ciągłego logowania się do pełnego systemu.

# **Dodatki**

## **Dodatek A: Diagram przypadków użycia**

### **Aktorzy systemu:**

* **Administrator**

* **Pracownik biura**

* **Pracownik terenowy**

### **Główne przypadki użycia:**

**Administrator:**

* Zarządzanie użytkownikami i rolami

* Konfiguracja systemu

* Generowanie raportów zbiorczych

* Przegląd statystyk realizacji zleceń

**Pracownik biura:**

* Tworzenie i edycja zleceń pogrzebowych

* Rejestracja i obsługa klientów

* Planowanie logistyki przewozu zwłok (kostnica, krematorium, cmentarz)

* Uzgadnianie procesów cmentarnych (wykup miejsca, kopanie grobu)

* Przegląd harmonogramów

* Generowanie raportów operacyjnych dla pojedynczych zleceń

**Pracownik terenowy:**

* Przegląd przypisanych zleceń

* Podgląd harmonogramu ceremonii i transportów

* Potwierdzanie wykonania czynności terenowych

## **Dodatek B: Persony**

### **Anna – pracownik biura**

* Wiek: 35 lat

* Doświadczenie: 10 lat w branży pogrzebowej

* Cele:

  * Sprawna organizacja zleceń pogrzebowych

  * Koordynacja logistyki transportu i terminów

  * Dopilnowanie dokumentacji

* Problemy:

  * Duża liczba równoległych zleceń

  * Ryzyko konfliktów terminów

  * Ręczne śledzenie formalności

* Oczekiwania wobec systemu:

  * Centralne miejsce do zarządzania całym procesem

  * Automatyczne wykrywanie konfliktów

  * Łatwy dostęp do raportów i harmonogramów

### **Marek – administrator**

* Wiek: 42 lata

* Rola: Administrator systemu i właściciel domu pogrzebowego

* Cele:

  * Kontrola jakości realizowanych usług

  * Analiza efektywności pracy zespołu

  * Dostęp do raportów zarządczych

* Problemy:

  * Brak danych do podejmowania decyzji

  * Trudności w analizie obciążenia pracowników

* Oczekiwania wobec systemu:

  * Generowanie raportów zbiorczych

  * Stabilny i bezpieczny system

  * Możliwość dalszej rozbudowy

## **Dodatek C: Kwestie do rozwiązania**

1. **Integracja z systemami urzędowymi**

   * Możliwość integracji z systemami administracji publicznej (np. USC) w celu automatycznego pobierania lub przesyłania danych

   * Wymaga analizy prawnej i technicznej

2. **Obsługa wielu oddziałów**

   * Możliwość rozszerzenia systemu o obsługę wielu lokalizacji domu pogrzebowego

   * Wymaga rozbudowy modelu danych oraz mechanizmów uprawnień

3. **Skalowalność raportowania**

   * Rosnąca liczba zleceń może wpłynąć na wydajność generowania raportów

   * Konieczność analizy wydajności i archiwizacji danych

4. **Bezpieczeństwo danych wrażliwych**

   * Dane osobowe i informacje o zmarłych wymagają szczególnej ochrony

   * Konieczność spełnienia wymagań RODO i kontroli dostępu
