# Astro-Logbuch – Setup

Dieses Paket enthält:

- **`index.html`** – die komplette App (Dark Mode, Übersicht, neue Sessions, Sternkarte, Doku). Alles in einer Datei, läuft ohne Server.
- **`data.json`** – deine Datenbank (34 Objekte, 66 Sessions aus deinen Screenshots, inkl. Katalogdaten und ⚠️-Markierungen für unklare Altdaten).

Ein dritter Bestandteil kommt automatisch hinzu, sobald du zu einer Session ein Foto hinzufügst: ein Ordner **`images/`** mit den (automatisch komprimierten) Astrofotos – die App legt ihn beim ersten Foto-Upload selbst im Repo an, kein manueller Schritt nötig.

## 1. GitHub-Repository anlegen

1. Auf [github.com](https://github.com) einloggen → oben rechts **+** → **New repository**.
2. Name z.B. `astro-logbuch`. Sichtbarkeit: **Public** wählen – GitHub Pages (Schritt 3) funktioniert im kostenlosen Plan nur mit öffentlichen Repos; ein privates Repo bräuchte GitHub Pro/Team. Bei einem öffentlichen Repo sind Beobachtungsorte/Ausrüstung/Fotos für jeden mit dem Link einsehbar, dafür aber ohne Zusatzkosten.
3. Repository erstellen (ohne README, ohne .gitignore – einfach leer).

## 2. Dateien hochladen

1. Im neuen Repo auf **„Add file" → „Upload files"** klicken.
2. `index.html` und `data.json` per Drag&Drop hochladen.
3. Commit-Message eingeben, **„Commit changes"**.

## 3. GitHub Pages aktivieren

1. Im Repo auf **Settings → Pages**.
2. Unter „Build and deployment" → **Source: Deploy from a branch**.
3. Branch: `main`, Ordner: `/ (root)` → **Save**.
4. Nach ca. 1 Minute ist die Seite erreichbar unter:
   `https://DEIN-BENUTZERNAME.github.io/astro-logbuch/`
5. Diesen Link auf dem Handy zum Homescreen hinzufügen (Safari/Chrome → „Zum Home-Bildschirm") für App-artiges Öffnen.

## 4. Automatischen Sync einrichten (Desktop ↔ Handy)

Damit neue Einträge auf beiden Geräten sichtbar sind, braucht die App Schreibrechte auf dein Repo:

1. Auf GitHub: **Profilbild → Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token**.
2. **Repository access**: „Only select repositories" → dein `astro-logbuch` Repo auswählen.
3. **Permissions → Repository permissions → Contents: Read and write**.
4. Token generieren, **einmalig kopieren** (wird danach nicht mehr angezeigt).
5. In der App: ⚙️-Symbol oben rechts → GitHub-Benutzername, Repo-Name, Branch (`main`) und den Token eintragen → **„Verbindung testen"** → **„Speichern"**.
6. Das Gleiche auf dem Handy wiederholen (gleicher Token oder ein zweiter Token für dasselbe Repo).

Ab jetzt wird jede neue Session automatisch als Commit in `data.json` gespeichert, und beim Öffnen der App wird immer der aktuelle Stand von GitHub geladen.

**Sicherheitshinweis:** Der Token liegt nur lokal im Browser-Speicher (`localStorage`) deines Geräts und wird ausschließlich an `api.github.com` gesendet. Bei gemeinsam genutzten/öffentlichen Rechnern den Token danach über „Token entfernen" in den Einstellungen löschen. Tokens lassen sich jederzeit über GitHub widerrufen.

## 5. Ohne GitHub-Sync nutzen

Die App funktioniert auch ganz ohne Token – dann bleiben neue Einträge nur im Browser-Speicher des jeweiligen Geräts. Über **⚙️ → „data.json exportieren"** lässt sich der aktuelle Stand jederzeit als Datei herunterladen und manuell im Repo ersetzen (z.B. per Drag&Drop auf GitHub), um Geräte zu synchronisieren.

## 6. Sternkarte / AR-Kamera

- Die 2D-Sternkarte funktioniert überall (auch Desktop), sobald ein Standort gesetzt ist (📍-Button oder Standard Berlin).
- Die AR-Kamera-Ansicht braucht **HTTPS** (bei GitHub Pages automatisch gegeben) sowie Kamera- und Bewegungssensor-Zugriff – funktioniert nur auf Smartphones, nicht am Desktop. Beim ersten Öffnen fragt der Browser nach Erlaubnis für Kamera und (auf iOS) „Bewegung & Ausrichtung".
- Die Positionsberechnung ist kompassbasiert und eine Näherung (siehe „Doku"-Button in der App, Abschnitt 9) – für eine grobe Orientierung gedacht, nicht für präzises Teleskop-Pointing.

## 7. Offene Prüfpunkte in den Altdaten

Beim Import der Screenshots waren einige Ordnernamen unklar oder abgeschnitten (u.a. Mond-Belichtungswerte, das Auriga-Mosaik, zwei NGC-7000-Sessions, ein zweinächtiger IC-405-Ordner, sowie RA/Dec für WASP-33 b, XO-1 b und die Kometenposition). Diese sind in der App mit ⚠️ „zu prüfen" markiert (Filter-Chip „⚠️ Zu prüfen" in der Übersicht) inkl. Erklärung, was genau zu prüfen ist. Am besten einmal durchgehen und bei Gelegenheit korrigieren/ergänzen.
