# Analyse: Globaler Waldverlust nach dominantem Treiber (2001–2023)

Portfolioprojekt im Rahmen einer Weiterbildung im Bereich Datenexpertise. Die Analyse untersucht globalen Waldverlust und Waldfläche anhand von Global-Forest-Watch- und Our-World-in-Data-Datensätzen, mit besonderem Fokus auf die Unterscheidung zwischen **temporärem** und **permanentem** Waldverlust sowie deren geografische und treiberbezogene Verteilung.

## Verwendete Datensätze

| Datei | Inhalt | Zeitraum | Quelle |
|---|---|---|---|
| `deforestation_dominant_drivers.csv` | Waldverlust (ha) je Land/Jahr, aufgeschlüsselt nach 7 Haupttreibern | 2001–2024 | Global Forest Watch (2025), via Our World in Data |
| `forest-area-km.csv` | Waldfläche (ha) je Land/Jahr | 1990–2025 | Our World in Data |

Die 7 Haupttreiber gliedern sich laut Metadaten in:
- **Temporär** (mit Regeneration): Logging, Shifting Cultivation, Wildfire, Other natural disturbances
- **Permanent** (keine Regeneration): Permanent Agriculture, Settlements and infrastructure, Mining and energy industry

## Datenaufbereitung

- Waldflächen-Datensatz auf den Zeitraum des Verlustdatensatzes (2001–2024) eingegrenzt
- Aggregate (Kontinente, Einkommensgruppen, "World") über den `Code`-Präfix `OWID_` von echten Ländern getrennt; Sonderfälle wie Kosovo (hat einen `OWID_`-Code, ist aber ein reales Land) manuell berücksichtigt
- Relative Kennzahlen nutzen die Waldfläche des Basisjahres (2001) als Bezugsgröße; Länder mit sehr geringer Ausgangsfläche (< 100.000 ha) werden ausgeschlossen, um Verzerrungen durch extreme Prozentwerte zu vermeiden

## Durchgeführte Analysen

1. **Kontinent-Vergleich** der Waldfläche, inkl. Sonderbetrachtung "Europa mit/ohne Russland" (Russland macht ~80 % der europäischen Waldfläche aus)
2. **Top-10-Länder** nach Waldverlust und Waldfläche, absolut und relativ zur Ausgangsfläche
3. **Treiber-Aufschlüsselung** je Kontinent und Land, inkl. Aufteilung in permanent vs. temporär
4. **Hotspot-Score**: Kombination aus Rangplatz (absolut) und Rangplatz (relativ), um Länder zu identifizieren, die in beiden Dimensionen stark betroffen sind
5. **Kartenvisualisierung** (Plotly Choropleth) für einzelne Jahre sowie als animiertes GIF mit kumuliertem Verlust über die Zeit

## Zentrale Erkenntnisse

- Der globale  Waldverlust beträgt von 2001 zu 2023 ca. 82 mio ha (ca. 2%)
- ~95 % des **permanenten** Waldverlusts weltweit gehen auf Permanent Agriculture zurück; Bergbau und Siedlungsbau spielen global eine untergeordnete Rolle
- Absolute und relative Betrachtung liefern unterschiedliche Rankings: große Flächenländer (Russland, Brasilien, Kanada) dominieren absolut, während kleinere Länder (Elfenbeinküste, Guatemala, Malaysia) relativ zur eigenen Waldfläche am stärksten betroffen sind


## Verwendete Tools

Python (pandas, matplotlib, plotly, kaleido, Pillow) in einem Jupyter Notebook (VS Code)
