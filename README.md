# NanoVNA für Einsteiger: Antennen richtig messen und verstehen

Ein NanoVNA ist eines der nützlichsten Werkzeuge, die du deinem Funk- oder Elektronik-Arbeitsplatz hinzufügen kannst. Er hilft dir, Antennen zu prüfen und abzustimmen, Resonanzfrequenzen zu finden, das SWR über einen ganzen Frequenzbereich zu betrachten, Impedanzen sichtbar zu machen, Filter zu messen und Probleme in Kabeln oder HF-Komponenten aufzuspüren.

Der NanoVNA ist klein, erschwinglich und erstaunlich leistungsfähig. Trotzdem ist er kein Gerät, das man einfach anschließt und dessen erste Anzeige automatisch die ganze Wahrheit zeigt. Für brauchbare Ergebnisse musst du den richtigen Frequenzbereich wählen, am passenden Punkt kalibrieren, den richtigen Messanschluss verwenden und verstehen, was die angezeigten Kurven bedeuten.

Dieser Guide zeigt dir deshalb nicht jedes einzelne Menü. Er beantwortet die praktisch wichtigere Frage:

> **Ich sehe diese Kurve. Was bedeutet sie für meine Antenne und was muss ich als Nächstes tun?**

---

## Was ist ein NanoVNA?
![Abbildung 1: NanoVNA-Geräteübersicht mit Anschlüssen und Bedienelementen](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/f5ada94be0.png)

*Abbildung 1: NanoVNA-Geräteübersicht mit Anschlüssen und Bedienelementen*

VNA steht für „Vector Network Analyzer“, auf Deutsch Vektor-Netzwerkanalysator. Das klingt komplizierter, als es für den Einstieg sein muss.

Vereinfacht gesagt sendet der NanoVNA ein sehr kleines Hochfrequenzsignal aus und misst, was mit diesem Signal passiert. Dabei erfasst er nicht nur die Stärke, sondern auch die Phasenlage des Signals. Aus diesen Informationen berechnet das Gerät unter anderem SWR, Impedanz, Return Loss und die Darstellung im Smith-Chart.

Mit einem NanoVNA kannst du zum Beispiel:

- eine Antenne auf ihre Resonanzfrequenz prüfen,
- einen Dipol oder eine Vertikalantenne abstimmen,
- die Anpassung einer Antenne an ein 50-Ohm-System beurteilen,
- mehrere Resonanzen einer Mehrbandantenne finden,
- Filter und Dämpfungsglieder untersuchen,
- Veränderungen vor und nach einer Anpassung vergleichen,
- Kabel, Stecker und andere HF-Bauteile untersuchen.

Dabei solltest du realistisch bleiben. Ein NanoVNA ist kein kalibriertes Hochleistungslabor. Für Antennenbau, Amateurfunk, CB-Funk, Meshtastic, SDR-Projekte und viele Elektronikexperimente ist er jedoch ein ausgezeichnetes Werkzeug.

Seine Ergebnisse sind nur so zuverlässig wie der Messaufbau. Lose Stecker, unnötig viele Adapter, ungeeignete Kabel oder eine falsche Kalibrierung können stärker auffallen als der eigentliche Prüfling. Besonders bei höheren Frequenzen sollte die Verbindungskette deshalb kurz, sauber und unverändert bleiben.

---

## Was misst der NanoVNA?
![Abbildung 2: Signalfluss vom NanoVNA über das Koaxkabel zur Antenne und zurück](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/cd57317574.png)

*Abbildung 2: Signalfluss vom NanoVNA über das Koaxkabel zur Antenne und zurück*

Wenn der NanoVNA eine Antenne prüft, sendet er ein Signal über das Koaxkabel zur Antenne.

Eine passende Antenne nimmt einen großen Teil der zugeführten Leistung auf. Eine Fehlanpassung sorgt dagegen dafür, dass ein Teil des Signals zurück in Richtung NanoVNA reflektiert wird. Der NanoVNA misst diese Reflexion.

Aus derselben Grundmessung kann das Gerät verschiedene Ansichten berechnen:

- SWR,
- LOGMAG beziehungsweise S11 in dB,
- Return Loss,
- Widerstand R,
- Reaktanz X,
- komplexe Impedanz R + jX,
- Smith-Chart,
- Phase.

