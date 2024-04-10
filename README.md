# KSN-Projekt 5CHEL
2. Semester Projekt in der 5. Klasse

## Thema: FM Radio
### Genauere Beschreibung: Einfaches Radio, Frequenz verstellbar
## Gruppenmitglieder: 
- Stefan Tesic
- Mensur Sehic
- Antonia Dzidzic
## Abgabetag: 10.04.2024


## Arbeitsprotokoll:
- #### 28.02.2024:
    - Aufgabenstellung erklärt bekommen
    - Kurze Einführung in GNU Radio Companion, kleine Übungen dazu
- #### 06.03.2024:
    - Hardware testen mit einem Spektrum Analyzer; UKW-Spektrum: 80-110 MHz
    - Gruppeneinteilung über Eduvidual
    - Projektthema suchen
- #### 13.03.2024:
    - Projektthema suchen
    - Hardware
- #### 20.03.2024:
    - FM Radio erstellt
- #### 03.04.2024:
    - FM Radio getestet
    - GitHub Protokoll erstellt
- #### 10.04.2024:
    - Abgabe, Präsentation des Projekts
    - Benotung 
---------------------------------------------------------------------------------
## Aufbau:
![FMRADIO](https://github.com/stev097/KSN-Projekt/assets/162420138/2c5001ab-5dee-43b3-839e-c76f62ee4484)

## Simulation:
![FMRADIO2](https://github.com/stev097/KSN-Projekt/assets/162420138/f5691430-bac7-4919-8a53-23911812f3b8)

---------------------------------------------------------------------------------
## Erklärungen:
Variable: Hier werden die zentralen Variablen definiert, die im gesamten Flussdiagramm verwendet werden.
Zum Beispiel samp_rate, die die Abtastrate des Systems angibt.

QT GUI Range: Dieses Widget stellt Schieberegler zur Verfügung, die es dem Benutzer ermöglichen, Parameter in Echtzeit zu ändern, wie zum Beispiel die Frequenz oder die Verstärkung.
PlutoSDR Source: Dies ist der Quellblock, der Daten von einem PlutoSDR-Hardwaregerät empfängt. SDR steht für Software Defined Radio, eine Technologie, die es ermöglicht, Radiosignale mit Software anstatt Hardware zu verarbeiten.

Rational Resampler: Ändert die Abtastrate des Signals durch Interpolation und Dezimation, um es für die nachfolgenden Verarbeitungsschritte vorzubereiten.

Low Pass Filter: Ein Filter, der nur Signale unterhalb einer bestimmten Frequenz durchlässt, um unerwünschte Frequenzkomponenten zu entfernen.

WBFM Receive: Ein Block, der für die Demodulation von breitbandigen FM-Signalen (WBFM) zuständig ist. Hier wird das FM-Radiosignal in ein Basisbandsignal umgewandelt.

Rational Resampler (zweiter Block): Ein weiterer Resampler, der die Abtastrate nach der FM-Demodulation anpasst, häufig zur Vorbereitung auf die Audioausgabe.

Audio Sink: Dies ist der Ausgabeblock, der das demodulierte Audiosignal an ein Audioausgabegerät, wie zum Beispiel die Lautsprecher oder Kopfhörer, sendet.

Zusätzlich zu diesen Verarbeitungsblöcken sieht man:
QT GUI Frequency Sink und QT GUI Waterfall Sink: Diese Blöcke stellen grafische Darstellungen für Frequenzspektrum (Frequency Sink) und Wasserfalldiagramm (Waterfall Sink) zur Verfügung, die in Echtzeit die Spektralkomponenten des Signals und deren Änderung über die Zeit zeigen.

Das Flussdiagramm ist so konzipiert, dass das empfangene Signal zuerst durch die SDR-Hardware (PlutoSDR Source) aufgenommen wird.
Die Abtastrate und die Zentralfrequenz werden durch die im Block definierten Parameter bestimmt. Danach wird das Signal durch den Rational Resampler geführt, um die Abtastrate effizient zu ändern und an die Anforderungen der Signalverarbeitung anzupassen.

Der nächste Schritt ist das Durchlaufen eines Tiefpassfilters, der höhere Frequenzen abschneidet, um die Bandbreite des Signals auf den gewünschten FM-Rundfunkfrequenzbereich zu beschränken und Interferenzen zu reduzieren. Nach dem Tiefpassfilter wird das Signal durch den WBFM Receive Block geleitet, der das FM modulierte Signal demoduliert und in ein Basisband-Audiosignal umwandelt.Ein weiterer Rational Resampler passt die Abtastrate des demodulierten Audiosignals an die für die Audioausgabe benötigte Rate an.

Schlussendlich wird das Signal zum Audio Sink weitergeleitet, der es in hörbares Audio umsetzt und über ein Ausgabegerät wiedergibt. Die QT GUI Frequency Sink und Waterfall Sink Blöcke sind grafische Werkzeuge, die dem Benutzer ermöglichen, das Spektrum des empfangenen Signals sowie die spektralen Änderungen über die Zeit zu visualisieren. Sie sind wichtige Diagnosewerkzeuge, die beim Design und der Fehlersuche von Radiosystemen helfen.Zusammenfassend stellt das Flussdiagramm einen vollständigen Prozess dar, von der Erfassung des Rohsignals über die SDR-Hardware, die Verarbeitung und Demodulation des Signals bis hin zur Ausgabe des hörbaren Audios. Das macht GNU Radio zu einem mächtigen Werkzeug für die Entwicklung und das Testen von Radiokommunikationssystemen.
