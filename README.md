# Quota-Hora-Est-
## LATIN WORD MEANING DRIFT TRACKER   
## Abstract:
This project seeks to test a new computational method to track diachronic semantic shift. By utilizing Word2Vec and Cosine similarity, a word list of the top 50 most similar words can be created for every unique word in a Vocabulary. This process can be done multiple times with separated W2V models, each trained on text from different time periods. By repurposing the technique put forward in “Simple, Interpretable and Stable Method for Detecting Words with Usage Change across Corpora”(Gonen et al.2020), inter-model comparisons can then be quickly and accurately made for the same word at different periods. The testing of this technique was made on temporally tagged Latin corpus spanning 580 years and proved to be an effective and easily implementable way to find notable semantic shifts en masse.

## Introduction: 
There has always been a gap between different branches of linguistics. The largest gap being between historical study and computational methods. However with the rise of new NLP techniques, a change in the methodology of historical study has started to take place. Libraries like NLTK, CLTK, and SpaCy have greatly cut down on the amount of time consuming work that the average linguist must do in order to complete their research. 
Normally when studying semantic shifts, a researcher has to spend time gathering the occurrences of a word, identifying the period, and disambiguating the word sense at that period.  

Obviously this process is daunting even with the help of computers. Moreover, with the ever growing sizes of corpora nowadays, it is nearly impossible for a researcher to cover all the material alone and to do so without error. As a consequence, finding faster and more accurate ways of completing this process has become more desirable. This project seeks to further close the gap by applying a new computational approach to the tracking of diachronic semantic shifts.  

The approach is largely a recontextualization of a the technique put forth in“Simple, Interpretable and Stable Method for Detecting Words with Usage Change across Corpora”(Gonen et al.2020) and uses a combination of Word2Vec, Cosine Similarity, and Jaccard Similarity to facilitate intermodal comparisons.  In the case of this project, we will be using it to generate a qualitative measure for the stability of a word across periods of time.   

As for the language on which to test the approach, Latin proved to be an excellent candidate. Given its long use as a lingua franca, it has undergone many drastic changes (semantic or otherwise) over the centuries. Moreover, despite it being a dead language, it is very data rich. In other words, it is relatively easy to find large quantities of high quality Latin text data online.  

## Method: 
### Corpus Creation 
In order to train the models, a corpus of Latin text data that was temporally tagged had to be found. Unfortunately after much searching, we came to the conclusion that there is no available temporally tagged corpora for Latin and endeavored to create one instead. Latin texts were taken from the University of Zurich’s Corpus Corporum and Tufts University's Perseus Project.  After aggregation, the corpus spans about 580 years of Roman literary history and includes works from 11 different prominent authors such as Ovid, St.Augustine, and Virgil.  

### Data Cleaning and Lemmatization 
Each text was then cleaned using various NLP techniques (removal of stopwords, numerics, and non-native characters, case normalization, non-Latin text removed, etc). The texts were then lemmatized in order to better capture each word in all its contexts regardless of derivational form. Secondarily, it also cuts down on the vocabulary size and computational complexity. Finally the texts were split by sentences tagged for author, work, and period then added to the corpus. Total number of items in the corpus at the end of the process was 56,888.  

### Training the models 
The corpus was split into 3 sub-corpora based on the selected time periods of Latin (Golden age, Silver age, Patristic age) and were used to train 3 separated Word2Vec models. Cosine similarity was then used to generate a list of the 50 most contextually similar words for every word in the vocabulary and was then saved as a tuple as (word,[word list]). 

### Getting comparisons 
In order to do the comparisons, the word list of one word from the vocabulary at t0 would be paired up with the word list of the same word from tn. Following the Gonen et al. technique, Jaccard Similarity was used as a metric for measuring the semantic similarity between the words at different periods. Furthermore, all comparisons were done sequentially to track the stability as we moved forward in time. In other words, golden age entries were only compared with silver and silver again compared with patristic.   
### Findings:
Jaccard Similarity in combination with Cosine Similarity allows us to quickly find words with notable shifts in meaning. Moreover, this method allows for us to see when the shift begins and  period-specific wordlists can help capture the semantic start and endpoints of a shift.     

After applying the technique, the range of scores fell between .01 and .32. The highest score belonged to sum, ‘be’, which given that it is a word that plays such an integral role within the Latin language it is unsurprising that it maintained a virtually unchanged meaning over the entire timeline. Conversely, there were many words that had gone under massive semantic changes and thus had scores hovering around 0. For example, albus, meaning white, underwent extreme semantic shifts. Having originally been associated with natural light during, its meaning shifted to take on a more Christian or religious aspect. Its Jaccard similarity score between the Golden and Silver age was .05 and between the Silver and Patristic Age dropped to .01. These scores accurately depict the extreme shifts that word underwent and help solidify this technique as valid means of measuring semantic shifts.     

Ultimately this technique proved to be very easily implemented and output a score and wordlist that was easily understandable. I believe further research could be done using this method as a jumping off point. By looking for words that correspond to a certain topic or particular semantic field, one could get a sense of how Romans viewed that topic. Subsequently one could look at historical accounts to verify those findings.   





