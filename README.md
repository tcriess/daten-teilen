# Pendeln über die Grenze messen, ohne Daten herzugeben

Klickbarer Prototyp für Crossing Forward 2026: Was Konstanz und Kreuzlingen über grenzquerende Pendelströme wüssten, wenn Zählstellen, Verkehrsbetriebe, Parkhäuser und Arbeitgeber gemeinsam rechnen, ohne ihre Rohdaten herauszugeben.

**Live:** https://tcriess.github.io/daten-teilen/

## Das Problem

Die Antwort auf „Wer pendelt wie über die Grenze?“ liegt verteilt. Das Parkhaus in Konstanz kennt Kennzeichen, aber keine Arbeitsorte. Der Arbeitgeber in Kreuzlingen kennt seine Beschäftigten, weiß aber nicht, wie sie zur Arbeit kommen. Erst zusammen zeigen die beiden zum Beispiel, wie viele mit dem Auto bis Konstanz fahren und dann zu Fuß über die Grenze gehen („Park & Walk“). An den Zählstellen erscheinen diese Menschen nur als Fußgänger.

Weitergeben darf aber keiner seine Daten: Kennzeichen und Personaldaten sind personenbezogen (DSGVO, Schweizer DSG), wurden für einen anderen Zweck erhoben und müssten dafür über die Grenze. Einen Treuhänder einzuschalten verschiebt das Problem nur. Und gehashte Kennzeichen lassen sich in Sekunden zurückrechnen.

## Die Lösung

Mit Kryptografie lässt sich gemeinsam rechnen, ohne dass eine Seite die Daten der anderen sieht:

| Trick | Wofür | Was herauskommt |
|---|---|---|
| **Private Schnittmenge (PSI)**: Verblinden mit geheimen Schlüsseln, deren Reihenfolge egal ist | Arbeitgeber × Parkhaus, Arbeitgeber × Verkehrsbetrieb (Jobticket) | nur die Anzahl der Treffer je Wohnort, keine Namen, keine Listen |
| **Differential Privacy**: kontrolliertes Rauschen vor dem Veröffentlichen | jede veröffentlichte Zahl aus der Verknüpfung | Zahlen, aus denen sich nichts über eine einzelne Person schließen lässt |
| **Sichere Summe**: jede Zahl in drei Zufallsteile zerlegt, verteilt auf drei Rechenstellen | Zählungen von Zählstellen, Bahn, Bus | nur die Summe je Verkehrsmittel, keine Einzelzahl |

Dazu kommt IPF (iteratives proportionales Anpassen), das aus offenen Randsummen der amtlichen Statistik eine Quelle-Ziel-Matrix schätzt.

## Aufbau der Seite

- **Worum es geht**: eine Einführung in sieben Schritten mit einem kleinen Beispiel (7 Parkhaus-Einträge, 6 Beschäftigte). Man kann spicken, gehashte Kennzeichen zurückrechnen, das PSI-Protokoll Schritt für Schritt durchgehen und dabei sehen, was jede Seite weiß, das Rauschen mit ε einstellen und eine sichere Summe aufteilen.
- **Überblick**: das Ergebnis mit rund 5 000 synthetischen Pendelnden. Karte, Verkehrsmittelanteile und Fehler im Vergleich: Wahrheit (nur im Generator) gegen Ebene 1 (nur Summen) gegen Ebene 1 + 2 (mit privaten Schnittmengen).
- **Datenhalter**: was bei wem liegt und was das Haus verlässt.
- **E1 Ohne Verknüpfung**: sichere Summe über drei Rechenstellen und IPF mit Iterationsregler.
- **E2 Mit Verknüpfung**: PSI auf den vollen Testdaten, Fehler abhängig von ε, Hash-Umkehr.

## Hinweise

Alle Zahlen stammen aus einem Zufallsgenerator. Orte sind real, Arbeitgeber, Kennzeichen und Werte erfunden. Die PSI läuft in einer Demo-Gruppe (Primzahl 2⁸⁹−1), nicht auf einer elliptischen Kurve. Für einen Pilot: MP-SPDZ oder Federated Secure Computing, openmined-psi, OpenDP.

Eine einzelne HTML-Datei ohne Build-Schritt und ohne Backend; läuft auch offline.
