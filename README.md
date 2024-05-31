# openllm_geoguesser
Repository for the experiment assignment of the OpenLLM course SS24

Aufgabe Ziel:
Ziel des Experiments ist es festzustellen, ob ein kleines Sprachmodell zusammenhängende und inhaltlich korrekte
geographische Informationen zur Lokalisierung von Ländern auf der Weltkarte generieren kann.
Insbesondere ist der Gedanke, dass ein unwissender Spieler mit den Informationen aus dem Sprachmodell zuverlässig
Länder im Kontext des folgenden Spiels lokalisieren kann.

Das Spiel: https://www.geoguessr.com/vgp/3198 (Es wird ein Ländername gegeben, und der Spieler muss das Land auf
der Weltkarte verorten).

Erste oberflächliche Tests mit Chat-GPT haben ergeben, dass Chat-GPT ausführliche Texte und Anweisungen
liefern kann, und somit im Stande ist, die o.g. Aufgabe zu lösen.
Analog dazu soll nun geprüft werden, ob auch ein kleineres Sprachmodell entsprechende Kapazitäten hat.

Hierbei soll das verhältnissmäßig neue, und kleine Gemma-2b herangezogen werden (https://huggingface.co/google/gemma-2b-it),
um die Antworten zu generieren.


Die Aufgabe kann dabei unterschiedlich schwierig gestaltet werden, indem die Ansprüche an die Präzision der Antworten erhöht werden.
Folgende Stufen können erster Ansatz festgehalten werden.

1. Angrenzende Länder Identifizieren
2. Angrenzende Länder in Richtungen Einordnen (e.g. NW, NNW
3. Richtungsanweisungen auf Basis von anderen Ländern, und geographischen Orientierungspunkten (z.B Gebirge, Seen etc.)

Die resultierenden Angaben müssen manuell überprüft werden, sowohl in Hinblick auf die Eignung zur Lösung der Aufgabe, 
als auch die Korrektheit der angaben (z.B. stimmt die Liste der angrenzenden Länder). Ggf. können die Antworten auf mit
Antworten von Chat-GPT verglichen werden.
