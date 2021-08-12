# Week Four, Day Two: Thursday (7/29/2021)
*Using the Text generation with an RNN script we developed during today's class, use the shakespeare.txt file to generate your own text that imitates the script from Shakespeare. Produce your generated text and describe how it was produced, addressing the following aspects.*
- *Processing, vectorizing and predicting text*
- *Building and training the model*
- *Generating text* 

## Producing the Model
To generate text that resembled a Shakespeare script, the model needed to be character-based, with a robust dataset that it could learn from before trying to replicate. The model itself was trained by first loading in a dataset of 1115394 characters consisting of combinations of 65 unique characters. The characters in this dataset were tokenized and vectorized (each character was given a numerical ID that the model could process better than its alphabetical counterpart). Then, the model was given the task of predicting what character would come next given a one-char minimum sequence, and was trained to accomplish this task by using three keras layers consisting of an input layer that matched character IDs to vectors, a GRU layer, and a dense output layer. The model then generated text by finding the predictive embedding for a given character, running the GRU with the embedding as input, and applying the dense output layer to determine which character should come next based on logarithmic likelihood.

## Results of the Model
The model ran for twenty epochs and was able to produce a somewhat readable text. Although it contains some gramamtical inconsistencies, spelling errors, and no real thread of conscious plot, it certainly sounds Shakespearean in its construction. 

ROMEO:

Thou art a bark! Though straight downright.


CAMILLO:
I was a fooler in the cause of his

counterfeit, speak weather; and the would revolting well

As for Coffer to their eyes,

And thou shalt see if I live in will:

What is the fight of cut off, closed pinch,

I'll find thee, keep your country's flight.


QUEEN:

Without thee to a censure of yours i' the dire,

Or of your distress't pleasure untimely

To yours, and speak to the duke: you being this new-day,

That cannot departed hither where for tents.


KING RICHARD III:

Ricerong, although

your peace in blood wereth three-piled stconlague.

And, to prepate which rends so loaths not

Of strongly.


AUTOLYCUS:

I confess to our southward back thou canst not keep ore:

yet I must not, to hide me not: my heart is peat,

And hath hid with some green seem's wind,

Or like a prayer than one part to speak a man

Have made them an answer to my shunning swords!

Look, when some great great presence thou art,

No, I pray, for to return to you wot well.