Diese Anzeigen widersprechen sich nicht. Sie betrachten dasselbe elektrische Verhalten lediglich aus unterschiedlichen Blickwinkeln.

---

## S11 und S21 richtig verstehen
![Abbildung 3: Vergleich zwischen S11-Reflexionsmessung und S21-Durchgangsmessung](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/c7cef7afb1.png)

*Abbildung 3: Vergleich zwischen S11-Reflexionsmessung und S21-Durchgangsmessung*

Bei vielen NanoVNA-Modellen wird der erste Anschluss als Port 1, CH0 oder S11 bezeichnet. Der zweite Anschluss trägt je nach Gerät Bezeichnungen wie Port 2, CH1 oder S21.

### S11: Was kommt zurück?

Für eine Antennenmessung verwendest du normalerweise Port 1.

S11 beschreibt die Reflexion am Eingang. Damit lässt sich untersuchen:

- wie stark eine Antenne reflektiert,
- wie hoch das SWR ist,
- wo eine Resonanz liegt,
- welche Impedanz anliegt,
- ob der Prüfling kapazitiv oder induktiv wirkt.

S11 ist kein eigener physischer Anschluss im eigentlichen Sinn, sondern die Bezeichnung der Messgröße. Im praktischen Umgang kannst du dir trotzdem merken:

> **Antenne an Port 1, dann S11 anzeigen.**

### S21: Was kommt hindurch?

Für eine Durchgangsmessung wird der Prüfling zwischen Port 1 und Port 2 angeschlossen.

S21 beschreibt, wie viel Signal vom ersten zum zweiten Port gelangt. Damit lassen sich beispielsweise untersuchen:

- Tiefpass-, Hochpass- und Bandpassfilter,
- Dämpfungsglieder,
- Koaxkabel,
- Sperrkreise,
- bestimmte Balun- und Mantelwellensperren-Aufbauten.

Für den Einstieg gilt:

> **Antennen misst du meist mit S11. Filter und Übertragungswege meist mit S21.**

---

## Den Frequenzbereich sinnvoll wählen

Bevor du kalibrierst, stellst du den Frequenzbereich ein, den du später tatsächlich untersuchen möchtest.

Bei einer 40-Meter-Antenne könntest du für einen ersten Überblick beispielsweise einen Bereich rund um das 40-Meter-Band wählen. Bei einer Antenne für 868 MHz wählst du einen entsprechend passenden Bereich um die gewünschte Betriebsfrequenz.

Ein extrem großer Frequenzbereich wirkt zwar übersichtlich, hat aber Nachteile:

- schmale Resonanzen können übersehen werden,
- einzelne Details werden schlechter dargestellt,
- die verfügbaren Messpunkte verteilen sich über einen größeren Bereich.

Ein bewährter Arbeitsablauf besteht aus zwei Schritten:

1. Zuerst einen etwas breiteren Bereich für den Überblick messen.
2. Danach den interessanten Bereich enger einstellen und erneut kalibrieren.

Die Kalibrierung gehört zum gewählten Frequenzbereich. Wenn du Start- und Stoppfrequenz deutlich veränderst, solltest du deshalb neu kalibrieren.

---

## Kalibrierung: der wichtigste Schritt
![Abbildung 4: OSL- und SOLT-Kalibrierung als klarer Ablauf](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/8689768173.png)

*Abbildung 4: OSL- und SOLT-Kalibrierung als klarer Ablauf*

Eine Kalibrierung zeigt dem NanoVNA, wie sich das Messgerät, die Anschlüsse und die bis zur Referenzebene verwendete Messkette verhalten.

Ohne passende Kalibrierung kann der NanoVNA nicht sauber zwischen dem Verhalten des Prüflings und den systematischen Fehlern des Messaufbaus unterscheiden.

### Für Antennen: Open, Short und Load

Für eine reine S11-Antennenmessung genügt normalerweise eine Ein-Port-Kalibrierung mit:

1. **Open:** offener Abschluss,
2. **Short:** Kurzschluss,
3. **Load:** möglichst genauer 50-Ohm-Abschluss.

Dieses Verfahren wird auch OSL-Kalibrierung genannt.

Der vereinfachte Ablauf lautet:

