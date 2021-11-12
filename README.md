# Let's Make it Pope-litical!

### Abstract
At first glance, one might think that the Pope does not have much impact on our everyday life and on our country’s politics, yet he influences over 1.3 billion Catholics worldwide and regularly meets with the most powerful political figures of the planet. In the present work, we want to investigate how one of the mightiest apolitical figures on Earth [1] influences one sixth of the world population by using a novel quotations corpus : Quotebank. The main idea is therefore to try to situate the Pope on a political spectrum, here the American political system, using characteristics extracted from the corpus of his quotes. This will help us determine whether such an influential and, suposedly, non-political figure can be aligned with a certain political party or not.
### Research questions

* Can we place the Pope on a simple political spectrum (e.g. American Democrates vs Republicans) using solely the quotations ?
* What crucial features of the quotations will we need to do that ?
  * Is the use of lexical fields in an individual's citation corpus sufficient?
  * Can performing sentiment analysis on quotes with similar topics be relevant and used to extract new features?

### Methods

The political spectrum we chose to place the Pope on is the American bipartite system with on one end the Democratic Party and on the other the Republican Party. We chose this system because Quotebank corpus is in English, their political spectrum is particularly simple and a high number of quotations are from American politicians. Our general approach consists in :
1. Extracting meaningful features from the quotations corpus of the pope
2. Doing the same for a few emblematic American political figures 
3. Applying a principal component analysis (PCA), each datapoint is one speaker
4. Appreciating the relative position of the politicians with regards to the pope in a 2D PCA

So far, we chose three Democrates and three Republicans with a substantial number of quotes and with varied predicted position on the political spectrum (either central or on the edge of the spectrum) [2,3,4].

| Political figure | Party      | Predicted position   | Number of quotations |
|------------------|------------|----------------------|----------------------|
| Elizabeth Warren | Democratic | Edge Democrates      | 48'397               |
| Bernie Sanders   | Democratic | Edge Democrates      | 84'018               |
| Hillary Clinton  | Democratic | Central Democrates   | 95'458               |
| Ted Cruz         | Republican| Edge Republicans     | 46'301               |
| Mike Pence       | Republican| Edge Republicans     | 46'893               |
| Mitt Romney      | Republican| Central Republicans  | 10'651               |

#### External libraries
* empath
* scipy
* langdetect

#### Pre-Processing
First, we transform the speakers' probability from object type into float numbers to simplify future analysis. We eliminate from the data the quotes that have too low a first speaker probability. Then, we perform simple pre-processing steps on the quotes such as removing the digits, punctuation, spaces at the beginning and ending of quotes, capitalization from words and removing rows with empty quotes. We also tokenize the quotes (break the strings into tokens) to remove the stop words and lemmatize the quotes to focus on meaning. Finally, after performing these steps, we delete quotes that are not in English.

#### Feature extraction
Then, we want to extract interesting features in the quotes that could ideally be used to cluster the different speakers into political groups and enable to find the Pope's position on this political spectrum. The first features that we extract for each speaker are:
* The median of the number of words in the quotes
* The median of the number of characters in the quotes
* The median of the number of occurences of the quotes
* The richness of the vocabulary, that we compute by counting the number of different words in the pre-processed quotes and by dividing it by the total number of quotes of the speaker.
* The scores returned by the analyze function of the Empath library for different lexical categories. We choose the categories listed below, and obtain a score for each one of them:  
*money, hate, family, health, dispute, nervousness, government, swearing_terms, suffering, optimism, divine, sexual, fear, business, religion, worship, leader, death, violence, military, war, rage, science, sadness, joy, economics, politics, anger, strength, power, terrorism, poor, pain, philosophy, negative_emotion, competing, law, achievement, contentment, positive_emotion*
   

### Timeline
In the following weeks we will implement our future intermediate milestones and think of additional approaches to deepen our project:

* Week 11: Improve pre-processing, feature extraction, PCA and PCA validation taking into account the feedback from Milestone 2
* Week 12: Develop sentiment analysis features, add other speakers to our analysis and try political party classification 
* Week 13: Finalization of the project

### Organization within the team
* Improve pre-processing techniques:  investigate faster language detection techniques and optimize the `probability` threshold method
* Check if the extracted features are relevant and not correlated with one another.
* Investigate if sentiment analysis can be used as a feature for the PCA (by extracting the general sentiment over a specific topic for each speaker), using VADER library
* Add other politicians or compare the Pope with another religious figure (Dalai Lama)
* Classify by party (Republican, Democratic, Apolitic) using a subsample of a speaker's quotes 

### Questions for the TAs
Do you advise us to focus mainly on improving our feature extraction for the PCA or adding a new axis to our project?


### References:
[1] https://www.forbes.com/profile/pope-francis/?list=powerful-people&sh=2f8961946e0a

[2] https://www.businessinsider.com/2020-democratic-presidential-candidates-political-spectrum-ranking-2019-5?IR=T

[3] https://www.bbc.com/news/election-us-2016-35703300

[4] https://www.isidewith.com/



