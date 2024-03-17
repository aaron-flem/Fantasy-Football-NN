# Fantasy-Football-NN

## Introduction
This is an initial attempt at using a simple multi-layer perceptron to predict whether a player will increase in fantasy football draft rank the next year. The most value you'll get from this project is 1) a baseplate for creating predictions about fantasy football player performance and 2) some simple curated datasets on the last 10 years of players to use for training.

## Model Description
The model generates a predicted class of whether a player will be a "Boom" or a "Bust" in the following year. A player is "Boom" if they increase in value, and "Bust" if the drop in value. This is pretty loose criteria (i.e. a player could increase a single draft spot and be a "Boom"), but this is just a starting point and can easily improve. Most public models try to predict overall scores a player will generate in the upcoming year (which most sites do already anyways) so I wanted an alternate prediction that gives value. In my league we keep 2 players per year, so it's helpful to identify players who are likely to have increasing value regardless of their overall score.

## Data Description
The data that is used is pulled from (https://www.fftoday.com/index.html). It uses very simple features, so this is good spot to improve this model in the future.

Current features include: 
- Position (one-hot-encoded)
- Team (one-hot-encoded)
- Number of Seasons Played
- Boom or Bust Previous year (i.e. did they increase in value the year before)
- Bye Week

## Model Performance
The predictions for the model aren't fantastic - the test AUC for the model is ~0.6AUC, which is normally better than chance. However, if you look at accuracy the actual performance is ~52%. The AUC isn't helpful here because of label imabalance where there are many more busts than booms. This is largely because I'm not including players that are outside of the first 150 picks (you can imagine many players who are new that are breakouts). Definitely plan to include these players in the future.

Below is a confusion matrix on the performance of the model on holdout data. You can see the model learns to be overly conservative, predicting most players to bust. Overall the model predictions more often will correctly pick a boom than incorretly pick a boom.

![image](https://github.com/aaron-flem/Fantasy-Football-NN/assets/133904679/7c220c24-92d7-423c-9ee2-3e22291baddb)

Hope you enjoy looking at the code. Feel free to use the data / code for whatever your purpose is. 