1. Gewünschten Frequenzbereich einstellen.
2. Alte Kalibrierung zurücksetzen.
3. Open an der späteren Referenzebene anschließen und messen.
4. Short anschließen und messen.
5. 50-Ohm-Load anschließen und messen.
6. Kalibrierung abschließen und speichern.
7. Prüfen, ob die Korrektur aktiv ist.

### Für Durchgangsmessungen: zusätzlich Thru

Wenn du S21 messen möchtest, benötigst du zusätzlich einen definierten Durchgang zwischen den beiden Ports. Dieser Schritt heißt **Thru**.

Open, Short, Load und Thru werden gemeinsam oft als SOLT-Kalibrierung bezeichnet. Thru ist für eine einfache S11-Antennenmessung meist nicht erforderlich, kann aber je nach NanoVNA-Modell und Firmware trotzdem Teil des angebotenen Kalibriervorgangs sein. Die Menüführung unterscheidet sich zwischen Geräten und Firmwareversionen.

### Nach der Kalibrierung nichts mehr verändern

Ein wichtiger Grundsatz lautet:

> **Alles, was sich zwischen Kalibrierung und Messung ändert, kann die Kalibrierung entwerten.**

Wenn du nachträglich einen Adapter, ein anderes Kabel oder einen zusätzlichen Verbinder einfügst, solltest du neu kalibrieren.

Auch die Stecker sollten während der Messung fest sitzen. Sie dürfen nicht wackeln, sollten aber ebenfalls nicht mit Gewalt angezogen werden.

---

## Die Referenzebene verstehen
![Abbildung 5: Kalibrierung am Gerät und am Ende des Messkabels im Vergleich](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/31166bb5d8.png)

*Abbildung 5: Kalibrierung am Gerät und am Ende des Messkabels im Vergleich*

Die Referenzebene ist der Punkt, ab dem dein Messergebnis gelten soll.

Kalibrierst du direkt am NanoVNA-Port und schließt danach ein Messkabel und mehrere Adapter an, gehören Kabel und Adapter zur gemessenen Anordnung. Sie können die angezeigte Impedanz verändern und zusätzliche Verluste oder Fehlanpassungen einbringen.

Kalibrierst du dagegen mit der vollständigen Messkette und setzt Open, Short und Load an deren Ende an, verschiebst du die Referenzebene an das Ende dieser Messkette.

Für das genaue Abstimmen einer Antenne ist die ideale Referenzebene möglichst nahe am Speisepunkt der Antenne.

In der Praxis ist dieser Punkt nicht immer leicht erreichbar. Dann gibt es zwei Möglichkeiten:

- den NanoVNA möglichst nahe zur Antenne bringen,
- oder eine feste, bekannte Messkette verwenden und immer unter denselben Bedingungen messen.

Wenn du am unteren Ende eines langen Koaxkabels misst, siehst du nicht ausschließlich die Antenne. Das Kabel transformiert die Impedanz, bringt Dämpfung mit und kann das Messergebnis glatter oder günstiger erscheinen lassen, als die Anpassung direkt am Speisepunkt tatsächlich ist.

---

## Die erste Antenne messen
![Abbildung 6: NanoVNA-Bildschirm mit Frequenzbereich, Trace, Marker und Resonanzpunkt](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/1e60b1a9cb.png)

*Abbildung 6: NanoVNA-Bildschirm mit Frequenzbereich, Trace, Marker und Resonanzpunkt*

Nach der Kalibrierung entfernst du den Kalibrierstandard und schließt die Antenne an, ohne die restliche Messkette zu verändern.

Wähle zunächst eine leicht verständliche Darstellung. Für den ersten Überblick eignen sich:

- SWR,
- S11 LOGMAG,
- Smith-Chart.

Aktiviere einen Marker und bewege ihn entlang der Kurve. Der Marker zeigt dir die Frequenz und den Messwert an der ausgewählten Stelle.

Suche nicht einfach nur den tiefsten Punkt der gesamten Anzeige. Prüfe vielmehr:

- Liegt das Minimum im gewünschten Frequenzbereich?
- Wie hoch ist das SWR an deiner Betriebsfrequenz?
- Wie tief ist S11 LOGMAG?
- Welche Impedanz zeigt der Marker?
- Liegt die Reaktanz X nahe null?

