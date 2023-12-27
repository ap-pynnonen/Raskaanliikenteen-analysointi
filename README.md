# Raskaanliikenteen-analysointi

Raskaan liikenteen analysoinnissa keskitytään:
- Onko raskaan liikenteen nopeudet hitaampia yöllä jokaisessa mittauspisteessä, vai onko aisia totta vain yksittäisissä mittauspisteissä
- Tutkitaan muutamaa Lam pistettä ja tehdään tutkimus niistä
- Ohjelmiston kehittäminen, jolla pystyy vaihtaa mittauspistettä vaivatta 

Kehitetyssä työkalussa käytettävät teknologiat:
- Python
- pandas
- Jupyter notebook

----

## Raskas liikenne Lam-pisteissä

Ensimmäisenä tutkittiin Lam-pisteet, joissa kulkee raskasta liikennettä (HCT). Raskaskaan liikenteen kulkua Lam-pisteillä tutkittiin käyttämällä [Lam visualisointi](https://github.com/ap-pynnonen/Lam-visualization) työkalua, jossa pystyi suodattamaan ajoneuvoluokat erikseen ja tarkistamaan 7 päivän ajalta onko kyseisellä Lam-pisteellä ollut raskasta liikennettä.

Lam-pisteet 115, joissa on kulkenut raskasta liikennettä on listattu alla olevaan taulukkoon.

| LAM-piste | LAM-id |
| ----------- | ----------- |
| Porvoo, rita | 1 |
| Espoo, kivenlahti | 3 |
| Vantaa, klaukkalantie | 5 |
| Vantaa, honkanummi | 7 |
| Vantaa, illola | 9 |
| Espoo, laajalahti | 10 |
| Helsinki, vartiokylä | 11 |
| Järvenpää, isokytö | 99 |
| Espoo, huopalahti | 103 |
| Vihti, palojärvi | 104 |
| Loviisa, liljendal | 111 |
| Espoo, keilaniemi | 118 |
| Karkkila | 122 |
| Raasepori, dragsvik | 124 |
| Helsinki, tuomarinkartano | 131 |
| Mäntsälä, arola | 136 |
| Vantaa, keimola | 137 |
| Helsinki, länsi-pakila | 146 |
| Kirkkonummi, jorvas | 156 |
| Helsinki, bäcknas | 172 |
| Espoo, lommila | 175 |
| Porvoo, lohijärvi | 185 |
| Loviisa, itä | 189 |
| Helsinki, satamatie | 195 |
| Ikaalinen | 204 |
| Pori | 207 |
| Lieto, aura | 208 |
| Marttila | 209 |
| Kaarina, kirismäki | 227 |
| Paimio, paimionjoki | 242 |
| Masku | 250 |
| Virolahti, virojoki | 307 |
| Virolahti, ravijoki | 308 |
| Virolahti, vaalimaa | 309 |
| Virolahti, vaalimaan tunneli itä | 310 |
| Hausjärvi | 408 |
| HHämeenlinna, hauho | 426 |
| Hämeenlinna, mo3 | 437 |
| Tampere, ruotula | 458 |
| Lahti, patomäki | 468 |
| Lahti, liipola | 469 |
| Lahti, lotila | 470 |
| Tampere, multisilta | 471 |
| Hamina, lelu | 506 |
| Kouvola, tuohikortti | 527 |
| Kotka, juurikorpi | 530 |
| Lappeenranta, joutseno | 563 |
| Hamina, kyminlinna | 574 |
| Kouvola, puhjo | 595 |
| Heinola, murhamäki | 628 |
| Joroinen, kuvansi | 631 |
| Mikkeli, pitkäjärvi | 633 |
| Joensuu, reijola | 731 |
| Tuusniemi, tuusjärvi | 804 |
| Kuopio, rahusenlampi | 828 |
| Laukaa, lievestuore | 903 |
| Joutsa, harvastensuo | 928 |
| Jämsä | 930 |
| Viitasaari, tuliniemi | 937 |
| Jyväskylä, lutakko | 938 |
| Mäntsälä | 998 |
| Kokkola | 1023 |
| Vaasa | 1030 |
| Ilmajoki, rengonkylä | 1068 |
| Seinäjoki,, kertunlaakso | 1069 |
| Oulu, ouluntulli | 1206 |
| Haukipudas | 1207 |
| Pudasjärvi, pintamo | 1224 |
| Ii, myllykangas | 1229 |
| Kuusamo, toranki | 1234 |
| Oulu, intiö | 1237 |
| Oulu, isko | 1238 |
| Liminka, luhasto | 1243 |
| Oulu, laanila | 1244 |
| Oulu, kuivasjärvi | 1246 |
| Oulu, kontinkangas | 1250 |
| Raahe, hurnasperä | 1255 |
| Oulu, kaukovainio | 1256 |
| Oulu, iinatti | 1257 |
| Sotkamo, korholanmäki | 1323 |
| Vaala, törmäkylä | 1324 |
| Tornio, Luukkaankangas | 1439 |
| Rovaniemi, revontuli | 1450 |
| Rovaniemi, ala-korkalo | 1451 |
| Tornioi | 1458 |
| Rovaniemi, pöykkölä | 1467 |
| Muonio, pahtonen | 1468 |
| Salo, lakiamäki | 1601 |
| Salo, kruusila | 1602 |
| Salo, syvälampi | 1603 |
| Salo, lahnajärvi | 1604 |
| Salo, haulampi | 1605 |
| Lohja, pitkämäki | 1606 |
| Lohja, karnainen | 1607 |
| Espoo, hirvisuo | 20002 |
| Espoo, lommila | 20003 |
| Espoo, kasavuori | 20004 |
| Espoo, sepänkylä | 20005 |
| Espoo, kuurinniitty | 20006 |
| Espoo, tuomarila | 20007 |
| Espoo, nihtisilta | 20008 |
| Espoo, stensgård | 20009 |
| Espoo, turveradantie | 20010 |
| Espoo, sinimäki | 20011 |
| Espoo, sinimäki2 | 20013 |
| Nurmijärvi, peräjänkulma | 20022 |
| Nurmijärvi, peräjänkulma2 | 20023 |
| Nurmijärvi, mäyränkallio | 20024 |
| Nurmijärvi, yli-hemmi | 20025 |
| Nurmijärvi | 20026 |
| Nurmijärvi, peräjä | 20027 |
| Juva, 1 | 20601 |
| Juva, 2 | 20602 |
| Juva, 3 | 20603 |
| Oulu, intiö | 21201 |

## Tarkemmin tutkittavat Lam pisteet

| LAM-piste | LAM-id |
| ----------- | ----------- |
| Espoo, laajalahti | 10 |
| Espoo, huopalahti | 103 |
| Espoo, keilaniemi | 118 |
| Helsinki, bäcknas | 172 |
| Helsinki, satamatie | 195 |
| Ikaalinen | 204 |
| Pori | 207 |
| Lieto, aura | 208 |
| Kaarina, kirismäki | 227 |
| Hämeenlinna, mo3 | 437 |
| Hamina, kyminlinna | 574 |
| Oulu, intiö | 1237 |
| Salo, kruusila | 1602 |

## Lam pisteiden kuvaajat (hct)

Valituista Lam pisteistä haettiin ja analysoitiin ensimmäisenä pelkästään ajoneuvoluokka High capacity truck.

Lam id 10 kuvaaja (hct) 1.6.2022-1.6.2023 ajalta  
![lamid 10 image (hct)](/images/lamid10_365days_hct.PNG)

Lam id 103 kuvaaja (hct) 1.6.2022-1.6.2023 ajalta  
![lamid 103 image (hct)](/images/lamid103_365days_hct.PNG)

Lam id 118 kuvaaja (hct) 1.6.2022-1.6.2023 ajalta  
![lamid 118 image (hct)](/images/lamid118_365days_hct.PNG)

Lam id 172 kuvaaja (hct) 1.6.2022-1.6.2023 ajalta  
![lamid 172 image (hct)](/images/lamid172_255days_hct.PNG)

Lam id 195 kuvaaja (hct) 1.6.2022-1.6.2023 ajalta  
![lamid 195 image (hct)](/images/lamid195_362days_hct.PNG)

Lam id 204 kuvaaja (hct) 1.6.2022-1.6.2023 ajalta  
![lamid 204 image (hct)](/images/lamid204_357days_hct.PNG)

Lam id 207 kuvaaja (hct) 1.6.2022-1.6.2023 ajalta  
![lamid 207 image (hct)](/images/lamid207_365days_hct.PNG)

Lam id 208 kuvaaja (hct) 1.6.2022-1.6.2023 ajalta  
![lamid 208 image (hct)](/images/lamid208_365days_hct.PNG)

Lam id 227 kuvaaja (hct) 1.6.2022-1.6.2023 ajalta  
![lamid 227 image (hct)](/images/lamid227_365days_hct.PNG)

Lam id 437 kuvaaja (hct) 1.6.2022-1.6.2023 ajalta  
![lamid 437 image (hct)](/images/lamid437_365days_hct.PNG)

Lam id 574 kuvaaja (hct) 1.6.2022-1.6.2023 ajalta  
![lamid 574 image (hct)](/images/lamid574_365days_hct.PNG)

Lam id 1237 kuvaaja (hct) 1.6.2022-1.6.2023 ajalta  
![lamid 1237 image (hct)](/images/lamid1237_365days_hct.PNG)

Lam id 1602 kuvaaja (hct) 1.6.2022-1.6.2023 ajalta  
![lamid 1602 image (hct)](/images/lamid1602_365days_hct.PNG)

## Lam pisteen kuvaajat (hct + kuorma-autot)

Samalta aikaväliltä haettiin ja analysoitiin myös ajoneuvoluokat kuorma-auto ilman perävaunua,  kuorma-auto ja puoliperävaunu, kuorma-auto ja täysperävaunu ja High Capacity Truck.

Lam id 10 kuvaaja 1.6.2022-1.6.2023 ajalta  
![lamid 10 image](/images/lamid10_365days.PNG)

Lam id 103 kuvaaja 1.6.2022-1.6.2023 ajalta  
![lamid 103 image](/images/lamid103_365days.PNG)

Lam id 118 kuvaaja 1.6.2022-1.6.2023 ajalta  
![lamid 118 image](/images/lamid118_365days.PNG)

Lam id 172 kuvaaja 1.6.2022-1.6.2023 ajalta  
![lamid 172 image](/images/lamid172_255days.PNG)

Lam id 195 kuvaaja 1.6.2022-1.6.2023 ajalta  
![lamid 195 image](/images/lamid195_362days.PNG)

Lam id 204 kuvaaja 1.6.2022-1.6.2023 ajalta  
![lamid 204 image](/images/lamid204_357days.PNG)

Lam id 207 kuvaaja 1.6.2022-1.6.2023 ajalta  
![lamid 207 image](/images/lamid207_365days.PNG)

Lam id 208 kuvaaja 1.6.2022-1.6.2023 ajalta  
![lamid 208 image](/images/lamid208_365days.PNG)

Lam id 227 kuvaaja 1.6.2022-1.6.2023 ajalta  
![lamid 227 image](/images/lamid227_365days.PNG)

Lam id 437 kuvaaja 1.6.2022-1.6.2023 ajalta  
![lamid 437 image](/images/lamid437_365days.PNG)

Lam id 574 kuvaaja 1.6.2022-1.6.2023 ajalta  
![lamid 574 image](/images/lamid574_365days.PNG)

Lam id 1237 kuvaaja 1.6.2022-1.6.2023 ajalta  
![lamid 1237 image](/images/lamid1237_365days.PNG)

Lam id 1602 kuvaaja 1.6.2022-1.6.2023 ajalta  
![lamid 1602 image](/images/lamid1602_365days.PNG)

## Analyysin tulokset

Kuvaajista (hct) pystyy näkemään, että osassa Lam pisteitä raskas liikenne (hct) kulkee hitaammin yön aikana. Valittujen 13 Lam pisteen kohdalla 6 kuvaajassa näkyy nopeuksien olevan hitaampia yön aikana.

Kuvaajista (hct + kuorma-autot) näkee, että osassa Lam pisteitä kuljetaan hitaammin yön aikana. Valittujen 13 Lam pisteen kohdalla 9 kuvaajassa näkyy nopeuksien olevan hitaampia yön aikana.

Raskas liikenne ei kulje hitaammin jokaisessa Lam pisteessä.
Valituista mittauspisteissä vain osassa yöllä kuljettu nopeus on hitaampi. 

Valittujen Lam pisteiden määrä on kuitenkin 13 / 115 Lam pisteestä, jossa kulkee raskasta liikennettä (hct). Todellisen määrän ja suhteen näkee silloin, kun tarkistaa jokaisen 115 Lam pisteen kuvaajan samalta aikaväliltä.

Repositorion /images kansiosta pystyy katsomaan jokaisen Lam pisteen kuvaajan (hct) 30 päivän ajalta. Nämä kuvaajat viittaavat, että suurimmalla osalla Lam pisteistä ajetaan samaa nopeutta yöllä ja päivällä tai ajetaan nopeammin yöllä kuin päivällä.
