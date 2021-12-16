# Let's Make it Pope-litical!

### Abstract
At first glance, one might think that the Pope does not have much impact on our everyday life and on our country’s politics, yet he influences over 1.3 billion Catholics worldwide and regularly meets with the most powerful political figures of the planet. In the present work, we want to investigate how one of the mightiest apolitical figures on Earth [1] influences one sixth of the world population by using a novel quotations corpus : Quotebank. The main idea is therefore to try to situate the Pope on a political spectrum, here the American political system, using characteristics extracted from the corpus of his quotes. This will help us determine whether such an influential and, suposedly, non-political figure can be aligned with a certain political party or not. If you want to learn more without scrolling through a boring notebook, check this amazing website: http://MelissaEPFL.github.io/Popelitical

### Research questions

* Can we place the Pope on a simple political spectrum (e.g. American Democrates vs Republicans) using solely the quotations ?
* What crucial features of the quotations will we need to do that ?
  * Is the use of lexical fields in an individual's citation corpus sufficient?

### Methods

The political spectrum we chose to place the Pope on is the American bipartite system with the Democratic and Republican Partys. We chose this system because Quotebank corpus is in English, their political spectrum is particularly simple due to its binarity and a lot of data (i.e. quotations) come from American politicians. Our general approach consists in :
1. Extracting meaningful features from the quotations corpus of the pope
2. Doing the same for a few emblematic American political figures 
3. Applying a principal component analysis (PCA), each datapoint is one speaker
4. Appreciating the relative position of the politicians with regards to the pope in a 2D PCA

We chose six Democrates and six Republicans with a substantial number of quotes and with varied predicted position on the political spectrum (either central or on the edge of the spectrum) [2,3,4].

| Political figure | Party      | Predicted position   | Number of quotations |
|------------------|------------|----------------------|----------------------|
| Elizabeth Warren | Democratic | Edge     | 48'397               |
| Bernie Sanders   | Democratic | Edge     | 84'018               |
| Hillary Clinton  | Democratic | Central   | 95'458               |
| Alexandria Ocasio-Cortes | Democratic | Edge | 18'653 |
| Pete Buttigieg | Democratic | Central | 24'523|
| Kamala Harris | Democratic | Central | 19'091|
| Ben Carson | Republican | Central | 22'448 |
| Marco Rubio| Republican | Edge | 41'650 |
| Nikki Haley| Republican | Central | 24'533 |
| Ted Cruz         | Republican| Edge Republicans     | 46'301               |
| Mike Pence       | Republican| Edge Republicans     | 46'893               |
| Mitt Romney      | Republican| Central Republicans  | 10'651               |

#### External libraries
* empath
* scipy, sklearn
* fastText (pre-trained model)
* matplotlib-venn
* spacy, nltk
* plotly, word cloud

#### Pre-Processing
First, we transform the speakers' probability from object type into float numbers to simplify future analysis. We eliminate from the data the quotes that have too low a first speaker probability. Then, we perform simple pre-processing steps on the quotes such as removing the digits, punctuation, spaces at the beginning and ending of quotes, capitalization from words and removing rows with empty quotes. We also tokenize the quotes (break the strings into tokens) to remove the stop words and lemmatize the quotes to focus on meaning. Finally, after performing these steps, we delete quotes that are not in English with a pre-trained model from fastText.

#### Feature extraction
Then, we want to extract interesting features in the quotes that could ideally be used to cluster the different speakers into political groups and enable to find the Pope's position on this political spectrum. The first features that we extract for each speaker are:
* The median of the number of words in the quotes
* The median of the number of characters in the quotes
* The median of the number of occurences of the quotes
* The richness of the vocabulary, that we compute by counting the number of different words in the pre-processed quotes and by dividing it by the total number of quotes of the speaker.
* The scores returned by the analyze function of the Empath library for all the available lexical categories.
* Pronouns perspective: the way a speaker talks based on frequency of the pronoun used (I, you, we).

#### Features selection for the final 2D PCA 

This task was performed on three parts:

* Features with low variance were removed at a threshold based on their distribution 
* When two features were too highly correlated (|r| >= 0.95) one was removed
* A random forest of 10’000 trees was trained to then find the optimal combination of features.

This selection led us to the the following features:
cold, occupation, nervousness, royalty, wealthy, journalism, blue collar jobs, college, optimism, real estate, home, divine, leader, celebration, violence, military, air_travel, meeting, war, urban, appearance, warmth, youth, politics, breaking, power, terrorism, negotiate, children

### tagADA-team members contribution
* Luca : EDA, pre-processing, ReadMe, Code cleaning
* Melissa : Website, …
* Paul : .Feature selection, … 
* Estelle : Website, …


### References:
[1] https://www.forbes.com/profile/pope-francis/?list=powerful-people&sh=2f8961946e0a

[2] https://www.businessinsider.com/2020-democratic-presidential-candidates-political-spectrum-ranking-2019-5?IR=T

[3] https://www.bbc.com/news/election-us-2016-35703300

[4] https://www.isidewith.com/



