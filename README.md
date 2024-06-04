
# Projekt jednoduchého sorteru
Projektem je jednoduchý sorter, který má zaznamenat velikost balíčku pomočí 4 ultrazvukových senzorů, esp32 wroom a lehkou konstrukcí z lega.

## Informace o verzích
Původně měl systém fungovat na kameře OV7670 u které bohužel většina knihoven byla buď zastaralá nebo nefunkční.
Tudíž jsem zvolil variantu s ultrazvukovým senzorem a konstrukcí z lega (Pro účel tohoto projektu jsem pracoval s náhodným generátorem velikosti pro zápis do firebase).

## Jak to funguje + odkaz na myšlenkovou mapu
odkaz: https://miro.com/app/board/uXjVKRKkyPE=/?share_link_id=638719125340

### Hlavní verze (Projekt pro pana učitele Jedličku))
4 ultrazvukové senzory zaznamenají vzdálenost a pomocí vzorce vydělí a tím spočítá velikost objektu v esp32
Následně vytvoří náhodně generovaný kod zásilky a zašle velikost osy X, Y a Z do Firebase
![image](https://github.com/Wirtrius/PAD-Projekt/assets/144933686/9ebfbe8a-70ed-4602-94e3-1a2e09075b7a) (ukázka z pohledu ve Firebase)

### Pracovní verze (Projekt pro pana učitele Vašíčka)
esp32 se připojí k hotspotu a v kodu má již prístup k Firebase databázi
esp32 pracuje s "fiktivními" senzory na které dosadí náhodné hodnoty pomocí tohoto kodu:
 // Simulace měření vzdálenosti s náhodnými hodnotami
  float vzdalenost1 = random(10, 100) * 58.31; // Simulace náhodné vzdálenosti v rozmezí 10 až 100 cm pro první senzor
  float vzdalenost2 = random(10, 100) * 58.31; // Simulace náhodné vzdálenosti v rozmezí 10 až 100 cm pro druhý senzor
  return (vzdalenost1 + vzdalenost2) / 2.0; // Vrátíme průměr ze dvou simulovaných hodnot

  Poté tyto hodnoty zapíše a odešle do Firestoru, kde si je připojený webhook vezme a zašle do discord channelu v discord serveru

## Závěr
  Důvod proč jsem si tento projekt vybral byl ten, že ve volném čase pracuji v logistice a zajímalo mě jestli by se dala udělat vlastní zjednodušená verze sorteru "třídiče", což si myslím že se mi nakonec povedlo.
