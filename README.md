# Big scale 2021 UBS 💸
- Sixtine Francey
- Alexandre Keusen
- Gabin Flourac

The purpose of this project is to revolutionize the way people learn and get better at a foreign language. To do so, we stand that reading is the key to improve level in a foreign language. However, this is valuable only if the text corresponds to the knowledge level of the reader. The Common European Framework of Reference for Languages: Learning, Teaching, Assessment abbreviated in English as CEFR is a guideline used to describe achievements of learners of foreign languages across Europe and, increasingly, in other countries. Knowledge levels are ranked from A1 (beginner) go C2 (proficiency). By using this labelling method, we would be able to evaluate the difficulty level of a text and in a second time,  adresse/recommend relevant ones to readers depending on their abilities to understand them. 

First step of the project: How to build a model able to evaluate the difficulty level of a text ?

## 🔎 Research phase: 	
- Multiple features can be extracted from text analysis using Lemma and Natural Language Process Tool. 
- An existing project has been made called Duolingo CEFR Checker and evaluates difficulty for a text based on the average difficulty per word. 
- Classification might be a good predictive model to evaluate Readability of a text.
- Existing datasets which evaluate french words level by their average frequency in learning books.

## 📈 Data & Github : 
The first step was to gather and create a dataset based on several sources. We tried to use diversified sources such as Wikipedia, Grammar exercises, and sources provided by the professor. After collecting 1000 sentences, we evaluated their levels objectively based on the tense verbs, the word difficulty, the structure of the sentence, its length, CEFR guideline, etc.

###Number of sentences per level
- A1 : 169
- A2 : 226
- B1 : 132
- B2 : 202
- C1 : 138
- C2 : 133

Relevant sources
https://lingolex.com/learn_french/giving_opinions_french.php
https://www.ebooksgratuits.org/ebooks.php
https://www.uqtr.ca/
https://en.wikipedia.org/wiki/Main_Page
https://www.lawlessfrench.com/faq/lessons-by-level/a2-reading/
https://lingua.com/french/reading/
https://french.kwiziq.com/learn/reading

We found interesting datasets related to verb conjugation and word difficulty. We intend to use them later in our model.

Relevant sources
https://cental.uclouvain.be/cefrlex/flelex
https://www.language-databases.com/database-conjugation.html

Then, we created a Github where we put several datasets and research papers. We will update it as well as this ReadMe file as we progress in the progress.

## ⚙️ Feature Extraction / Modeling 

### Main approach : 
Determine an overall score/level for each sentence based on the verb tense, word difficulty and cognates words. Indeed, some tenses and words are more difficult than others (we learn present tense first, and more complex tenses after). Conversely, cognates can be easier to learn and use. 

### Feature Extraction : 
- Verb Conjugation : From several sources, we saw that verb tenses are correlated with the difficulty of the language. Typically, we learn first present tense which requires basic knowledge and then, we will start to learn more complicated ones. We found a DB which contains a lot of verbs, conjugated in all tenses. We want to associate each tense with a difficulty level (A2, B1, …). The idea is that every time a verb in a text matches with one in the DB, it will return us the tense and the difficulty.

- Lemmatization categories : In order to standardize our sentences and to determine which word is part of a certain type (Adjective, Noun, Verb, …)

- Word difficulty : words (e.g. pronouns, verbes, nouns) can be evaluated using CEFR classification. We will try to extract some features in order to emphasize the average level of a set of french words using frequency. We will also use the FLELex-CRF dataset.   

- Cognates words : Some words have similarities from a language to another and when learning a new language, these words would be easier to understand, use and remember. That is why, we plan to take it into account in our model. A word which is similar to another from a different language should depreciate the overall difficulty of the sentence. We plan to assign a grade or a coefficient related to the similarities of words between languages and when a cognate word appears in a text, it will reduce its grade.


### Modelling : 
- Simple algorithm (heuristic) : Frequency Level 
- Deep Learning (Transfer learning) : Finetune an existing language model to our classification task.  

## 🏅 Performance
Confusion Matrix, F1 score, etc. → Make a choice between model 

## 🚘 Auto ML :
we will use this method to include AI perspective and let our pipeline evolve by itself by automating some processes.  

## 🤖 Build API : 
Restful API with flask and Microsoft Azure server
