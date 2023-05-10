# 4. Narzędzia developerskie

## 4.1.  Wprowadzenie

### Czym jest środowisko developerskie?

Środowisko developerskie to zestaw narzędzi używanych do pracy nad projektem. Na środowisko developerskie składają się:

- katalog roboczy;
- edytor kodu;
- system kontroli wersji;
- manager pakietów (NPM);
- etc.

Określenie "lokalne" oznacza, że wszystkie niezbędne narzędzia znajdują się na maszynie lokalnej programisty.

### Po co nam środowisko developerskie?

Zalety pracy z lokalnym środowiskiem developerskim:

- możliwość pracy offline, brak utraty postępów w przypadku awarii sieci;
- łatwość obsługi większych projektów (edytory online nie wspierają rozbudowanej struktury katalogów);
- elastyczność wyboru i konfiguracji narzędzi;
- połączenie z systemem kontroli wersji;

> Umiejętność konfiguracji i obsługi lokalnego środowiska developerskiego jest niezbędna dla programisty. Znajomość tych narzędzi może być wymagana podczas rekrutacji na stanowisko developerskie.

## 4.2.  Elementy środowiska developerskiego

### Katalog roboczy

Katalog roboczy to wydzielone miejsce na dysku komputera, którego przeznaczeniem jest przechowywanie plików projektów. Taki katalog można utworzyć w dowolnej lokalizacji, ale najlepiej w innym niż pliki systemu operacyjnego.

> Istotne jest utrzymywanie porządku na dysku komputera przeznaczonego do pracy nad projektem, co pozwala na skrócenie czasu poruszania się pomiędzy plikami tworzonych stron lub aplikacji.

#### Struktura katalogów w projekcie

Katalog projektu również powinien być uporządkowany. Z tego względu pliki grupuje się w podkatalogach. Struktura będzie zawsze zależała od projektu.
Jednym z prostszych przykładów uporządkowania może być poniższy podział:

- `/sass` - katalog przeznaczony do tworzenia i edycji plików w SASS - `*.scss`;
- `/css` - katalog, do którego będą trafiały pliki `*.css` wygenerowane przez SASS;
- `/vendor` - katalog przeznaczony na pliki zewnętrznych zasobów, podłączanych do projektu (np. Bootstrap); tych plików nie należy edytować;
- `/images` - katalog przeznaczony na pliki graficzne wykorzystywane w projekcie;
- `/js` - katalog, w którym będą umieszczane skrypty JavaScript;

> Istotne jest przyjęcie zasady, że pliki bibliotek i pluginów, które znajdują się w katalogu `/vendor` nie będą modyfikowane.
> W przypadku potrzeby aktualizacji takich plików nie będzie wątpliwości, czy były one wcześniej zmieniane.
> W przypadku potrzeby modyfikacji pliku zewnętrznego zasobu, np. pliku `.css` Bootstrapa, należy przenieść go do katalogu `/sass` uprzednio zmieniając jego rozszerzenie na `.scss`.

### Edytor kodu

**Edytor kodu** to podstawowe narzędzie pracy programisty.
Zasadniczo do pisania kodu może posłużyć dowolny edytor do pracy na czystym tekście (np. Notatnik w Windows, ale już nie Word).
Jednakże dedykowane edytory znacząco usprawniają pracę dzięki takim funkcjonalnościom jak:

- kolorowanie składni;
- podświetlanie błędów składni;
- obsługa *snippetów* - często powtarzających się fragmentów kodu;
- używanie wielu kursorów do jednoczesnej edycji kodu w wielu miejscach;
- przeglądanie katalogu projektu i obsługa plików;

Ponadto podstawowe funkcjonalności można rozbudowywać za pomocą wtyczek.

Przykłady edytorów kodu:

