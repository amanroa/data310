# Text Generation with RNN

In this exercise, we used a text from Romeo and Juliet to
train a model. The model used 3 steps to create it's output. 

### Processing, vectorizing, and predicting text

The first part of the program was to convert
letters into numbers. This makes it easier for the 
computer to build a model and come up with an output, 
as models use weighted sums to calculate an output. We 
also needed to create a method to turn numbers back into
letters/characters, so we could read the final output.

Next we had to train the computer to predict a phrase.
We took the phrase and used all characters except the last
one as the input, and that same phrase without the first
character as the target. This helps the computer associate
a phrase with a letter, so it knows what to output to complete
the phrase. 

### Building and training the model

The model that we used has 3 layers, two of which are input
and output layers. The middle layer is an RNN layer, 
specifically a GRU layer. This model takes the letters,
converts them into numbers, performs the algorithm, and 
gives back what it thinks are the next characters.

When training the model, we added an optimizer and a loss
function.

The model took a while to train, so I only trained it for 3 
epochs.

### Generating Text

To generate text, I ran a for loop for 1000 cycles. Each
cycle takes the input character/phrase and predicts what
will come next. Then that new prediction is sent back
through the for loop as a new input, and the cycle continues.
The very first input phrase I gave the model was 
'ROMEO:'. 

And this was the text that came out of it! Enjoy :) 

    ROMEO:
    
    Will not, that?
    
    Simon:
    
    But no thou musting's will wou bright rrown.
    
    SICINIUS:
    
    Mare wonsore take and may ame baik of
    
    York that desarge in very any do;
    
    Even wo brow tho no last sbirch with celvermone:
    
    Your conouriep and winctly taldwer whore, thy that:
    
    'Twill that thy frinces
    
    Well that hay be 
    
    KING EDWARD IV:
    
    what nare, he looks, are good ofre.
    
    First Yor:
    
    Is is hay myse catter, I knew have;
    
    And that the prevent, where's shalls
    
    With lige to. Would and my mistice?
    
    MENENIUS:
    
    Why, he was many, come, go, coult and worthy trity offeced
    
    viched trow thou a liresule-are princedies;
    
    I know, new the down to yee? By re unto
    
    Ansidrome, and thy king and makes, lathers will that
    
    and so enderntime the peritol would
    
    Had not let me caubin, must no.
    
    CAMILLO:
    
    Farthall hore, thence farsule and as your manqubre
    
    And bas for at a from both saignt?
    
    And againiked sore bolidering nor.
    
    SIANSA:
    
    In, in wear this try I at
    
    He it 'taibled shil;
    
    On pad with it forlive both or'T!
    
    Will Coret, prownot, O soe and, make 


This text is interesting, because it is kind of on the 
border between making sense and being completely gibberish.
I also thought it was interesting that the model came up with
new characters. To improve the model, I would have run it for
more epochs. 





