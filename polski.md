# Indeks

* [Wymagane elementy](#wymagane-elementy)
* [Identyfikowanie uszkodzonych danych](#identyfikowanie-uszkodzonych-danych)
* [Jak usunąć uszkodzone dane](#jak-usunąć-uszkodzone-dane)
* ["Zwykła poprawka"](#zwykła-poprawka)
* [Zapobieganie uszkodzeniu danych](#zapobieganie-uszkodzeniu-danych)
* [Więcej zasobów](#więcej-zasobów)

> **Przed wykonaniem któregokolwiek z tych kroków wykonaj pełną kopię zapasową plików zapisów gry!**

---

# Wymagane elementy

## Folder modów Steam Workshop (mody Workshop)

* Można uzyskać do niego dostęp, klikając ikonę folderu przy modzie Steam Workshop w menu modów Paralives.
* Przechodząc do:

**Windows:**

```text
C:\Program Files (x86)\Steam\steamapps\workshop\content\1118520\
```

**Mac:**

```text
~/Library/Application Support/Steam/steamapps/workshop/content/1118520
```

## Folder Paralives (mody lokalne)

* Można uzyskać do niego dostęp, klikając ikonę folderu przy lokalnym modzie w menu modów Paralives.
* Przechodząc do:

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
* Zawiera dzienniki bieżącej lub ostatnio rozegranej sesji Paralives.

## Folder Paralives\MySavedGames.mod

* Folder zawierający wszystkie bieżące zapisy gry i zapisy automatyczne.
* Znajduje się w folderze Paralives\Paralives.
* Ten folder jest ważniejszy niż jakikolwiek inny.
* Regularnie wykonuj pełną kopię tego folderu i przechowuj ją w bezpiecznej lokalizacji poza plikami gry!

## Folder Paralives\MyPremadeHouseholds.mod

* Gospodarstwa domowe zapisane w bibliotece.

## Folder Paralives\MyPremadeLot.mod

* Działki zapisane w bibliotece.

## Folder Paralives\MyPremadeOutfits.mod

* Stroje zapisane w bibliotece.

## Folder Paralives\Local.mod i 0.mod

* Przechowuje ustawienia gry, takie jak niestandardowe warianty kolorystyczne.

---

# Identyfikowanie uszkodzonych danych

Uszkodzone dane składają się z plików, które zostały zmienione i nie są już w formie ani kolejności, której gra oczekuje.

## Nieaktualne pliki

* Gra została zaktualizowana, a te pliki nie są już zgodne z aktualną składnią.
* Chociaż może się to sporadycznie zdarzać w przypadku modów, niemal wszystkie pluginy wstrzykujące kod bepinex stają się nieaktualne po aktualizacji gry.
* Jeśli plugin bepinex jest zainstalowany, ale mody nadal nie działają, plugin może powodować więcej szkody niż pożytku.

## Nieprawidłowo zmodyfikowane pliki

* Zostały zmodyfikowane przez gracza, moddera lub nawet silnik gry i są teraz nieprawidłowe.
* Dotyczy to sytuacji, gdy mody lub pluginy były używane, a następnie zostały usunięte.

Na przykład mod został użyty do dodania niestandardowego stroju, następnie mod został usunięty, ale strój nadal jest identyfikowany w plikach gry.

Usunięcie niektórych modów bez uszkodzenia pliku zapisu gry może być niemożliwe.

## Nieprawidłowo przeniesione pliki

* Pliki są często przenoszone przez gracza, silnik gry lub Steam, a niektóre części pliku pozostają na miejscu lub zostają usunięte.

## W jaki sposób gra poinformuje mnie, które pliki są uszkodzone?

Silnik gry będzie próbował poinformować użytkownika o wystąpieniu błędu za pomocą bezpośrednich i pośrednich powiadomień.

### Bezpośrednie:

* Wyskakujące okna na ekranie
* Powiadomienia w konsoli
* Zdarzenia w player.log

### Pośrednie:

* Migotanie
* Błyski
* Zacinanie
* Lagi
* Wyłączanie się gry
* Anulowanie operacji

## Odczytywanie Error Console i Player.Log

Raporty error console i player.log pokrywają się tylko częściowo, dlatego podczas próby zidentyfikowania błędu ważne jest sprawdzenie obu.

Ważne jest zidentyfikowanie początkowego błędu i zignorowanie dodatkowych błędów spowodowanych przez pierwszy błąd. Podczas odczytywania dziennika błędów należy próbować naprawiać błędy od góry do dołu, w kolejności ich występowania.

Jeśli jednocześnie pojawi się wiele błędów, diagnozowanie może być bardzo trudne. Ważne jest, aby pomiędzy testami wprowadzać tylko niewielką liczbę zmian.

Jeśli gra działa płynnie, zanotuj błędy w dzienniku, aby można było je później wykluczyć, gdy coś zacznie działać nieprawidłowo.

### ERROR CONSOLE

* Error console jest dostępna w grze jako zakładka w menu cheatów.
* Nie można jej używać, jeśli gra się nie ładuje.

1. Naciśnij Ctrl+Shift+C, aby otworzyć menu cheatów.
2. Naciśnij strzałkę, aby przełączyć się na zakładkę konsoli.
3. Konsola jest podzielona na trzy kategorie według ważności.
4. W kontekście tego poradnika ważne są tylko czerwone błędy.

### PLAYER.LOG & PLAYER-PREV.LOG

* Ten plik rejestruje działania wykonywane przez silnik gry Unity uruchamiający Paralives.
* Player.log jest nadpisywany przy każdym uruchomieniu gry i przenoszony do Player-prev.log.
* Znajduje się w lokalnym folderze modów Paralives\Paralives.
* Więcej informacji można umieścić w dzienniku, włączając opcje w panelu sterowania. Zbyt wiele opcji może szybko spowodować, że dziennik stanie się bardzo duży.
* Jeśli coś w dzienniku jest ważne, wykonaj kopię!

### Dobre błędy (a przynajmniej nie złe):

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

> Uwaga: W wersji 1.7 w konsoli i player.log pojawiają się trzy nowe czerwone błędy, które nie wydają się negatywnie wpływać na wydajność gry.
>
> * `+ System Exception: Invalid Path...`
> * `+ Runtime data is null...`
> * `+ OperationException: Addressables...`

> Uwaga: W wersji 1.8A importer .fbx nie działał prawidłowo i zatrzymywał się na ekranie importowania assetów.

---

# Rodzaje błędów

Rodzaje problemów występujących na poziomie technicznym.

## Null Reference

* Czasami nazywane odwołaniem do pustego wskaźnika.
* Dowolny błąd wskazujący, że nie można znaleźć ustawienia, przedmiotu, mesha lub wartości.
* Gra odwołuje się do obiektu, którego nie może znaleźć, albo nie rozumie tego, co znalazła.

> Uwaga: Gra potrafi obsługiwać niektóre odwołania null, a kilka z nich jest częścią wersji gry we wczesnym dostępie.

## Out of Bounds

* Gra otrzymała wartość spoza oczekiwanego zakresu.
* Jeśli gra oczekuje wartości pomiędzy 0 a 10, ale otrzyma 10842, może to spowodować błąd.

## Translation

* Gra próbowała naprawić plik uznany za uszkodzony, ale wynik był nieprawidłowy.

Na przykład problem z plikami .tmp ⁠.mod.meta i .tmp

## Syntax

* Gra została zaktualizowana, a mod nie jest już zgodny ze standardami określonymi przez grę. Najczęściej dotyczy to pluginów wstrzykujących kod Bepinex.
* Niektóre mody utworzone w momencie premiery gry nie zawierają dwukropków w pliku tekstowym.

---

# Kategorie objawów

Gdy przyczyna błędu jest nieznana, celem jest powiązanie objawów z konkretną przyczyną. Po naprawieniu każdego błędu gra będzie działać. Poniżej znajdują się arbitralne kategorie pomagające grupować podobne błędy.

Ważne jest zidentyfikowanie początkowego błędu i zignorowanie dodatkowych błędów spowodowanych przez pierwszy błąd.

## Cat A — Uruchamianie gry

### Objawy

* Gra nie może przejść do głównego menu Paralives
* Ekran jest czarny
* Gra zawiesza się podczas uruchamiania przez Steam
* Podczas uruchamiania gry przez Steam pojawia się błąd
* Gra zatrzymuje się na obrazie chmur.

### Możliwe rozwiązania

* Sprawdź, czy sprzęt spełnia minimalne wymagania do uruchomienia Paralives.
* Krytyczny plik używany podczas uruchamiania gry jest uszkodzony, nieczytelny lub niedostępny.
* Zacznij od sprawdzenia plików gry.
* Dodaj wyjątek dla Paralives w programie antywirusowym.
* Sprawdź player.log pod kątem błędów w lokalnym folderze modów paralives/paralives.

## Cat B — Importowanie assetów

### Objawy

* Gra zatrzymuje się na etapie importowania assetów

### Możliwa przyczyna

Plik moda jest nieczytelny.

### Możliwe rozwiązania

* Usuwaj najnowsze mody z lokalnego folderu modów paralives/paralives lub folderów Steam Workshop, aż problem zostanie rozwiązany.
* Sprawdź pliki gry.

## Cat C — Wybór zapisu

### Objawy

* Gra wraca do głównego menu podczas próby załadowania zapisu
* Plik zapisu jest biały

### Możliwa przyczyna

Plik zapisu ma nieprawidłowe nazwy plików, brakuje w nim plików lub jest nieczytelny.

### Możliwe rozwiązanie

Zacznij od sprawdzenia, czy nazwa zapisu odpowiada plikom meta znajdującym się wewnątrz oraz czy zapis zawiera wszystkie wymagane komponenty.

## Cat D — Ładowanie zapisu

### Objawy

* Gra zatrzymuje się podczas ładowania zapisu
* Gra pozostaje na ekranie ładowania w nieskończoność

### Możliwa przyczyna

Uszkodzony mod, nieprawidłowo usunięty mod lub uszkodzenie pliku zapisu, takie jak błąd null reference.

Usunięcie niektórych modów bez uszkodzenia pliku zapisu może być niemożliwe.

### Możliwe rozwiązanie

Sprawdź, czy błędy występują również w nowym zapisie gry.

## Cat E — Tryb Live

### Objawy

* Gra zatrzymuje się lub zawiesza podczas otwierania menu w trybie Live
* Gra zatrzymuje się lub zawiesza podczas wykonywania określonej czynności w trybie Live

### Możliwa przyczyna

Uszkodzony mod, nieprawidłowo usunięty mod lub uszkodzenie pliku zapisu, takie jak błąd null reference.

Usunięcie niektórych modów bez uszkodzenia pliku zapisu może być niemożliwe.

### Możliwe rozwiązanie

Sprawdź, czy błędy występują również w nowym zapisie gry.

## Cat F — Menu

### Objawy

* Menu gry nie otwiera się po kliknięciu
* Menu gry jest puste po kliknięciu
* Menu gry nie zamyka się

### Możliwa przyczyna

Uszkodzony mod, nieprawidłowo usunięty mod lub uszkodzenie pliku zapisu, takie jak błąd null reference.

Usunięcie niektórych modów bez uszkodzenia pliku zapisu może być niemożliwe.

### Możliwe rozwiązanie

Sprawdź, czy błędy występują również w nowym zapisie gry.

## Cat G — Instalowanie modów

### Objawy

* Mody nie chcą się zainstalować

### Możliwe rozwiązania

* Sprawdź foldery modów Steam i lokalnych pod kątem niekompletnych plików.
* Usuń uszkodzone pliki modów uniemożliwiające pobranie.

## Cat H — Brakujące mody

### Objawy

* Zainstalowane mody nie pojawiają się w menu modów
* Zainstalowane mody pojawiają się w menu modów, ale nie pojawiają się w grze

### Możliwe rozwiązania

* Sprawdź, czy nie ma uszkodzonych modów.
* Sprawdź, czy nie ma zduplikowanych plików modów.

## Cat I — Sprawdzanie modów

### Objawy

* Zainstalowane przedmioty z modów nie pojawiają się po wyposażeniu postaci
* Zainstalowane przedmioty z modów zniknęły
* Postać z przedmiotami z modów zniknęła
* Przedmioty z modów wyglądają dziwnie
* Przedmioty z modów zachowują się w nieoczekiwany sposób
* Przedmioty z modów mają niewłaściwy kolor, kształt lub rozmiar

### Możliwe rozwiązanie

Sprawdź, czy nie ma uszkodzonych modów.

---

> **Przed wykonaniem któregokolwiek z tych kroków wykonaj pełną kopię zapasową plików zapisów gry!**

---

# Jak usunąć uszkodzone dane

Posortowane według poziomu trudności i złożoności.

## Łatwe

### Wyłączanie i włączanie modów

* Czasami mody nie inicjalizują się prawidłowo, co można naprawić, wyłączając i ponownie włączając tylko jeden mod za pomocą menu modów w grze.

### Uruchom ponownie Paralives

* Gra posiada zabezpieczenia przed uszkodzonymi danymi, które są aktywowane podczas uruchamiania gry.
* Może się to wydawać głupie, ale wielokrotne ponowne uruchomienie gry może być skuteczne w niektórych sytuacjach.

### Rozpocznij nowy zapis gry

* Jeśli błędy są zbyt skomplikowane lub nie można ich naprawić, rozpoczęcie nowego zapisu gry może być najlepszą opcją.

### Sprawdź pliki gry lub zainstaluj ponownie grę za pomocą Steam

* W kliencie Steam, gdy gra jest zamknięta:

  * Steam > Paralives > Properties > Verify integrity of games files

### Ponownie zasubskrybuj wszystkie mody, aby usunąć uszkodzone pliki

1. Dodaj wszystkie zasubskrybowane mody do niestandardowej kolekcji
2. Anuluj subskrypcję wszystkich modów
3. Zasubskrybuj wszystkie mody znajdujące się w kolekcji

### Usuwaj mody, aż uszkodzony mod zostanie usunięty

* Usuwaj jeden mod na raz lub użyj metody 50/50, aby usuwać połowę modów, aż uszkodzony mod zostanie zidentyfikowany.
* Mody nadal mogą powodować błędy nawet po wyłączeniu. Muszą zostać całkowicie usunięte poprzez przeniesienie, anulowanie subskrypcji lub usunięcie plików moda.
* Gra może wymagać ponownego uruchomienia pomiędzy każdym testem, aby upewnić się, że pliki z pamięci podręcznej zostały usunięte.
* Dokumentuj swoje ustalenia i zapisuj, które mody działają!

### Ponownie zasubskrybuj mody powoli, aby upewnić się, że instalują się prawidłowo

* Teoria zakłada, że instalowanie zbyt wielu modów naraz powoduje błędy, dlatego instaluj mody powoli.
* Gra została zaprojektowana tak, aby instalować mody szybko, ale być może jest w tym coś prawdziwego.

---

## Średniozaawansowane

### Przenieś mody Steam Workshop do lokalnego folderu modów Paralives\Paralives

* Mody zainstalowane lokalnie są interpretowane przez silnik gry w inny sposób, co może naprawić błąd.
* Gdy gra nie jest uruchomiona, otwórz eksplorator plików i wróć do folderu modów Steam Workshop:

  ```text
  C:\Program Files (x86)\Steam\steamapps\workshop\content\1118520\
  ```
* Wpisz ".mod" w pasku wyszukiwania. Jeśli nie będzie wyników, spróbuj "*.mod".
* Spowoduje to wyświetlenie folderów zawierających mody w folderze Steam Mods.
* Zaznacz, wytnij i wklej wszystkie foldery .mod do lokalnego folderu modów Paralives\Paralives.
* Wszystkie foldery powinny zostać przeniesione jednocześnie.
* Następnie anuluj subskrypcję modów, aby uniemożliwić Steamowi skopiowanie ich z powrotem.
* Upewnij się, że kopia w folderze modów Steam Workshop została prawidłowo usunięta, ponieważ dwie kopie tego samego moda mogą powodować błędy.

### Usuń wszystkie pozostałe pliki z folderów modów Steam Workshop

* Wróć do workshop\content\1118520\ i usuń wszystkie pliki, które nie zostały prawidłowo usunięte.
* Zwróć szczególną uwagę na szczegóły, ponieważ drobne błędy będą później trudne do znalezienia.
* Pozostawione pliki bardzo często powodują błędy, gdy gra ich nie oczekuje.

### Użyj poleceń konsoli, aby naprawić uszkodzony plik zapisu poprzez usunięcie uszkodzonych danych

* `CLEARALLOCCUPATIONS` usunie wszystkie prace i historię pracy wybranego para i nie można tego cofnąć.
* `CLEARCHARACTEROUTFITS` usunie wszystkie stroje wybranego para i nie można tego cofnąć.
* `CLEARINVENTORY` opróżni ekwipunek wybranego para i nie można tego cofnąć.
* Poniższy poradnik wyjaśnia dostępne polecenia cheatów.

Tutorial for cheat commands ⁠Console and Cheat Commands

### Zainstaluj plugin wstrzykujący kod, aby zarządzać błędami modów

* Pluginy te działają poprzez zapewnienie silnikowi gry większej ilości czasu na przetworzenie każdego pliku moda oraz pomagają silnikowi gry diagnozować błędy.
* Pluginy mogą również powodować dodatkowe uszkodzenia danych, jeśli nie są odpowiednio utrzymywane i aktualizowane.
* Miejmy nadzieję, że pluginy staną się niepotrzebne, gdy twórcy Paralives dodadzą do gry więcej kodu korygującego błędy.

Paralines Launcher Plugin ⁠Paraline Launcher [Help | Bug R…

---

## Zaawansowane

### Wyczyść lokalny folder modów

* Jest to konieczne, aby uzyskać prawidłowy świeży start.
* Steam Cloud może wymagać wyłączenia, aby zapobiec przywracaniu uszkodzonych plików podczas testowania.

1. Wytnij i wklej lokalny folder modów do bezpiecznej lokalizacji poza plikami gry, takiej jak pulpit
2. Sprawdź pliki gry za pomocą Steam
3. Uruchom ponownie grę. Po uruchomieniu Paralives odtworzy cały lokalny folder modów od podstaw.
4. Sprawdź, czy został wygenerowany nowy lokalny folder modów.
5. Sprawdź, czy problem został rozwiązany.

   * Tak: Przywróć ważne pliki z kopii utworzonej w kroku 1.
   * Nie: Spróbuj innych metod naprawienia problemu przed przywróceniem starych plików.


The contents of this repository, source code, documentation, and associated files, may not be used for AI model training, dataset creation, or other machine-learning purposes.
7. Dodawaj do nowo wyg
