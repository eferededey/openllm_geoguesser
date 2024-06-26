# Experiment Bericht: OpenLLM Geoguessr

## Experiment

Das Ziel des Experiments war es festzustellen, ob ein verhältnismässig kleines Sprachmodell zusammenhängende und inhaltlich korrekte geographische Informationen zur Lokalisierung von Ländern auf der Weltkarte generieren kann.

Um diese Fähigkeit des Modells auszuwerten, wurden drei Schwierigkeitsstufen definiert.

1.  Angrenzende Länder Identifizieren
2.  Angrenzende Länder in Richtungen Einordnen (e.g. NW, NNW
3.  Richtungsanweisungen auf Basis von anderen Ländern, und geographischen Orientierungspunkten (z.B Gebirge, Seen etc.)

Für jede dieser Stufen wurde nach einigen Tests ein Base Prompt erzeugt, dass sich als zielführend erwiesen hat. Die Experimente fanden außerdem auf Englisch statt, um die Performance möglichst optimal zu halten.

Zur Auswertung wurde aus der Liste der 150 flächenmäßig größten Länder uniform zehn Länder gezogen. Um die Performance pro Schwierigkeitsstufe und Modell möglichst konsistent, sowie Land vergleichen zu können, wurden diese zehn Länder für alle Stufen und beide Modelle genutzt.

Um die Qualität der Ausgabe von gemma-2b zu bewerten, wurde das Prompt sowohl in Chat-GPT (3.5) gegeben, als auch in Gemma-2b. Außerdem wurde die entsprechende ground-truth aus dem entsprechenden Wikipedia Ausschnitt eingefügt.

Anschließend wurden die Ausgaben der beiden Modelle mit der ground-truth verglichen.


## Ergebnisse

### Tier 1

Base Prompt: List _ neighboring countries.

Beispiel Prompt: List List Estonias neighboring countries.

Beobachtungen: Chat-GPT gibt effektiv Wort für Wort den entsprechenden Ausschnitt aus Wikipedia wieder. Auffallen ist hier aber, dass Chat-GPT in der Regel nur die Länder auflistet, und Ozeane, oder Ähnliche weglässt. So ist zum Beispiel in der ground truth für die Elfenbeinküste (Ivory Coast), in Wikipedia der folgende Satz enthalten: „Gulf of Guinea (Atlantic Ocean) to the south.“ Chat-GPT gibt dies nicht wieder, wohl in dem Wissen, dass Länder gesucht sind und der Golf von Guinea nicht darunterfällt.

Gemma-2b liefert eine reichlich schlechte Performance ab. Auch wenn sich die Antworten effektiv eins zu eins aus Wikipedia übernehmen lassen, halluziniert das Modell, und ergänzt die Ausgabe um ungewünschte Informationen, oder formuliert die Ausgabe gänzlich um. So wird zum Beispiel die Antwort von Gemma zu Mexiko als Quiz formuliert. Außerdem werden ungefragt teilweise Beziehungen zu den entsprechenden Ländern gegeben (ebenfalls Elfenbeinküste), oder das Land selber wird als Nachbar gelistet (Ägypten, Elfenbeinküste,  ..). Die Ausgaben werden unregelmäßig und wahllos formatiert, teilweise als Text (Estland), Liste (Serbien), oder Tabelle (Australien).

### Tier 2

Stufe 2 verhält sich analog zu Stufe 1. Chat-GPT liefert weiterhin gute Antworten, die effektiv 1:1 aus Wikipedia stammen könnten. Die von Chat-GPT generierten antworten sind zweckdienlich und würden die Aufgabe lösen. 
Gemma-2b wird bei dem komplexeren Promp noch unberechenbarer und generiert noch seltsamere Antworten, außerdem sind die Ausgaben nach wie vor größtenteils Falsch.

### Tier 3

Schwierigkeitsstufe drei wurde aus diversen praktischen Gründen nicht durchgeführt. Unteranderem wurden die Ladezeiten für die Prompts exzessiv, und die schlechte Performance von Gemma-2b bei den ersten beiden Stufen, lässt keine Hoffnung offen, das für Stufe 3 gute Antworten generiert werden.