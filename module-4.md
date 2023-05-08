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
