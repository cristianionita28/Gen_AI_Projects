# SymSpell + BERT Spellchecker

This project combines **SymSpell** (a fast method for looking up near‑matching words in a dictionary) with **BERT** (a language model that understands context) to correct mistakes in text. SymSpell generates candidate corrections, and BERT selects the candidate that best fits the sentence context.  
The goal of this repository is to provide a clean, reproducible implementation along with guidance on how to install, use and extend the code.

## Table of Contents

* [How it works](#how-it-works)
* [Installation](#installation)
* [Usage](#usage)
* [Contributing](#contributing)
* [License](#license)

## How it works

1. **Loading the SymSpell dictionary (`load_symspell`)**  
   - Creates a `SymSpell` object with `max_dictionary_edit_distance=3`, meaning it can suggest words up to a Levenshtein distance of three letters.  
   - It looks for the file `frequency_dictionary_en_82_765.txt` in the `symspellpy` package or in the current directory. This file contains words and their frequency of occurrence.  
   - Loads the dictionary into memory so that SymSpell can quickly propose corrections.

2. **Loading the BERT model (`load_bert`)**  
   - Uses the `pipeline("fill-mask", model="bert-base-uncased")` function from the HuggingFace library.  
   - This creates a “Masked Language Model” that can predict which word best fits a sentence when you replace a word with `[MASK]`.

3. **Selecting the best candidate (`choose_best_with_bert`)**  
   - For each misspelled word, SymSpell generates a list of candidate corrections.  
   - The function replaces the current word in the sentence with `[MASK]`, then asks BERT to predict appropriate words.  
   - It builds a dictionary of scores, associating each word predicted by BERT with its probability.  
   - It maps the SymSpell candidates to the BERT scores (or 0 if BERT didn’t propose them) and selects the candidate with the highest score.

4. **Preserving capitalization (`apply_original_casing`)**  
   - Adjusts the final candidate to match the original word’s casing: if the original was uppercase, the correction is also uppercase; if it started with a capital letter, the correction starts with a capital letter.

5. **Correcting the text (`correct_text`)**  
   - Splits the text into sentences so BERT can work with full context.  
   - Splits each sentence into words and generates candidates for each word using SymSpell.  
   - If the original word is already among the candidates (so it appears correct), it does nothing.  
   - Otherwise, it reorders the candidates with BERT and applies the best correction, preserving the original form.  
   - Reconstructs the text with the corrections applied.

6. **User interface (`get_text` and `main`)**  
   - Asks the user whether they want to use the default misspelled text (`default_text`) or enter their own text.  
   - Displays the corrected text and a report of all words that were replaced.

## Installation

To get started with this project you will need a Python environment (Python 3.8+ recommended) and a few dependencies.  

1. **Clone or download** the repository to your local machine.
2. **Install required packages** using your preferred package manager.  

   ```bash
   conda/mamba env create -f environment.yaml
   conda/mamba activate genai_env
   pip install -r requirments.txt

