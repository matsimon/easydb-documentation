---
title: "How To CSV-Import"
menu:
  main:
    name: "How To CSV-Import"
    identifier: "tutorials/how-to-csv-import"
    parent: "tutorials"
    weight: 100
---
# How To CSV-Import

Um die Funktion des Importes von CSV und Bildern nutzen zu können, benötigen Sie einen webserver. Damit die easydb5 auch die Bilder in die easydb importieren darf, muss der Webserver mit ***CORS*** konfiguriert werden. 

------
## Webserver Konfigurationen
### Apache 2
#### CORS Konfiguration
Um CORS nutzen zu können, muss als erstes die Apache2 Modifikation aktiviert werden. Um dies zu aktivieren, lassen sie folgendes Kommando auf der Maschine wo Apache2 läuft, auf der Konsole laufen. 

```bash
a2enmod headers
```

#### CORS auf einen Pfad beschränken:
In der nachfolgenden Konfiguration werden wir den Zugriff mit CORS nur auf den Ordner *easydb* zulassen.
```apache
<VirtualHost *:80>
        ServerName csv-import.beispieldomain.example
        DocumentRoot "/srv/www/csv-import-daten/easydb/"

        <Directory "/srv/www/csv-import-daten/easydb/">
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Require all granted
                Header set Access-Control-Allow-Origin "*"
        </Directory>
</VirtualHost>
```

**Hinweis:** *Servername, Port und Pfad* müssen auf ihr System angepasst werden.

Am Ende des Pfades sollte der Speicherort ihrer zu importierenden Dateien sein. 

Nach der Konfiguration muss Apache2 einem reload unterzogen werden. Wir empfehlen vor dem reload einen Konfigurations test durchzuführen, um sicherzustellen, dass keine Fehlkonfiguration in ihrem apache2 Webserver vorhanden ist. 
```bash
apache2ctl configtest #Folgendes sollte nun in der Konsole erscheinen: Syntax OK
/etc/init.d/apache2 reload
```

---

### Web Server for Chrome

***Webserver for Chrome*** ist eine Modifikation, welche es ihnen erlaubt innerhalb des gestarteten Chrome browsers, einen Webserver laufen zu lassen.

#### CORS Konfiguration

Im gegensatz zu Apache2 muss hier nur noch ***CORS*** mithilfe einer Checkbox aktiviert werden. Die CORS Option kann unter ***Show Advanced Settings*** angezeigt werden lassen. 

Wenn der Haken gesetzt ist, müssen sie noch den Ordner wählen wo alle Dateien enthalten sind (Lokaler PC).

---

# Import von CSV + Bild

## CSV Importer Einstellungen

Die Bilder die mittels CSV importer in die easydb geladen werden sollen, müssen mittels URL in dem jeweiligen Feld notiert werden. 

Hier ein Beispiel:
CSV Inhalt:
```csv
datei,titel,untertitel,beschreibung 
http://csv-import.beispieldomain.example/meinbild.jpg,Hallo Welt,Ich bin ein Untertitel,Ich bin eine Beschreibung
```

**Hinweis:** bitte tauschen Sie ***http://csv-import.beispieldomain.example/meinbild.jpg*** gegen die Adresse ihres Webserver mit CORS aus. Am Ende der URL sollte der Dateiname + Dateiendung stehen.

### Import der CSV Datei in die easydb

Wenn die CSV Datei nun valide URL enthält, können wir nun den Import der CSV Datei vornehmen.

- Gehen sie dazu in ihr easydb Webfrontent und öffnen Sie den CSV-Importer. 
- Anschließend laden sie die abgeänderte CSV-Datei in die easydb. 
- Weisen sie den CSV-Feldnamen und den CSV-Feldnamen zu. 
- Wählen sie einen Objekttypen, Pool und eine Maske. 
- Als ***Upload Typ für Dateien*** wählen Sie: `URL (remote put)`. 
- Wenn sie das erledigt haben, können wir uns dem Mapping der CSV Felder widmen. 

Mapping am obigen CSV Beispiel:

| CSV-Feld | Objekttyp-Feld | Beschreibung |
|----------|----------------|--------------|
| `datei`    | `picturefile#url` | Beachten Sie, dass beim Export einer CSV Datei aus der easydb, das Feld ohne Angabe von #url exportiert wird. Wenn sie einen erfolgreichen Import von Dateien mittels CSV tätigen möchten, müssen Sie hier ihr gewünschtes Feld mit #url angeben. |
| `titel`    | `picturetitle`   | Der Inhalt des CSV Feldes `titel` soll auf das Feld `picturetitle` innerhalb unseres gewünschten Objekttypen gemappt werden. |
| `untertitel` | `subtitle`  | Der Inhalt des CSV Feldes `untertitel` soll auf das Feld `subtitle` innerhalb unseres gewünschten Objekttypen gemappt werden. |
| `beschreibung` | `description` | Der Inhalt des CSV Feldes `beschreibung` soll auf das Feld `description` innerhalb unseres gewünschten Objekttypen gemappt werden. |