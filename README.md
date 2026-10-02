# Pendeln über die Grenze messen, ohne Daten herzugeben

Klickbarer Prototyp für Crossing Forward 2026: Was Konstanz und Kreuzlingen über grenzquerende Pendelströme wüssten, wenn Zählstellen, Verkehrsbetriebe, Parkhäuser und Arbeitgeber gemeinsam rechnen, ohne ihre Rohdaten herauszugeben.

**Live:** https://tcriess.github.io/daten-teilen/

- **Ebene 1, ohne Verknüpfung:** sichere Summe (additive Geheimteilung über drei Rechenstellen) für Verkehrsmittelanteile, danach IPF auf Randsummen für eine Quelle-Ziel-Matrix.
- **Ebene 2, mit Verknüpfung:** private Schnittmengenberechnung (ECDH-artige PSI) Arbeitgeber × Parkhaus bzw. × Verkehrsbetrieb, veröffentlicht mit Differential Privacy (Laplace, Regler für ε).
- **Kontrast:** SHA-256-gehashte Kennzeichen werden im Browser in Sekunden zurückgerechnet.

Alle Zahlen stammen aus einem Zufallsgenerator (rund 5 000 Pendelnde). Orte sind real, Arbeitgeber und Werte erfunden. Die PSI läuft in einer Demo-Gruppe (Primzahl 2⁸⁹−1), nicht auf einer elliptischen Kurve.

Eine einzelne HTML-Datei ohne Build-Schritt und ohne Backend; läuft auch offline.