Erst die Kombination dieser Informationen ergibt ein brauchbares Bild.

---

## SWR richtig verstehen
![Abbildung 7: SWR-Kurven mit abgestufter Bewertung](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/fb7f355b71.png)

*Abbildung 7: SWR-Kurven mit abgestufter Bewertung*

SWR steht für „Standing Wave Ratio“, auf Deutsch Stehwellenverhältnis.

Das SWR beschreibt die Stärke der Fehlanpassung zwischen der angeschlossenen Last und dem Bezugssystem des Messgeräts, normalerweise 50 Ohm.

Ein SWR von 1:1 ist der theoretische Idealfall. In der Praxis ist ein extrem niedriger Wert jedoch nicht immer notwendig.

Als grobe Orientierung:

- **1,0 bis 1,2:** ausgezeichnet,
- **1,2 bis 1,5:** sehr gut,
- **1,5 bis 2,0:** für viele Anwendungen gut,
- **2,0 bis 3,0:** je nach Funkgerät und Anwendung möglicherweise noch nutzbar,
- **über 3,0:** genauer prüfen.

Diese Einteilung ist keine universelle Freigabe. Welche Werte zulässig sind, hängt auch vom Sender, der gewünschten Frequenzspanne und der Anwendung ab.

Wichtig ist außerdem:

> **Ein gutes SWR beweist nur eine gute Anpassung. Es beweist nicht automatisch, dass eine Antenne die zugeführte Leistung wirksam abstrahlt.**

Ein Abschlusswiderstand kann beispielsweise hervorragend angepasst sein, ist aber trotzdem keine gute Funkantenne. Auch Kabelverluste können ein SWR am Messgerät künstlich verbessern.

SWR ist deshalb ein guter Einstieg, aber nicht die vollständige Diagnose.

---

## LOGMAG: die Reflexion in dB
![Abbildung 8: Dieselbe Antennenmessung als SWR- und S11-LOGMAG-Darstellung](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/227c266879.png)

*Abbildung 8: Dieselbe Antennenmessung als SWR- und S11-LOGMAG-Darstellung*

LOGMAG steht für logarithmische Betragsdarstellung. Bei einer S11-Messung zeigt LOGMAG den Betrag des Reflexionsfaktors in Dezibel an.

Typische S11-LOGMAG-Werte sind negativ:

- **0 dB:** vollständige Reflexion,
- **-6 dB:** deutliche Reflexion,
- **-10 dB:** häufig ein brauchbarer Ausgangspunkt,
- **-15 dB:** gute Anpassung,
- **-20 dB:** sehr gute Anpassung,
- **-30 dB:** ausgezeichnete Anpassung, sofern die Messung und Kalibrierung diese Genauigkeit zuverlässig hergeben.

Je negativer der S11-LOGMAG-Wert, desto kleiner ist die gemessene Reflexion.

### LOGMAG und Return Loss sind eng verwandt

Hier ist eine saubere Begriffsunterscheidung wichtig:

- **S11 LOGMAG** wird üblicherweise als negativer dB-Wert dargestellt, zum Beispiel **-20 dB**.
- **Return Loss** wird als positiver Betrag angegeben, im gleichen Beispiel also **20 dB**.

Beide Größen beschreiben dieselbe Reflexion mit umgekehrtem Vorzeichen.

LOGMAG ersetzt das SWR nicht. Es stellt dieselbe Reflexionsinformation lediglich auf einer logarithmischen Skala dar. Der Vorteil liegt in der Darstellung: Kleine Unterschiede guter Anpassungen lassen sich in dB häufig besser vergleichen als auf einer SWR-Skala.

Beispielsweise entsprechen ungefähr:

- 10 dB Return Loss einem SWR von 1,92,
- 15 dB Return Loss einem SWR von 1,43,
- 20 dB Return Loss einem SWR von 1,22.

Deshalb ist LOGMAG besonders nützlich, wenn du Resonanzstellen, Nebenresonanzen oder kleine Vorher-Nachher-Unterschiede vergleichen möchtest.

---

## Widerstand und Reaktanz
![Abbildung 10: Widerstand und Reaktanz im kapazitiven, resonanten und induktiven Bereich](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/90f3b22d16.png)

*Abbildung 10: Widerstand und Reaktanz im kapazitiven, resonanten und induktiven Bereich*

