
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

**[Monty Python Landing Repo](https://github.com/jerzy-jarczynski/monty-python-landing/commits/master)** - link do repozytorium przykładowej strony, utworzonej na potrzeby nauki Gita

**[Moty Python Landing Demo](https://codepen.io/jerzyjarczynski/pen/WNKJGZY)** - link do demo przykładowej strony, utworzonej na potrzeby nauki Gita

**[Monty Python Git Screenshots](https://drive.google.com/drive/folders/1B4TMyScMypqqBYEPwSi7Tmv-etrwPuGI?usp=sharing)** - link do zrzutów ekranu pierwszych commitów

## 4.4.  Git – repozytorium zdalne

### Github, Gitlab, Bitbucket

Bywa tak, że firmy developerskie posiadają własne serwery przeznaczone do utrzymywania repozytoriów zdalnych.
Innym rozwiązaniem są platformy udostępniające odpłatnie lub za darmo zdalne repozytoria Gita na swoich serwerach. Najpopularniejsze z nich to:
- **[GitHub](https://github.com/)**
- **[GitLab](https://about.gitlab.com/)**
- **[BitBucket](https://bitbucket.org/)**

> Podczas kursu zostanie wykorzystany Github.
>Do celów edukacyjnych można korzystać z repozytoriów publicznych. Żeby uzyskać do nich dostęp wystarczy udostępnić link.
> Do celów komercyjnych można korzystać z repozytoriów prywatnych.

### Konfiguracja: klucze SSH

Publiczne repozytorium jest dostępne dla każdego wyłącznie **do odczytu**. W celu dodawania commitów niezbędna jest **autoryzacja**.

Żeby uniknąć każdorazowego wpisywania hasła, warto skonfigurować klucze SSH.

Klucze to specjalnie wygenerowane ciągi znaków, które będą przechowywane w dwóch plikach:
- id_ed25519.pub - plik dla **klucza publicznego**;
- id_ed25519 - plik dla **klucza prywatnego**;

Klucz publiczny może być przekazany każdemu. Służy do zaszyfrowania tesktu.
Klucz prywatny musi być przechowywany w tajemnicy. Służy do odszyfrowania tesktu.

#### Sprawdzenie, czy klucze SSH już istnieją

Sprawdzenie, czy na maszynie lokalnej znajdują się już wygenerowane wcześniej klucze SSH:

```markup
ls -al ~/.ssh
```

Jeśli wyświetli się błąd lub pusty katalog, klucze nie istnieją na komputerze.

Jeśli polecenie wyświetla pliki kluczy, klucze zostały już wcześniej utworzone i nie trzeba ich generować od zera.

#### Generowanie kluczy SSH

W pierwszej kolejności należy wywołać poniższą komendę, podająć w argumencie własny adres e-mail:
```markup
ssh-keygen -t ed25519 -C "adres@example.com"
```

Skrypt zapyta o docelową lokalizację dla utworzonych plików. Wciśnięcie `Enter` wybiera lokalizację domyślną.

W kolejnym kroku skrypt zapyta o hasło do klucza prywatnego. Wciśnięcie `Enter` zatwierdza puste hasło.

Ostatnim krokiem jest potwierdzenie hasła. W przypadku pustego hasła wystarczy wcisnąć `Enter`. W tym kroku zostanie wyświetlona lokalizacja kluczy na komputerze.

#### Konfiguracja kluczy SSH w GitHubie

Na stronie GitHub, po zalogowaniu, należy pokonać poniższą ścieżkę:

*GitHub ⇒ Ustawienia ⇒ Klucze SSH i GPG ⇒ Klucze SSH ==> Dodaj nowy klucz*

W polu **Tytuł** należy wprowadzić dowolną treść. Tytuł służy do rozróżnienia kluczy, kiedy jest dodana ich większa ilość.

W polu **Klucz** należy podać zawartość pliku z wygenerowanym wcześniej kluczem publicznym.

Po wszystkim wystarczy zatwierdzić dodanie nowego klucza.

### Zakładanie repozytorium na GitHubie

Każdy projekt powinien mieć własne repozytorium.

#### Konfiguracja w panelu GitHuba

Na stronie głównej GitHub należy wybrać opcję **Start a project**.

W wyświetlonym formularzu wystarczy wprowadzić nazwę nowego repozytorium bez automatycznego dodawania plików `README.md` oraz `.gitignore`.

Po zatwierdzeniu formularza wyświetli się ekran z komunikatami konfiguracyjnymi.

W pierwszej sekcji *Quick setup* należy zaznaczyć opcję **SSH**.

> Należy unikać sytuacji, w której podłącza się 2 repozytoria zawierającego wcześniej commity. Połączenie takich repozytoriów jest problematyczne.
>
> Należy trzymać się zasady, że jedno z dwóch repozytoriów powinno być puste przed podłączeniem.

#### Podłączanie repozytorium zdalnego do lokalnego

Polecenie `git remote add` ze wskazaną nazwą repozytorium dodaje zdalne repozytorium do lokalnego.

Polecenie `git remote -v` pozwala sprawdzić listę dodanych serwerów.

> Repozytorium lokalne może być synchronizowane z wieloma repozytoriami zdalnymi. Przyjęło się, że główne repozytorium zdalne w projekcie nazywa się *origin*.

Polecenie `git push -u origin master` przesyła dotychczasowe zmiany z repozytorium lokalnego do zdalnego.

Po pomyślnym przesłaniu zmian, commity powinny być widoczne po odświeżeniu repozytorium na GitHub.

#### Alternatywa do podłączania — klonowanie repozytorium

**Klonowanie** stosuje się tylko w przypadku, w którym istnieje repozytorium zdalne, ale nie istnieje repozytorium lokalne na komputerze.

Skopiowany adres repozytorium należy wkleić do komendy
```markup
git clone adres-repozytorium
```

Wywołanie komendy `git clone` skutkuje:
- utworzeniem katalogu projektu;
- zainicjowaniem repozytorium;
- dodaniem adresu zdalnego repozytorium;
- pobraniem zmian z serwera;

### Podłączanie repo — podsumowanie

<br>

**Nowy projekt - brak repozytorium - brak plików**
1. Nowe repozytorium na GitHub, można zaznaczyć dodatkowe opcje
2. Sklonowanie repozytorium do maszyny lokalnej
```markup
git clone adres-repozytorium
```

<br>

**Repozytorium istnieje na maszynie lokalnej**
1. Nowe (puste!) repozytorium na GitHub - tylko nazwa repozytorium
2. Podłączenie repozytorium zdalnego do lokalnego
```markup
git remote add origin adres-repozytorium
``` 
3. Wysłanie pierwszych commitów do repozytorium zdalnego
```markup
git push -u origin master
```

<br>

**Brak repozytorium lokalnego - istnieją pliki projektu na maszynie lokalnej**

1. Wykorzystanie pierwszego sposobu, przeniesienie plików do katalogu sklonowanego repozytorium
2. Zainicjowanie repozytorium w katalogu projektu `git init`, dodanie commita, wykorzystanie drugiego sposobu

### Podstawowe komendy Gita

#### Push, czyli wysyłamy nasze zmiany na zdalne repo

`git push` - wysłanie commitów do zdalnego repozytorium

`git remote add adres-repozytorium` - podłączenie adresu repozytorium zdalnego

`git push -u origin main/master` - pierwsze użycie komendy `push` po dodaniu repozytorium zdalnego

#### Pull, czyli pobieramy zmiany ze zdalnego repo

`git pull` - odwrotność komendy `push`, pobieranie zmian z repozytorium zdalnego

### Zadanie:  pierwsze repozytorium na GitHubie

**[Link do repozytorium wykonanego zadania](https://github.com/jerzy-jarczynski/nauka-gita.git)**

## 4.5.  NPM - rozpoczęcie pracy w projekcie

### Czym jest manager pakietów?

**Manager pakietów** - w zależności od potrzeby pozwala na dodawanie do projektu narzędzi wspomagających pracę. W przypadku narzędzi wymagających doinstalowania dodatkowych pakietów, manager samodzielnie dokona instalacji dodatkowych zależności.

Manager pakietów ułatwia pracę zespołową. Wystarczy współdzielić ten sam plik konfiguracyjny, żeby każdy developer miał dostęp do tych samych narzędzi do pracy nad projektem. W przypadku dołączania do projektu, taki plik wystarczy pobrać ze zdalnego repozytorium i wykonać jedną komendę służącą do instalacji.

W kursie korzysta się z managera pakietów **NPM** - NodeJS Package Manager.

Przykłady zastosowań dla narzędzi, które można zainstalować za pomocą NPM:
- sprawdzanie poprawności kodu;
- łączenie i minifikacja plików;
- wstawianie fragmentów kodu;
- dodawanie wymaganych prefiksów dla styli CSS;
- kasowanie niepotrzebnych plików np. pustych arkuszy styli;
- tworzenie paczki .zip projektu;
- automatyczne odświeżanie strony po zapisywaniu zmian w plikach;

### Czym jest task runner?

![image](https://uploads.kodilla.com/bootcamp/wdp/04/wd-7-1-11.png)

**Task runner** służy do uruchamiania wielu narzędzi za pomocą jednej komendy.
Task runner pozwala na przyspieszenie i automatyzację czynności, które muszą być wykonywane często.
W kursie, do stworzenia task runnera zostaną wykorzystane **skrypty NPM**.

### Alternatywne oprogramowanie

Alternatywy dla Gita: **SVN**, **Mercurial**
Alternatywne task runnery: **Grunt**, **Gulp**, **Webpack**

Wybór narzędzi jest kwestią preferencji programisty lub wymagań projektu.

### Instalacja Node.js

NPM jest częścią Node.js

`node -v` - sprawdza wersję Node.js, jeżeli jest zainstalowany.

**[Pakiet instalacyjny Node.js](https://nodejs.org/en/download)**

`sudo  npm  install npm@latest -g` - aktualizacja pakietu **npm**

### Inicjalizacja NPM-a w projekcie

W każdym projekcie należy jednorazowo nainicjować **NPM**.
```markup
npm init -y
```
Wynikiem wywołania powyższej komendy utworzy domyślny plik konfiguracyjny `package.json` w głównym katalogu projektu.

Plik zawiera informacje między innymi o zainstalowanych pakietach.

### Dodajemy plik .gitignore

Plik **`.gitignore`** służy do wskazywania plików, które nie mają być przesyłane do zdalnego repozytorium.

Do utworzenia tego pliku można wykorzystać udostępniony bezpłatnie przez GitHub szablon:

https://github.com/github/gitignore/blob/main/Node.gitignore

Komenda do utworzenia pliku:
```markup
touch .gitignore
```

### Instalujemy pierwszy pakiet — BrowserSync

BrowserSync to pakiet, który obserwuje zmiany wprowadzane do projektu i automatycznie odświeża podgląd strony w przeglądarce.

Instalacja:
```markup
npm install --save-dev browser-sync
```

Efektem będzie instalacja pakietu i dodanie wpisu do `package.json` w sekcji *dependencies*.
To umożliwi instalacje tego pakietu przez innego developera po dołączeniu do projektu.

### BrowserSync — pierwsze uruchomienie

Uruchomienie BrowserSync:
```markup
node_modules/.bin/browser-sync start --server --files "css/*.css" "*.html"
```

BrowserSync otworzy podgląd w domyślnej przeglądarce pod adresem `http://localhost:3000/`. Numer portu może być inny.

Uruchomiony BrowserSync umożliwia dodatkowy adres, który umożliwia podgląd projektu na innych urządzeniach połączonych do tej samej sieci.

### Zadanie:  instalacja i uruchamianie pakietów

[html-validate](https://html-validate.org/usage/index.html) - paczka sprawdzająca poprawność kodu HTML

## 4.6.  NPM - budujemy własny task runner

W task runnerze definiuje się różne scenariusze nazywane taskami. Najczęściej spotykanymi są:
- `build` - konwersja plików źródłowych na te, które zostaną wykorzystane w wersji do publikacji. 
- `watch` - obserwowanie zmian i wykonywanie potrzebnych operacji w locie.
- `test` - sprawdzanie poprawności kodu.

Każdy task może uruchamiać również inne taski i składać się z podtasków np. `test:html` itp.

### Struktura task runnera

- `init-project`
	- instalacja niezbędnych pakietów
	- stworzenie pożądanej struktury katalogów
	- stworzenie pliku `README.md`
	- stworzenie pustych plików startowych
	- pobranie i umiejscowienie pliku `.gitignore`
- `test`
	- sprawdzanie poprawności kodu
-  `build`
	- konwersja `.scss` do `.css`
	- uruchomienie *Autoprefixera*
	- minifikacja `.css`
	- przetestowanie poprawności kodu
- `watch`
	- kompilowanie `.scss` do `.css` w locie
	- dodawanie prefiksów w `.css`
	- odświeżanie przeglądarki po zmianach w plikach projektu

Task runner będzie umiejscowiony w pliku `package.json` w sekcji `scripts`.

### Task 1: inicjalizacja projektu

#### Instalacja niezbędnych pakietów

Dołączając do istniejącego projektu nie należy wywoływać komendy `npm init -y`. W zamian wystarczy wywołać `npm install`, żeby zainstalować wszystkie pakiety wylistowane w pliku `package.json`.

Dodawanie taska `init-project`:
```json
"init-project": "npm install"
```

#### Stworzenie katalogów

Do stworzenia katalogów można wykorzystać **[pakiet mkdirp](https://www.npmjs.com/package/mkdirp)**.
Uchroni to przed nadpisywaniem plików w projekcie.

Instalacja `mkdirp`:
```markup
npm install mkdirp --save-dev
```

Utworzenie subtaska `init:dirs`:
```json
"init:dirs": "mkdirp sass css vendor images js"
```

Na potrzeby innych projektów lista utworzonych w ten sposób katalogów może być inna od powyższej.

#### Stworzenie plików

Dodanie subtaska `init:files` w celu uniknięcia dodawania plików startowych ręcznie w projekcie:
```json
"init:files": "touch README.md index.html sass/style.scss js/script.js"
```

#### Pobranie pliku .gitignore

Pobranie pliku `.gitignore` za pomocą komendy `curl` z zasobów internetowych <- [szablon GitHub]:(https://github.com/github/gitignore/blob/master/Node.gitignore)

```json
"init:gitignore": "curl https://raw.githubusercontent.com/github/gitignore/master/Node.gitignore -o .gitignore"
```

> flaga `-o` w komendzie `curl` pozwala na nadawanie dowolnej nazwy dla pobranego pliku.

#### Składając wszystko w całość

Subtaski mogą uruchamiać się sekwencyjnie (jeden po drugim). Dla takiego zachowania task runnera można zastosować łącznik `AND` pod postacią operatora `&&`.

Wywołanie subtasków w tasku `init-project`:
```json
"init-project": "npm install && npm run init:dirs && npm run init:files && npm run init:gitignore"
```

> Subtaski uruchamia się za pomocą komendy `npm run nazwa-taska`

#### Optymalizacja taska

W celu zbiorczego wywoływania subtasków można posłużyć się pakietem **[npm-run-all](https://www.npmjs.com/package/npm-run-all)**.

Instalacja:
```markup
npm install npm-run-all --save-dev
```

Zastosowanie w `package.json`:
```json
"init-project": "npm install && npm-run-all init:*",
```

> Istostne jest wywołanie `npm install` w pierwszej kolejności w celu doinstalowania potrzebnych paczek przed wywołaniem subtasków za pomocą pakietu `npm-run-all`.

### Task 2: testowanie plików

Walidację HTML można osiągnąć korzystając z pakietu [html-validate](https://www.npmjs.com/package/html-validate).

Dodanie subtaska `test:html`:
```json
"test:html": "html-validate *.html"
}
```
> Modyfikując plik `package.json` należy mieć na uwadze przecinki. Po każdym elemencie zbioru. Przecinka nie stawia się po **ostatnim** elemencie zbioru.

### Task 3: generowanie wersji produkcyjnej

#### Kompilacja .scss do .css i minifikacja

Instalacja pakietu **[sass](https://www.npmjs.com/package/sass)** do automatycznej konwersji `.scss` do `.css`.
```markup
npm install sass --save-dev
```

Subtask:
```json
"build:sass": "sass --style=compressed --no-source-map sass:css"
```

> Flaga `--style` z wartością `compressed` odpowiada za minifikację pliku `.css` po konwersji.

#### Uruchomienie Autoprefixera

Potrzebne pakiety:
- `PostCSS` - łatwa modyfikacja plików `.css`
- `PostCSS-cli` - modyfikacja z poziomu terminala
- `Autoprefixer` - dodawanie wymaganych prefixów do `.css`

Instalacja zbiorcza:
```markup
npm install autoprefixer@10.2.4 postcss-cli@8.3.1 postcss@8.2.6 --save-dev
```

Subtask:
```json
"build:autoprefixer": "postcss css/*.css --use autoprefixer -d css"
```

Wywołanie komendy znajduje wszystkie pliki z rozszerzeniem `.css` i wykonuje na nich narzędzie `autoprefixer`. Zmieniona wersja zastępuje pliki wejściowe.

#### Budujemy  `build`

Utworzenie tasku `build` z wywołaniem tasku `test`:
```json
"build": "npm-run-all build:* test"
```

#### Dodatkowy task  `build-dev`

> **Source map** - mapa źródeł może być tworzona w momencie generowania pliku `.css` za pomocą prekompilatora.
> Source map może zawierać informacje o tym, skąd pochodzi dana wygenerowana linijka w pliku `.scss`, co można zweryfikować w narzędziach deweloperskich przeglądarki.

Subtask:
```json
"build-dev:sass": "sass --style=expanded --source-map sass:css"
```

Wywoałanie tego subtaska utworzy pliki `.css` w wersji deweloperskiej z mapami źródeł.

### Task 4: bieżąca praca nad projektem

#### Odświeżanie przeglądarki

Utworzenie subtaska z wykorzystaniem pakietu **BrowserSync**:
```json
"watch:browsersync": "browser-sync start --server --files \"css/*.css\" \"*.html\""
```

#### Kompilacja Sassa i Autoprefixer

Instalacja pakietu **[OnChange](https://www.npmjs.com/package/onchange)** do śledzenia zmian. Autoprefixer domyślnie nie posiada takiej funkcji.
```markup
npm install onchange --save-dev
```

Utworzenie subtaska do uruchamiania pakietu OnChange. Po będą uruchamiane kompilator Sass, następnie Autoprefixer.
```json
"watch:sassprefixer": "onchange sass/*.scss -- npm run build-dev"
```

#### Budujemy task  `watch`

Wywołanie taska `watch` rozpoczyna wywołania `build` zawierającego `test`. Takie postępowanie to dobra praktyka, dzięki której błędy zostaną pokazane przed rozpoczęciem pracy nad projektem, a nie po.
```json
"watch": "npm-run-all build build-dev -p watch:*"
```

### Podsumowanie

Pełny kod `package.json` utworzonego na potrzeby pracy z HTML, CSS i JS na tym etapie:
```json
{
  "name": "taskrunner",
  "version": "1.0.0",
  "description": "",
  "main": "index.html",
  "scripts": {
    "init-project": "npm install && npm-run-all init:*",

    "init:dirs": "mkdirp sass css vendor images js",
    "init:files": "touch README.md index.html sass/style.scss js/script.js",
    "init:gitignore": "curl https://raw.githubusercontent.com/github/gitignore/master/Node.gitignore -o .gitignore",

    "test": "npm run test:html",
    "test:html": "html-validate *.html",

    "build": "npm-run-all build:* test",
    "build:sass": "sass --style=compressed --no-source-map sass:css",
    "build:autoprefixer": "postcss css/*.css --use autoprefixer -d css",

    "build-dev": "npm-run-all build-dev:sass build:autoprefixer",
    "build-dev:sass": "sass --style=expanded --source-map sass:css",

    "watch": "npm-run-all build build-dev -p watch:*",
    "watch:browsersync": "browser-sync start --server --files \"css/*.css\" \"*.html\"",
    "watch:sassprefixer": "onchange sass/*.scss -- npm run build-dev"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {},
  "devDependencies": {
    "browser-sync": "^2.26.3",
    "mkdirp": "^0.5.1",
    "sass": "^1.44.0",
    "npm-run-all": "^4.1.5",
    "html-validate": "^2.8.0",
    "onchange": "^5.2.0",
    "autoprefixer": "^10.2.4",
    "postcss-cli": "^8.3.1",
    "postcss": "^8.2.6"
  }
}
```

### Zadanie:  projekt z task runnerem

**[Link do wykonanego projektu na GitHub](https://github.com/jerzy-jarczynski/task-runner-project.git)**

## 4.7.  Podsumowanie

### Pogłębianie znajomości Gita

-   [Learn Version Control with Git](https://www.git-tower.com/learn/git/ebook/en/command-line/introduction)  – przystępnie napisany ebook dla początkujących
-   [Git Guide](https://backlog.com/git-tutorial/)  – mnóstwo przydatnych wskazówek, które pomogą Ci w pracy samodzielnej i grupowej
-   [Git for beginners: 12 commands you need to know](https://blog.prototypr.io/git-for-beginners-12-commands-you-need-to-know-e084cce9cc94)  – przystępne omówienie najbardziej podstawowych komend Gita
-   [Learn Git branching](https://learngitbranching.js.org/)  – interaktywne narzędzie pozwalające lepiej zrozumieć, jak działają branche
-   [Git Cheatsheet](https://education.github.com/git-cheat-sheet-education.pdf)  – przygotowana przez GitHuba ściągawka, zawierająca podstawowe komendy Gita
