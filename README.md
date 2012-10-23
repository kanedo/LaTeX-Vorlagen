#LaTeX Vorlagen 
Dieses Repository soll eine lose Sammlung von LaTeX Vorlagen darstellen, die ich für die Uni verwende. Dabei hoffe ich auch anderen Leuten helfen zu können und vor allem zu verhindern, dass ständig das Rad neu erfunden werden muss.
Ich weiß dabei selbst, dass meine Vorlagen defintiv nicht vollständig sein und hier erhoffe ich mir Feedback und Pull-Requests bis zum Umfallen, dass diese Sammlung möglichst sinnvoll und verwendbar wird.

##Dokumentation der Vorlagen
Ich versuche so ausführlich und verständlich wie Möglich meinen Quellcode zu kommentieren. Sollten fragen dazu auftauchen, einfach ein Ticket erstellen.

##Struktur
###Uebungen
Diese Vorlage ist vor allem für Übungen gedacht, die abgegeben werden müssen. Daher stehen auch in der Kopfzeile zwei Personen mit Matrikelnummer (Die Übungsgruppe sollte man in der Regel auch notieren). 
An der RWTH ist es usus, eine Übung in zweier Gruppen zu lösen, daher zwei Namen.

##FAQ
###Wie binde ich Quellcode ein
Leider müssen wir an der RWTH öfter Quellcode (im Moment in JAVA) ausdrucken. Ich hoffe das kein vernünftiger Editor dieses Feature unterstützt (den das würde bedeuten, es wurde weniger Zeit in wichtige Dinge investiert). Gott sei Dank kann LaTeX wunderbar diverse  Sprachen formatieren.  
Das ganze passiert mit dem Paket `listings` und `framed`.  
Der Inhalt eines Dokuments sollte nie per Copy&Paste eingebunden werden, da man meistens vergisst, diese Stellen zu aktualisieren. Daher hier meine Empfehlung:  

	\begin{framed}
		\lstset{language=Java, numbers=left, breaklines=true, showspaces=false, showstringspaces=false, morecomment=[l]{//}, tabsize=2}
		\lstinputlisting{file.java}
	\end{framed}  

Die `framed`- Umgebung zeichnet lediglich einen Rahmen um den Sourcecode. Mit dem Befehl `\lstset` konfiguriert man `listings` folgendermaßen:  

* **language**: Ok sollte klar sein, die Sprache. Verfügbare Sprachen findet ihr im   [texblog](http://texblog.org/2008/04/02/include-source-code-in-latex-with-listings/)  
* **numbers**: Bestimmt ob Zeilennummern angezeigt werden und wo. Sollte immer auf left stehen   
* **breaklines**: Wenn die Zeile zu lang wird, wird automatisch umgebrochen. Um zu drucken sehr wichtig (Daher auch immer Zeilennummern anzeigen, damit klar ist wo ein echter Umbruch war und wo nur das A4-Papier zu schmal ist)  
* **showspaces**: Stellt ein ob ein Zeichen für Leerzeichen gedruckt werden soll oder nicht
* **showstringspaces**: Wie `showspaces` nur explizit für Strings
* **morecomment**: Sollen Kommetare in `italic` dargestellt werden?
* **tabsize** Wie viele Leerzeichen ist ein Tab? Für den Druck empfehle ich 2 - nicht so viel Platzverschwendung

Mit dem Befehl `\lstinputlisting` gibt man den Pfad zur Datei an. Das hat den Vorteil, dass bei jedem compile auch der aktuelle Quellcode verwendet wird.
###Wie schreibe ich etwas über ein anderes Zeichen
Gerade in Mathe wird häufig verlangt, dass man Axiome oder Beweise über die Gleichheitszeichen (oder andere Symbole) notiert. Das ist mit LaTeX relativ einfach machbar:

	\overset{\text{Text}}{=}
das war es schon. Es ist nur recht Umständlich jedes mal `overset` zu schreiben. Weil man meist etwas über das `=` schreiben muss, habe ich einen neuen Befehl definiert:

	\newcommand{\equal}[1]{\overset{\text{#1}}{=}}
	
ab jetzt kann man das gleiche Ergebnis einfach mit `\equal{Dein Text}` erreichen.