Die Impedanz einer Antenne besteht aus zwei Anteilen:

> **Z = R + jX**

Dabei ist:

- **R** der ohmsche Anteil,
- **X** der reaktive Anteil.

In einem 50-Ohm-System ist eine Impedanz nahe **50 + j0 Ohm** sehr gut angepasst.

### Widerstand R

Ein Wert von 50 Ohm ist am Zielpunkt ideal für ein 50-Ohm-System. Ein abweichender Widerstand bedeutet jedoch nicht automatisch, dass die Antenne unbrauchbar ist. Die Anpassung kann gegebenenfalls mit einem geeigneten Netzwerk oder Transformator verbessert werden.

### Reaktanz X

Die Reaktanz zeigt, ob die Impedanz an der betrachteten Frequenz kapazitiv oder induktiv ist:

- **X < 0:** kapazitiv,
- **X = 0:** rein ohmisch beziehungsweise resonant,
- **X > 0:** induktiv.

Die Aussage „X negativ bedeutet Antenne zu kurz“ beziehungsweise „X positiv bedeutet Antenne zu lang“ ist nur als vereinfachte Orientierung bei bestimmten einfachen Antennen in der Nähe ihrer gewünschten Resonanz brauchbar. Bei Mehrbandantennen, geladenen Antennen, Anpassnetzwerken und Leitungstransformationen kann diese Regel in die Irre führen.

Die sicherere Vorgehensweise lautet:

1. Resonanzfrequenz bestimmen.
2. Mit der gewünschten Betriebsfrequenz vergleichen.
3. Erst daraus ableiten, ob ein einfacher Strahler länger oder kürzer werden muss.

---

## Smith-Chart ohne Angst
![Abbildung 11: Vereinfachter Smith-Chart für Einsteiger](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/5083222b9c.png)

*Abbildung 11: Vereinfachter Smith-Chart für Einsteiger*

Der Smith-Chart fasst Widerstand und Reaktanz in einer einzigen Darstellung zusammen.

Für den Einstieg reichen vier Regeln:

- **Mitte:** 50 Ohm und keine Reaktanz, also 50 + j0 Ohm,
- **oberhalb der waagerechten Mittellinie:** induktiv,
- **unterhalb der Mittellinie:** kapazitiv,
- **je näher am Mittelpunkt:** desto besser die Anpassung an 50 Ohm.

Entlang der waagerechten Mittellinie ist X gleich null. Links vom Mittelpunkt liegt der ohmsche Widerstand unter 50 Ohm, rechts davon über 50 Ohm.

Der Smith-Chart zeigt außerdem etwas, das SWR allein nicht verrät: Zwei Messpunkte können dasselbe SWR haben, aber völlig unterschiedliche Impedanzen besitzen. Der Smith-Chart zeigt dir, in welche Richtung du dich vom Mittelpunkt entfernst.

Für die ersten Messungen musst du keine Kreise berechnen. Beobachte einfach, wo der Marker liegt und wie er sich bei einer Änderung der Antenne bewegt.

---

## Resonanz finden und Bandbreite beurteilen
![Abbildung 9: Resonanz zu niedrig, im Ziel und zu hoch](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/b4a385e38d.png)

*Abbildung 9: Resonanz zu niedrig, im Ziel und zu hoch*

Eine Resonanz liegt dort, wo die Reaktanz X durch null geht. Bei einer einfachen, verlustarmen Antenne liegt dort häufig auch ein SWR-Minimum beziehungsweise ein deutliches Minimum im S11-LOGMAG-Trace.

Diese Punkte müssen jedoch nicht immer exakt zusammenfallen. Eine Antenne kann bei X = 0 resonant sein und trotzdem einen Widerstand deutlich über oder unter 50 Ohm haben. Dann ist die Antenne resonant, aber nicht optimal angepasst.

Prüfe deshalb am Marker immer gemeinsam:

- Frequenz,
- SWR,
- S11 LOGMAG,
- R,
- X,
- Position im Smith-Chart.

### Bandbreite ist kein bloßer Kurveneindruck

Die Bandbreite bezeichnet den Frequenzbereich, in dem ein festgelegtes Kriterium eingehalten wird. Das kann beispielsweise sein:

