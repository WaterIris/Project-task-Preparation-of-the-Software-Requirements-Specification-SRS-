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

---
