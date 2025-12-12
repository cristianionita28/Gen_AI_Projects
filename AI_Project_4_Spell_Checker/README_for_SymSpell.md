
# SpellChecker with SymSpell (User Input)

This project implements a simple spell‑checker using the [**SymSpell**](https://github.com/mammothb/symspellpy) algorithm. It corrects words with up to five spelling mistakes by looking up the nearest match in a frequency dictionary. The script is interactive: it either uses a built‑in default text containing obvious misspellings or prompts the user to enter their own text. After processing, it outputs the corrected text and a report of all corrected words.

## Table of Contents

* [How it works](#how-it-works)
* [Installation](#installation)
* [Usage](#usage)
* [Example](#example)
* [Contributing](#contributing)
* [License](#license)

## How it works

The notebook (or Python script) defines a few helper functions and runs them in a `main()` function:

1. **`load_symspell(max_distance=5)`** – Creates a `SymSpell` object with a maximum edit distance of five. It searches for the file `frequency_dictionary_en_82_765.txt` in the `symspellpy` package or in the current working directory. If found, it loads the dictionary into memory; otherwise it instructs the user to download the file.  
2. **Default text** – A multi‑line string containing eight sentences with intentionally misspelled words. 
3. **`get_input_text()`** – Prompts the user to choose between using the default text or entering new lines. Custom input ends when the user enters an empty line.  
4. **`correct_text(sym_spell, text)`** – Tokenizes the text into words, looks up corrections via `sym_spell.lookup()` and constructs a new string where each misspelled word is replaced by the top suggestion. It also records all corrections in a dictionary for reporting.  
5. **`main()`** – Orchestrates the loading of the dictionary, gathering input, applying corrections and printing the results. It prints a report summarizing how many words were corrected and lists each original word alongside its replacement.

## Installation

To run this notebook or script you will need Python 3 and the `symspellpy` package. You also need the SymSpell dictionary file `frequency_dictionary_en_82_765.txt`.

1. **Install dependencies**:

   ```bash
   conda/mamba env create -f environment.yaml
   conda/mamba activate genai_env
   pip install -r requirments.txt
