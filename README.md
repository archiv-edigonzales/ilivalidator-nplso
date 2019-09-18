# ilivalidator-nplso
Workaround Version für die vielen zusätzlichen Tests der NPLSO-Daten. Einige der Tests funktionieren aufgrund von Bugs in ilivalidator/iox-ili noch nicht. Andere benötige selber programmierte Zusatzfunktionen.

Die Bedingung, dass gewissen Typen mindestens ein Dokument zugewiesen haben, ist test- und teilweise umgesetzt:
- Noch kein Filter auf den Typen, sondern CONSTRAINT gilt für alle Typen.
- Nich sicher, ob die Super-Frickel-Lösung negative Auswirkungen hat.

## iox-ili AREA-Prüfung-Path
```
git clone https://github.com/edigonzales/iox-ili.git iox-ili-area-patch

gradle clean build jar -x test
```

Jar-Datei umbennen: `1.20.14-PATCH.jar` und in `libs`-Ordner in diesem Repository kopieren.

## ilivalidator-nplso builden
```
gradle clean jar
```


Run:
```
java -jar build/libs/ilivalidator-nplso.jar --config models/so_nutzungsplanung_20171118.toml --modeldir "http://models.geo.admin.ch;models" --plugins plugins/ /Users/stefan/Downloads/2457.xtf
```




## TODO
```
        CLASS ClassZA =
			Geometrie : SURFACE WITH (STRAIGHTS,ARCS) VERTEX Lkoord WITHOUT OVERLAPS > 0.001;
			Art: (a, b, c);
			SET CONSTRAINT WHERE Art == #a : INTERLIS.areAreas(ALL, UNDEFINED, >> Geometrie);
		END ClassZA;

```