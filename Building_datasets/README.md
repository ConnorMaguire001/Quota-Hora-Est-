# These are the required elements to building the final data that will be used to train the Word2Vec models  
## The Corpus Builder   
This code takes the dir with all the collected texts of an author and formats it into a Pandas DataFrame. 
Each sentence in a text becomes a unique entry with the features: 
Author of the work, Period in which was written, the name of the work, the sentence, the sentence tokenized, the sentence tokenize and lemmatized    

## The Data Aggragator
This code unites all the smaller, author specific datasets and concatanates them into the inal dataset. 
The final dataset can be found in the file, final.rar.

## Raw Texts
Contains the raw texts in xml form 

## Final Datasets
The datasets for each author 





