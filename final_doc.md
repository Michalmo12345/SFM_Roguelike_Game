# The Binding of Isaac: klon gry
## PROI 23L grupa 103 
Autorzy projektu:

```
Antoni Grajek
Michał Mokrzycki
Igor Szabłowski
```

## Założenia projektowe

Projekt zakłada stworzenie gry inspirowanej tytułem "The Binding of Isaac". Jest to gra 2D typu Roguelike, z widokiem z góry. Celem gry jest przejście wszystkich etapów rozgrywki składających się z losowo generowanych pomieszczeń w których będą znajdowali się przeciwnicy. Celem gry jest zebranie jak największej ilośći oraz pokonanie wszystkich bossów. Jeden poziom mapy składa się z 9 pokojów, a żeby ukończyć grę należy przejść dwa piętra.

## Architrktura rozwiązania

Projekt jest realizowany w języku C++, z naciskiem na programowanie obiektowe. Wartstwę trwałości projektu stanowią zapis i odczyt z plików z rozszerzeniem csv oraz txt. Kontakt z użytkownikiem i interfejs użytkownika są oparte na bibliotece SFML, a reszta programu będzie zrealizowana z wykorzystywaniem elementów biblioteki standardowej.

## Moduły

Gra dzieli się na cztery główne moduły: Game, Entity, Map, Menu

### Game

Klasa Game zajmuje się główną pętlą gry (przechodzeniem pomiędzy stanami gry), tworzy okno oraz jest główną klasą trzymającą całą resztę gry.

### Entity

Klasa Entity jest bazową klasą dla większości obiektów znajdujących się na mapie, posiadających swoją pozycje oraz możliwość ruchu. Dziedziczącymi po niej Klasami są między innymi takie klasy jak: Player, Enemy, Bullet. Player jako swoje atrybuty posiada obiekty takich klas jak BulletList (trzymająca pociski będące w grze), oraz Healthbar, klasa Healthbar posiada kolekcję obiektów klasy Heart i pozwala na zarządzanie zdrowiem gracza. Klasa Enemy to podstawowy przeciwnik, który powstał jako pierwszy, ale są także inni przeciwnicy dziedziczący po Enemy, modyfikujący na przykład sposób ruchu oraz strzelania dzięki polimorfizmowi. Klasa Bullet jest odpowiadzialna za pociski wystrzeliwane przez gracza, a EnemyBullet dziedzicząca po Bullet, za pociski wystrzeliwane przez przeciwników. Boss jest wyjątkowym typem Enemy, posiada on własny Healtbar (klasa Bossbar), która trzyma kolekcję obiektów klasy Bar, dziedziczącej po klasie Heart.

### Map

Moduł ten zawiera logikę generacji i rozmieszczenia na dwuwymiarowej mapie pseudolosowych grywalnych pomieszczeń, klasy map, room oraz gamefield stanowią główny rdzeń tego modułu, są wzorowane na wzorcu kompozytu. To tutaj odbywa sie rozgrywka.

### Menu
Interfejs użytkownika jest relizowany przy pomocy kilku klas takich jak menu, endmenu oraz options menu. Przy połączeniu z klasą game, pozwalają:
* W klasie menu:
    * Rozpoczęcie nowej gry
    * Wczytanie zapisu gry z pliku `.csv` i `.txt`
    * Włączenie menu opcji
    * Wyjście z gry
* W klasie options menu
    * Wybór poziomu trudności
    * Wybór czy ma być dokonywany autozapis
    * Opcja włączenia i wyłączenia dźwięku
    * Powrót do menu głównego
* W klasie end menu
    * Wyświetlany jest 'total score' zdobyty przez użytkownika oraz posep gry ( wygrana lub przegrana)
    * Opcja rozpoczęcia gry od nowa lub zakończenie programu
Użytkownik ma możliwość poruszania się po menu za pomocą strzałek oraz zatwierdzania opcji przy pomocy klawisza *Enter*.
