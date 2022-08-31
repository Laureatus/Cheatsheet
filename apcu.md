# APCu

APCu ist der Nachfolger des "Alternativ PHP Cache" kurz APC. APC war eine PHP Erweiterung welche zwei Aufgaben abdeckte. Zum einen als PHP Beschleuniger der Bytecode im Arbeitsspeicher ablegte. Durch diesen Bytecode-Cache muss der PHP-Interpreter nicht bei jedem Aufruf den gesamten Bytecode interpretieren. Stattdessen kann der bereits berechnete Code ausgeführt werden. Diese Funktionalität wurde durch OPcache ersetzt.

Zum anderen hat APC einen Daten Cache in welchem eine PHP Applikation selbst Daten ablegen konnte. Diese Funktion übernimmt nun «APC User Cache» kurz APCu. Dank APCu lassen sich zum Beispiel Datenbankabfragen in den Zwischenspeicher legen und damit Zeit sparen.



## Erhöhen der apc.shm\_size value

Falls dem APCu nicht genügend memory zugewiesen ist können Fehler wie dieser Auftreten:

```PHP Warning: apc_store(): Unable to allocate memory for pool.```

Um den Fehler zu beheben kann man APCu mehr memory zuweisen.

Um den Wert Korrekt einstellen zu können, muss man erst einmal wissen wie viel memory APCu mommentan hat. Am einfachsten ist es dafür die apc.shm\_sie einstellungen in der Kommandozeile zu überprüfen.

```$ php -i | grep aapc.shm_size```

```Apc.shm_size => 8M => 8M```

Um den wert auf zum Beispiel 16M zu erhöhen müssen Änderungen in der ```php.ini``` Datei vorgenommen werden.

```Apc.shm_size = 16M```

Anschliessend muss php-fpm neu gestartet werden.

```$ sudo service php7.0-fpm restart```

```[ok] Restarting PHP 7.0 FastCGI Process Manager: php-fpm7.0```

## APCu monitoring

Um APCu zu überwachen kann das apc.php script verwendet werden.

Das Script gibt wichtige Informationen wie zum Beispiel:

### APCu memory usage

Das Script berechnet freien und belegten speicherplatz und gibt eine Klare Übersicht von cache hits und misses. Wie in jedem caching system gilt hier, desto mehr hits desto besser.

![image](https://user-images.githubusercontent.com/47870802/187645357-8caf875b-ba36-4d71-9265-2b6518232c47.png)

### APCu cache fragmentation

Die cache fragmentation ist um einiges komplizierter. Man sollte sich einfach folgendes merken: Desto weniger fragmentation desto besser.

![image](https://user-images.githubusercontent.com/47870802/187645421-782b129f-b23d-47bc-85df-7747d7077669.png)

### Host stats

- General Cache Information (APCu version, uptime)
- Cache Information (cached variables, hit rate)
- Runtime settings (APCu settings, eg. ```apc.shm_size```)

### User Cache Entries

Um auf die User Cache Entries zugreifen zu können, muss im apc.php script der default password string editiert werden .

```defaults('ADMIN_USERNAME','apc'); //Admin Username```

```defaults('ADMIN_PASSWORD','password'); //Admin Password – CHANGE THIS TO ENABLE!!!```

Den Aufwand die Einstellungen vorzunehmen lohnt sich da man zugriff auf granulare daten in jeder einzelnen cache entry erhält.

- Anzahl der Hits
- Grösse
- Zuletzt modifiziert, erstellt am und timeout (falls gesetzt)
- Pfad zur Datei (doppelklick auf einen Eintrag)

Man hat auch die option alle cache einträge für den APCu cache zu leeren.
