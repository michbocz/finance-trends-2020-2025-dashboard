# 📈 Investor Behavior & Psychology Dashboard (2020-2025)

Kompletna analiza behawioralna inwestorów, badająca relacje między demografią, skłonnością do ryzyka a wyborem instrumentów finansowych.
---

<img width="1318" height="742" alt="image" src="https://github.com/user-attachments/assets/7bea7ced-6d2b-4841-bbe7-d2d55f5b84e5" />

## Cel Projektu (Business Case)
Większość raportów finansowych skupia się na tym, **ile** kapitału płynie na rynek. Ten projekt odpowiada na pytanie: **dlaczego** tam płynie. Celem dashboardu jest dostarczenie instytucjom finansowym i doradcom wiedzy o psychologii inwestorów, co pozwala na lepsze profilowanie produktów i optymalizację strategii marketingowych.


## 📊 Główne Wnioski Biznesowe (Key Insights)
Na podstawie analizy danych wyodrębniono następujące wzorce behawioralne:
1. **Premia za ryzyko (Chciwość vs Bezpieczeństwo):** Analiza macierzy cieplnej (Heatmap) udowadnia, że inwestorzy deklarujący skłonność do ryzyka oczekują w zamian skrajnie wysokich stóp zwrotu (rzędu 30-40%). Większość rynku woli jednak bezpieczne zwroty na poziomie 10-20%.
2. **Motywacje a Lokaty (Fixed Deposits):** Głównym i bezapelacyjnym powodem zamrażania gotówki w bezpiecznych aktywach jest chęć uzyskania "Stałych zysków" (Fixed Returns), co deklasuje inne powody jak ochrona kapitału.
3. **Wiek a Czas Inwestycji:** Projekt obala mit "niecierpliwego pokolenia Z" – młodzi inwestorzy równie często co starsi decydują się na budowę kapitału w długim horyzoncie czasowym.



## 🏗️ Architektura Dashboardu

Raport został zaprojektowany z myślą o maksymalnej czytelności (UI/UX) i podzielony na 3 logiczne sekcje:

### 1. Executive Summary (Overview)
Główny panel sterowania z wykorzystaniem zjawiska *Glassmorphism* oraz efektem *Neon Glow*. Zawiera:
* Demografię inwestorów (Płeć, Wiek).
* Ranking najpopularniejszych instrumentów (Avenues).
* Indeks codziennego sprawdzania portfela (Stres rynkowy).


### 2. Risk Analysis (Ryzyko vs Oczekiwane Zyski)
Sekcja analityczna udowadniająca korelacje.
* **Mapa Cieplna (Heatmap):** Weryfikująca zależność między deklarowanym ryzykiem a oczekiwaniami finansowymi.
* **Wskaźniki Zegarowe (Gauge):** Pokazujące stopień "rozgrzania" rynku i partycypację w giełdzie.

### 3. Psychological Drivers (Cele i Powody)
* Szczegółowy podział powodów, dla których inwestorzy wybierają giełdę (Equity) w kontrze do bezpiecznych lokat (Fixed Deposits).
<img width="1326" height="741" alt="image" src="https://github.com/user-attachments/assets/d99491c9-2b1d-4406-8620-ad225d8063e5" />
---

## 🛠️ Wykorzystane Technologie i Umiejętności
* **Power Query (M):** Czyszczenie danych, transformacja typów, automatyczny Unpivot kolumn z ocenami instrumentów.
* **Modelowanie Danych:** Budowa relacyjnego modelu typu Star Schema (Fakty i Wymiary).
* **DAX (Data Analysis Expressions):** Zaawansowane miary analityczne. Przykładowy kod z projektu:
  ```dax
  % Fixed Deposits = 
  VAR FdUsers = CALCULATE(COUNTROWS('Dim_investor'), 'Dim_investor'[Avenue] = "Fixed Deposits")
  VAR TotalUsers = COUNTROWS('Dim_investor')
  RETURN DIVIDE(FdUsers, TotalUsers, 0)
