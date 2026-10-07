# Indeks

* [Wymagane elementy](#wymagane-elementy)
* [Identyfikowanie uszkodzonych danych](#identyfikowanie-uszkodzonych-danych)
* [Jak usunąć uszkodzone dane](#jak-usunąć-uszkodzone-dane)
* ["Typowe rozwiązanie"](#typowe-rozwiązanie)
* [Zapobieganie uszkodzeniu danych](#zapobieganie-uszkodzeniu-danych)
* [Więcej zasobów](#więcej-zasobów)

---

> **Przed wykonaniem któregokolwiek z tych kroków wykonaj pełną kopię zapasową swoich zapisów gry!**

# Wymagane elementy

## Folder modów Steam Workshop (Workshop Mods)

* Dostęp do niego można uzyskać, klikając ikonę folderu przy modzie Steam Workshop w menu modów Paralives.
* Można również przejść do:

**Windows:**

```text
C:\Program Files (x86)\Steam\steamapps\workshop\content\1118520\
```

**Mac:**

```text
~/Library/Application Support/Steam/steamapps/workshop/content/1118520
```

## Folder Paralives (Local Mods)

* Dostęp do niego można uzyskać, klikając ikonę folderu przy lokalnym modzie w menu modów Paralives.
* Można również przejść do:

**Windows:**

```text
C:\Users\USER\AppData\LocalLow\Paralives\Paralives
```

**Mac:**

```text
~/Library/Application Support/com.Paralives.Paralives/
```

## Paralives\Player.Log

* Można go odczytać za pomocą dowolnego programu do odczytywania plików tekstowych, takiego jak Notatnik lub Notepad++.
* Znajduje się w folderze Paralives\Paralives.
* Zawiera logi bieżącej lub ostatnio uruchomionej sesji Paralives.

## Folder Paralives\MySavedGames.mod

* Folder zawierający wszystkie bieżące zapisy gry oraz automatyczne zapisy.
* Znajduje się w folderze Paralives\Paralives.
* Jest to najważniejszy folder ze wszystkich.
* Regularnie wykonuj pełną kopię tego folderu i przechowuj ją w bezpiecznym miejscu poza plikami gry!

## Folder Paralives\MyPremadeHouseholds.mod

* Gospodarstwa domowe zapisane w bibliotece.

## Folder Paralives\MyPremadeLot.mod

* Działki zapisane w bibliotece.

## Folder Paralives\MyPremadeOutfits.mod

* Stroje zapisane w bibliotece.

## Folder Paralives\Local.mod i 0.mod

* Przechowuje ustawienia gry, takie jak niestandardowe próbki kolorów.

# Identyfikowanie uszkodzonych danych

Uszkodzone dane to pliki, które zostały zmienione i nie mają już formy lub kolejności, której gra oczekuje.

## Nieaktualne pliki

* Gra została zaktualizowana, a te pliki nie są już zgodne z aktualną składnią.
* Chociaż czasami może się to zdarzyć w przypadku modów, niemal wszystkie wtyczki wstrzykujące kod BepInEx stają się nieaktualne po aktualizacji gry.
* Jeśli wtyczka BepInEx jest zainstalowana, ale mody nadal nie działają, wtyczka może powodować więcej szkody niż pożytku.

## Nieprawidłowo zmodyfikowane pliki

* Zostały zmodyfikowane przez gracza, twórcę moda lub nawet silnik gry i w rezultacie są nieprawidłowe.
* Dotyczy to modów lub wtyczek, które były używane, a następnie zostały usunięte.

Na przykład mod został użyty do dodania niestandardowego stroju, a następnie usunięty, ale strój nadal jest identyfikowany w plikach gry.

Usunięcie niektórych modów bez uszkodzenia pliku zapisu może być niemożliwe.

## Nieprawidłowo przeniesione pliki

* Pliki są często przenoszone przez gracza, silnik gry lub Steam, a niektóre ich części pozostają lub zostają usunięte.

## W jaki sposób gra poinformuje mnie, które pliki są uszkodzone?

Silnik gry będzie próbował poinformować użytkownika o błędzie za pomocą bezpośrednich i pośrednich komunikatów.

### Bezpośrednie:

* Wyskakujące okna na ekranie
* Powiadomienia w konsoli
* Zdarzenia w player.log

### Pośrednie:

* Migotanie
* Błyskanie
* Zacinanie
* Opóźnienia
* Awaria gry
* Anulowanie operacji

## Odczytywanie konsoli błędów i Player.Log

Informacje w konsoli błędów i player.log tylko częściowo się pokrywają, dlatego podczas identyfikowania błędu należy sprawdzić oba źródła.

Ważne jest zidentyfikowanie pierwszego błędu i zignorowanie dodatkowych błędów spowodowanych przez pierwszy błąd. Podczas czytania logu błędów należy próbować naprawiać błędy od góry do dołu, w kolejności ich występowania.

Jeśli kilka błędów zostanie wprowadzonych jednocześnie, diagnozowanie problemu może być bardzo trudne. Ważne jest, aby pomiędzy testami wprowadzać tylko niewielką liczbę zmian.

Jeśli gra działa płynnie, zanotuj błędy znajdujące się w logu, aby można było je później wykluczyć, gdy coś przestanie działać.

### KONSOLA BŁĘDÓW

* Konsola błędów jest dostępna w grze jako karta w menu kodów.
* Nie można z niej korzystać, jeśli gra się nie uruchamia.

1. Naciśnij Ctrl+Shift+C, aby otworzyć menu kodów.
2. Naciśnij symbol daszka, aby przełączyć się na kartę konsoli.
3. Konsola jest podzielona na trzy kategorie ważności.
4. Na potrzeby tego poradnika ważne są tylko czerwone błędy.

### PLAYER.LOG I PLAYER-PREV.LOG

* Ten plik rejestruje działania wykonywane przez silnik gry Unity uruchamiający Paralives.
* Player.log jest nadpisywany przy każdym uruchomieniu gry i przenoszony do Player-prev.log.
* Znajduje się w lokalnym folderze modów Paralives\Paralives.
* Więcej informacji może zostać zapisanych w logu po włączeniu odpowiednich opcji w panelu sterowania. Zbyt wiele opcji może szybko spowodować znaczny wzrost rozmiaru logu.
* Jeśli coś w logu jest ważne, wykonaj kopię!

### Dobre błędy (a przynajmniej nieszkodliwe):

```text
+ Meta cache is expired
+ Loaded asset database (No metacache) of mod Local.mod in 0.06581748 seconds
+ The referenced script on this Behaviour (Game Object 'SlackService') is missing!
+ Serialization depth limit 10 exceeded
+ Loaded asset database of mod MyPremadeLot.mod in 0.04702377 seconds
+ Unloading 10 unused Assets to reduce memory usage
```

### Złe błędy:

```text
- NullReferenceException: Object reference not set to an instance of an object
- Material builder got given parameters that don't match any shaders
- Could not resolve 'ProceduralRig/ReachWithLeftArm/ArmLChainIK/TargetArmLChainIK'
- FileNotFoundException
- Failed to find setting class
- Could not register Paralives Town.saved
```

> Uwaga: W wersji 1.7 pojawiły się trzy nowe czerwone błędy w konsoli i player.log, które nie wydają się negatywnie wpływać na działanie gry.
>
> * `+ System Exception: Invalid Path...`
> * `+ Runtime data is null...`
> * `+ OperationException: Addressables...`

> Uwaga: W wersji 1.8A importer .fbx nie działał prawidłowo i zawieszał się na ekranie importowania zasobów.

# Rodzaje błędów

Rodzaje problemów występujących na poziomie technicznym.

## Odwołanie do wartości null

* Czasami nazywane odwołaniem wskaźnika null.
* Każdy błąd dotyczący ustawienia, elementu, siatki lub wartości, której nie można znaleźć.
* Gra odwołuje się do obiektu, którego nie może znaleźć, lub nie rozumie tego, co znalazła.

> Uwaga: Gra potrafi obsługiwać niektóre odwołania null, a kilka z nich jest częścią wersji wczesnego dostępu gry.

## Poza zakresem

* Gra otrzymała wartość spoza oczekiwanego zakresu.
* Jeśli gra oczekuje wartości od 0 do 10, ale otrzyma 10842, może to spowodować błąd.

## Tłumaczenie

* Gra próbowała naprawić plik uznany za uszkodzony, ale wynik był nieprawidłowy.

Na przykład problem z plikami .tmp, .mod.meta i .tmp.

## Składnia

* Gra została zaktualizowana, a mod nie jest już zgodny ze standardami określonymi przez grę. Najczęściej dotyczy to wtyczek wstrzykujących kod BepInEx.
* W niektórych modach utworzonych w momencie premiery gry brakuje dwukropków w plikach tekstowych.

# Kategorie objawów

Gdy przyczyna błędu jest nieznana, celem jest powiązanie objawów z konkretną przyczyną. Po naprawieniu każdego błędu gra powinna działać. Poniżej znajdują się arbitralne kategorie pomagające grupować podobne błędy.

Ważne jest zidentyfikowanie pierwszego błędu i zignorowanie dodatkowych błędów spowodowanych przez pierwszy błąd.

## Kategoria A — Uruchamianie gry

### Objawy

* Gra nie może przejść do głównego menu Paralives
* Ekran jest czarny
* Gra zawiesza się podczas uruchamiania z poziomu Steam
* Podczas uruchamiania gry przez Steam pojawia się błąd
* Gra zatrzymuje się na obrazie chmur.

### Możliwe rozwiązania

* Sprawdź, czy sprzęt spełnia minimalne wymagania do uruchomienia Paralives.
* Krytyczny plik używany podczas uruchamiania gry jest uszkodzony, nieczytelny lub niedostępny.
* Zacznij od sprawdzenia poprawności plików gry.
* Dodaj Paralives do wyjątków programu antywirusowego.
* Sprawdź player.log pod kątem błędów w lokalnym folderze mods paralives/paralives.

## Kategoria B — Importowanie zasobów

### Objawy

* Gra zatrzymuje się podczas importowania zasobów

### Możliwa przyczyna

Plik moda jest nieczytelny.

### Możliwe rozwiązania

* Usuń najnowsze mody z lokalnego folderu paralives/paralives lub folderów Steam Workshop, aż problem zostanie rozwiązany.
* Sprawdź poprawność plików gry.

## Kategoria C — Wybór zapisu

### Objawy

* Gra wraca do głównego menu podczas próby wczytania zapisu
* Plik zapisu jest biały

### Możliwa przyczyna

Plik zapisu ma nieprawidłowe nazwy plików, brakuje w nim plików lub jest nieczytelny.

### Możliwe rozwiązanie

Najpierw sprawdź, czy nazwa zapisu odpowiada plikom meta znajdującym się w środku oraz czy zapis zawiera wszystkie wymagane elementy.

## Kategoria D — Wczytywanie zapisu

### Objawy

* Gra zatrzymuje się podczas wczytywania zapisu
* Gra pozostaje na ekranie ładowania bez końca

### Możliwa przyczyna

Uszkodzony mod, nieprawidłowo usunięty mod lub uszkodzenie zapisu, takie jak błąd odwołania null.

Usunięcie niektórych modów bez uszkodzenia pliku zapisu może być niemożliwe.

### Możliwe rozwiązanie

Sprawdź, czy błędy nadal występują w nowym zapisie gry.

## Kategoria E — Tryb życia

### Objawy

* Gra zatrzymuje się lub zawiesza podczas otwierania menu w trybie życia
* Gra zatrzymuje się lub zawiesza podczas wykonywania określonej czynności w trybie życia

### Możliwa przyczyna

Uszkodzony mod, nieprawidłowo usunięty mod lub uszkodzenie zapisu, takie jak błąd odwołania null.

Usunięcie niektórych modów bez uszkodzenia pliku zapisu może być niemożliwe.

### Możliwe rozwiązanie

Sprawdź, czy błędy nadal występują w nowym zapisie gry.

## Kategoria F — Menu

### Objawy

* Menu gry nie otwiera się po kliknięciu
* Menu gry jest puste po kliknięciu
* Menu gry nie zamyka się

### Możliwa przyczyna

Uszkodzony mod, nieprawidłowo usunięty mod lub uszkodzenie zapisu, takie jak błąd odwołania null.

Usunięcie niektórych modów bez uszkodzenia pliku zapisu może być niemożliwe.

### Możliwe rozwiązanie

Sprawdź, czy błędy nadal występują w nowym zapisie gry.

## Kategoria G — Instalowanie modów

### Objawy

* Mody nie chcą się instalować

### Możliwe rozwiązania

* Sprawdź folder Steam i lokalny folder modów pod kątem niepełnych plików.
* Usuń uszkodzone pliki modów uniemożliwiające pobranie.

## Kategoria H — Brakujące mody

### Objawy

* Zainstalowane mody nie pojawiają się w menu modów
* Zainstalowane mody pojawiają się w menu modów, ale nie pojawiają się w grze

### Możliwe rozwiązania

* Sprawdź, czy mody nie są uszkodzone.
* Sprawdź, czy nie ma zduplikowanych plików modów.

## Kategoria I — Sprawdzanie modów

### Objawy

* Zainstalowane elementy modów nie pojawiają się po wyposażeniu postaci
* Zainstalowane elementy modów zniknęły
* Postać z elementami moda zniknęła
* Elementy modów wyglądają dziwnie
* Elementy modów zachowują się w nieoczekiwany sposób
* Elementy modów mają niewłaściwy kolor, kształt lub rozmiar

### Możliwe rozwiązanie

Sprawdź, czy mody nie są uszkodzone.

---

> **Przed wykonaniem któregokolwiek z tych kroków wykonaj pełną kopię zapasową swoich zapisów gry!**

# Jak usunąć uszkodzone dane

Uporządkowane według poziomu trudności i złożoności.

## Łatwe

### Wyłączanie i włączanie modów

* Czasami mody nie inicjalizują się prawidłowo, co można naprawić, wyłączając i ponownie włączając tylko jeden mod za pomocą menu modów w grze.

### Ponowne uruchomienie Paralives

* Gra posiada zabezpieczenia przed uszkodzonymi danymi, które aktywują się podczas uruchamiania gry.
* Może się to wydawać dziwne, ale wielokrotne ponowne uruchomienie gry może być skuteczne w niektórych sytuacjach.

### Rozpoczęcie nowego zapisu gry

* Jeśli błędy są zbyt skomplikowane lub nie można ich naprawić, rozpoczęcie nowego zapisu gry może być najlepszym rozwiązaniem.

### Sprawdzenie poprawności plików gry lub ponowna instalacja gry przez Steam

* W kliencie Steam, gdy gra jest wyłączona:

  * Steam > Paralives > Właściwości > Sprawdź spójność plików gry

### Ponowna subskrypcja wszystkich modów w celu usunięcia uszkodzonych plików

1. Dodaj wszystkie subskrybowane mody do niestandardowej kolekcji
2. Anuluj subskrypcję wszystkich modów
3. Zasubskrybuj wszystkie mody znajdujące się w kolekcji

### Usuwanie modów do momentu usunięcia uszkodzonego moda

* Usuwaj jeden mod na raz lub użyj metody 50/50, aby usuwać połowę modów do momentu zidentyfikowania uszkodzonego moda.
* Mody mogą nadal powodować błędy nawet po ich wyłączeniu. Muszą zostać całkowicie usunięte poprzez przeniesienie, anulowanie subskrypcji lub usunięcie plików moda.
* Gra może wymagać ponownego uruchomienia pomiędzy każdym testem, aby upewnić się, że pliki pamięci podręcznej zostały usunięte.
* Dokumentuj swoje ustalenia i zapisuj, które mody działają!

### Powolne ponowne subskrybowanie modów w celu upewnienia się, że instalują się prawidłowo

* Teoria zakłada, że instalowanie zbyt wielu modów jednocześnie powoduje błędy, dlatego instaluj mody powoli.
* Gra została zaprojektowana tak, aby szybko instalować mody, ale być może jest w tym trochę prawdy.

## Średnio zaawansowane

### Przenoszenie modów Steam Workshop do lokalnego folderu modów Paralives\Paralives

* Mody zainstalowane lokalnie są interpretowane inaczej przez silnik gry, co może naprawić błąd.

* Gdy gra nie jest uruchomiona, otwórz eksplorator plików i wróć do folderu modów Steam Workshop:

  ```text
  C:\Program Files (x86)\Steam\steamapps\workshop\content\1118520\
  ```

* Wpisz ".mod" w pasku wyszukiwania. Jeśli nie ma wyników, spróbuj "*.mod".

* Spowoduje to wyświetlenie folderów zawierających mody w folderze Steam Mods.

* Zaznacz, wytnij i wklej wszystkie foldery .mod do lokalnego folderu modów Paralives\Paralives.

* Wszystkie foldery powinny zostać przeniesione jednocześnie.

* Następnie anuluj subskrypcję modów, aby uniemożliwić Steam ponowne ich skopiowanie.

* Upewnij się, że kopia w folderze Steam Workshop została prawidłowo usunięta, ponieważ posiadanie dwóch kopii tego samego moda może powodować błędy.

### Usuwanie pozostałych plików z folderów modów Steam Workshop

* Wróć do workshop\content\1118520\ i usuń wszystkie pliki, które nie zostały prawidłowo usunięte.
* Zwróć szczególną uwagę na szczegóły, ponieważ późniejsze znalezienie drobnych błędów może być trudne.
* Pozostawione pliki bardzo prawdopodobnie spowodują błędy, gdy gra nie będzie ich oczekiwać.

### Używanie poleceń konsoli do naprawy uszkodzonego pliku zapisu poprzez usunięcie uszkodzonych danych

* `CLEARALLOCCUPATIONS` usunie wszystkie zawody i historię pracy wybranego para i tej operacji nie można cofnąć.
* `CLEARCHARACTEROUTFITS` usunie wszystkie stroje wybranego para i tej operacji nie można cofnąć.
* `CLEARINVENTORY` opróżni ekwipunek wybranego para i tej operacji nie można cofnąć.
* Poniższy poradnik wyjaśnia dostępne polecenia cheatów.

Poradnik dotyczący poleceń cheatów ⁠Console and Cheat Commands

### Instalowanie wtyczki wstrzykującej kod w celu zarządzania błędami modów

* Wtyczki te działają poprzez zapewnienie silnikowi gry większej ilości czasu na przetworzenie każdego pliku moda i pomagają silnikowi gry diagnozować błędy.
* Wtyczki mogą również powodować dodatkowe uszkodzenia danych, jeśli nie są odpowiednio utrzymywane i aktualizowane.
* Wtyczki prawdopodobnie staną się zbędne, gdy twórcy Paralives dodadzą więcej kodu korygującego błędy.

Paralines Launcher Plugin ⁠Paraline Launcher [Help | Bug R…

## Zaawansowane

### Wyczyszczenie lokalnego folderu modów

* Jest to wymagane, aby uzyskać prawdziwie świeży start.
* Może być konieczne wyłączenie Steam Cloud, aby zapobiec przywracaniu uszkodzonych plików podczas testowania.

1. Wytnij i wklej lokalny folder modów w bezpieczne miejsce poza plikami gry, na przykład na pulpit
2. Sprawdź poprawność plików gry za pomocą Steam
3. Uruchom ponownie grę. Po uruchomieniu Paralives odtworzy cały lokalny folder modów od podstaw.
4. Sprawdź, czy został utworzony nowy lokalny folder modów.
5. Sprawdź, czy problem został rozwiązany.

   * Tak: Przywróć ważne pliki z kopii utworzonej w kroku 1.
   * Nie: Spróbuj innych metod naprawienia problemu przed przywróceniem starych plików.
6. Dodawaj do nowo utworzonego folderu Paralives tylko pliki, które uważa się za bezpieczne, aby zmniejszyć ryzyko skopiowania uszkodzonych danych.

### Bezpośrednia edycja plików zapisu w celu usunięcia uszkodzonych danych

* Pliki zapisów są plikami tekstowymi i można je bezpośrednio modyfikować.
* Można użyć dowolnego edytora tekstu, ale zalecany jest Notepad++ z wtyczką do formatowania plików json.
* Poniższy poradnik wyjaśnia, jak sformatowane są pliki zapisów.

Wyjaśnienie lokalnego folderu modów ⁠Mod Folder/Save Folder

### Przenoszenie bezpiecznych części zapisu do nowego pliku zapisu

* Jeśli nie można zidentyfikować problemu z zapisem, przenieś małe fragmenty do nowego zapisu.
* Ta metoda może być pomocna przy próbie zidentyfikowania uszkodzonych plików.
* Na przykład foldery gospodarstw domowych można przeciągać pomiędzy zapisami przy stosunkowo niewielkiej utracie danych.
* Poniższy poradnik wyjaśnia, jak sformatowane są pliki zapisów.

Wyjaśnienie lokalnego folderu modów ⁠Mod Folder/Save Folder

### Używanie poleceń konsoli do odtworzenia postaci w nowym zapisie

* Gdy wszystko inne zawiedzie, najlepszym rozwiązaniem może być rozpoczęcie od nowego zapisu, ale z pewnym ułatwieniem na początek.
* Polecenia takie jak `SETMONEY` mogą być używane do dodawania pieniędzy.
* Poleceń można używać do przywracania umiejętności, przepisów i innych elementów.

Poradnik dotyczący poleceń cheatów ⁠Console and Cheat Commands

---

> **Przed wykonaniem któregokolwiek z tych kroków wykonaj pełną kopię zapasową swoich zapisów gry!**

# „Typowe rozwiązanie”

Metoda spalenia wszystkiego do gołej ziemi, polegająca na usunięciu każdego pliku powiązanego z grą w celu uzyskania możliwie najlepszego świeżego startu. Nie polecam tego rozwiązania w przypadku wszystkich problemów, ponieważ może ono sprawić, że stare zapisy korzystające z modów staną się niemożliwe do uruchomienia bez modów, od których zależą.

## Usunięcie wszystkich plików gry w celu uzyskania świeżego startu

1. Usuń pliki gry, wycinając i wklejając cały lokalny folder modów paralives/paralives na pulpit.
2. Anuluj subskrypcję wszystkich modów Steam Workshop i usuń wszystkie pozostałe pliki modów.
3. Sprawdź poprawność plików gry za pomocą Steam lub ponownie zainstaluj grę.
4. Uruchom ponownie Paralives.
5. Rozpocznij nowy zapis gry.
6. Jeśli gra działa poprawnie, stopniowo wycofuj wprowadzone zmiany, aż problem ponownie wystąpi. Wtedy poznasz jego przyczynę.

# Zapobieganie uszkodzeniu danych

## Twórz kopie WSZYSTKIEGO i RÓB TO CZĘSTO

* Wykonuj fizyczną kopię ważnych plików i przechowuj ją w bezpiecznym miejscu, na przykład na pulpicie poza plikami gry.
* Pliki dostępne dla silnika gry Paralives zawsze mogą ulec uszkodzeniu.

> Uwaga: Polecenie ZIPSAVEFILE utworzy kopię bieżącego zapisu na pulpicie. Jeśli polecenie zostanie użyte dwukrotnie, może nadpisać starą kopię.

Poradnik dotyczący poleceń cheatów ⁠Console and Cheat Commands

`ZIPSAVEFILE` tworzy plik zip bieżącego zapisu na pulpicie

## Czytaj recenzje modów

* I również zostawiaj recenzje!
* Komentarze dotyczące modów są sposobem, w jaki twórca moda i inni użytkownicy dzielą się informacjami o modach.
* Jeśli mod wydaje się uszkodzony, poinformuj o tym twórcę, aby mógł go naprawić!

## Wyłącz Steam Cloud

* Steam Cloud świetnie chroni ważne pliki, ale czasami powoduje trudne do wykrycia problemy.
* Steam Cloud lubi przywracać nieaktualne pliki bez informowania o tym użytkownika i po prostu umieszczać je z powrotem w folderze.

## Prawidłowe usuwanie modów

* Mody dodają do gry odwołania do elementów.
* Każde wystąpienie tych elementów musi zostać ręcznie usunięte z zapisu gry PRZED usunięciem moda.
* O wiele łatwiej jest usuwać elementy modów w grze niż poprzez modyfikowanie pliku zapisu.
* Usuń tę fantazyjną kanapę i ten zabawny sweter, zanim usuniesz mod!

## Aktualizuj sterowniki

* W tym poradniku należy skupić się na sterowniku karty graficznej (GPU).
* W systemie Windows pobierz aplikację Nvidia lub AMD i instaluj nowy sterownik co kilka miesięcy.

## Aktualizuj system operacyjny

* Tak, fuj, ale jest to ważne!
* Regularnie uruchamiaj wbudowane narzędzie aktualizacji, takie jak Windows Update.

## Instaluj mody powoli i sprawdzaj zainstalowane mody pojedynczo lub w małych partiach

* Może to pomóc grze w przetwarzaniu każdego pliku bez popełniania błędów.

## Konserwacja sprzętu

* Dbaj o komputer, a on zadba o Ciebie.
* Instaluj i uruchamiaj bezpiecznie pozyskane oprogramowanie antywirusowe.
* Sprawdzaj uszkodzenia fizyczne i usuwaj kurz.
* Uruchamiaj wbudowane programy służące do sprawdzania stanu i stabilności podzespołów.



Treść tego repozytorium, kod źródłowy, dokumentacja oraz powiązane pliki nie mogą być wykorzystywane do trenowania modeli AI, tworzenia zbiorów danych ani do innych celów związanych z uczeniem maszynowym.
