
# WeatherPy
----

### Analysis
* As expected, the weather becomes significantly warmer as one approaches the equator (0 Deg. Latitude). More interestingly, however, is the fact that the southern hemisphere tends to be warmer this time of year than the northern hemisphere. This may be due to the tilt of the earth.
* There is no strong relationship between latitude and cloudiness. However, it is interesting to see that a strong band of cities sits at 0, 80, and 100% cloudiness.
* There is no strong relationship between latitude and wind speed. However, in northern hemispheres there is a flurry of cities with over 20 mph of wind.

---

#### Note
* Instructions have been included for each segment. You do not have to follow them exactly, but they are included to help you think through the steps.


```python
# Dependencies and Setup
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import requests
import time

# Import API key
import api_keys

# Incorporated citipy to determine city based on latitude and longitude
from citipy import citipy

# Output File (CSV)
output_data_file = "output_data/cities.csv"

# Range of latitudes and longitudes
lat_range = (-90, 90)
lng_range = (-180, 180)
```

## Generate Cities List


```python
# List for holding lat_lngs and cities
lat_lngs = []
cities = []

# Create a set of random lat and lng combinations
lats = np.random.uniform(low=-90.000, high=90.000, size=1500)
lngs = np.random.uniform(low=-180.000, high=180.000, size=1500)
lat_lngs = zip(lats, lngs)

# Identify nearest city for each lat, lng combination
for lat_lng in lat_lngs:
    city = citipy.nearest_city(lat_lng[0], lat_lng[1]).city_name
    
    # If the city is unique, then add it to a our cities list
    if city not in cities:
        cities.append(city)

# Print the city count to confirm sufficient count
len(cities)
```




    616



### Perform API Calls
* Perform a weather check on each city using a series of successive API calls.
* Include a print log of each city as it'sbeing processed (with the city number and city name).



