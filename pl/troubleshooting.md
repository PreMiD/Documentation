---
title: Rozwiązywanie problemów
description: Wszystko, by rozwiązać twój problem
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:17:32.312Z
---

> Upewnij się, że masz zainstalowane rozszerzenie **i** aplikacji! 
> 
> {.is-warning}

Zawarte na tej stronie:
1. [Ogólne rozwiązywanie problemów](https://docs.premid.app/troubleshooting#general)
2. [Rozwiązywanie problemów na Linux](https://docs.premid.app/troubleshooting#linux)
3. [Rozwiązywanie problemów na MacOS](https://docs.premid.app/troubleshooting#macos)

<a name="general"></a>

# Ogólne rozwiązywanie problemów
### Odśwież stronę
Możesz również nacisnąć <kbd>CTRL + R</kbd>/<kbd>F5</kbd> (Windows) lub <kbd>CMD + R</kbd> (MacOS) na klawiaturze zamiast szukać przycisku odświeżania.

### Czy używasz aplikacji Discord?
PreMiD **nie** działa w wersji przeglądarkowej Discorda, musisz pobrać aplikację [tutaj](https://discord.com/download).

### Upewnij się, że w ustawieniach włączono Discord Game Activity
**Ustawienia użytkownika** > **Aktywność w grze**
<img src="https://i.imgur.com/9SfrrWm.png" width="500px" style="max-width:100%;" />

### Upewnij się, że Discord NIE działa jako administrator
Naprawdę ważne. RPC Discorda nie zadziała, jeśli uruchomisz Discorda jako administrator.

### Czy używasz aktywności z ustawieniami?
Wiele aktywności (w tym `Twitch` i `SoundCloud`) jest dotkniętych przez problem rozszerzenia. Powoduje on, że rozszerzenie nie przechwytuje domyślnych wartości ustawień.

Aby rozwiązać ten problem, wystarczy przełączyć najwyższe ustawienie:
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### Uruchom ponownie przeglądarkę
<kbd>Alt</kbd>+<kbd>F4</kbd> (Windows) lub <kbd>CMD</kbd>+<kbd>Q</kbd> (MacOS) również dobrze się spisuje. (Oczywiście musisz uruchomić ponownie swoją przeglądarkę.)

### Uruchom ponownie PreMiD (aplikacja)
<img src="https://i.imgur.com/g3ShdnU.png" width="500px" style="max-width:100%;" />
Następnie uruchom ponownie PreMiD.

### Odśwież/uruchom ponownie Discorda
Naciśnij klawisze <kbd>CTRL + R</kbd> (Windows) lub <kbd>CMD + R</kbd> (MacOS) na klawiaturze albo ręcznie uruchom ponownie Discorda.

### Sprawdź czy masz uruchomiony program antywirusowy lub zaporę sieciową na swoim komputerze
Czasami programy antywirusowe i zapory blokują aplikacje, które tworzą lub hostują serwery lub po prostu łączą się z Internetem. Używamy lokalnego serwera do odbierania i przekazywania danych między naszą aplikacją i rozszerzeniem, więc jeśli zablokujesz zdolność aplikacji do przekazywania danych, prawdopodobnie nie będziesz mógł użyć PreMiD.

### Wyłącz dodatki
Wyłącz wszystkie dodatki i sprawdź, czy działa. Jeśli tak, spróbuj włączyć swoje dodatki krok po kroku i powiedz nam, który dodatek zepsuł PreMiD.

### Uruchom ponownie komputer
Mam nadzieję, że wiesz jak uruchomić ponownie komputer.

### Ponowna instalacja PreMiD
Czasami jest coś nie tak z plikami... Poradniki dotyczące instalacji można znaleźć [tutaj](/install).

### Ręczne usuwanie
Windows: Napisz `%appdata%` w eksploratorze plików i usunć folder `PreMiD`. MacOS:`~/users/USER/~Library/Application Support/`i usuń katalog `PreMiD``.

### McAfee wykrył PreMiD jako wirus (Windows)
Jest to fałszywy alarm ze strony McAfee i zgłosiliśmy im ten problem, na razie możesz wykluczyć PreMiD ze skanowania, wykonując następujące kroki:

> Jeżeli nie czujesz się dzielny podczas podejmowania podanych kroków, utwórz bilet na [#support](https://discord.premid.app/) i jeden z naszych Agentów Pomocy będzie Ci w stanie pomóc! 
> 
> {.is-warning}

1. Otwórz aplikację McAfee i kliknij ikonę ustawień w prawym górnym rogu. <img src="https://i.imgur.com/rPLZn6c.png" width="500px" style="max-width:100%;" />
2. Kliknij "Elementy w kwarantannie" (drugi od góry).
3. Rozwiń i kliknij ikonę `>` przed elementem o nazwie "settings.dat".
4. Upewnij się, że ścieżka zawiera "AppData\Local\Temp\PreMiD", jeśli tak, wybierz ją i naciśnij "Przywróć". <img src="https://i.imgur.com/9nvHmiI.png" width="500px" style="max-width:100%;" />
5. Po przywróceniu możesz zamknąć wyskakujące okno "Elementy w kwarantannie", a następnie ponownie naciśnij ikonę ustawień w prawym górnym rogu.
6. Kliknij "Skanowanie w czasie rzeczywistym" (Trzecie od góry).
7. Rozwiń i kliknij "Dodaj plik".
8. Wpisz "%appdata%" w pasku adresu URL menedżera plików i naciśnij Enter. <img src="https://i.imgur.com/2bchwLe.png" width="500px" style="max-width:100%;" />
9. Otwórz folder "PreMiD", wybierz plik "PreMiD.exe" i kliknij przycisk Otwórz. <img src="https://i.imgur.com/aHOyv3V.png" width="500px" style="max-width:100%;" />
10. McAfee powinno teraz ignorować nasz plik. Po prostu uruchom aplikację i wszystko powinno być gotowe.

### Status PreMiD buguje się na Discord
Nie martw się. Naciśnij skrót klawiszowy <kbd>CTRL+R</kbd> (Windows) lub <kbd>CMD+R</kbd> (MacOS) skupiając się na oknie Discord by go odświeżyć.

<a name="linux"></a>

# Rozwiązywanie problemów na Linux
### Dystrybucje oparte na Ubuntu/Debian
Jeśli pobrałeś Discorda przez Snapcraft, RPC nie będzie działać. Musisz odinstalować wersję Snapcraft wykonując polecenie `sudo snap remove discord` w terminalu, pobierz **[Discord w wersji na Linux](https://discordapp.com/api/download?platform=linux)** (**[lub Discord Canary](https://discordapp.com/api/canary/download?platform=linux)**), następnie przejdź do katalogu do którego pobrałeś Discord (często `$HOME/Pobrane`), następnie zainstaluj pakiet używając `sudo dpkg -i discord*.deb`. Jeżeli AppImage nie działa, należy rozważyć sprawdzenie naszych innych pakietów przez **[ten link](https://packagecloud.io/premid/linux)**.

### Dystrybucje oparte na Arch Linux
Dystrybucje oparte na Arch Linux powinny używać pakietu AUR (Arch User Repository) o nazwie <code>premid</code> lub <code>premid-git</code> (<em x-id="3">OSTRZEŻENIE: To repozytorium buduje PreMiDa z kodu źródłowego</em>). Jeśli nie chcesz instalować menadżera AUR (yay itd.), możesz sprawdzić AppImage który pobierany jest z naszego <strong x-id="1"><a href="https://github.com/premid/linux/releases">Repozytorium Linux</a></strong>.
<em x-id="3">Ostrzeżenie: pakiet w repozytorium <strong x-id="1">AUR</strong> nie jest utrzymywany przez nas (jako organizację PreMiD), ale przez innych ludzi.</em>

### Przydzielanie portów
Powinieneś wiedzieć, że <strong x-id="1">PreMiD</strong> łączy się z portem <strong x-id="1">3020</strong>. Jest to konieczne do komunikacji między Rozszerzeniem a Aplikacją. Jeżeli <strong x-id="1">PreMiD</strong> wyświetla błąd na temat tego portu, powinieneś sprawdzić czy coś innego nie jest powiązane z portem 3020 uruchamiając <code>sudo lsof -i:3020</code> lub <code>sudo netstat -tnlp | grep :3020</code> w terminalu. Jeśli jakiż proces jest do niego powiązany, powinieneś upewnić się by zwolnić ten port i spróbować uruchomić ponownie <code>PreMiD</code>.

### PreMiD AppImage nie uruchamia się przy logowaniu
Jak stwierdziliśmy w naszym **repozytorium Linux**, AppImage nie może być uruchamiane przy logowaniu. Możesz dodać go ręcznie do autostartu wykonując te kroki:
1. Utwórz plik o nazwie <strong x-id="1">rc.local</strong> w katalogu <code>/etc</code>.
2. Otwórz plik w twoim ulubionym edytorze i wklej podany kod zmieniając kilka rzeczy:
```bash
#!/bin/bash
# Wymagane aby było uruchomione za pomocą /bin/bash (jeśli używasz zsh itp. możesz to zmienić.)

# Na przykład: /home/PreMiD/PreMiD*.AppImage
<ścieżka do appimage>/PreMiD*.AppImage

exit 0
```
3. Zapisz plik i zaznacz go jako plik wykonywalny za pomocą `sudo chmod a+x /etc/rc.local`.
4. Uruchom ponownie komputer i PreMiD AppImage powinien zostać uruchomiony po zalogowaniu.

<a name="macos"></a>

# Rozwiązywanie problemów na MacOS
### Błąd podczas tworzenia katalogu
<img src="https://i.imgur.com/td92lf6.png" width="300px" style="max-width:100%;" />

Jeżeli widzisz ten błąd, znaczy to, że twoje konto nie posiada uprawnień Administratora, i musisz utworzyć folder manualnie poprzez wykonanie nastepujących kroków:
1. Otwórz wyszukiwanie folderów i otwórz **Aplikacje**.
2. Kliknij prawym przyciskiem myszy na puste miejsce i kliknij **Stwórz folder**.
3. Przypisz nazwę `PreMiD` do tego folderu (nie zapomnij o dużych literach).
4. Uruchom instalator ponownie.

# To nie rozwiązało mojego problemu
Prosimy otworzyć zgłoszenie w [#support](https://discord.premid.app/).
