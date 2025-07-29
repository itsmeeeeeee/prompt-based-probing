# Multilinguale Evaluation von LLMs mittels In-Context Learning

## Abstract

Diese Masterarbeit untersucht systematisch die Fähigkeit großer Sprachmodelle (LLMs), faktisches und linguistisches Wissen mittels In-Context-Learning (ICL) multilingual abzurufen. Die Modelle LLaMA-3 (3.2B) und OLMo (7B) werden hierbei über verschiedene Sprachen hinweg in Zero- und Few-Shot-Szenarien evaluiert. Untersucht wird insbesondere der Einfluss der Anzahl sowie der Permutationen von Few-Shot-Beispielen auf die Genauigkeit der Modellvorhersagen. Die Ergebnisse zeigen, dass bereits der Übergang von Zero- zu One-Shot signifikante Verbesserungen bringt, zusätzliche Shots jedoch nicht zwangsläufig weitere Leistungssteigerungen garantieren. Eine qualitative Fehleranalyse verdeutlicht Herausforderungen bei komplexen morphologischen Aufgaben (Komparative, Superlative, Vergangenheitsformen), insbesondere in morphologisch reichen Sprachen wie Deutsch, Italienisch und Französisch. Trotz geringerer Modellgröße liefert LLaMA-3 vergleichbare Ergebnisse wie OLMo, allerdings treten Schwierigkeiten speziell in nicht-europäischen Sprachen sowie bei bestimmten Relationstypen auf. Außerdem wurden spezifische sprachliche Biases identifiziert, welche die Modellvorhersagen beeinflussen. Insgesamt zeigt diese Studie, dass die Zuverlässigkeit des Wissensabrufs maßgeblich von Sprache, Relationstyp sowie der Anzahl und Reihenfolge der Few-Shot-Beispiele abhängt.

## Repository-Struktur und Inhalte

* **`generation_llama_output.ipynb`**
  Enthält den zentralen Code zur Evaluation des LLaMA-Sprachmodells. Das Notebook lädt zunächst das Modell, generiert anschließend Vorhersagen für Prompt-Abfragen mittels der Funktion `new_test_prompt` und speichert die Ergebnisse als JSON-Dateien. Die Funktion berechnet zudem die tokenweise Accuracy. Mithilfe von `calculate_average_accuracy` wird anschließend die durchschnittliche Accuracy pro Relation ermittelt.

* **`generation_olmo_output.ipynb`**
  Analog zu `generation_llama_output.ipynb`, jedoch spezifisch für das OLMo-Modell.

* **`extend_data.ipynb`**
  Erweitert den Datensatz um neue Prompt-Templates und zusätzliche Few-Shot-Beispiele. Außerdem generiert das Notebook systematisch unterschiedliche Permutationen der Few-Shot-Beispiele, um den Einfluss der Reihenfolge auf die Modellleistung zu untersuchen.

* **`wikidata_translate_data.ipynb`**
  Extrahiert Wikidata-IDs für faktische Samples und Few-Shot-Beispiele und führt mithilfe dieser IDs automatische Übersetzungen durch.

* **`gpt_translate_data.ipynb`**
  Übersetzt das jeweils beste Prompt-Template sowie alle linguistischen (morphologischen) Daten mithilfe von GPT-4o.
