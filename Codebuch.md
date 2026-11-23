# Codebuch – Netzwerk der Talkshow „Anne Will“ (2022)

## 1. Beschreibung des Datensatzes

Der Datensatz umfasst die Gäste der politischen Talkshow „Anne Will“ in den Folgen 500 bis 503 aus dem Jahr 2022. Alle vier Sendungen beschäftigen sich mit dem Ukraine-Konflikt beziehungsweise dem russischen Angriffskrieg gegen die Ukraine.

Ziel ist es, ein gerichtetes, bipartites Netzwerk zu erstellen, das die Beziehungen zwischen Talkshowgästen, Talkshowfolgen und politischen Parteien abbildet.

**Untersuchungszeitraum:** 20.02.2022 bis 13.03.2022

**Untersuchte Folgen:**

| Folge | Datum |
|---|---|
| 500 | 20.02.2022 |
| 501 | 27.02.2022 |
| 502 | 06.03.2022 |
| 503 | 13.03.2022 |

**Netzwerktyp:** Gerichtetes Two-Mode-Netzwerk

**Modus 1:** Talkshowgäste (Personen)

**Modus 2:** Talkshowfolgen und politische Parteien

**Datenquelle:** fernsehserien.de – Episodenguide „Anne Will“

## 2. Nodelist (nodes.csv)

Die Nodelist enthält alle Knoten des Netzwerks. Jeder Gast, jede Talkshowfolge und jede politische Partei wird als eigenständiger Knoten erfasst.

| Variable | Beschreibung | Ausprägungen / Beispiel |
|---|---|---|
| id | Eindeutige ID des Knotens | P01, F500, CDU |
| name | Name des Knotens | Lars Klingbeil |
| type | Art des Knotens | Person, Folge, Partei |
| mode | Zugehörigkeit zum Netzwerkmodus | 1 = Person, 2 = Folge/Partei |
| partei | Parteizugehörigkeit der Person zum Untersuchungszeitpunkt | SPD, CDU, FDP, Grüne, Linke, keine |
| beruf | Berufliche Funktion der Person zum Untersuchungszeitpunkt | Politiker, Journalist, Wissenschaftler, Sonstige |
| datum | Ausstrahlungsdatum der Folge | 2022-02-20 |

### Codierungsregeln der Nodelist

- Jede Person erhält eine eindeutige ID (P01, P02 usw.).
- Wiederholt auftretende Gäste werden nur einmal in der Nodelist erfasst.
- Die vier Talkshowfolgen erhalten die IDs F500 bis F503.
- Jede vorkommende politische Partei wird als eigener Knoten erfasst.
- Für Knoten, bei denen eine Variable nicht zutrifft, bleibt das Feld leer.
- Die Parteizugehörigkeit bezieht sich auf den Zeitpunkt der jeweiligen Sendung im Jahr 2022.
- Personen ohne belegte Parteizugehörigkeit erhalten den Wert „keine“.

## 3. Edgelist (edges.csv)

Die Edgelist enthält alle gerichteten Verbindungen zwischen den Knoten.

| Variable | Beschreibung | Ausprägungen / Beispiel |
|---|---|---|
| from | ID des Ausgangsknotens | P01 |
| to | ID des Zielknotens | F500 |
| relation | Art der Beziehung | Teilnahme, Parteizugehörigkeit |
| directed | Gibt an, ob die Beziehung gerichtet ist | 1 = gerichtet |
| weight | Gewichtung der Verbindung | 1 |

### Codierungsregeln der Edgelist

Es werden zwei Arten von Beziehungen erfasst:

**1. Teilnahme an einer Talkshowfolge**

Eine gerichtete Verbindung verläuft von einem Gast zu der Talkshowfolge, an der die Person teilgenommen hat.

Beispiel: Lars Klingbeil → Folge 500

**2. Parteizugehörigkeit**

Eine gerichtete Verbindung verläuft von einem Gast zu der politischen Partei, der die Person zum Zeitpunkt der Sendung angehörte.

Beispiel: Lars Klingbeil → SPD

Weitere Regeln:

- Jede Teilnahme wird als eigene Verbindung erfasst.
- Tritt eine Person in mehreren Folgen auf, erhält sie mehrere Verbindungen.
- Eine Parteizugehörigkeit wird pro Person nur einmal erfasst, sofern sie im Untersuchungszeitraum unverändert bleibt.
- Personen ohne belegte Parteizugehörigkeit erhalten keine Verbindung zu einem Parteiknoten.
- Alle Verbindungen sind gerichtet und haben das Gewicht 1.
- Es werden keine Verbindungen zwischen Knoten desselben Modus erfasst.

## 4. Hinweise zur Datenerhebung

Die Gäste werden anhand der offiziellen Gästelisten im Episodenguide von fernsehserien.de erfasst.

Die Moderatorin Anne Will wird nicht als Gast berücksichtigt.

Für jede Person werden der Name, die berufliche Funktion und gegebenenfalls die politische Parteizugehörigkeit dokumentiert.

Bei fehlenden oder uneindeutigen Informationen wird die Parteizugehörigkeit anhand weiterer geeigneter Quellen überprüft.

## 5. Quellen

- fernsehserien.de: Anne Will, Episodenguide, Folgen 500–503 (2022)
- Ergänzende Quellen zur Überprüfung der Parteizugehörigkeit, sofern erforderlich

Abrufdatum: 23.11.2026