- SWR kleiner als 2:1,
- Return Loss größer als 10 dB,
- S11 LOGMAG kleiner als -10 dB.

Setze zwei Marker an die beiden Grenzpunkte. Die Frequenzdifferenz zwischen diesen Markern ist die Bandbreite nach dem gewählten Kriterium.

Eine schmale Kurve ist nicht automatisch schlecht und eine breite Kurve nicht automatisch gut. Die benötigte Bandbreite hängt von der Anwendung ab. Verluste können eine Kurve außerdem verbreitern, ohne die Antenne besser zu machen.

---

## Einen Dipol abstimmen
![Abbildung 12: Dipol vor und nach dem vorsichtigen Abstimmen](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/2e604b30c7.png)

*Abbildung 12: Dipol vor und nach dem vorsichtigen Abstimmen*

Bei einem einfachen, mittig gespeisten Dipol gilt als praktische Grundregel:

- Liegt die Resonanz **unterhalb** der gewünschten Frequenz, ist der Dipol meist zu lang.
- Liegt die Resonanz **oberhalb** der gewünschten Frequenz, ist der Dipol meist zu kurz.

Angenommen, der Dipol soll bei 7,1 MHz arbeiten, die Resonanz liegt aber bei 6,8 MHz. Dann ist der Dipol zu lang.

Kürze beide Schenkel gleichmäßig und nur in kleinen Schritten. Danach misst du erneut.

Wichtig:

> **Abschneiden ist endgültig. Umlegen oder Zurückfalten ist für den ersten Abgleich sicherer.**

Der praktische Ablauf lautet:

1. Antenne in der später vorgesehenen Höhe und Umgebung aufbauen.
2. Resonanz messen.
3. Beide Seiten gleichmäßig und vorsichtig verändern.
4. Antenne wieder in die ursprüngliche Position bringen.
5. Erneut messen.
6. Vorher- und Nachher-Kurve vergleichen.

Berühre die Antenne während der Messung nicht. Auch Hände, Leitern, Metallteile und Gebäude in der Nähe können das Ergebnis verändern.

---

## EndFed- und Mehrbandantennen

Eine EndFed besitzt häufig mehrere nutzbare Resonanzen. Ein breiter Sweep kann dir zunächst zeigen, wo diese Resonanzen liegen. Danach betrachtest du jedes gewünschte Band in einem engeren Frequenzbereich.

Achte darauf, dass eine Veränderung an einer Stelle mehrere Bänder beeinflussen kann. Bei einer Mehrbandantenne solltest du deshalb nach jeder Änderung alle gewünschten Frequenzbereiche kontrollieren.

Bei einer EndFed beeinflussen außerdem unter anderem:

- Transformator,
- Strahlerlänge,
- Aufbauform,
- Höhe,
- Gegengewicht,
- Speiseleitung,
- mögliche Gleichtaktströme

das Messergebnis. Ein einziges SWR-Minimum reicht deshalb nicht für eine vollständige Beurteilung.

---

## Vertikalantennen

Bei Vertikalantennen gehören Radials oder eine andere Form des Gegengewichts zum Gesamtsystem.

Veränderungen an:

- Anzahl,
- Länge,
- Winkel,
- Höhe,
- Bodenabstand,
- Umgebung

können Resonanz und Impedanz verändern.

Miss die Antenne möglichst in ihrer späteren Einbausituation. Eine Vertikalantenne auf dem Arbeitstisch kann sich deutlich anders verhalten als am endgültigen Montageort.

---

## Koaxkabel, Stecker und Filter prüfen

Für die reine Durchgangsdämpfung eines Kabels oder Filters verwendest du S21. Der Prüfling wird zwischen Port 1 und Port 2 angeschlossen.

Dafür brauchst du eine geeignete Zwei-Port-Kalibrierung mit einem definierten Thru.

### Filter

Bei einem Filter zeigt S21 LOGMAG:

- den Durchlassbereich,
- den Sperrbereich,
- die Einfügedämpfung,
- Übergänge und Grenzfrequenzen,
- gegebenenfalls unerwünschte Nebenbereiche.

### Koaxkabel