- **[Visual Studio Code](https://code.visualstudio.com/)**
- **[Sublime Text](https://www.sublimetext.com/)**
- **[Brackets](https://brackets.io/)**
- **[Web Storm lub PHP Storm](https://www.jetbrains.com/)**
- **[Atom](https://github.blog/2022-06-08-sunsetting-atom/)** - nie jest rozwijany od 2022 roku

### Terminal

Ze względu na sposób obsługi, interfejsy użytkownika można podzielić na:
- **GUI** (ang. *Graphical User Interface*) - interfejs graficzny np. eksplorator plików Windows;
- **CLI** (ang. *Command Line Interface*) - interfejs tekstowy np. konsola CMD w Windows;

W interfejsach graficznych wykorzystuje się:
- wiele równolegle dostępnych informacji np.:
	- lista plików w głównym oknie;
	- lista katalogów w bocznej kolumnie;
	- pasek adresu wskazujący obecnie przeglądaną lokalizację;
- guziki i menu pozwalające na wywoływanie różnych akcji np. utworzenie pliku/katalogu, zmiana nazwy pliku/katalogu etc.
- akcje obsługiwane za pomocą kursora myszy np. drag&drop;

W interfejsach tekstowych stosuje się:
- akcje wykonywane za pomocą komend tekstowych;
- wszystkie komunikaty i informacje są prezentowane za pomocą tekstu;
- informacje są wyświetlane jednorazowo po wykonaniu komendy;

**[Poradnik obsługi linii komend](https://uploads.kodilla.com/bootcamp/pdf/obsluga-linii-komend.pdf)**

### Repozytorium

**Repozytorium** to miejsce (platforma) pozwalające na przechowywanie plików projektu wraz z pełną historią zmian w projekcie. Repozytorium pozwala pobrać i otworzyć projekt na maszynie lokalnej.

Trzymanie kodu "na zewnątrz" zabezpiecza również projekt w przypadku awarii sieci na urządzeniu lokalnym.

Repozytorium udostępnia również możliwość pracy na gałęziach projektu (kopii roboczej), które służą do tego aby przygotować konkretną zmianę i połączyć ją z gałęzią główną dopiero wtedy, kiedy będzie ukończona.

### System kontroli wersji

System kontroli wersji to zestaw narzędzi do obsługi repozytoriów. Jego podstawowe funkcjonalności to:

- wysyłanie kodu do zdalnego repozytorium;
- pobieranie kodu ze zdalnego repozytorium;
- tworzenie nowych gałęzi;
- dowiązywanie gałęzi;

Korzyści płynące z pracy z systemem kontroli wersji:

- znikome ryzyko utraty plików;
- usprawnienie współpracy z innymi developerami;
- utrzymywanie porządku w projekcie przy jednoczesnym rozwijaniu kilku funkcjonalności;
- dokumentacja przebiegu prac w przypadku powrotu do wcześniejszej wersji;
- komunikacja z developerami za pomocą czytelnych opisów wprowadzonych zmian;
- przy skomplikowanej konfiguracji po stronie serwera automatyzacja niektórych procesów;

> Upraszczając system kontroli wersji służy do zapisu kolejnych wersji projektu. Dla przykładu nową wersję projetu można zapisać np. po dodaniu nowego komponentu typu nawigacja na stronie.

![Git](https://uploads.kodilla.com/bootcamp/wdp/04/wd-7-1-8.gif)

> Pozwala to łatwo znaleźć pożądaną zmianę w projekcie i jej autora. Możliwe jest również przywrócenie wersji z daną zmianą w projekcie.

> System kontroli wersji pozwala również na łatwą synchronizację zmian wykonanych przez kilku developerów bez konieczności ręcznej edycji plików.

![Git](https://uploads.kodilla.com/bootcamp/wdp/04/wd-7-1-9.gif)

Jednym z najpopularniejszych systemów kontroli wersji jest **Git**.

### Trzy słowa podsumowania

## 4.3.  Git – podstawy

**Git** - system kontroli wersji obsługiwany najczęściej z poziomu wiersza poleceń.

**Commit** - każda zmiana w projekcie, która jest wysyłana do zdalnego repozytorium.

> Każdy commit zapisuje zmiany wyłącznie względem poprzedniej wersji. Pliki, które nie ulegają zmianie nie są ponownie zapisywane.

**[Poradnik Gita](http://rogerdudler.github.io/git-guide/)** - bardziej zaawansowane przykłady zastosowania Gita

### Instalacja Gita

> **Winows**
> Wraz z Gitem zostanie zainstalowany *Git Bash*.
> Git Bash emuluje terminal linuksowy i niweluje różnice pomiędzy korzystaniem z Gita na terminalu i w konsoli `cmd.exe`.
> Git Bash można otworzyć w dowolnym katalogu wybierając go z listy opcji po wciśnięciu `PPM`.

**[Instalacja Gita](https://git-scm.com/downloads)** - odnośnik do platformy z plikami instalacyjnymi dla Windows, MacOS oraz Linux.

> **Master vs Main**
> Obecnie odchodzi się od nazewnictwa głównej gałęzi projektu jako `master` (poprawność polityczna) na rzecz `main`.
> Master może być nadal wykorzystywany w starszych projektach.

### Podstawowa konfiguracja Gita

Git wymaga konfiguracji danych użytkownika. Dane te są wykorzystywane do podpisywania autora przesyłanych commitów. Konfiguracja jest jednorazowa i przebiega w następujący sposób:

1. Otworzenie terminala w dowolnej lokalizacji;
2. `git config --global user.name "Jan Kowalski"` - komenda z dowolnym imieniem i nazwiskiem;
3. `git config --global user.email "jan.kowalski@example.com"` - komenda konfigurująca e-mail użytkownika;
4. `git config --global -l` - komenda pozwalająca zweryfikować wprowadzone ustawienia;

<br>

Tworzenie aliasu `git tree` dla komendy:
```markup
git log --graph --decorate --pretty=oneline --abbrev-commit
```
Alias zostanie skonfigurowany po wywołaniu w terminalu poniższej komendy:
```markup
git config --global alias.tree "log --graph --decorate --pretty=oneline --abbrev-commit"
```
Weryfikacja wprowadzonych zmian:
```markup
git config --global -l
```

<br>

Wywoływanie komendy `git push` bez dodatkowego komunikatu:
```markup
git config --global push.default simple
```

### Inicjalizacja repozytorium

Do inicjalizacji repozytorium Gita w projekcie służy komenda:
```markup
git init
```
Jej wywołanie tworzy w katalogu roboczym folder `.git`, w którym będą przechowywane informacje o repozytorium.

> Utworzenie katalogu `.git` można zweryfikować za pomocą polecenia `ls -a`, które służy do wyświetlania zawartości katalogu wraz z ukrytymi plikami i folderami.

> Repozytorium w projekcie inicjujemy tylko jeden raz.
> W przypadku dołączania do istniejącego projektu repozytorium należy sklonować bez inicjacji.

### Pierwsze commity

W commicie są zapisywane zmiany względem poprzedniego commita. Nadpisywane są tylko te pliki, które uległy modyfikacji. Utworzenie nowego pliku zapisuje go w całości.

`git status` - wyświetlenie informacji o aktualnym stanie repozytorium.

> "untracked files" to pliki, które nie były jeszcze zapisane w żadnym commicie.

**Staging** - przygotowanie pliku do commitu:
```markup
git add "nazwa pliku"
```
Wynikiem wywołania tej komendy będzie dodanie wskazanego pliku do **Indexu**, który funkcjonuje jako poczekalnia dla plików oczekujących na commit.

Dodanie nowego commita:
```markup
git commit -m "Nazwa commita"
```
>  Użycie flagi `-m` pozwala na dodanie komentarza do commita.

> Wszystkie zmienione pliki można dodać do Indexu za pomocą komenty `git add .`

### Dobre praktyki nazewnictwa commitów

**Zwięzłość**
Tytuł commita powinien krótko opisywać co zostało zmienione względem poprzedniej wersji. Nie należy przekraczać 50 znaków.

**Język**
Commity należy redagować w języku angielskim rozpoczynając od czasownika pisanego wielką literą w czasie Present Simple np. "Add", "Change", "Fix", "Remove" etc.

**Czytelność**
Treść komentarzy należy redagować konkretnie np. "Add styles for footer".

### Tagi

Tagi to dodatkowe oznaczenia dla commitów. Mogą okazać się skuteczne w sytuacji, w której po kolejnych zmianach w projekcie chce się uzyskać wgląd do uwag dla wcześniejszej wersji.

Tagi można dodawać na 2 sposoby:
```markup
git tag "v1"
```
Powyższa komenda dodaje tag do najnowszego commita.
```markup
git tag "v1" e754f41
```
Powyższa komenda dodaje tag do commita o wskazanym identyfikatorze. Identyfikator można wyświetlić za pomocą komendy `git tree`.

### Podsumowanie — przykład standardowego użycia

Dobrą praktyką jest dodawnia commita po każdym wykonanym zadaniu. Można przyjąć podejście szczegółowe lub bardziej ogólne:
- szczegółowe - przykład:
	-  dodanie HTML dla logo strony -> commit;
	- dodanie stylów dla logo strony -> commit;
	- dodanie HTML bannera strony -> commit;
	- ostylowanie bannera strony -> commit;
	- dodanie HTML głównej nawigacji -> commit;
	- ostylowanie głównej nawigacji -> commit;
	- etc.
- bardziej ogólne - przykład:
	- dodanie nagłówka -> commit;
	- dodanie stopki -> commit;
	- etc.

### Zadanie:  pierwsze samodzielne commity 
