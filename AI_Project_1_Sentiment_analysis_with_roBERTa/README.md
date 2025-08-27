# Gen_AI_Project 1

Sentiment Analysis on the IMDB dataset from HugginFace
What it does: takes movie reviews as input and returns "positive" or "negative".
Approach: 
1. Runs roBERTa and fine tunes all weights and evaluate results
2. Runs roBERTa + LORA and evaluate the results again

Conclusion: roBERTA + LORA is much faster and with better accuracy, suprisingly! 


* PEFT technique: LoRA
* LLM Model: roBERTa
* Evaluation approach: epoch
* Fine-tuning dataset: imdb
* libraries used: from HugginFace
