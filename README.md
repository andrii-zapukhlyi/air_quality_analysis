# Air quality analysis - projekt zaliczeniowy z przedmiotu "Eksploracja danych"
Autorzy: Mateusz Drozd, Andrii Zapukhlyi

## Cel projektu
Celem projektu jest zbudowanie modelu regresyjnego, który na podstawie dostępnych pomiarów (wszystkich kolumn z wyjątkiem `Date` i `Time`) będzie w stanie jak najdokładniej przewidzieć godzinową wartość stężenia benzenu (`C6H6(GT)`). W tym celu:
**wszystkie zmienne użyte do przewidywania (`C6H6(GT)`):**  
   - Odpowiedzi pięciu sensorów półprzewodnikowych (`PT08.S1(CO)`, `PT08.S2(NMHC)`, `PT08.S3(NOx)`, `PT08.S4(NO2)`, `PT08.S5(O3)`)  
   - Pomiary referencyjne innych gazów (`CO(GT)`, `NMHC(GT)`, `NOx(GT)`, `NO2(GT)`)  
   - Warunki meteorologiczne (`T`, `RH`, `AH`)  

## Zbiór Danych
Zbiór danych <a href = "https://archive.ics.uci.edu/dataset/360/air+quality">Air Quality UCI</a> zawiera 9 358 instancji godzinnych uśrednionych odpowiedzi pięciu czujników półprzewodnikowych (metal-oxide) zainstalowanych w urządzeniu wieloczujnikowym do monitoringu jakości powietrza w terenie, wraz z jednoczesnymi pomiarami referencyjnymi stężeń zanieczyszczeń przez certyfikowany analizator.  
Dane obejmują okres od marca 2004 do lutego 2005 (13 miesięcy).  

| Nr | Nazwa zmiennej               | Opis                                                                                   |
| -- | ---------------------------- | -------------------------------------------------------------------------------------- |
| 0  | **Date**                     | Data pomiaru w formacie DD/MM/YYYY                                                     |
| 1  | **Time**                     | Godzina pomiaru w formacie HH.MM.SS                                                    |
| 2  | **True CO (mg/m³)**          | Rzeczywiste stężenie tlenku węgla (CO) zmierzone przez analizator referencyjny         |
| 3  | **PT08.S1 (tin oxide)**      | Odpowiedź sensora tlenku cyny (nominalnie celowanego w CO)                             |
| 4  | **True NMHC (µg/m³)**        | Rzeczywiste stężenie węglowodorów niemetanicznych (NMHC) przez analizator referencyjny |
| 5  | **True Benzene (µg/m³)**     | Rzeczywiste stężenie benzenu przez analizator referencyjny                             |
| 6  | **PT08.S2 (titania)**        | Odpowiedź sensora tlenku tytanu (nominalnie celowanego w NMHC)                         |
| 7  | **True NOx (ppb)**           | Rzeczywiste stężenie tlenków azotu (NOx) w ppb przez analizator referencyjny           |
| 8  | **PT08.S3 (tungsten oxide)** | Odpowiedź sensora tlenku wolframu (nominalnie celowanego w NOx)                        |
| 9  | **True NO₂ (µg/m³)**         | Rzeczywiste stężenie dwutlenku azotu (NO₂) przez analizator referencyjny               |
| 10 | **PT08.S4 (tungsten oxide)** | Odpowiedź sensora tlenku wolframu (nominalnie celowanego w NO₂)                        |
| 11 | **PT08.S5 (indium oxide)**   | Odpowiedź sensora tlenku indu (nominalnie celowanego w O₃)                             |
| 12 | **Temperature (°C)**         | Temperatura powietrza w stopniach Celsjusza                                            |
| 13 | **Relative Humidity (%)**    | Wilgotność względna powietrza w procentach                                             |
| 14 | **Absolute Humidity**        | Wilgotność bezwzględna (AH)                                                            |


## Charakterystyka danych
- **Typ:** Wielozmiennowy, szereg czasowy.  
- **Zadanie:** Regresja.  
- **Typ cech:** wartości rzeczywiste (float).  
- **Liczba instancji:** 9 358.  
- **Liczba cech:** 15.  


## Osiągnięcia
Najlepszy model *Polynomial Regression* osiągnąl najmniejsze błędy predykcji na zbiorze testowym:

- RMSE: 0.0319
- MAE: 0.027
- $R^2$: 1.0

Zmienna docelowa, C6G6(GT) (stężenie benzenu w powietrzu), ma średnią 10.08 i odchylenie standardowe 7.45, z wartościami od 0.1 do 63.7. Wyniki te wskazują na stosunkowo małe błędy przewidywania w porównaniu do skali danych.