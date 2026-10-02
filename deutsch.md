# Index

* [Erforderliche Elemente](#erforderliche-elemente)
* [Beschädigte Daten identifizieren](#beschädigte-daten-identifizieren)
* [So entfernen Sie beschädigte Daten](#so-entfernen-sie-beschädigte-daten)
* ["Die übliche Lösung"](#die-übliche-lösung)
* [Datenbeschädigung verhindern](#datenbeschädigung-verhindern)
* [Weitere Ressourcen](#weitere-ressourcen)

> **Erstellen Sie eine vollständige Sicherung Ihrer Speicherdateien, bevor Sie einen dieser Schritte durchführen!**

---

# Erforderliche Elemente

## Steam Workshop Mods-Ordner (Workshop Mods)

* Kann durch Klicken auf das Ordnersymbol bei einem Steam Workshop-Mod im Paralives-Mod-Menü aufgerufen werden.
* Durch Navigieren zu:

**Windows:**

```text
C:\Program Files (x86)\Steam\steamapps\workshop\content\1118520\
```

**Mac:**

```text
~/Library/Application Support/Steam/steamapps/workshop/content/1118520
```

## Paralives-Ordner (Lokale Mods)

* Kann durch Klicken auf das Ordnersymbol bei einem lokalen Mod im Paralives-Mod-Menü aufgerufen werden.
* Durch Navigieren zu:

**Windows:**

```text
C:\Users\USER\AppData\LocalLow\Paralives\Paralives
```

**Mac:**

```text
~/Library/Application Support/com.Paralives.Paralives/
```

## Paralives\Player.Log

* Kann mit jeder Software zum Lesen von Textdateien wie Notepad oder Notepad++ gelesen werden.
* Befindet sich im Paralives\Paralives-Ordner.
* Liefert Protokolle für die aktuelle oder zuletzt gespielte Paralives-Sitzung.

## Paralives\MySavedGames.mod-Ordner

* Ordner, der alle aktuellen Speicherstände und automatischen Speicherungen enthält.
* Befindet sich im Paralives\Paralives-Ordner.
* Dieser Ordner ist wichtiger als jeder andere.
* Bitte erstellen Sie regelmäßig eine vollständige Kopie dieses Ordners und speichern Sie sie an einem sicheren Ort außerhalb der Spieldateien!

## Paralives\MyPremadeHouseholds.mod-Ordner

* Haushalte, die in der Bibliothek gespeichert wurden.

## Paralives\MyPremadeLot.mod-Ordner

* Grundstücke, die in der Bibliothek gespeichert wurden.

## Paralives\MyPremadeOutfits.mod-Ordner

* Outfits, die in der Bibliothek gespeichert wurden.

## Paralives\Local.mod und 0.mod-Ordner

* Speichert Spieleinstellungen wie benutzerdefinierte Farbfelder.

---

# Beschädigte Daten identifizieren

Beschädigte Daten bestehen aus Dateien, die so verändert wurden, dass sie nicht mehr in der Form oder Reihenfolge vorliegen, die das Spiel erwartet.

## Veraltete Dateien

* Das Spiel wurde aktualisiert und diese Dateien entsprechen nicht mehr der aktuellen Syntax.
* Während dies gelegentlich bei Mods vorkommen kann, werden fast alle BepInEx-Code-Injection-Plugins nach einem Spiel-Update veraltet.
* Wenn ein BepInEx-Plugin installiert ist, Mods aber weiterhin nicht funktionieren, kann das Plugin mehr Schaden als Nutzen verursachen.

## Unsachgemäß geänderte Dateien

* Diese wurden von einem Spieler, Modder oder sogar der Game Engine geändert und sind nun fehlerhaft.
* Dies kann passieren, wenn Mods oder Plugins verwendet und anschließend entfernt wurden.

Zum Beispiel ein Mod, der verwendet wurde, um ein benutzerdefiniertes Outfit hinzuzufügen, und anschließend entfernt wird, während das Outfit weiterhin in den Spieldateien identifiziert wird.

Es kann unmöglich sein, einige Mods zu entfernen, ohne eine Speicherdatei zu beschädigen.

## Unsachgemäß verschobene Dateien

* Dateien werden häufig vom Spieler, der Game Engine oder Steam verschoben, wobei Teile der Datei zurückbleiben oder gelöscht werden.

## Wie teilt mir das Spiel mit, welche Dateien beschädigt sind?

Die Game Engine versucht, den Benutzer bei einem Fehler durch direkte und indirekte Benachrichtigungen darauf hinzuweisen.

### Direkt:

* Popups auf dem Bildschirm
* Benachrichtigungen in der Konsole
* Ereignisse in der player.log

### Indirekt:

* Flackern
* Blinken
* Ruckeln
* Verzögerungen
* Abstürze
* Abgebrochene Vorgänge

## Fehlerkonsole und Player.Log lesen

Die Berichte der Fehlerkonsole und der player.log überschneiden sich nur teilweise. Daher ist es wichtig, beide zu überprüfen, wenn Sie versuchen, einen Fehler zu identifizieren.

Es ist wichtig, den ursprünglichen Fehler zu identifizieren und zusätzliche Fehler zu ignorieren, die durch den ersten Fehler verursacht wurden. Versuchen Sie beim Lesen des Fehlerprotokolls, die Fehler von oben nach unten in sequenzieller Reihenfolge zu beheben.

Wenn mehrere Fehler gleichzeitig eingeführt werden, kann die Diagnose sehr schwierig sein. Es ist wichtig, zwischen Tests nur eine kleine Anzahl von Änderungen vorzunehmen.

Wenn das Spiel reibungslos läuft, notieren Sie die Fehler im Protokoll, damit sie später ausgeschlossen werden können, wenn etwas nicht mehr funktioniert.

### FEHLERKONSOLE

* Die Fehlerkonsole wird im Spiel als Tab im Cheat-Menü aufgerufen.
* Sie kann nicht verwendet werden, wenn das Spiel nicht geladen wird.

1. Drücken Sie Strg+Umschalt+C, um das Cheat-Menü zu öffnen.
2. Drücken Sie das Karotten-Symbol, um zum Konsolen-Tab zu wechseln.
3. Die Konsole ist in drei Kategorien nach Wichtigkeit sortiert.
4. Nur rote Fehler sind für dieses Tutorial wichtig.

### PLAYER.LOG & PLAYER-PREV.LOG

* Diese Datei protokolliert Aktionen der Unity Game Engine, die Paralives ausführt.
* Player.log wird bei jedem Spielstart überschrieben und nach Player-prev.log verschoben.
* Sie befindet sich im lokalen Paralives\Paralives-Mods-Ordner.
* Durch Aktivieren von Optionen im Bedienfeld können weitere Informationen in das Protokoll aufgenommen werden. Zu viele Optionen können das Protokoll schnell sehr groß machen.
* Wenn etwas im Protokoll wichtig ist, erstellen Sie eine Kopie!

### Gute Fehler (zumindest nicht schlecht):

```text
+ Meta cache is expired
+ Loaded asset database (No metacache) of mod Local.mod in 0.06581748 seconds
+ The referenced script on this Behaviour (Game Object 'SlackService') is missing!
+ Serialization depth limit 10 exceeded
+ Loaded asset database of mod MyPremadeLot.mod in 0.04702377 seconds
+ Unloading 10 unused Assets to reduce memory usage
```

### Schlechte Fehler:

```text
- NullReferenceException: Object reference not set to an instance of an object
- Material builder got given parameters that don't match any shaders
- Could not resolve 'ProceduralRig/ReachWithLeftArm/ArmLChainIK/TargetArmLChainIK'
- FileNotFoundException
- Failed to find setting class
- Could not register Paralives Town.saved
```

> Hinweis: In Version 1.7 gibt es drei neue rote Fehler in der Konsole und der player.log, die sich offenbar nicht negativ auf die Spielleistung auswirken.
>
> * `+ System Exception: Invalid Path...`
> * `+ Runtime data is null...`
> * `+ OperationException: Addressables...`

> Hinweis: In Version 1.8A funktionierte der .fbx-Importer nicht ordnungsgemäß und blieb beim Bildschirm zum Importieren von Assets hängen.

---

# Arten von Fehlern

Die Arten von Problemen, die auf technischer Ebene auftreten.

## Null Reference

* Manchmal auch Null-Pointer-Referenz genannt.
* Jeder Fehler, bei dem eine Einstellung, ein Element, ein Mesh oder ein Wert nicht gefunden werden konnte.
* Das Spiel verweist auf ein Objekt, das es nicht finden kann, oder es hat nicht verstanden, was es gefunden hat.

> Hinweis: Das Spiel kann mit einigen Null-Referenzen umgehen, und mehrere davon sind Bestandteil der Early-Access-Version des Spiels.

## Out of Bounds

* Das Spiel hat einen Wert außerhalb des erwarteten Bereichs erhalten.
* Wenn das Spiel einen Wert zwischen 0 und 10 erwartet, aber den Wert 10842 erhält, kann dies einen Fehler verursachen.

## Übersetzung

* Das Spiel hat versucht, eine als beschädigt erkannte Datei zu reparieren, und die Ausgabe war falsch.

Zum Beispiel ein Problem mit .tmp-Dateien, ⁠.mod.meta und .tmp

## Syntax

* Das Spiel wurde aktualisiert und der Mod entspricht nicht mehr den vom Spiel festgelegten Standards. Am häufigsten bei BepInEx-Code-Injection-Plugins.
* Einige Mods, die beim Start des Spiels erstellt wurden, enthalten fehlende Doppelpunkte in der Textdatei.

---

# Kategorien von Symptomen

Wenn die Ursache des Fehlers unbekannt ist, besteht das Ziel darin, Symptome mit einer bestimmten Ursache in Verbindung zu bringen. Nachdem jeder Fehler behoben wurde, sollte das Spiel funktionieren. Hier sind willkürliche Kategorien, um ähnliche Fehler zu Gruppen zusammenzufassen.

Es ist wichtig, den ursprünglichen Fehler zu identifizieren und zusätzliche Fehler zu ignorieren, die durch den ersten Fehler verursacht wurden.

## Kat A — Spiel starten

### Symptome

* Das Spiel erreicht nicht das Paralives-Hauptmenü
* Der Bildschirm ist schwarz
* Das Spiel stürzt ab, wenn es über Steam gestartet wird
* Beim Starten des Spiels über Steam erscheint ein Fehler
* Das Spiel bleibt bei einem Bild von Wolken hängen.

### Mögliche Lösungen

* Überprüfen Sie, ob die Hardware die Mindestanforderungen zum Spielen von Paralives erfüllt.
* Eine kritische Datei, die während des Spielstarts verwendet wird, ist beschädigt, nicht lesbar oder nicht zugänglich.
* Beginnen Sie mit der Überprüfung der Spieldateien.
* Erstellen Sie eine Ausnahme für Paralives im Antivirenprogramm.
* Überprüfen Sie player.log im lokalen Mods-Ordner paralives/paralives auf Fehler.

## Kat B — Assets importieren

### Symptome

* Hängt beim Importieren von Assets fest

### Mögliche Ursache

Eine Mod-Datei ist nicht lesbar.

### Mögliche Lösungen

* Entfernen Sie die neuesten Mods aus dem lokalen Mod-Ordner paralives/paralives oder den Steam-Workshop-Ordnern, bis das Problem behoben ist.
* Überprüfen Sie die Spieldateien.

## Kat C — Speicherstand auswählen

### Symptome

* Das Spiel kehrt zum Hauptmenü zurück, wenn versucht wird, einen Speicherstand zu laden
* Die Speicherdatei ist weiß

### Mögliche Ursache

Die Speicherdatei hat falsche Dateinamen, es fehlen Dateien oder sie ist nicht lesbar.

### Mögliche Lösung

Überprüfen Sie zunächst, ob der Name des Speicherstands mit den darin enthaltenen Metadateien übereinstimmt und der Speicherstand alle erforderlichen Komponenten enthält.

## Kat D — Speicherstand laden

### Symptome

* Das Spiel bleibt beim Laden des Speicherstands hängen
* Das Spiel bleibt für immer auf dem Ladebildschirm

### Mögliche Ursache

Beschädigter Mod, ein Mod wurde unsachgemäß entfernt oder eine Beschädigung der Speicherdatei, beispielsweise durch einen Null-Referenz-Fehler.

Es kann unmöglich sein, einige Mods zu entfernen, ohne eine Speicherdatei zu beschädigen.

### Mögliche Lösung

Testen Sie, ob die Fehler in einem neuen Speicherstand weiterhin auftreten.

## Kat E — Live-Modus

### Symptome

* Das Spiel bleibt hängen oder friert ein, wenn ein Menü im Live-Modus geöffnet wird
* Das Spiel bleibt hängen oder friert ein, wenn eine bestimmte Aktion im Live-Modus ausgeführt wird

### Mögliche Ursache

Beschädigter Mod, ein Mod wurde unsachgemäß entfernt oder eine Beschädigung der Speicherdatei, beispielsweise durch einen Null-Referenz-Fehler.

Es kann unmöglich sein, einige Mods zu entfernen, ohne eine Speicherdatei zu beschädigen.

### Mögliche Lösung

Testen Sie, ob die Fehler in einem neuen Speicherstand weiterhin auftreten.

## Kat F — Menüs

### Symptome

* Das Spielmenü lässt sich beim Anklicken nicht öffnen
* Das Spielmenü ist beim Anklicken leer
* Das Spielmenü lässt sich nicht schließen

### Mögliche Ursache

Beschädigter Mod, ein Mod wurde unsachgemäß entfernt oder eine Beschädigung der Speicherdatei, beispielsweise durch einen Null-Referenz-Fehler.

Es kann unmöglich sein, einige Mods zu entfernen, ohne eine Speicherdatei zu beschädigen.

### Mögliche Lösung

Testen Sie, ob die Fehler in einem neuen Speicherstand weiterhin auftreten.

## Kat G — Mods installieren

### Symptome

* Mods lassen sich nicht installieren

### Mögliche Lösungen

* Überprüfen Sie den Steam- und den lokalen Mods-Ordner auf unvollständige Dateien.
* Löschen Sie beschädigte Mod-Dateien, die den Download verhindern.

## Kat H — Fehlende Mods

### Symptome

* Installierte Mods werden nicht im Mod-Menü angezeigt
* Installierte Mods werden im Mod-Menü angezeigt, aber nicht im Spiel

### Mögliche Lösungen

* Überprüfen Sie auf beschädigte Mods.
* Überprüfen Sie auf doppelte Mod-Dateien.

## Kat I — Mods überprüfen

### Symptome

* Installierte Mod-Elemente werden beim Ausrüsten eines Charakters nicht angezeigt
* Installierte Mod-Elemente sind verschwunden
* Ein Charakter mit Mod-Elementen ist verschwunden
* Mod-Elemente sehen seltsam aus
* Mod-Elemente verhalten sich unerwartet
* Mod-Elemente haben die falsche Farbe, Form oder Größe

### Mögliche Lösung

Überprüfen Sie auf beschädigte Mods.

---

> **Erstellen Sie eine vollständige Sicherung Ihrer Speicherdateien, bevor Sie einen dieser Schritte durchführen!**

---

# So entfernen Sie beschädigte Daten

Nach Schwierigkeitsgrad und Komplexität sortiert.

## Einfach

### Mods aus- und einschalten

* Manchmal werden die Mods nicht richtig initialisiert, was behoben werden kann, indem nur ein Mod über das Ingame-Mod-Menü aus- und wieder eingeschaltet wird.

### Paralives neu starten

* Das Spiel verfügt über Schutzmechanismen gegen beschädigte Daten, die beim Start des Spiels aktiviert werden.
* Dies mag albern erscheinen, aber ein mehrfacher Neustart des Spiels kann in einigen Szenarien effektiv sein.

### Einen neuen Speicherstand starten

* Wenn die Fehler zu kompliziert sind oder nicht behoben werden können, ist das Starten eines neuen Speicherstands möglicherweise die beste Option.

### Spieldateien über Steam überprüfen oder das Spiel neu installieren

* Im Steam-Client bei beendetem Spiel:

  * Steam > Paralives > Eigenschaften > Integrität der Spieldateien überprüfen

### Alle Mods erneut abonnieren, um beschädigte Dateien zu entfernen

1. Fügen Sie alle abonnierten Mods zu einer benutzerdefinierten Sammlung hinzu
2. Kündigen Sie alle Mod-Abonnements
3. Abonnieren Sie alle Mods in der Sammlung

### Mods entfernen, bis der beschädigte Mod entfernt wurde

* Entfernen Sie jeweils einen Mod oder verwenden Sie die 50/50-Methode, um die Hälfte der Mods zu entfernen, bis der beschädigte Mod identifiziert wurde.
* Mods können auch dann Fehler verursachen, wenn sie deaktiviert sind. Sie müssen vollständig entfernt werden, indem die Mod-Dateien verschoben, das Abonnement gekündigt oder die Dateien gelöscht werden.
* Das Spiel muss möglicherweise zwischen jedem Test neu gestartet werden, um sicherzustellen, dass zwischengespeicherte Dateien gelöscht werden.
* Dokumentieren Sie Ihre Ergebnisse und notieren Sie, welche Mods funktionieren!

### Mods langsam erneut abonnieren, um sicherzustellen, dass sie ordnungsgemäß installiert werden

* Die Theorie besagt, dass die gleichzeitige Installation zu vieler Mods Fehler verursacht, also installieren Sie Mods langsam.
* Das Spiel ist darauf ausgelegt, Mods schnell zu installieren, aber vielleicht ist etwas Wahres daran.

---

## Mittel

### Steam Workshop-Mods in den lokalen Paralives\Paralives-Mods-Ordner verschieben

* Lokal installierte Mods werden von der Game Engine anders interpretiert, was den Fehler beheben kann.
* Wenn das Spiel nicht läuft, öffnen Sie den Datei-Explorer und kehren Sie zum Steam Workshop-Mods-Ordner zurück:

  ```text
  C:\Program Files (x86)\Steam\steamapps\workshop\content\1118520\
  ```
* Geben Sie ".mod" in die Suchleiste ein. Wenn keine Ergebnisse angezeigt werden, versuchen Sie "*.mod".
* Dadurch werden die Ordner mit Mods innerhalb des Steam-Mods-Ordners angezeigt.
* Wählen Sie alle .mod-Ordner aus, schneiden Sie sie aus und fügen Sie sie in den lokalen Mods-Ordner Paralives\Paralives ein.
* Alle Ordner sollten gleichzeitig verschoben werden.
* Kündigen Sie anschließend die Abonnements der Mods, damit Steam sie nicht zurückkopiert.
* Stellen Sie sicher, dass die Kopie im Steam Workshop-Mods-Ordner ordnungsgemäß gelöscht wurde, da zwei Kopien eines Mods Fehler verursachen können.

### Verbleibende Dateien in den Steam-Workshop-Mod-Ordnern löschen

* Kehren Sie zu workshop\content\1118520\ zurück und entfernen Sie alle Dateien, die nicht ordnungsgemäß entfernt wurden.
* Achten Sie genau auf die Details, da kleine Fehler später schwer zu finden sein werden.
* Zurückgebliebene Dateien verursachen sehr wahrscheinlich Fehler, wenn das Spiel sie nicht erwartet.

### Konsolenbefehle verwenden, um einen beschädigten Speicherstand durch Entfernen beschädigter Daten zu reparieren

* `CLEARALLOCCUPATIONS` löscht alle Jobs und den Jobverlauf für den ausgewählten Para und kann nicht rückgängig gemacht werden.
* `CLEARCHARACTEROUTFITS` löscht alle Outfits für den ausgewählten Para und kann nicht rückgängig gemacht werden.
* `CLEARINVENTORY` leert das Inventar des ausgewählten Para und kann nicht rückgängig gemacht werden.
* Das unten verlinkte Tutorial erklärt die verfügbaren Cheat-Befehle.

Tutorial für Cheat-Befehle ⁠Console and Cheat Commands

### Ein Code-Injection-Plugin installieren, um Mod-Fehler zu verwalten

* Diese Plugins funktionieren, indem sie der Game Engine mehr Zeit geben, jede Mod-Datei zu verarbeiten, und die Game Engine bei der Diagnose von Fehlern unterstützen.
* Plugins können zusätzliche Datenbeschädigungen verursachen, wenn sie nicht ordnungsgemäß gewartet und aktualisiert werden.
* Plugins werden hoffentlich unnötig werden, wenn die Paralives-Entwickler dem Spiel weitere Fehlerkorrekturen hinzufügen.

Paralines Launcher Plugin ⁠Paraline Launcher [Help | Bug R…

---

## Fortgeschritten

### Lokalen Mods-Ordner löschen

* Dies ist erforderlich, um einen ordnungsgemäßen Neustart zu ermöglichen.
* Steam Cloud muss möglicherweise deaktiviert werden, damit beschädigte Dateien während des Tests nicht wiederhergestellt werden.

1. Verschieben Sie den lokalen Mods-Ordner durch Ausschneiden und Einfügen an einen sicheren Ort außerhalb der Spieldateien, beispielsweise auf den Desktop
2. Überprüfen Sie die Spieldateien über Steam
3. Starten Sie das Spiel neu. Beim Start erstellt Paralives den gesamten lokalen Mods-Ordner von Grund auf neu.
4. Überprüfen Sie, ob ein neuer lokaler Mods-Ordner erstellt wurde.
5. Überprüfen Sie, ob das Problem behoben ist.

   * Ja: Fügen Sie wichtige Dateien aus der in Schritt 1 erstellten Kopie wieder hinzu.
   * Nein: Versuchen Sie andere Methoden zur Behebung des Problems, bevor Sie alte Dateien wieder hinzufügen.
6. Fügen Sie dem neu erstellten Paralives-Ordner nur Dateien hinzu, die als sicher gelten, um die Wahrscheinlichkeit zu verringern, beschädigte Datendateien zu kopieren.

### Speicherdateien direkt bearbeiten, um beschädigte Daten zu entfernen

* Speicherdateien sind Textdateien und können direkt geändert werden.
* Jeder Texteditor kann verwendet werden, aber Notepad++ mit einem Plugin zur Formatierung von JSON-Dateien wird bevorzugt.
* Das unten verlinkte Tutorial erklärt, wie Speicherdateien formatiert sind.

Erklärung des lokalen Mods-Ordners ⁠Mod Folder/Save Folder

### Sichere Teile eines Speicherstands in eine neue Speicherdatei verschieben

* Wenn das Problem mit dem Speicherstand nicht identifiziert werden kann, verschieben Sie kleine Teile in einen neuen Speicherstand.
* Diese Methode kann hilfreich sein, wenn versucht wird, beschädigte Dateien zu identifizieren.
* Beispielsweise können Haushaltsordner mit relativ geringem Datenverlust zwischen Speicherständen verschoben werden.
* Das unten verlinkte Tutorial erklärt, wie Speicherdateien formatiert sind.

Erklärung des lokalen Mods-Ordners ⁠Mod Folder/Save Folder

### Konsolenbefehle verwenden, um Charaktere in einem neuen Speicherstand neu aufzubauen

* Wenn alles verloren ist, ist es vielleicht am besten, in einem neuen Speicherstand neu anzufangen, aber mit einem kleinen Vorsprung.
* Befehle wie `SETMONEY` können verwendet werden, um Geld hinzuzufügen.
* Befehle können verwendet werden, um Fähigkeiten, Rezepte und mehr wiederherzustellen.
* Das unten verlinkte Tutorial erklärt die verfügbaren Cheat-Befehle.

Tutorial für Cheat-Befehle ⁠Console and Cheat Commands

---

> **Erstellen Sie eine vollständige Sicherung Ihrer Speicherdateien, bevor Sie einen dieser Schritte durchführen!**

# "Die übliche Lösung"

Die radikale Methode zur Behebung der meisten Probleme, bei der jede mit dem Spiel verbundene Datei gelöscht wird, um den bestmöglichen Neustart zu ermöglichen. Ich empfehle diese Lösung nicht für alle Probleme, da dadurch alte modifizierte Speicherstände ohne die für ihre ordnungsgemäße Funktion erforderlichen Mods unspielbar werden können.

## Alle Spieldateien für einen Neustart löschen

1. Löschen Sie die Spieldateien, indem Sie den gesamten lokalen Mods-Ordner paralives/paralives ausschneiden und auf den Desktop verschieben.
2. Kündigen Sie alle Steam Workshop-Mod-Abonnements und löschen Sie alle verbliebenen Mod-Dateien.
3. Überprüfen Sie die Spieldateien über Steam oder installieren Sie das Spiel neu.
4. Starten Sie Paralives neu.
5. Starten Sie einen neuen Speicherstand.
6. Wenn das Spiel jetzt funktioniert, machen Sie die Änderungen langsam rückgängig, bis das Problem wieder auftritt. Dann kennen Sie die Ursache des Problems.

---

# Datenbeschädigung verhindern

## VON ALLEM und OFT Kopien erstellen

* Erstellen Sie eine physische Kopie wichtiger Dateien und speichern Sie diese an einem sicheren Ort wie dem Desktop außerhalb der Spieldateien.
* Dateien, auf die die Paralives Game Engine zugreifen kann, können immer beschädigt werden.

> Hinweis: Der Befehl ZIPSAVEFILE erstellt eine Kopie Ihres aktuellen Speicherstands auf dem Desktop. Bei einer zweiten Verwendung des Befehls kann die alte Kopie überschrieben werden.

Tutorial für Cheat-Befehle ⁠Console and Cheat Commands

`ZIPSAVEFILE` erstellt eine ZIP-Datei des aktuellen Speicherstands auf dem Desktop.

## Mod-Bewertungen lesen

* Und hinterlassen Sie auch Bewertungen!
* Kommentare zu Mods sind eine Möglichkeit für Modder und andere Benutzer, Informationen über Mods auszutauschen.
* Wenn der Mod beschädigt zu sein scheint, informieren Sie den Modder, damit er ihn reparieren kann!

## Steam Cloud deaktivieren

* Steam Cloud ist hervorragend zum Schutz wichtiger Dateien geeignet, verursacht aber manchmal schwer zu findende Probleme.
* Steam Cloud bringt gerne abgelaufene Dateien zurück, ohne jemanden darüber zu informieren, und legt sie einfach dort ab, damit Sie sie später finden.

## Mods ordnungsgemäß entfernen

* Mods fügen dem Spiel Referenzen auf Elemente hinzu.
* Jede Instanz dieser Elemente muss VOR dem Entfernen des Mods manuell aus dem Spielstand entfernt werden.
* Es ist wesentlich einfacher, Mod-Elemente im Spiel zu entfernen, als eine Speicherdatei zu bearbeiten.
* Löschen Sie das schicke Sofa und den lustigen Pullover, bevor Sie den Mod entfernen!

## Treiber aktualisieren

* Für dieses Tutorial ist der Treiber der Grafikkarte (GPU) relevant.
* Unter Windows laden Sie die Nvidia- oder AMD-App herunter und installieren Sie alle paar Monate den neuen Treiber.

## Betriebssystem aktualisieren

* Ja, eww, unangenehm, aber es ist wichtig!
* Führen Sie regelmäßig integrierte Update-Software wie Windows Update aus.

## Mods langsam installieren und installierte Mods einzeln oder in kleinen Gruppen überprüfen

* Dies kann dem Spiel helfen, jede Datei zu verarbeiten, ohne Fehler zu machen.

## Vorbeugende Hardware-Wartung

* Kümmern Sie sich um den Computer, und er wird sich um Sie kümmern.
* Installieren und führen Sie sicher beschaffte Anti-Malware-Software aus.
* Überprüfen Sie auf physische Schäden und entfernen Sie Staub.
* Führen Sie integrierte Programme zur Überprüfung der Komponentenintegrität und -stabilität aus.

---

# Weitere Ressourcen

## Threads über Mod-Probleme (wo ich meine Testobjekte finde)

* Empfehlungen der Entwickler zur Fehlerbehebung
  https://steamcommunity.com/app/1118520/discussions/1/569288683937662349/
* Mega-Thread zu fehlenden Mods
  https://discord.com/channels/595045400805769238/1517352862395404499
* Mods werden nicht geladen
  https://discord.com/channels/595045400805769238/1517449529174130779
* Null-Referenz-Fehler
  https://discord.com/channels/595045400805769238/1517532031662424154
* Null-Referenz-Fehler
  https://discord.com/channels/595045400805769238/1513991069379858515/1517000216207822899
* Beschädigte Mod-Dateien
  https://discord.com/channels/595045400805769238/1517266950944981062
* Paralives-Wiki
  https://paralives.wiki.gg/wiki/Portal:Modding_guides
* Paralives-Änderungsprotokoll
  https://www.paralives.com/news
* Paralives-Entwicklung
  https://www.paralives.com/development
* Paralives-Roadmap
  https://paralives.notion.site/f138c4f6cb234604be16fe4198d17f51
* Bekannte Fehler
  https://discord.com/channels/595045400805769238/1508927230154244216
* Paralives-Roadmap
  https://paralives.notion.site/f138c4f6cb234be16fe4198d17f51
* Bekannte Fehler
  known-issues-and-bugs