```python

```

    Beginning Data Retrieval     
    -----------------------------
    Processing Record 1 of Set 1 | lompoc
    Processing Record 2 of Set 1 | klaksvik
    Processing Record 3 of Set 1 | bisignano
    Processing Record 4 of Set 1 | bengkulu
    City not found. Skipping...
    Processing Record 5 of Set 1 | hilo
    Processing Record 6 of Set 1 | rikitea
    Processing Record 7 of Set 1 | ahipara
    Processing Record 8 of Set 1 | lebu
    Processing Record 9 of Set 1 | hamilton
    Processing Record 10 of Set 1 | castro
    Processing Record 11 of Set 1 | ashland
    Processing Record 12 of Set 1 | ushuaia
    Processing Record 13 of Set 1 | haines junction
    Processing Record 14 of Set 1 | punta arenas
    Processing Record 15 of Set 1 | salalah
    Processing Record 16 of Set 1 | port macquarie
    Processing Record 17 of Set 1 | mataura
    Processing Record 18 of Set 1 | saint-philippe
    Processing Record 19 of Set 1 | kaitangata
    Processing Record 20 of Set 1 | souillac
    Processing Record 21 of Set 1 | srednekolymsk
    Processing Record 22 of Set 1 | busselton
    Processing Record 23 of Set 1 | severo-kurilsk
    Processing Record 24 of Set 1 | belushya guba
    City not found. Skipping...
    Processing Record 25 of Set 1 | ivaipora
    City not found. Skipping...
    Processing Record 26 of Set 1 | cape town
    Processing Record 27 of Set 1 | ambilobe
    Processing Record 28 of Set 1 | yellowknife
    Processing Record 29 of Set 1 | talnakh
    Processing Record 30 of Set 1 | namatanai
    Processing Record 31 of Set 1 | scottsburgh
    City not found. Skipping...
    Processing Record 32 of Set 1 | leningradskiy
    Processing Record 33 of Set 1 | khormuj
    City not found. Skipping...
    Processing Record 34 of Set 1 | kodiak
    Processing Record 35 of Set 1 | muros
    Processing Record 36 of Set 1 | tamandare
    Processing Record 37 of Set 1 | taolanaro
    City not found. Skipping...
    Processing Record 38 of Set 1 | albany
    Processing Record 39 of Set 1 | lumut
    Processing Record 40 of Set 1 | sukumo
    Processing Record 41 of Set 1 | chapais
    Processing Record 42 of Set 1 | khatanga
    Processing Record 43 of Set 1 | ordzhonikidze
    Processing Record 44 of Set 1 | jiangyou
    Processing Record 45 of Set 1 | ancud
    Processing Record 46 of Set 1 | vila franca do campo
    Processing Record 47 of Set 1 | shchelkun
    Processing Record 48 of Set 1 | vanimo
    Processing Record 49 of Set 1 | kalmanhaza
    Processing Record 50 of Set 1 | butaritari
    Processing Record 0 of Set 2 | codrington
    Processing Record 1 of Set 2 | ayolas
    Processing Record 2 of Set 2 | kapaa
    Processing Record 3 of Set 2 | east london
    Processing Record 4 of Set 2 | vaini
    Processing Record 5 of Set 2 | tessalit
    Processing Record 6 of Set 2 | panguna
    Processing Record 7 of Set 2 | cockburn town
    Processing Record 8 of Set 2 | valerianovsk
    Processing Record 9 of Set 2 | tingrela
    City not found. Skipping...
    Processing Record 10 of Set 2 | novobirilyussy
    Processing Record 11 of Set 2 | krasnoborsk
    Processing Record 12 of Set 2 | mar del plata
    Processing Record 13 of Set 2 | new norfolk
    Processing Record 14 of Set 2 | khonuu
    City not found. Skipping...
    Processing Record 15 of Set 2 | vila do maio
    Processing Record 16 of Set 2 | dikson
    Processing Record 17 of Set 2 | tsihombe
    City not found. Skipping...
    Processing Record 18 of Set 2 | toliary
    City not found. Skipping...
    Processing Record 19 of Set 2 | kazalinsk
    City not found. Skipping...
    Processing Record 20 of Set 2 | livani
    Processing Record 21 of Set 2 | urucui
    Processing Record 22 of Set 2 | ribeira grande
    Processing Record 23 of Set 2 | qaanaaq
    Processing Record 24 of Set 2 | sentyabrskiy
    City not found. Skipping...
    Processing Record 25 of Set 2 | tuatapere
    Processing Record 26 of Set 2 | bocaiuva
    Processing Record 27 of Set 2 | jiexiu
    Processing Record 28 of Set 2 | quelimane
    Processing Record 29 of Set 2 | rujewa
    Processing Record 30 of Set 2 | cherskiy
    Processing Record 31 of Set 2 | port elizabeth
    Processing Record 32 of Set 2 | yanchukan
    City not found. Skipping...
    Processing Record 33 of Set 2 | fortuna
    Processing Record 34 of Set 2 | belyy yar
    Processing Record 35 of Set 2 | venezuela
    Processing Record 36 of Set 2 | bambous virieux
    Processing Record 37 of Set 2 | illoqqortoormiut
    City not found. Skipping...
    Processing Record 38 of Set 2 | barrow
    Processing Record 39 of Set 2 | mitsamiouli
    Processing Record 40 of Set 2 | hunza
    City not found. Skipping...
    Processing Record 41 of Set 2 | bunia
    Processing Record 42 of Set 2 | boa vista
    Processing Record 43 of Set 2 | kudahuvadhoo
    Processing Record 44 of Set 2 | mys shmidta
    City not found. Skipping...
    Processing Record 45 of Set 2 | bluff
    Processing Record 46 of Set 2 | okhotsk
    Processing Record 47 of Set 2 | muzaffarabad
    Processing Record 48 of Set 2 | avarua
    Processing Record 49 of Set 2 | esperance
    Processing Record 0 of Set 3 | arenapolis
    Processing Record 1 of Set 3 | tuktoyaktuk
    Processing Record 2 of Set 3 | nemuro
    Processing Record 3 of Set 3 | attawapiskat
    City not found. Skipping...
    Processing Record 4 of Set 3 | rio gallegos
    Processing Record 5 of Set 3 | svetlaya
    Processing Record 6 of Set 3 | nome
    Processing Record 7 of Set 3 | caravelas
    Processing Record 8 of Set 3 | karamea
    City not found. Skipping...
    Processing Record 9 of Set 3 | mandalgovi
    Processing Record 10 of Set 3 | carnarvon
    Processing Record 11 of Set 3 | atuona
    Processing Record 12 of Set 3 | pemangkat
    City not found. Skipping...
    Processing Record 13 of Set 3 | karaul
    City not found. Skipping...
    Processing Record 14 of Set 3 | qiqihar
    Processing Record 15 of Set 3 | cabo san lucas
    Processing Record 16 of Set 3 | jamestown
    Processing Record 17 of Set 3 | komsomolskiy
    Processing Record 18 of Set 3 | arraial do cabo
    Processing Record 19 of Set 3 | tiksi
    Processing Record 20 of Set 3 | amnat charoen
    Processing Record 21 of Set 3 | provideniya
    Processing Record 22 of Set 3 | luang prabang
    Processing Record 23 of Set 3 | hami
    Processing Record 24 of Set 3 | saskylakh
    Processing Record 25 of Set 3 | kyren
    Processing Record 26 of Set 3 | yuanping
    Processing Record 27 of Set 3 | dukat
    Processing Record 28 of Set 3 | barentsburg
    City not found. Skipping...
    Processing Record 29 of Set 3 | chuy
    Processing Record 30 of Set 3 | dorfen
    Processing Record 31 of Set 3 | ayan
    Processing Record 32 of Set 3 | port alfred
    Processing Record 33 of Set 3 | nanortalik
    Processing Record 34 of Set 3 | nizhneyansk
    City not found. Skipping...
    Processing Record 35 of Set 3 | vertientes
    Processing Record 36 of Set 3 | charters towers
    Processing Record 37 of Set 3 | nenjiang
    Processing Record 38 of Set 3 | hermanus
    Processing Record 39 of Set 3 | saleaula
    City not found. Skipping...
    Processing Record 40 of Set 3 | puerto del rosario
    Processing Record 41 of Set 3 | husavik
    Processing Record 42 of Set 3 | maldonado
    Processing Record 43 of Set 3 | bintulu
    Processing Record 44 of Set 3 | warqla
    City not found. Skipping...
    Processing Record 45 of Set 3 | luderitz
    Processing Record 46 of Set 3 | vardo
    Processing Record 47 of Set 3 | faanui
    Processing Record 48 of Set 3 | muzhi
    Processing Record 49 of Set 3 | zhangye
    Processing Record 0 of Set 4 | nouadhibou
    Processing Record 1 of Set 4 | oussouye
    Processing Record 2 of Set 4 | agaro
    Processing Record 3 of Set 4 | samusu
    City not found. Skipping...
    Processing Record 4 of Set 4 | tasiilaq
    Processing Record 5 of Set 4 | amderma
    City not found. Skipping...
    Processing Record 6 of Set 4 | bathsheba
    Processing Record 7 of Set 4 | pacific grove
    Processing Record 8 of Set 4 | half moon bay
    Processing Record 9 of Set 4 | goderich
    Processing Record 10 of Set 4 | severnyy
    City not found. Skipping...
    Processing Record 11 of Set 4 | erenhot
    Processing Record 12 of Set 4 | hasaki
    Processing Record 13 of Set 4 | agadez
    Processing Record 14 of Set 4 | hobart
    Processing Record 15 of Set 4 | drummondville
    Processing Record 16 of Set 4 | selfoss
    Processing Record 17 of Set 4 | carman
    Processing Record 18 of Set 4 | kurumkan
    Processing Record 19 of Set 4 | rawson
    Processing Record 20 of Set 4 | osakarovka
    Processing Record 21 of Set 4 | sitka
    Processing Record 22 of Set 4 | pec
    Processing Record 23 of Set 4 | nacala
    Processing Record 24 of Set 4 | vaitupu
    City not found. Skipping...
    Processing Record 25 of Set 4 | ewo
    Processing Record 26 of Set 4 | alihe
    Processing Record 27 of Set 4 | felipe carrillo puerto
    Processing Record 28 of Set 4 | sept-iles
    Processing Record 29 of Set 4 | anzio
    Processing Record 30 of Set 4 | abeche
    Processing Record 31 of Set 4 | chokurdakh
    Processing Record 32 of Set 4 | sao filipe
    Processing Record 33 of Set 4 | yatou
    Processing Record 34 of Set 4 | pangkalanbuun
    Processing Record 35 of Set 4 | namibe
    Processing Record 36 of Set 4 | caltagirone
    Processing Record 37 of Set 4 | araguacu
    City not found. Skipping...
    Processing Record 38 of Set 4 | atuntaqui
    Processing Record 39 of Set 4 | marshfield
    Processing Record 40 of Set 4 | saint-joseph
    Processing Record 41 of Set 4 | chambas
    Processing Record 42 of Set 4 | mahebourg
    Processing Record 43 of Set 4 | abadan
    Processing Record 44 of Set 4 | lagoa
    Processing Record 45 of Set 4 | axim
    Processing Record 46 of Set 4 | sioux lookout
    Processing Record 47 of Set 4 | voh
    Processing Record 48 of Set 4 | puerto ayora
    Processing Record 49 of Set 4 | sinnamary
    Processing Record 0 of Set 5 | duz
    City not found. Skipping...
    Processing Record 1 of Set 5 | upernavik
    Processing Record 2 of Set 5 | port hardy
    Processing Record 3 of Set 5 | vieste
    Processing Record 4 of Set 5 | dalvik
    Processing Record 5 of Set 5 | tual
    Processing Record 6 of Set 5 | novopokrovka
    Processing Record 7 of Set 5 | soyo
    Processing Record 8 of Set 5 | broken hill
    Processing Record 9 of Set 5 | columbia
    Processing Record 10 of Set 5 | sao joao da barra
    Processing Record 11 of Set 5 | lumphat
    Processing Record 12 of Set 5 | ciudad bolivar
    Processing Record 13 of Set 5 | san quintin
    Processing Record 14 of Set 5 | bredasdorp
    Processing Record 15 of Set 5 | torbay
    Processing Record 16 of Set 5 | hithadhoo
    Processing Record 17 of Set 5 | tabarqah
    City not found. Skipping...
    Processing Record 18 of Set 5 | vila velha
    Processing Record 19 of Set 5 | samaniego
    Processing Record 20 of Set 5 | kruisfontein
    Processing Record 21 of Set 5 | tumannyy
    City not found. Skipping...
    Processing Record 22 of Set 5 | dunedin
    Processing Record 23 of Set 5 | nikolskoye
    Processing Record 24 of Set 5 | geraldton
    Processing Record 25 of Set 5 | sarangani
    Processing Record 26 of Set 5 | bontang
    Processing Record 27 of Set 5 | jacareacanga
    Processing Record 28 of Set 5 | palabuhanratu
    City not found. Skipping...
    Processing Record 29 of Set 5 | raudeberg
    Processing Record 30 of Set 5 | terrenate
    Processing Record 31 of Set 5 | vao
    Processing Record 32 of Set 5 | asau
    City not found. Skipping...
    Processing Record 33 of Set 5 | hovd
    Processing Record 34 of Set 5 | bure
    Processing Record 35 of Set 5 | ranot
    Processing Record 36 of Set 5 | barawe
    City not found. Skipping...
    Processing Record 37 of Set 5 | merauke
    Processing Record 38 of Set 5 | prichard
    Processing Record 39 of Set 5 | gravelbourg
    Processing Record 40 of Set 5 | searcy
    Processing Record 41 of Set 5 | chagda
    City not found. Skipping...
    Processing Record 42 of Set 5 | victoria
    Processing Record 43 of Set 5 | sisimiut
    Processing Record 44 of Set 5 | trelew
    Processing Record 45 of Set 5 | aban
    City not found. Skipping...
    Processing Record 46 of Set 5 | vakhrushev
    Processing Record 47 of Set 5 | pierre
    Processing Record 48 of Set 5 | ilulissat
    Processing Record 49 of Set 5 | lorengau
    Processing Record 0 of Set 6 | mokrousovo
    Processing Record 1 of Set 6 | baltay
    Processing Record 2 of Set 6 | kainantu
    Processing Record 3 of Set 6 | goulburn
    Processing Record 4 of Set 6 | lincoln
    Processing Record 5 of Set 6 | harnosand
    Processing Record 6 of Set 6 | camana
    City not found. Skipping...
    Processing Record 7 of Set 6 | pleshanovo
    Processing Record 8 of Set 6 | ostrovnoy
    Processing Record 9 of Set 6 | porto novo
    Processing Record 10 of Set 6 | kawana waters
    City not found. Skipping...
    Processing Record 11 of Set 6 | quatre cocos
    Processing Record 12 of Set 6 | marzuq
    Processing Record 13 of Set 6 | prince george
    Processing Record 14 of Set 6 | grand river south east
    City not found. Skipping...
    Processing Record 15 of Set 6 | sorsk
    Processing Record 16 of Set 6 | port blair
    Processing Record 17 of Set 6 | shihezi
    Processing Record 18 of Set 6 | coffs harbour
    Processing Record 19 of Set 6 | rasova
    Processing Record 20 of Set 6 | dingle
    Processing Record 21 of Set 6 | la primavera
    Processing Record 22 of Set 6 | tezu
    Processing Record 23 of Set 6 | qasigiannguit
    Processing Record 24 of Set 6 | westport
    Processing Record 25 of Set 6 | peleduy
    Processing Record 26 of Set 6 | yei
    City not found. Skipping...
    Processing Record 27 of Set 6 | dakar
    Processing Record 28 of Set 6 | temaraia
    City not found. Skipping...
    Processing Record 29 of Set 6 | pisco
    Processing Record 30 of Set 6 | buzuluk
    Processing Record 31 of Set 6 | jahrom
    City not found. Skipping...
    Processing Record 32 of Set 6 | ponferrada
    Processing Record 33 of Set 6 | kaeo
    Processing Record 34 of Set 6 | chimbote
    Processing Record 35 of Set 6 | rocha
    Processing Record 36 of Set 6 | kurkino
    Processing Record 37 of Set 6 | kavaratti
    Processing Record 38 of Set 6 | puri
    Processing Record 39 of Set 6 | maues
    Processing Record 40 of Set 6 | kapit
    Processing Record 41 of Set 6 | sinegorye
    Processing Record 42 of Set 6 | thompson
    Processing Record 43 of Set 6 | kadykchan
    City not found. Skipping...
    Processing Record 44 of Set 6 | itaueira
    Processing Record 45 of Set 6 | georgetown
    Processing Record 46 of Set 6 | parana
    Processing Record 47 of Set 6 | govindgarh
    Processing Record 48 of Set 6 | laguna
    Processing Record 49 of Set 6 | tura
    Processing Record 0 of Set 7 | nhulunbuy
    Processing Record 1 of Set 7 | buala
    Processing Record 2 of Set 7 | ngunguru
    Processing Record 3 of Set 7 | abu zabad
    Processing Record 4 of Set 7 | katete
    Processing Record 5 of Set 7 | flin flon
    Processing Record 6 of Set 7 | fayaoue
    Processing Record 7 of Set 7 | umzimvubu
    City not found. Skipping...
    Processing Record 8 of Set 7 | port hedland
    Processing Record 9 of Set 7 | omsukchan
    Processing Record 10 of Set 7 | la asuncion
    Processing Record 11 of Set 7 | hambantota
    Processing Record 12 of Set 7 | matagami
    Processing Record 13 of Set 7 | palmer
    Processing Record 14 of Set 7 | dzhebariki-khaya
    Processing Record 15 of Set 7 | shitanjing
    Processing Record 16 of Set 7 | ixtapa
    Processing Record 17 of Set 7 | bethel
    Processing Record 18 of Set 7 | khani
    Processing Record 19 of Set 7 | saint george
    Processing Record 20 of Set 7 | whitehorse
    Processing Record 21 of Set 7 | isiolo
    Processing Record 22 of Set 7 | sao paulo de olivenca
    Processing Record 23 of Set 7 | buckeye
    Processing Record 24 of Set 7 | wewak
    Processing Record 25 of Set 7 | huarmey
    Processing Record 26 of Set 7 | satitoa
    City not found. Skipping...
    Processing Record 27 of Set 7 | la libertad
    Processing Record 28 of Set 7 | norman wells
    Processing Record 29 of Set 7 | dicabisagan
    Processing Record 30 of Set 7 | kavieng
    Processing Record 31 of Set 7 | wladyslawowo
    Processing Record 32 of Set 7 | kemin
    Processing Record 33 of Set 7 | coolum beach
    Processing Record 34 of Set 7 | rosetta
    Processing Record 35 of Set 7 | bermeo
    Processing Record 36 of Set 7 | turtas
    Processing Record 37 of Set 7 | mount gambier
    Processing Record 38 of Set 7 | key west
    Processing Record 39 of Set 7 | aklavik
    Processing Record 40 of Set 7 | tikapur
    Processing Record 41 of Set 7 | oranjestad
    Processing Record 42 of Set 7 | calvinia
    Processing Record 43 of Set 7 | kahului
    Processing Record 44 of Set 7 | gaziantep
    Processing Record 45 of Set 7 | port augusta
    Processing Record 46 of Set 7 | turukhansk
    Processing Record 47 of Set 7 | roma
    Processing Record 48 of Set 7 | buraydah
    Processing Record 49 of Set 7 | andenes
    City not found. Skipping...
    Processing Record 0 of Set 8 | coihaique
    Processing Record 1 of Set 8 | surt
    Processing Record 2 of Set 8 | rawannawi
    City not found. Skipping...
    Processing Record 3 of Set 8 | nanjangud
    Processing Record 4 of Set 8 | saravan
    Processing Record 5 of Set 8 | penzance
    Processing Record 6 of Set 8 | mehamn
    Processing Record 7 of Set 8 | baherden
    Processing Record 8 of Set 8 | minbu
    Processing Record 9 of Set 8 | hamina
    Processing Record 10 of Set 8 | mackay
    Processing Record 11 of Set 8 | omaruru
    Processing Record 12 of Set 8 | roald
    Processing Record 13 of Set 8 | tashtyp
    Processing Record 14 of Set 8 | kyra
    City not found. Skipping...
    Processing Record 15 of Set 8 | walvis bay
    Processing Record 16 of Set 8 | kloulklubed
    Processing Record 17 of Set 8 | le port
    Processing Record 18 of Set 8 | hokitika
    Processing Record 19 of Set 8 | guapi
    Processing Record 20 of Set 8 | manyana
    Processing Record 21 of Set 8 | airai
    Processing Record 22 of Set 8 | wajid
    Processing Record 23 of Set 8 | mumford
    Processing Record 24 of Set 8 | labuhan
    Processing Record 25 of Set 8 | sabang
    Processing Record 26 of Set 8 | batagay-alyta
    Processing Record 27 of Set 8 | ambodifototra
    City not found. Skipping...
    Processing Record 28 of Set 8 | gouyave
    Processing Record 29 of Set 8 | avera
    Processing Record 30 of Set 8 | zonguldak
    Processing Record 31 of Set 8 | tokur
    Processing Record 32 of Set 8 | pyay
    Processing Record 33 of Set 8 | ulladulla
    Processing Record 34 of Set 8 | grand-santi
    Processing Record 35 of Set 8 | urusha
    Processing Record 36 of Set 8 | lata
    Processing Record 37 of Set 8 | anar darreh
    City not found. Skipping...
    Processing Record 38 of Set 8 | tazovskiy
    Processing Record 39 of Set 8 | kefamenanu
    Processing Record 40 of Set 8 | agva
    City not found. Skipping...
    Processing Record 41 of Set 8 | kysyl-syr
    Processing Record 42 of Set 8 | wajima
    Processing Record 43 of Set 8 | kargopol
    Processing Record 44 of Set 8 | tubruq
    City not found. Skipping...
    Processing Record 45 of Set 8 | ovalle
    Processing Record 46 of Set 8 | wadi musa
    Processing Record 47 of Set 8 | iguape
    Processing Record 48 of Set 8 | san juan
    Processing Record 49 of Set 8 | vinh
    Processing Record 0 of Set 9 | kuminskiy
    Processing Record 1 of Set 9 | samalaeulu
    City not found. Skipping...
    Processing Record 2 of Set 9 | honningsvag
    Processing Record 3 of Set 9 | harper
    Processing Record 4 of Set 9 | batasan
    Processing Record 5 of Set 9 | yumen
    Processing Record 6 of Set 9 | tutoia
    Processing Record 7 of Set 9 | tazmalt
    Processing Record 8 of Set 9 | lavrentiya
    Processing Record 9 of Set 9 | sarmanovo
    Processing Record 10 of Set 9 | edgewater
    Processing Record 11 of Set 9 | gushikawa
    Processing Record 12 of Set 9 | kalmunai
    Processing Record 13 of Set 9 | houma
    Processing Record 14 of Set 9 | vila
    Processing Record 15 of Set 9 | umba
    Processing Record 16 of Set 9 | pevek
    Processing Record 17 of Set 9 | adrar
    Processing Record 18 of Set 9 | termiz
    Processing Record 19 of Set 9 | luanda
    Processing Record 20 of Set 9 | maniitsoq
    Processing Record 21 of Set 9 | yuncheng
    Processing Record 22 of Set 9 | port shepstone
    Processing Record 23 of Set 9 | truth or consequences
    Processing Record 24 of Set 9 | acapulco
    Processing Record 25 of Set 9 | necochea
    Processing Record 26 of Set 9 | broome
    Processing Record 27 of Set 9 | laredo
    Processing Record 28 of Set 9 | paradwip
    City not found. Skipping...
    Processing Record 29 of Set 9 | fort smith
    Processing Record 30 of Set 9 | comodoro rivadavia
    Processing Record 31 of Set 9 | ferme-neuve
    Processing Record 32 of Set 9 | dengzhou
    Processing Record 33 of Set 9 | kamennogorsk
    Processing Record 34 of Set 9 | padang
    Processing Record 35 of Set 9 | sorvag
    City not found. Skipping...
    Processing Record 36 of Set 9 | sorland
    Processing Record 37 of Set 9 | huangchuan
    Processing Record 38 of Set 9 | alofi
    Processing Record 39 of Set 9 | sur
    Processing Record 40 of Set 9 | tocopilla
    Processing Record 41 of Set 9 | rudbar
    City not found. Skipping...
    Processing Record 42 of Set 9 | galesong
    Processing Record 43 of Set 9 | paamiut
    Processing Record 44 of Set 9 | narsaq
    Processing Record 45 of Set 9 | sungaipenuh
    Processing Record 46 of Set 9 | papara
    Processing Record 47 of Set 9 | kuche
    City not found. Skipping...
    Processing Record 48 of Set 9 | isangel
    Processing Record 49 of Set 9 | kamyshlov
    Processing Record 0 of Set 10 | ponta do sol
    Processing Record 1 of Set 10 | lengshuitan
    Processing Record 2 of Set 10 | thinadhoo
    Processing Record 3 of Set 10 | saint anthony
    Processing Record 4 of Set 10 | yulara
    Processing Record 5 of Set 10 | kokopo
    Processing Record 6 of Set 10 | iqaluit
    Processing Record 7 of Set 10 | longyearbyen
    Processing Record 8 of Set 10 | los llanos de aridane
    Processing Record 9 of Set 10 | hayden
    Processing Record 10 of Set 10 | erzurum
    Processing Record 11 of Set 10 | bonthe
    Processing Record 12 of Set 10 | ketchikan
    Processing Record 13 of Set 10 | barkhan
    Processing Record 14 of Set 10 | euclides da cunha
    Processing Record 15 of Set 10 | sanghar
    Processing Record 16 of Set 10 | te anau
    Processing Record 17 of Set 10 | valleyview
    Processing Record 18 of Set 10 | cidreira
    Processing Record 19 of Set 10 | banda aceh
    Processing Record 20 of Set 10 | tagusao
    Processing Record 21 of Set 10 | terrace
    Processing Record 22 of Set 10 | el chichicaste
    Processing Record 23 of Set 10 | gberia fotombu
    Processing Record 24 of Set 10 | ranir bazar
    Processing Record 25 of Set 10 | grindsted
    Processing Record 26 of Set 10 | katsuura
    Processing Record 27 of Set 10 | qaqortoq
    Processing Record 28 of Set 10 | pontes e lacerda
    Processing Record 29 of Set 10 | bata
    Processing Record 30 of Set 10 | kingston
    Processing Record 31 of Set 10 | aleksandrovka
    Processing Record 32 of Set 10 | vostok
    Processing Record 33 of Set 10 | puerto madryn
    Processing Record 34 of Set 10 | yuzhnyy
    Processing Record 35 of Set 10 | bulungu
    Processing Record 36 of Set 10 | kollam
    Processing Record 37 of Set 10 | progreso
    Processing Record 38 of Set 10 | visby
    Processing Record 39 of Set 10 | ilebo
    Processing Record 40 of Set 10 | ajdabiya
    Processing Record 41 of Set 10 | maine-soroa
    Processing Record 42 of Set 10 | sayreville
    Processing Record 43 of Set 10 | palana
    Processing Record 44 of Set 10 | acajutiba
    Processing Record 45 of Set 10 | lakatoro
    Processing Record 46 of Set 10 | solsvik
    City not found. Skipping...
    Processing Record 47 of Set 10 | lakes entrance
    Processing Record 48 of Set 10 | ludza
    Processing Record 49 of Set 10 | zvishavane
    Processing Record 0 of Set 11 | mao
    Processing Record 1 of Set 11 | seaham
    Processing Record 2 of Set 11 | kaa-khem
    Processing Record 3 of Set 11 | grindavik
    Processing Record 4 of Set 11 | pangody
    Processing Record 5 of Set 11 | zhuzhou
    Processing Record 6 of Set 11 | clyde river
    Processing Record 7 of Set 11 | estelle
    Processing Record 8 of Set 11 | ulaanbaatar
    Processing Record 9 of Set 11 | victoria point
    Processing Record 10 of Set 11 | flores
    Processing Record 11 of Set 11 | cairns
    Processing Record 12 of Set 11 | beyneu
    Processing Record 13 of Set 11 | hoquiam
    Processing Record 14 of Set 11 | kurilsk
    Processing Record 15 of Set 11 | albuquerque
    Processing Record 16 of Set 11 | tomatlan
    Processing Record 17 of Set 11 | blackfoot
    Processing Record 18 of Set 11 | anito
    Processing Record 19 of Set 11 | meybod
    Processing Record 20 of Set 11 | muscat
    Processing Record 21 of Set 11 | san patricio
    Processing Record 22 of Set 11 | pali
    Processing Record 23 of Set 11 | atambua
    Processing Record 24 of Set 11 | mocambique
    City not found. Skipping...
    Processing Record 25 of Set 11 | kuytun
    Processing Record 26 of Set 11 | lamu
    Processing Record 27 of Set 11 | bandarbeyla
    Processing Record 28 of Set 11 | eenhana
    Processing Record 29 of Set 11 | newburn
    Processing Record 30 of Set 11 | changli
    Processing Record 31 of Set 11 | toowoomba
    Processing Record 32 of Set 11 | banjar
    Processing Record 33 of Set 11 | hohhot
    Processing Record 34 of Set 11 | debre birhan
    Processing Record 35 of Set 11 | nelson bay
    Processing Record 36 of Set 11 | sibu
    Processing Record 37 of Set 11 | black river
    City not found. Skipping...
    Processing Record 38 of Set 11 | thaba-tseka
    Processing Record 39 of Set 11 | hobyo
    Processing Record 40 of Set 11 | bela vista de goias
    Processing Record 41 of Set 11 | ugoofaaru
    Processing Record 42 of Set 11 | dali
    Processing Record 43 of Set 11 | kadaya
    Processing Record 44 of Set 11 | kensington
    Processing Record 45 of Set 11 | zhigansk
    Processing Record 46 of Set 11 | merritt island
    Processing Record 47 of Set 11 | yamada
    Processing Record 48 of Set 11 | kamenskoye
    City not found. Skipping...
    Processing Record 49 of Set 11 | baghdad
    Processing Record 0 of Set 12 | havre-saint-pierre
    Processing Record 1 of Set 12 | alta floresta
    Processing Record 2 of Set 12 | rio grande
    Processing Record 3 of Set 12 | wuwei
    Processing Record 4 of Set 12 | arman
    Processing Record 5 of Set 12 | salamiyah
    Processing Record 6 of Set 12 | vestmannaeyjar
    Processing Record 7 of Set 12 | dondo
    Processing Record 8 of Set 12 | gallup
    Processing Record 9 of Set 12 | micheweni
    Processing Record 10 of Set 12 | yanam
    Processing Record 11 of Set 12 | nipawin
    Processing Record 12 of Set 12 | jalu
    Processing Record 13 of Set 12 | brae
    Processing Record 14 of Set 12 | alappuzha
    City not found. Skipping...
    Processing Record 15 of Set 12 | leonidovo
    Processing Record 16 of Set 12 | krasnyy yar
    Processing Record 17 of Set 12 | nyimba
    Processing Record 18 of Set 12 | simao
    Processing Record 19 of Set 12 | kharsia
    Processing Record 20 of Set 12 | asekeyevo
    Processing Record 21 of Set 12 | haibowan
    City not found. Skipping...
    Processing Record 22 of Set 12 | les herbiers
    Processing Record 23 of Set 12 | bonavista
    Processing Record 24 of Set 12 | belaya gora
    Processing Record 25 of Set 12 | gao
    Processing Record 26 of Set 12 | yerbogachen
    Processing Record 27 of Set 12 | porechye-rybnoye
    Processing Record 28 of Set 12 | san andres
    Processing Record 29 of Set 12 | fairbanks
    Processing Record 30 of Set 12 | george
    Processing Record 31 of Set 12 | bradford
    Processing Record 32 of Set 12 | lago da pedra
    City not found. Skipping...
    Processing Record 33 of Set 12 | jomalig
    City not found. Skipping...
    Processing Record 34 of Set 12 | port lincoln
    Processing Record 35 of Set 12 | carutapera
    Processing Record 36 of Set 12 | awjilah
    Processing Record 37 of Set 12 | naryan-mar
    Processing Record 38 of Set 12 | la ronge
    Processing Record 39 of Set 12 | natal
    Processing Record 40 of Set 12 | nevsehir
    Processing Record 41 of Set 12 | turayf
    Processing Record 42 of Set 12 | temiscaming
    Processing Record 43 of Set 12 | gardan diwal
    City not found. Skipping...
    Processing Record 44 of Set 12 | kupang
    Processing Record 45 of Set 12 | port-cartier
    Processing Record 46 of Set 12 | storm lake
    Processing Record 47 of Set 12 | manokwari
    Processing Record 48 of Set 12 | julich
    Processing Record 49 of Set 12 | makung
    City not found. Skipping...
    Processing Record 0 of Set 13 | viedma
    Processing Record 1 of Set 13 | dolbeau
    City not found. Skipping...
    Processing Record 2 of Set 13 | sarkand
    Processing Record 3 of Set 13 | jhang
    Processing Record 4 of Set 13 | naze
    Processing Record 5 of Set 13 | zory
    Processing Record 6 of Set 13 | labuan
    Processing Record 7 of Set 13 | luwuk
    Processing Record 8 of Set 13 | sao felix do xingu
    Processing Record 9 of Set 13 | fonte boa
    Processing Record 10 of Set 13 | mahibadhoo
    Processing Record 11 of Set 13 | loukhi
    Processing Record 12 of Set 13 | mount isa
    Processing Record 13 of Set 13 | kargasok
    Processing Record 14 of Set 13 | mandera
    Processing Record 15 of Set 13 | praya
    -----------------------------
    Data Retrieval Complete      
    -----------------------------
    