Bei einem Kabel kannst du mit einer geeigneten S21-Messung die Durchgangsdämpfung über der Frequenz betrachten. Ein einfacher S21-Sweep sagt jedoch nicht automatisch, an welcher Stelle ein Kabel beschädigt ist. Für eine Ortsbestimmung sind zusätzliche Verfahren wie eine Zeitbereichsdarstellung und ein bekannter Verkürzungsfaktor erforderlich.

### Stecker und Adapter

Wenn sich die Kurve verändert, sobald du einen Stecker leicht berührst, steckt oft ein mechanisches Problem dahinter:

- loser Kontakt,
- beschädigte Buchse,
- verschmutzte Verbindung,
- ungeeigneter Adapter,
- mechanische Belastung des NanoVNA-Ports.

Halte die Adapterkette so kurz und so konstant wie möglich.

---

## Messergebnisse richtig deuten

Eine einzelne schöne Kurve ist noch keine vollständige Diagnose.

### Gute Resonanz, aber schlechtes SWR

Eine Antenne kann resonant sein, weil X nahe null liegt, aber trotzdem einen Widerstand besitzen, der deutlich von 50 Ohm abweicht.

Dann ist die Antenne zwar resonant, aber nicht gut an das 50-Ohm-System angepasst.

### Gutes SWR, aber schlechte Antenne

Ein niedriges SWR kann auch durch Verluste entstehen. Ein verlustreiches Kabel oder ein ungeeigneter Aufbau kann reflektierte Energie dämpfen und dadurch die Anzeige am Messgerät verbessern.

Das Messgerät sieht dann eine gute Anpassung, aber nicht zwingend eine wirksame Abstrahlung.

### Mehrere Minima

Mehrere Minima können auf verschiedene Resonanzen hinweisen. Das ist bei Mehrbandantennen oft erwünscht. Es kann aber auch durch Aufbau, Leitungen, Umgebung oder unerwünschte Resonanzen entstehen.

Betrachte deshalb nicht nur die Tiefe eines Minimums, sondern auch:

- seine Frequenz,
- die Impedanz am Marker,
- die Position im Smith-Chart,
- die Wiederholbarkeit der Messung.

---

## Die häufigsten Fehler
![Abbildung 13: Typische NanoVNA-Messfehler mit Ursache und Lösung](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/4c7a6129cc.png)

*Abbildung 13: Typische NanoVNA-Messfehler mit Ursache und Lösung*

### Nicht oder falsch kalibriert

**Erkennbar an:** ungewöhnlichen Werten, unstabiler Kurve oder unplausibler Impedanz.

**Lösung:** Frequenzbereich festlegen, Kalibrierung zurücksetzen und an der richtigen Referenzebene neu kalibrieren.

### Frequenzbereich zu groß

**Erkennbar an:** grober Kurve und leicht übersehbaren Minima.

**Lösung:** Erst einen Grobscan durchführen, dann den gewünschten Bereich enger einstellen und neu kalibrieren.

### Messkette nach der Kalibrierung verändert

**Erkennbar an:** veränderten Ergebnissen nach dem Wechsel eines Adapters oder Kabels.

**Lösung:** Messkette vollständig aufbauen und anschließend neu kalibrieren.

### Antenne in ungeeigneter Umgebung gemessen

**Erkennbar an:** deutlichen Veränderungen beim Bewegen der Antenne oder beim Annähern von Personen.

**Lösung:** Antenne möglichst in ihrer späteren Betriebsposition und mit Abstand zu störenden Gegenständen messen.

### Nur auf SWR geschaut

**Erkennbar an:** gutes SWR, aber unklare oder unerwartete Impedanz.

**Lösung:** Zusätzlich S11 LOGMAG, R, X und Smith-Chart betrachten.

### Stecker oder Antenne während der Messung bewegt

**Erkennbar an:** springenden oder stark schwankenden Kurven.

**Lösung:** Messaufbau fixieren, Zug auf den Anschlüssen vermeiden und während des Sweeps nichts berühren.

---

## Praxisrezept: Eine Antenne in wenigen Schritten prüfen

1. Lege den gewünschten Frequenzbereich fest.
2. Baue die vollständige Messkette auf.
3. Kalibriere an der vorgesehenen Referenzebene.
4. Schließe die Antenne an Port 1 an.
5. Zeige zunächst S11 LOGMAG oder SWR an.
6. Setze den Marker auf das interessante Minimum.
7. Lies Frequenz, SWR und S11 in dB ab.
8. Prüfe R und X am gleichen Marker.
9. Betrachte die Position im Smith-Chart.
10. Verändere die Antenne nur in kleinen Schritten.
11. Miss nach jeder Änderung erneut.
12. Vergleiche die Kurven unter gleichen Bedingungen.

