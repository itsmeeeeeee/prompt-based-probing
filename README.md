
# Multilingual Probing of Large Language Models (LLMs)

## Abstract

Große Sprachmodelle (LLMs) ermöglichen die effiziente Abfrage faktischen und linguistischen Wissens, was sie zu vielversprechenden multilingualen Wissensdatenbanken macht. Diese Masterarbeit untersucht systematisch das In-Context-Learning-Verhalten (Zero-/Few-Shot) der Modelle LLaMA-3 (3.2B) und OLMo (7B). Dabei liegt der Fokus auf der Robustheit der Modelle bei faktischen und linguistischen Abfragen über ressourcenreiche und ressourcenarme Sprachen hinweg. Insbesondere wird untersucht, wie sich Anzahl und Reihenfolge der Few-Shot-Beispiele auf die Modellgenauigkeit auswirken. Die Ergebnisse zeigen, dass bereits der Übergang von Zero- zu One-Shot signifikante Leistungssteigerungen erzielt, während zusätzliche Shots nicht zwingend zu weiteren Verbesserungen führen. Die qualitative Fehleranalyse deckt spezifische Herausforderungen bei linguistischen Phänomenen (Komparativ, Superlativ, Verbformen) auf, besonders in morphologisch komplexen Sprachen. Trotz geringerer Parameterzahl erreicht LLaMA-3 eine vergleichbare Performance zu OLMo, jedoch bleiben Herausforderungen bei nicht-europäischen Sprachen und spezifischen Relationen bestehen. Zudem treten Biases (z. B. Common-Token-Bias) auf, die den Wissensabruf beeinflussen. Insgesamt verdeutlichen die Ergebnisse, dass Sprache, Relationstyp sowie Anzahl und Anordnung der Beispiele maßgeblich die Modellperformance bestimmen.

---

## Repository-Struktur und Inhalte

### Notebooks

* **`generation_llama_output.ipynb`**
  Enthält den Hauptcode zur Evaluation des LLaMA-Sprachmodells. Das Notebook lädt zunächst das Modell und generiert anschließend mithilfe der Funktion `new_test_prompt` Vorhersagen für Prompt-Anfragen. Die Ergebnisse werden in JSON-Dateien gespeichert und eine tokenweise berechnete Accuracy ausgegeben. Die Funktion `calculate_average_accuracy` ermittelt die durchschnittliche Accuracy für jede Relation.

* **`generation_olmo_output.ipynb`**
  Analog zu `generation_llama_output.ipynb`, jedoch speziell für die Evaluation des OLMo-Sprachmodells.

* **`extend_data.ipynb`**
  Erweitert den bestehenden Datensatz durch Hinzufügen neuer Prompt-Templates sowie zusätzlicher Few-Shot-Beispiele. Zudem generiert dieses Notebook systematisch verschiedene Permutationen der Few-Shot-Beispiele, um deren Einfluss auf die Modellleistung zu untersuchen.

* **`wikidata_translate_data.ipynb`**
  Extrahiert zunächst Wikidata-IDs für vorhandene Samples und Few-Shot-Beispiele, um anschließend mithilfe dieser IDs die Übersetzung der faktischen Daten in verschiedene Sprachen automatisiert durchzuführen.

* **`gpt_translate_data.ipynb`**
  Führt die Übersetzung des jeweils besten Prompt-Templates sowie der linguistischen (morphologischen) Daten mithilfe von GPT-4o durch.


## Daten

Alle übersetzten und generierten Datensätze befinden sich im Ordner `data` Die Daten sind strukturiert abgelegt und beinhalten:

* Übersetzte Daten in allen verwendeten Sprachen.
* Für jede Relation, jede Permutation sowie jede Shots-Anzahl wurden zusätzlich die Modelloutputs als Logits gespeichert.
* Berechnete Ergebnisse zur Top-1- und Top-10-Accuracy sind für jede Relation, Sprache und Permutation separat verfügbar.
* Die übersetzten Daten liegen sowohl in Zwischenstufen (Schritt-für-Schritt-Übersetzungen) als auch in finaler Form vor.

