## Smart Study WordPiece Tokenizer from Scratch

 ## Project Overview

This project implements a WordPiece Tokenizer from scratch using Python without using pre-built tokenization libraries.

WordPiece is a subword tokenization algorithm used by BERT-family models. Instead of selecting only the most frequent pair, WordPiece calculates a score using the frequency of the pair and the frequencies of the individual tokens.

This project demonstrates the complete WordPiece training and tokenization process using a small study-related English word dataset.

---

 ## Objectives

The main objectives of this project are:

- To understand how WordPiece tokenization works.
- To create an initial character-level vocabulary.
- To calculate token frequencies.
- To calculate pair frequencies.
- To calculate WordPiece scores.
- To select the highest-scoring pair.
- To merge subword tokens.
- To train a vocabulary automatically.
- To tokenize new words using the longest-match-first method.
- To handle unknown words using "[UNK]".
- To convert tokens into numerical Token IDs.
- To visualize vocabulary growth.

---

 ## What is WordPiece?

WordPiece breaks words into smaller subword units.

For example:

studying
↓
study + ##ing

The "##" symbol indicates that the token occurs inside a word rather than at the beginning.

The tokenizer tries to find the longest subword available in the vocabulary.

---

 ## Dataset

The project uses a small custom training dataset containing study-related words.

study      → 5
student    → 4
studying   → 3
studies    → 3
teacher    → 3
teaching   → 2
learn      → 4
learning   → 3
learner    → 2

The numbers represent the frequency of each word in the training data.

---

 ## Working Process

The project follows these steps:

Training Words
      ↓
Character Splitting
      ↓
Initial Vocabulary
      ↓
Token Frequency Calculation
      ↓
Pair Frequency Calculation
      ↓
WordPiece Score Calculation
      ↓
Select Highest-Scoring Pair
      ↓
Merge Pair
      ↓
Update Vocabulary
      ↓
Repeat
      ↓
Final Vocabulary
      ↓
Tokenize New Word
      ↓
Convert Tokens to IDs

---

 ## WordPiece Score

The WordPiece score used in this project is:

Score =
Pair Frequency
-------------------------------
First Token Frequency × Second Token Frequency

The pair with the highest score is selected for merging.

This is the main difference between BPE and WordPiece.

BPE| WordPiece
Uses pair frequency| Uses a score
Selects most frequent pair| Selects highest-scoring pair
Frequency-based| Considers individual token frequencies

---

 ## Technologies Used

- Python
- Jupyter Notebook
- Collections ("Counter")
- Matplotlib

No external NLP/tokenization library is required for the core WordPiece implementation.

---

## Project Structure

Smart-Study-WordPiece-Tokenizer/
│
├── WordPiece_Tokenizer.ipynb
│
├── README.md
│
└── requirements.txt

---

 ## How to Run

Step 1: Install Python

Make sure Python is installed on your system.

Step 2: Install Jupyter Notebook

pip install notebook

Step 3: Install Matplotlib

pip install matplotlib

Step 4: Open Jupyter Notebook

jupyter notebook

Step 5: Open the Project

Open:

WordPiece_Tokenizer.ipynb

Run each cell from top to bottom.

---

## Features

1. Initial Character Splitting

Each word is initially divided into characters.

Example:

study
↓
s ##t ##u ##d ##y

---

2. Token Frequency

The program counts how frequently each token occurs in the training dataset.

---

3. Pair Frequency

Adjacent token pairs are counted.

Example:

s + ##t
##t + ##u
##u + ##d

---

4. WordPiece Scoring

A score is calculated for every adjacent pair.

The highest-scoring pair is selected.

---

5. Token Merging

The selected pair is merged into a new subword token.

Example:

##i + ##n
↓
##in

The process continues until the desired vocabulary size is reached.

---

6. Longest-Match Tokenization

For a new word, the tokenizer searches for the longest matching subword.

For example:

student
↓
stud
↓
##ent

The exact result depends on the vocabulary learned during training.

---

7. Unknown Token

If a word cannot be completely represented using the learned vocabulary, the tokenizer returns:

[UNK]

---

8. Token IDs

Every vocabulary token is assigned a numerical ID.

Example:

"studying"
      ↓
["study", "##ing"]
      ↓
[7, 12]

The exact IDs depend on the generated vocabulary.

---

 Visualization

The project also generates a graph showing how the vocabulary size changes as merge operations are performed.

Merge Operations
       ↓
Vocabulary Growth
       ↓
Matplotlib Graph

This helps visualize the WordPiece training process.

---

 Example Pipeline

Input:
student

       ↓

WordPiece Tokenizer

       ↓

Subword Tokens:
["student"]

       ↓

Token IDs:
[...]

Another word may be divided into multiple subwords depending on the learned vocabulary.

---

## What Makes This Project Different?

This project is designed as a from-scratch educational implementation.

Unlike a simple tokenizer demonstration, it includes:

- Custom training data
- Automatic vocabulary learning
- WordPiece score calculation
- Automatic pair selection
- Repeated token merging
- Longest-match-first tokenization
- "[UNK]" handling
- Token-to-ID conversion
- Vocabulary growth visualization

Therefore, the project demonstrates both the training side and the tokenization side of WordPiece.

---

 ## Limitations

This is a small educational implementation and is not intended to replace production tokenizers used by large language models.

The training dataset is small, and the learned vocabulary is limited to the words and subwords available in the dataset.

---

 ## Future Enhancements

The project can be extended by:

- Using a larger text corpus.
- Supporting punctuation.
- Supporting numbers.
- Adding lowercase/uppercase normalization.
- Adding special tokens such as "[CLS]", "[SEP]", and "[PAD]".
- Comparing WordPiece with BPE.
- Comparing tokenization results for different vocabularies.
- Building a simple graphical user interface.
- Testing the tokenizer on larger datasets.

---

 ## Conclusion

This project provides a simple and practical implementation of WordPiece Tokenization from scratch.

By implementing vocabulary initialization, frequency calculation, scoring, merging, tokenization, unknown-token handling, and Token ID conversion, the project demonstrates how a WordPiece tokenizer works internally.

It provides a foundation for understanding the tokenization techniques used in modern NLP models such as BERT.

---

 ## Project Type

Language: Python

Platform: Jupyter Notebook

Algorithm: WordPiece Tokenization
