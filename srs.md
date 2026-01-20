# **Specyfikacja Wymagań Oprogramowania (SRS)**

## **System Rezerwacji Zasobów Uczelnianych (SRZU)**

**Wersja:** 1.0

---

## **1\. Wstęp**

### **1.1. Cel dokumentu**

Celem niniejszego dokumentu jest kompletne, jednoznaczne i weryfikowalne zdefiniowanie wymagań dla Systemu Rezerwacji Zasobów Uczelnianych (SRZU). Dokument pełni rolę kontraktu pomiędzy interesariuszami biznesowymi a zespołem wytwórczym i stanowi podstawę do projektowania, implementacji, testowania oraz walidacji systemu.

### **1.2. Wizja, zakres i cele produktu**

**Wizja:**  
Stworzenie jednego, centralnego systemu umożliwiającego studentom i pracownikom uczelni szybki, bezkonfliktowy i przejrzysty dostęp do rezerwacji sal, laboratoriów oraz sprzętu dydaktycznego.

**Zakres systemu:**  
System SRZU umożliwia:

* przegląd i wyszukiwanie zasobów uczelnianych,  
* rezerwację zasobów w określonych przedziałach czasowych,  
* zarządzanie rezerwacjami przez użytkowników,  
* administracyjne zarządzanie zasobami i ich dostępnością,  
* kontrolę konfliktów rezerwacyjnych.

**Cele biznesowe i użytkowe (KPIs):**

* średni czas wykonania rezerwacji ≤ 2 minuty,  
* 0 konfliktów czasowych w zatwierdzonych rezerwacjach,  
* ≥ 90% pozytywnych ocen użyteczności w ankiecie użytkowników,  
* wyelimowanie zgłoszeń mailowych dotyczących rezerwacji.

**Poza zakresem:**

* obsługa płatności, rozliczeń i ubezpieczeń zasobów,  
* automatyczne planowanie zajęć dydaktycznych,  
* integracja z systemami zewnętrznych instytucji spoza uczelni.

### **1.3. Definicje, akronimy i skróty**

* **Zasób** – sala, laboratorium lub sprzęt podlegający rezerwacji.  
* **Rezerwacja** – przydzielenie zasobu użytkownikowi na określony czas.  
* **Konflikt rezerwacji** – nakładające się czasowo rezerwacje tego samego zasobu.  
* **SRZU** – System Rezerwacji Zasobów Uczelnianych.

### **1.4. Przegląd dokumentu**

Rozdział 2 zawiera ogólny opis systemu. Rozdział 3 opisuje interfejsy zewnętrzne. Rozdział 4 definiuje wymagania funkcjonalne wraz z kryteriami akceptacji. Rozdział 5 opisuje wymagania niefunkcjonalne. Rozdział 6 prezentuje analizę porównawczą. Dodatki zawierają modele analityczne, persony oraz otwarte kwestie.

---
