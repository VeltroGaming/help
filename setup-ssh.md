# Veltro SSH Tutorial

Da Sicherheit bei uns an erster Stelle steht, ist das anfängliche Einrichten
einer SSH-Verbindung anfangs vielleicht ein bisschen komplizierter, aber das ist
kein Problem. Dafür gibt's ja dieses Tutorial.

Wir nehmen in diesem Tutorial an, dass du **Windows 7 / 8 / 10** benutzt.
Ein Linux User würde sicherlich kein Tutorial brauchen. :wink:


### 1. PuTTY installieren

Um dich per SSH mit unserem Server zu verbinden, benötigst du zuerst einen SSH
Client. Wir empfehlen **PuTTY**.

Lade dir PuTTY bitte nur direkt von der [Entwickler-Website][1] herunter.
Wähle den PuTTY Windows *Installer* aus oder klicke einfach hier:
[`putty-0.66-installer.exe`][2]

[1]: http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html
[2]: http://the.earth.li/~sgtatham/putty/latest/x86/putty-0.66-installer.exe

Führe den Installer aus und installiere PuTTY. Ändere nichts an den
Einstellungen und klicke einfach immer auf `Next >` und am Ende auf `Install`.

Nach Abschluss der Installation entferne das Häkchen bei `View README.txt` und
klicke `Finish`.

Happy Birthday, du hast ein Programm installiert. :tada:


### 2. FileZilla installieren

Da du sicherlich auch Datein transferieren möchtest, solltest du auch einen
SFTP-Client habe. Wir empfehlen **FileZilla**.

Lade dir FileZilla bitte nur direkt von der [Entwickler-Website][3] herunter.

[3]: https://filezilla-project.org/download.php?show_all=1

Führe den Installer aus und installiere FileZilla.


### 3. Einen SSH-Key erzeugen

Jetzt musst du dir einen SSH-Key erzeugen. Starte hierzu das Programm
**PuTTYgen**.

Ersetze unten rechts die `2048` durch `4096`. Klicke dann auf `Generate`.
Jetzt musst du solange im Fentser die Maus bewegen, bis der Fortschritssbalken
einmal durchgelaufen ist. Dadurch werden Zufallswerte erzeugt.

Nach dem zweiten Durchlauf werden nun mehrere neue Felder angezeigt.

Führe folgende Änderungen durch:

* `Key comment`: Hier deinen vollen Namen einfügen.
* Setze nur eine Passphrase, wenn du nicht vorhast FileZilla zu benutzen.
  Im Zwefeilsfall, setze keine Passphrase.

Klicke jetzt `Save private key`. Speichere den Key an einem Ort, wo du ihn
leicht wiederfindest, aber er dich nicht stört und aus Versehen gelöscht wird.
Dein Benutzerordner ist ein guter Platz.

Gib dem Key einen aussagekräftigen Namen ohne Leerzeichen.
`Veltro` wäre eine Möglichkeit.

Nach dem Speichern, mach einen Rechtsklick in das große Textfeld, in dem so
etwas wie `ssh-rsa AAAAB3Nza...` steht, und klicke `Alle auswählen`. Dann noch
ein Rechtsklick und dann `Kopieren`.

Schicke diesen Public Key (`Ctrl + V`) an den Admin, der deinen Account
einrichtet. Nutze hierzu bitte [GitHub Gist][4] und schicke ihm die URL.

[4]: https://gist.github.com/


### 4. PuTTY konfigurieren

Setze folgende Einstellungen:

##### Connection

* Setze `Seconds between keepalives` auf `300` (5 Minuten)
* Setze einen Haken bei `Enable TCP keepalives`

##### Connection > SSH > Auth

* Wähle über den Button `Browse` den gerade erstellten SSH Key aus.

##### Session

* Trage in das Feld `Host Name (or IP address)` die Adresse ein, die wir dir
  zugewiesen haben. Sie sieht wahrscheinlich ähnlich aus wie `abcdef.veltro.de`.

* Trage bei `Saved Sessions` einen Namen für diese Konfiguration ein. Wie wär's
  mit `Veltro`?

* Klicke auf `Save`.

Mit einem Klick auf `Open` sollte sich nun eine SSH Session öffnen.


### 5. FileZilla konfigurieren

##### Bearbeiten > Einstellungen > Verbindung > SFTP

* `Schlüsseldatei hinzufügen`: Wähle hier deinen SSH Key aus.

##### Bearbeiten > Einstellungen > Oberfläce

* Setze einen Haken bei `Servermanager bei Programmstart anzeigen`.

Schließe den Einstellungs-Dialog indem du unten links auf `OK` klickst.

##### Datei > Servermanager oder Ctrl + S

1. Klicke auf `Neuer Server`.

2. Benenne ihn sinnvoll. `Veltro` vielleicht?

3. Setze im rechten Fenster folgende Einstellungen:

  * **Server:** Die Adresse, die wir dir zugeteilt haben. So ähnlich wie
    `abcdef.veltro.de`.

  * **Protokoll:** `SFTP - SSH File Transfer Protocol`

  * **Verbindungsart:** `Normal`

  * **Benutzer:** `dein-username-hier`

  * **Passwort:** frei lassen

4. Klicke auf `Verbinden`.

Du solltest dich nun erfolgreich verbinden können.


## Probleme?

* Hat dein betreuender Admin dir eine Bestätigung gegeben, dass dein Key auf dem
  Server installiert wurde?

* Stelle sicher, dass du tatsächlich jeden Schritt korrekt ausgeführt hat.

* Immer noch Probleme? Installiere oder starte [TeamViewer][5]
  ([`TeamViewer_Setup_de.exe`][6]). Schicke deine ID und dein Kennwort an den
  Admin, so dass er sich auf deinen PC verbinden kann.

[5]: https://www.teamviewer.com/de/download/windows.aspx
[6]: http://download.teamviewer.com/download/TeamViewer_Setup_de.exe
