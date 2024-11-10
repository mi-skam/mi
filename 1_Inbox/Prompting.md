---
modified: 2024-10-28T17:51:15+01:00
---

> [!INFO] TL;DR: Wesentliche Strategien des Prompt-Engineering
> 1. **Beispiele nutzen**: Prompts mit konkreten Beispielen geben Struktur und Detailtiefe vor.
> 
> • _Beispiel_: „Matrix: Ein Science-Fiction-Film…“
> 
> 2. **Schritt-für-Schritt-Vorgehen (Chain of Thought)**: Fördert durchdachte und logische Antworten, besonders bei komplexen Fragen.
> 
> • _Beispiel_: „Lass uns schrittweise vorgehen.“
> 
> 3. **Rollenzuweisung**: Die KI in eine spezifische Rolle versetzen, um präzisere Antworten zu erhalten.
> 
> • _Beispiel_: „Du bist ein Quiz-Teilnehmer…“
> 
> 4. **Unkonventionelle Ansätze**: Absurde Anweisungen wie „Atme tief ein“ oder symbolische Belohnungen erhöhen oft die Antwortqualität.
> 
> • _Beispiel_: „Atme tief ein und dann lass uns…“
> 
> 5. **Zusätze zur Konkretisierung**: Begriffe wie „Schritt für Schritt“ steigern die Kohärenz und Struktur in den Antworten.

## Beispielorientierte Prompts

• **Ansatz**: KI-Modelle orientieren sich stark an gegebenen Beispielen, sodass durch das Einfügen von passenden Beispielen eine gewünschte Struktur und Detailtiefe angeregt wird. Dies hilft besonders bei generativen Aufgaben wie Texterstellung, wo Stil und Umfang häufig schwer genau zu spezifizieren sind.

• **Beispiel-Prompt**:

• „Mach mir Vorschläge für einen Filmtitel und eine kurze Inhaltsbeschreibung. Orientiere dich an folgenden Beispielen: ‘Matrix: Ein Science-Fiction-Film über das Leben in einer virtuellen Welt.’; ‘Psycho: Ein Horrorfilm über einen schizophrenen Mörder.’“

• **Warum es funktioniert**: Beispiele wirken als Kontextanker, da sie dem Modell ein konkretes Format vorgeben und die Wahrscheinlichkeit erhöhen, dass es der Stilistik und Struktur der Beispiele folgt.


## Chain of Thought (Gedankenkette)

• **Ansatz**: Indem man das Modell explizit anweist, Schritt für Schritt zu denken, werden Ergebnisse meist strukturierter und durchdachter. Dieser Ansatz, auch „Chain of Thought“ genannt, eignet sich hervorragend für komplexe Fragen oder Aufgaben, die mehrschichtige Antworten erfordern.

• **Beispiel-Prompt**:

• „Ich suche eine Lösung für das Problem. Lass uns schrittweise vorgehen.“

• **Warum es funktioniert**: Durch das schrittweise Vorgehen strukturiert das Modell seine Antwort und kann in komplexen Fragestellungen logischer und kohärenter arbeiten. Die Formulierung „Schritt für Schritt“ ruft zudem oft Beispiele aus dem Trainingsmaterial auf, die selbst detaillierte Prozesse beschreiben.

## Rollenzuweisung

• **Ansatz**: Ein spezifischer Rollenauftrag führt dazu, dass das KI-Modell Antworten in einem bestimmten Ton und mit einer spezifischen Perspektive formuliert. Rollenzuweisungen sind äußerst flexibel und können für viele Anwendungsfälle angepasst werden, um die Antwortqualität zu verbessern.

• **Beispiel-Prompt**:

• „Du bist Teilnehmer in einem Quiz mit Allgemeinwissen und antwortest immer richtig. Ich bin der Moderator des Spiels und stelle die Fragen.“

• **Warum es funktioniert**: Die KI bezieht sich auf die Rolle, um kontextuell passende und oft sachlich präzisere Antworten zu geben. Durch diese Perspektivverschiebung kann das Modell realistischer und zielgerichteter auf die jeweilige Aufgabenstellung reagieren.

## Unkonventionelle Ansätze

• **Ansatz**: Ungewöhnliche oder absurde Anweisungen wie „Atme tief ein“ oder symbolische Belohnungen können unerwartet positive Auswirkungen auf die Antworten haben, oft durch eine Veränderung der semantischen Strukturen und Wahrscheinlichkeiten im Modell.

• **Beispiele**:

• **„Atme tief ein“**: „Atme tief ein und aus und dann lass uns das Problem Schritt für Schritt angehen.“ – Diese Aufforderung zur Entspannung steigert häufig die Genauigkeit und Detailtiefe der Antwort.

• **Belohnungen**: „Ich gebe dir 200 $ Trinkgeld.“ – Trotz ihrer symbolischen Natur können hypothetische Belohnungen die Länge und Detailtiefe der Antworten beeinflussen.

• **Emotionale Appelle**: „Ich habe keine Finger und ein Trauma wegen abgeschnittener Texte. Ich brauche von dir den gesamten Code.“ – Emotionale Ansätze können verhindern, dass der Text abgeschnitten wird und fördern vollständige Antworten.

• **Warum es funktioniert**: Diese Ansätze verschieben oft subtile Wahrscheinlichkeiten im Modell, die zu detaillierteren oder strukturierteren Antworten führen. Da KI-Modelle als Wahrscheinlichkeitsmodelle funktionieren, können auch scheinbar willkürliche Zusätze die Antwortform beeinflussen.

## Prompt-Zusätze zur Konkretisierung

• **Ansatz**: Zusätze wie „Schritt für Schritt“ oder „denk detailliert“ haben einen starken Einfluss auf die Antwortqualität, da sie die Wahrscheinlichkeit erhöhen, dass die Ausgabe gezielt strukturiert und spezifiziert wird.

• **Erklärungsansatz**: Modelle reagieren besonders auf Begriffe, die in strukturierten und hochwertigen Texten häufig vorkommen, sodass diese Zusätze helfen, die Struktur und Kohärenz der Antworten zu verbessern. Besonders nützlich sind diese Zusätze in Aufgaben, die eine systematische Abarbeitung erfordern.