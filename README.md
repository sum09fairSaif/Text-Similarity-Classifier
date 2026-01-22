Text Similarity Classifier (Python)
Overview

This project is a fully self-designed and independently implemented text similarity classifier built in Python as the final project for CS111: Introduction to Computer Science I course that I took in Fall 2024. The system models bodies of text statistically and determines which known source a new, unknown text is most likely derived from.

Unlike black-box machine learning models or prebuilt NLP libraries, every component of this classifier was built from first principles, including text preprocessing, feature extraction, probability modeling, similarity scoring, and classification logic.

This project demonstrates a strong understanding of:

Core Python programming

Data structures (dictionaries, lists)

Algorithmic thinking

Basic statistical language modeling

Software design, testing, and debugging

Project Purpose

The primary goal of this project was to:

Explore how texts can be represented numerically

Understand how statistical patterns differ across writing styles

Build a transparent, interpretable text classifier

Apply probability and logarithmic scoring to real-world data

Design a reusable object-oriented system for text analysis

Rather than predicting sentiment or topics, this classifier answers the question:

“Given two known text sources, which one is more likely to have produced this unknown text?”

What This Project Does

At a high level, the classifier:

Analyzes text corpora and extracts multiple linguistic features

Builds statistical models for each text source

Computes log-likelihood similarity scores

Classifies an unknown text by comparing it against known sources

Core Features Extracted

Each TextModel object represents a body of text and captures five distinct feature sets, all stored as frequency dictionaries:

1. Word Frequency

Counts how often each word appears

Text is lowercased and cleaned of punctuation

Captures vocabulary usage and stylistic differences

2. Word Length Distribution

Records how frequently words of each length appear

Helps distinguish concise vs. complex writing styles

3. Stem Frequency

Custom-built stemming algorithm

Removes common prefixes and suffixes

Groups morphological variants of words

Implemented without external NLP libraries

4. Sentence Length Distribution

Measures how many words appear per sentence

Uses punctuation-based sentence detection

Captures structural writing patterns

5. Vowel Count per Word

Tracks how many vowels appear in each word

Acts as a subtle stylistic and phonetic feature

Each of these features contributes independent evidence toward classification.

Text Preprocessing
Cleaning

Text is cleaned by:

Removing punctuation and special characters

Converting to lowercase

Splitting into words

Stemming

A custom stemming function was designed to:

Handle common English prefixes (un-, dis-, in-, etc.)

Remove suffixes (-ing, -ed, -ly, -ness, etc.)

Preserve exceptions and irregular words

Avoid overstemming common English terms

This stemmer is intentionally rule-based and transparent, prioritizing clarity over completeness.

Statistical Similarity Model
Log-Likelihood Scoring

Similarity between two models is computed using log probabilities, which:

Prevent numerical underflow

Allow additive scoring

Penalize unseen words appropriately

For each feature dictionary:

Observed frequencies are normalized

Log probabilities are accumulated

A small fallback probability is used for unseen features

Each feature produces a log similarity score, and all scores are compared across sources.

Classification Logic

To classify an unknown text:

The text is modeled as a TextModel

It is compared independently against two known sources

Feature-wise similarity scores are computed

The source that “wins” the most feature comparisons is selected

This majority-based approach avoids over-reliance on any single feature.

Object-Oriented Design
TextModel Class

Each TextModel:

Represents a body of text

Stores feature dictionaries

Can save and reload itself from disk

Can compare itself to other models

Supports classification between sources

This design allows:

Reusability

Clear separation of concerns

Easy experimentation with new texts

File Persistence

Models can be:

Saved to disk as text-based dictionary files

Reloaded later for reuse or comparison

This allows training and classification to be separated across sessions.

Example Use Case

The included test setup:

Trains models on articles from two different news sources

Classifies a mystery article

Outputs similarity scores for transparency

Reports the most likely source

Learning Outcomes

Through this project, I gained experience with:

Designing algorithms from scratch

Implementing probabilistic reasoning in code

Working with real text data

Debugging complex logical flows

Writing modular, extensible Python programs

Thinking critically about feature selection
