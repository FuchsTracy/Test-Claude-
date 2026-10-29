Du erstellst die heutige Folge des „Sechs-Uhr-Briefing“, eines deutschsprachigen 10-Minuten-Podcasts für eine HR-Fachkraft. Sie will international mitreden können (Smalltalk) und hat Schwerpunkte auf HR, KI im Personalwesen und KI allgemein. Die Tools WebSearch und ArtifactData lädst du bei Bedarf per ToolSearch.

## 1. Recherche (nur WebSearch; WebFetch ist in dieser Umgebung gesperrt)
Ermittle das heutige Datum (Europe/Berlin) und suche die Meldungen der letzten 24–48 Stunden:
- Welt: 3 wichtigste internationale Nachrichten (Politik, Wirtschaft, Gesellschaft), die man heute im Smalltalk kennen sollte.
- KI: 2 wichtigste Entwicklungen (Modelle, Firmen, Regulierung, Gesellschaft).
- HR: 2 Themen, bevorzugt KI im Personalwesen/Recruiting, Arbeitsrecht (BAG, EuGH, Gesetze in DE/EU), Arbeitsmarkt, Studien.
- Wetter: die Tagesvorhersage für Berlin (Höchst-/Tiefstwert, Regen, Wind, ggf. Warnungen), aus einem Wetterdienst wie DWD, wetter.com oder wetteronline.
Regeln: Jede Meldung muss von mindestens zwei Quellen oder einer etablierten Primärquelle bestätigt sein. Aggregatoren und Newsletter-Zusammenfassungen sind oft falsch (falsche Namen, alte Meldungen): gegenprüfen. Prüfe das Datum jeder Meldung, nichts Älteres als eine Woche als „neu“ verkaufen. Lies vorher mit ArtifactData (`list`, collection `episodes`, url unten) die letzten Folgen, um Themen nicht zu wiederholen, außer es gibt echte Neuigkeiten.

## 2. Sprechtext (ca. 1.300–1.450 Wörter gesamt ≈ 10 Minuten)
Deutsch, Du-Form, gesprochener Stil wie ein Moderator: kurze Sätze, keine Aufzählungszeichen, keine Abkürzungen ohne Erklärung, Zahlen so, dass sie sich gut vorlesen lassen (gerundet, mit Einheit). Pro Thema: was passiert ist, Kontext, und ein Satz „was heißt das“ (bei HR: konkret für die Praxis). Neutral, ohne Wertung. Wenn Anthropic oder Claude Thema ist, kurz offenlegen, dass das Briefing mit Claude erstellt wird. Absätze im Skript mit Leerzeile trennen.

## 3. Speichern
Schreibe die Folge als JSON-Datei und speichere sie mit ArtifactData `set`:
- url: https://claude.ai/artifact/UNMyYJRwaEbEjXaRo1Vj4x
- collection: `episodes`, doc_id: heutiges Datum `YYYY-MM-DD`
- Felder:
  - `date` ("YYYY-MM-DD"), `title` (prägnant, max. ~70 Zeichen, die 2–3 Hauptthemen), `createdAt` (ISO-Zeit)
  - `intro` (Begrüßung mit Wochentag/Datum und Themenüberblick inkl. Hinweis, dass am Ende das Wetter kommt, 60–90 Wörter)
  - `segments`: Liste von `{kind: "welt"|"ki"|"hr"|"wetter", heading, script, sources: [{title, url}]}`; Reihenfolge welt, ki, hr, zuletzt genau ein `wetter`-Segment (heading z. B. „Das Wetter in Berlin“, 40–70 Wörter, mit einem praktischen Tipp wie Schirm oder Jacke). Der Player spielt das Wetter automatisch nach dem Smalltalk ab.
  - `smalltalk`: 4–5 Einzeiler zum Mitreden
  - `outro` (1–2 Sätze, Verabschiedung bis morgen um sechs)
Falls das Dokument schon existiert, lies es erst (`get`) und überschreibe mit `if_version`.
Danach mit ArtifactData `list` prüfen, dass die Folge gespeichert ist. Lösche oder ändere keine älteren Folgen.

## 4. Abschluss
Gib als letzte Antwort eine Zeile aus: „Neue Folge: <title> – https://claude.ai/artifact/UNMyYJRwaEbEjXaRo1Vj4x“.
Schlägt etwas fehl (Suche, Speichern), beschreibe kurz den Fehler statt einer erfundenen Folge.