---

## Schnellreferenz
![Abbildung 15: Druckbarer NanoVNA-Spickzettel](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/70eea94b4c.png)

*Abbildung 15: Druckbarer NanoVNA-Spickzettel*

### Kalibrierung für eine Antennenmessung

**Frequenzbereich setzen → Reset → Open → Short → Load → Done → Save**

### Zusätzlicher Schritt für S21

**Thru durchführen und passende Zwei-Port-Kalibrierung verwenden.**

### S11 LOGMAG und Return Loss

| S11 LOGMAG | Return Loss | Einordnung |
|---:|---:|---|
| -6 dB | 6 dB | schwache Anpassung |
| -10 dB | 10 dB | meist brauchbar |
| -15 dB | 15 dB | gut |
| -20 dB | 20 dB | sehr gut |
| -30 dB | 30 dB | ausgezeichnet, wenn zuverlässig messbar |

### Ungefähre Zuordnung zum SWR

| SWR | Return Loss |
|---:|---:|
| 3,0 | 6,0 dB |
| 2,0 | 9,5 dB |
| 1,5 | 14,0 dB |
| 1,2 | 20,8 dB |
| 1,1 | 26,4 dB |

### Welche Anzeige wofür?

| Aufgabe | Sinnvolle Anzeige |
|---|---|
| Schneller Überblick | SWR |
| Reflexion in dB vergleichen | S11 LOGMAG |
| Resonanz bestätigen | X und S11 |
| Impedanz beurteilen | R + jX |
| Anpassungsrichtung erkennen | Smith-Chart |
| Filter messen | S21 LOGMAG |
| Kabeldämpfung messen | S21 LOGMAG |
| Bandbreite bestimmen | Zwei Marker und festgelegter Grenzwert |

---

## Der optimale NanoVNA-Workflow
![Abbildung 14: Empfohlener NanoVNA-Arbeitsablauf von der Kalibrierung bis zur Kontrollmessung](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/b8e89fa70c.png)

*Abbildung 14: Empfohlener NanoVNA-Arbeitsablauf von der Kalibrierung bis zur Kontrollmessung*

1. Gewünschten Frequenzbereich festlegen.
2. Messkette vollständig aufbauen.
3. An der richtigen Referenzebene kalibrieren.
4. Prüfling anschließen, ohne die Messkette zu verändern.
5. Mit SWR oder S11 LOGMAG einen Überblick gewinnen.
6. Marker auf die interessante Stelle setzen.
7. Frequenz, R, X und Smith-Chart gemeinsam betrachten.
8. Nur eine Änderung auf einmal vornehmen.
9. Unter denselben Bedingungen erneut messen.
10. Vorher- und Nachher-Ergebnis vergleichen.

Mit diesem Ablauf vermeidest du die häufigsten Anfängerfehler. Vor allem lernst du, Kurven nicht nur anzusehen, sondern daraus eine sinnvolle nächste Handlung abzuleiten.

Der NanoVNA nimmt dir das Denken nicht ab. Er macht aber sichtbar, was an Antenne, Kabel und HF-Bauteilen tatsächlich geschieht. Genau darin liegt sein größter Nutzen.

---

## Quellen und weiterführende Informationen

- [NanoVNA Praxisguide für echte Messungen – NextTechWorld](https://nexttechworld.com/de/amateurfunk/nanovna-praxisguide/)
- [NanoVNA Setup Guide: Calibration, SWR, Smith Chart and Antenna Testing – SDRStore](https://www.sdrstore.eu/nanovna-setup-guide-calibration-swr-smith-chart-antenna-testing/?sl=de)
- [SWR messen mit dem NanoVNA – VESAB (PDF)](https://www.vesab.de/wpvesab/wp-content/uploads/SWR_messen_V01_2022_10_13.pdf)
- [NanoVNA – Der Antenne unter den Rock geschaut – Björns Techblog](https://www.bjoerns-techblog.de/2019/11/nanovna-der-antenne-unter-den-rock-geschaut/)

