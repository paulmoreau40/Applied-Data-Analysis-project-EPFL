# Let's Make it Popelitical
# Let's Talk about Popelitics
# Popelitical Spectrum

### Abstract
At first glance, one might think that the Pope does not have much impact on our everyday life and on our country’s politics, yet he influences over 1.3 billion Catholics worldwide and regularly meets with the most powerful political figures of the planet. In the present work, we want to investigate how one of the mightiest apolitical figures on Earth [1] influences one sixth of the world population by using a novel quotations corpus : Quotebank [2].

### Research questions

* Can we place the Pope on a simple political spectrum (e.g. American Democrates vs Republicans) using solely the quotations ?
* What crucial features of the quotations will we need to do that ?
  * Is the use of lexical fields in an individual's citation corpus sufficient?


### Additional datasets


### Methods
#### Choice of speakers/ Different datasets
#### Pre-Processing
First, we perform the crucial step of pre-processing the data. This enhances the quality of the feature extraction we perform in the following steps. We transform the speakers' probability from object type into float numbers to simplify future analysis. We eliminate from the data the quotes that have too low a first speaker probability. (EXPLIQUER SI THRESHOLD) Then, we perform simple pre-processing steps on the quotes such as removing the digits, punctuation, spaces at the beginning and ending of quotes, capitalization from words and removing rows with empty quotes. We also tokenize the quotes (break the strings into tokens) to remove the stop words and lemmatize the quotes to focus on meaning. Finally, after performing these steps, we delete quotes that are not in English.

#### Feature extraction
Then, we want to extract interesting features in the quotes that could ideally be used to cluster the different speakers into political groups and enable to find the Pope's position on this political spectrum. The first features that we extract for each speaker are:
* The mean, median and standard deviation of the number of words in the quotes
* The mean, median and standard deviation of the number of characters in the quotes (this is probably redundant! QUE DIRE?)
* The mean, median and standard deviation of the number of occurences of the quotes
* The richness of the vocabulary, that we compute by counting the number of different words in the pre-processed quotes and by dividing it by the total number of quotes of the speaker.
* The scores returned by the analyze function of the Empath library for different lexical categories. We choose the categories listed below, and obtain a score for each one of them:  
*money, hate, family, health, dispute, nervousness, government, swearing_terms, suffering, optimism, divine, sexual, fear, business, religion, worship, leader, death, violence, military, war, rage, science, sadness, joy, economics, politics, anger, strength, power, terrorism, poor, pain, philosophy, negative_emotion, competing, law, achievement, contentment, positive_emotion*
   

#### Place the Pope on a political spectrum


#### Validate our method


### Timeline

#### Intermediate steps until Milestone 3


### Questions for the TAs


### References:
[1] Forbes list of the World's Most Powerful People, Forbes, 2018, https://www.forbes.com/profile/pope-francis/?list=powerful-people&sh=2f8961946e0a, last accessed November 10 2021

[2] Vaucher Timoté, et al. "Quotebank: A Corpus of Quotations from a Decade of News." (2021) Proceedings of the 14th ACM International Conference on Web Search and Data Mining