### Convert Raw Data to DataFrame
* Export the city data into a .csv.
* Display the DataFrame


```python

```




    City          547
    Cloudiness    547
    Country       547
    Date          547
    Humidity      547
    Lat           547
    Lng           547
    Max Temp      547
    Wind Speed    547
    dtype: int64




```python

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>City</th>
      <th>Cloudiness</th>
      <th>Country</th>
      <th>Date</th>
      <th>Humidity</th>
      <th>Lat</th>
      <th>Lng</th>
      <th>Max Temp</th>
      <th>Wind Speed</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>lompoc</td>
      <td>1</td>
      <td>US</td>
      <td>1534984500</td>
      <td>44</td>
      <td>34.64</td>
      <td>-120.46</td>
      <td>77.00</td>
      <td>11.41</td>
    </tr>
    <tr>
      <th>1</th>
      <td>klaksvik</td>
      <td>92</td>
      <td>FO</td>
      <td>1534983600</td>
      <td>100</td>
      <td>62.23</td>
      <td>-6.59</td>
      <td>50.00</td>
      <td>13.87</td>
    </tr>
    <tr>
      <th>2</th>
      <td>bisignano</td>
      <td>0</td>
      <td>IT</td>
      <td>1534981800</td>
      <td>88</td>
      <td>39.50</td>
      <td>16.27</td>
      <td>66.20</td>
      <td>5.82</td>
    </tr>
    <tr>
      <th>3</th>
      <td>hilo</td>
      <td>90</td>
      <td>US</td>
      <td>1534984860</td>
      <td>90</td>
      <td>19.71</td>
      <td>-155.08</td>
      <td>77.00</td>
      <td>8.05</td>
    </tr>
    <tr>
      <th>4</th>
      <td>rikitea</td>
      <td>8</td>
      <td>PF</td>
      <td>1534986579</td>
      <td>100</td>
      <td>-23.12</td>
      <td>-134.97</td>
      <td>69.58</td>
      <td>19.71</td>
    </tr>
  </tbody>
</table>
</div>



### Plotting the Data
* Use proper labeling of the plots using plot titles (including date of analysis) and axes labels.
* Save the plotted figures as .pngs.

#### Latitude vs. Temperature Plot


```python

```


![png](Images/output_11_0.png)


#### Latitude vs. Humidity Plot


```python

```


![png](Images/output_13_0.png)


#### Latitude vs. Cloudiness Plot


```python

```


![png](Images/output_15_0.png)


#### Latitude vs. Wind Speed Plot


```python

```


![png](Images/output_17_0.png)

