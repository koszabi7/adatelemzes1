# Ingatlanár-előrejelzés USA adathalmazon
# Projekt áttekintés
Ez a projekt egy adatelemzési és gépi tanulási feladat, amelynek célja az amerikai ingatlanpiaci adatok feldolgozása, tisztítása, vizualizálása és előrejelzése.
A feladat központi kérdése: hogyan lehet előrejelezni az ingatlanok négyzetméterárát (ár/m²) különböző években és jellemzők alapján.
# Adatok
Forrásfájl: Dataset_Ingatlan_USA_meres.csv (33 606 sor, 21 oszlop)
Tartalom:
  Ingatlan azonosítók (rowid, address, suburban, postcode, koordináták)
  Fizikai jellemzők (szobák száma, fürdők, garázs, telek- és alapterület, építés éve)
  Ár adatok (iprice, sqm_price)
  Közlekedési és oktatási jellemzők (központi távolság, közeli iskola és állomás adatai)
A feldolgozás során kiszámításra került a négyzetméterár, valamint egy 2024-re normalizált célváltozó, amely lehetővé teszi az idősoros összehasonlítást.
# Adattisztítás
Hiányzó értékek pótlása mediánnal.
Új bináris jelzőváltozók létrehozása a hiányzó adatok jelzésére.
Szélsőséges értékek kezelése (±5 szórás vágás).
Normalizáció a 2024-es árszinthez igazítva.
# Modellépítés
Három regressziós modellt alkalmaztam:
  Lineáris regresszió
  Random Forest Regressor (GridSearchCV paraméterhangolással)
  Gradient Boosting Regressor (GridSearchCV paraméterhangolással)
A modellek teljesítményét a MAPE (Mean Absolute Percentage Error) alapján értékeltük.
# Eredmények
Lineáris regresszió: ~0.14
Random Forest: ~0.125
Gradient Boosting: ~0.046 (legjobb egyedi modell)
Modellátlagolás (ensemble) tovább javította az eredményeket (legjobb kombináció: ~0.071 MAPE)
# 2025-ös előrejelzés
A 2025-ös adatokra a GBM modellt alkalmazva a prediktált ingatlanárak átlaga ~516 603 USD lett.
Az előrejelzések elmentésre kerültek: predictions_2025_gbm.csv
# Használt eszközök és könyvtárak
Python 3
Könyvtárak:
  pandas, numpy – adatok kezelése
  matplotlib – vizualizáció
  scikit-learn – modellek és metrikák
