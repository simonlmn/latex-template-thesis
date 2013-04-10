latex-template-thesis
=====================
LaTeX-Vorlage für die Erstellung von Abschlussarbeiten

Übersicht
---------

Das Template verwendet die KOMA-Script Dokumentenklasse _scrrprt_ und setzt einige LaTeX Pakete voraus, die unter Umständen nicht im Standardumfang der lokalen LaTeX Distribution enthalten sind. Erhältlich sind diese Pakete über das CTAN (<http://www.ctan.org/>). Zur Installation siehe die Dokumentation des jeweiligen Pakets und der LaTeX Distribution.

Weiterhin ist das Template auf die Verwendung von UTF-8 als Zeichenkodierung ausgelegt. Dadurch können Umlaute und andere Sonderzeichen direkt verwendet werden. Damit das reibungslos funktioniert, müssen alle Textdateien auch so gespeichert werden (UTF-8-Kodierung), was bei den meisten Programmen beim Speichern (bzw. Speichern unter...) einstellbar ist.

Es sind für die variablen Felder auf der Titelseite und den formalen Erklärungen Befehle definiert, mit denen diese gesetzt werden können. Siehe dazu weiter unten den Abschnitt 'Einrichten des Dokuments'.

Für die Glossarerstellung wird das _glossaries_ Paket als Nachfolger von _glossary_ verwendet. Das Paket ist möglicherweise nicht von Haus aus verfügbar und muss eventuell manuell über das CTAN (s.o.) bezogen werden. Doku siehe <http://tug.ctan.org/tex-archive/macros/latex/contrib/glossaries/glossaries-manual.html>. Das für das Erzeugen der Glossare verwendete Skript `makeglossaries` wird von den meisten LaTeX-Editoren (z.B. TeXnicCenter oder TeXworks unter Windows) nicht direkt angeboten, muss daher entweder eingerichtet werden oder über die Kommandozeile gestartet werden. Für nähere Informationen dazu siehe ebenfalls die Doku des Pakets und/oder eine Websuche nach 'makeglossaries TeXnicCenter' oder ähnlichem.

Zum Übersetzen sind in der Regel folgende Durchläufe nötig:

 1. latex arbeit
 2. bibtex arbeit (nur wenn Zitate im Text vorhanden sind)
 3. makeglossaries arbeit
 4. latex arbeit
 5. latex arbeit (damit Referenzen und Verzeichnisse stimmen)
 

Dateien
-------

Das Template besteht aus einigen wenigen Dateien, wobei die wichtigste das sogenannte _Hauptdokument_ ist und unter `arbeit.tex` zu finden ist. Dort finden sich alle Einstellmöglichkeiten und dort werden auch die Kapitel der Arbeit eingebunden. Die Kapitel sollten in dem gleichnamige Verzeichnis `kapitel` abgelegt werden, dort ist auch schon ein erstes Beispielkapitel vorhanden.

Für das Literaturverzeichnis der Arbeit ist bereits ein leeres BibTeX Dokument unter `literatur.bib` angelegt. Dort sollte die verwendete Literatur im BibTeX-Format eingetragen werden, im Hauptdokument wird dieses bereits passend eingebunden.

Zusätzlich ist noch ein Glossar vorgesehen, der unter `glossar.tex` gespeichert wird. Ein Beispieleintrag ist dort schon vorhanden, zur genauen Verwendung siehe aber die [Doku zum _glossaries_ Paket](http://tug.ctan.org/tex-archive/macros/latex/contrib/glossaries/glossaries-manual.html). Wird kein Glossar benötigt, muss nichts weiter getan werden, da der Glossar nur erzeugt wird, wenn auch Einträge daraus im Dokument auftauchen.

Im Verzeichnis `vorlage` befinden sich einige intern verwendete Teildokumente, die normalerweise nicht verändert werden müssen oder sollten. Hier ist auch eine Logografik der Hochschule RheinMain zu finden, sowohl als EPS als auch PDF. Im Hauptdokument kann die Logografik auch durch eine andere ersetzt (oder ganz entfernt) werden, mehr dazu im nächsten Abschnitt.


Einrichten des Dokuments
------------------------

Das Template stellt im wesentlichen schon alles so ein, dass man direkt mit dem Schreiben anfangen kann. Aber natürlich müssen früher oder später noch so Sachen wie Titel der Arbeit, Namen des Verfassers, der Referenten und so weiter eingetragen werden. Für die Anpassung dieser und anderer Dinge gibt es eine Reihe von Befehlen, die alle im Hauptdokument unter 'Vorspann' eingetragen werden:

 * Hochschule: `\university{Name der Hochschule}`
 * Hochschullogo (oder ein anderes Logo): `\universitylogo{Pfad zur Logo-Datei}`; Um das Logo zu entfernen, entweder den Befehl weglassen oder einen leeren Pfad angeben (`\universitylogo{}`).
 * Fachbereich: `\department{Name des Fachbereichs}`
 * Bezeichnungs des Abschlusses: `\academicdegree{Bachelor of Science (B.Sc.)}`
 * Titel: `\title{Titel der Arbeit}`
 * Verfasser: `\author{Vorname Nachname}`
 * Referent: `\supervisor{Name des Referenten}`
 * Korreferent: `\cosupervisor{Name des Korreferenten}`
 * Externer Betreuer: `\externalsupervisor{Name eines externen Betreuers}` (diese Angabe ist optional und kann auch weggelassen werden)
 * Abgabedatum: `\date{Datum der Abgabe}`
 * Ort der Anfertigung: `\city{Ort}`

Neben diesen essentiellen Daten gibt es noch die Möglichkeit einige Angaben darüber zu machen, wie die Arbeit der Öffentlichkeit zugänglich gemacht werden darf. Als Voreinstellung darf die Arbeit nicht veröffentlicht werden. Um das zu ändern gibt es folgende Befehle:

 * `\publishInLibrary` erlaubt das Einstellen in die Hochschulbibliothek
 * `\publishTitleOnline` erlaubt das Veröffentlichen des Titels der Arbeit im Internet
 * `\publishDocumentOnline` erlaubt zusätzlich das Veröffentlichen der ganzen Arbeit im Internet


Zeilenabstand und Bindekorrektur
--------------------------------

Das Template sieht zwei Einstellungen vor, die das Layout betreffen. Diese werden in der Dokumentenpräambel eingetragen (das ist der Teil vor dem `\begin{document}`).

Der __Zeilenabstand__ kann mit Hilfe der Befehle `\singlespacing`, `\onehalfspacing` und `\doublespacing` eingestellt werden. Die Befehle stammen aus dem _setspace_ Paket und können auch im restlichen Dokument verwendet werden,  um Zeilenabstände umzuschalten.

Die __Bindekorrektur__ setzt man mit `\setbindingcorrection{breitenangabe}` (für Breitenangabe setzt man z.B. `1cm` oder `9mm` ein). Die Bindekorrektur vergrößert den linken Seitenrand und ermöglicht so Platz für eine Heftung oder Buchbindung zu schaffen. In der Regel sollte die voreingestellte Korrektur schon ganz gut passen, aber im Fall der Fälle kann hier eingegriffen werden. Noch ein Hinweis: Verändern der Bindekorrektur ändert auch die Textbreite, was zur Verschiebung von Überschriften, Absätzen und vor allem Abbildungen führen kann.
