---
title: "Apache2"
menu:
  main:
    name: "Apache2"
    identifier: "tutorials/cors/apache2"
    parent: "tutorials/cors"
    weight: 100
---

# Apache2 CORS

## Installation

Um bei Apache2 die *CORS* Funktion nutzen zu können, müssen wir als erstes das Apache2 Modul *headers* aktivieren.

Dies kann mit folgendem Kommando auf der Konsole aktiviert werden (unter Linux):

```bash
a2enmod headers
```

## Apache2 CORS auf Ordner ***easydb*** restricten:

In der nachfolgenden Konfiguration werden wir den Zugriff nur auf den Ordner *easydb* zulassen.
```apache
<VirtualHost *:80>
        ServerName csv-import.beispieldomain.de
        DocumentRoot "/srv/www/csv-import-daten/easydb/"

        <Directory "/">
                AllowOverride None
                Require all denied
        </Directory>

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

Nach der Konfiguration muss Apache2 einem reload unterzogen werden. Wir empfehlen vor dem reload einen Konfigurations test durchzuführen um sicherzustellen, dass keine Fehlkonfiguration in ihrem Apache2 Webserver vorhanden ist. 
```bash
apache2ctl configtest
```
Der Apache2 Configtest, sollte Ihnen normalerweise ```Syntax OK``` zurückgeben. Sollte dies nicht der Fall sein, schauen Sie sich das Logfile unter ```/var/log/apache2.log``` an und beheben Sie die Fehler. 

Sollte ```Syntax OK``` erschienen sein, können Sie nun den Apache2 neu starten/laden. Dies kann mit einem der folgenden Kommandos als Beispiel auf der Konsole geschehen:
```bash
sudo apache2ctl graceful

sudo /etc/init.d/apache2 reload

sudo service apache2 reload
```