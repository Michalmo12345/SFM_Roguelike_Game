# The Binding of Isaac: klon gry
## PROI 23L grupa 103 
Autorzy projektu:

```
Antoni Grajek
Michał Mokrzycki
Igor Szabłowski
```

## Wstępne założenia projektowe

Projekt zakłada stworzenie gry inspirowanej tytułem "The Binding of Isaac". Będzie to gra 2D typu Roguelike, z widokiem z góry. Celem gry jest przejście wszystkich etapów rozgrywki składających się z losowo generowanych pomieszczeń w których będą znajdowali się przeciwnicy oraz przeszkody. Urozmaiceniem gry będą przedmioty które będzie można znaleźć w pokojach, bądź kupić od handlarza. Dzięki przedmiotom będziemy mogli zmieniać atrybuty naszej postaci takie jak np: poziom zdrowia lub prędkość ruchu oraz atrybuty broni między innymi zasięg, prędkość czy siła ataku.

## Wykorzystywane narzędzia i biblioteki

Projekt jest realizowany w języku C++, z naciskiem na programowanie obiektowe. Wartstwę trwałości projektu będą stanowić najprawdopodobniej zapisy do plików z rozszerzeniem csv oraz json. Kontakt z użytkownikiem i interfejs użytkownika będą oparte na bibliotece SFML, a reszta programu będzie zrealizowana z wykorzystywaniem elementów biblioteki standardowej.

### Klasa Game
Klasa odpowiedzialna za działanie gry, interakcje z użytkownikiem, interfejs startowy.

### Klasa GameCharacter

Klasa **GameCharacter** będzie funkcjonowała równocześnie z klasą **Sprite** z biblioteki SFML.
Klasa **GameCharacter** będzie klasą odpowiedzialną za każdą postać znajdująca się w grze.
Zawiera atrybuty i metody wspólne dla klasy **Player** oraz klasy **Enemy**.
###### Atrybuty

- speed
- health_power
- name
### Klasa Player

Dziedziczy po klasie **GameCharacter**. Jest instancją gracza na polu rozgrywki.
###### Atrybuty

Zawiera atrybuty klasy **GameCharacter** oraz własne takie jak:

- items
- gold
- weapons

### Klasa Enemy
Dziedziczy po klasie **GameCharacter**. Jest instancją wroga na polu rozgrywki.
###### Atrybuty

Zawiera atrybuty klasy **GameCharacter**.

### Klasa Bullet
Klasa odpowiedzialna za pociski wystrzelane przez postać.
###### Atrybuty
- attack_speed
- attack_range
- damage
### Klasa Items
Zawiera zbiór statystyk i funkcjonalności przedmiotu.
Zawiera atrybuty i metody wspólne dla klas **PurchasableItems** i **ItemDrops**.
###### Atrybuty
- additional_health
- additional_damage
- additional_range
- additional_attack_speed
- additional_player_speed

#### Klasa PurchasableItems
Dziedziczy po klasie Items.
###### Atrybuty
- item_cost


### Klasa Shop
Obiekt pozwalający graczowi na zakupienie przedmiotu.
###### Atrybuty
- kolekcja przedmiotów możliwych do kupienia(kolekcja obiektów PurchasableItems)

### Klasa Map
Zbiór i ułożenie pokojów do przejścia(obiektów klasy Room)
###### Atrybuty
- kolekcja pokojów
- TBA

### Klasa Room
Klasa opisująca konfiguracje przeszkód oraz przeciwników znajdujących się w konkretnym pokoju.

###### Atrybuty
- enemies_amount
- is_boss_room
- enemies_collection
