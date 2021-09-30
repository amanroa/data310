# Final Project

## Video Presentation

[Here is my presentation!](https://www.youtube.com/watch?v=LEXrYl_rzew)

## Abstract

Artificial Intelligence is becoming our new normal. Siri,
Alexa, Google Home, all of these machines use AI. Even 
every day machines and apps use some form of AI or machine 
learning to make our lives simpler. However, we learned in 
ethics that these machines that use AI aren't really "intelligent",
because everything about them was created by a human. Their
code, their algorithm, etc. Therefore, they cannot make their
own "intelligent" decisions. However, I would like to propose
a step towards creating "intelligent" machines. In class,
we learned about Text Generation. I want to know if,
using a dataset of code, I can get a text 
generation model that can learn how to write code and 
output its own runnable program. 
The program does not have to be complex, it can be something
very simple, but it will be very interesting to see if a 
computer can really write its own program.

## Data

I am using [this text file](https://www.kaggle.com/veeralakrishna/python-code-data)
from Kaggle. It can also be found on The School of AI's site.
It has 4600+ entries of mostly simple Python programs. The
model that I used was taken from [this website](https://towardsdatascience.com/building-a-python-code-generator-4b476eec5804),
more specifically, [here](https://github.com/divyam96/English-to-Python-Converter). 
The way that this text file is laid out is: description, then code. 
Here is an example. 

    # write a python function to add two user provided numbers and return the sum
    def add_two_numbers(num1, num2):
        sum = num1 + num2
        return sum

## Model

The model consists of an Encoder, a Decoder, and an Attention
mechanism. The creators also decided to treat this as a 
Sequence to Sequence problem. A Seq2Seq model turns
one sequence into another sequence, using an RNN and a 
GRU/LSTM. Each Seq2Seq model includes an Encoder and a 
Decoder. The Encoder takes the input and turns it into a 
vector with the item and its context. The Decoder takes the
vector and converts it back into output. This model also uses
Attention, which lets the Decoder or Encoder look at specific parts 
of the vector that are the most important. 

The creators of this model included some very helpful 
graphics of the Encoder, Decoder, and Attention mechanism.

### Encoder

![](https://camo.githubusercontent.com/f5e9af2d641603536654d6d1551881c51573a1f0/68747470733a2f2f7261772e67697468756275736572636f6e74656e742e636f6d2f62656e747265766574742f7079746f7263682d736571327365712f393437396663623533323231346164323666643462646139666366303831613035653161616634652f6173736574732f7472616e73666f726d65722d656e636f6465722e706e67)

The Encoder consists of Encoding Layers, which use a 
Multi-Head Attention model. This helps the model focus on
the more important aspects of the input. A Multi-Head model
can look at multiple inputs in parallel, increasing the learning
capacity of the model. Here is a graphic of a Multi-Head Attention model. 

![](https://camo.githubusercontent.com/2ee38f2359aa03ae42b9b22ef111fcf19d1cc95d/68747470733a2f2f7261772e67697468756275736572636f6e74656e742e636f6d2f62656e747265766574742f7079746f7263682d736571327365712f393437396663623533323231346164323666643462646139666366303831613035653161616634652f6173736574732f7472616e73666f726d65722d617474656e74696f6e2e706e67)


### Decoder

![](https://camo.githubusercontent.com/9bded9703e3f61fba6a5c4cb7f80fa0f34bf7f04/68747470733a2f2f7261772e67697468756275736572636f6e74656e742e636f6d2f62656e747265766574742f7079746f7263682d736571327365712f393437396663623533323231346164323666643462646139666366303831613035653161616634652f6173736574732f7472616e73666f726d65722d6465636f6465722e706e67)

The Decoder is similar to the Encoder, except it receives
two input values. Those values are the target sequence and
the vector from the Encoder. The Decoder also has Decoder
Layers that use two types of Attention: Multi-Head and 
Self-Attention. The Decoder uses two Multi-Head Attention
operations, which differentiates it from the Encoder. 

### Seq2Seq

Sequence to Sequence is a type of machine learning algorithm
used for language processing. It was developed by Google. 
It can be used in many ways, but one of the main ways 
that it is used is in language translation.
I think this is why the developer of this model chose it for 
this problem, because we are essentially "translating"
English to Python. Certain words in English correspond to 
different words in Python. For example, "function" could 
translate to "def". 

This was the main part of the model. This is where the 
Encoder and Decoder were used. 

![](https://github.com/divyam96/English-to-Python-Converter/blob/main/res/transformer_multihead.png?raw=true)

This is the full model.

# Model Performance

## Running

The website which I took the model from suggested that I run 50 epochs. However, I only did 2 runs - one of 5 epochs and the other of 10. 
This is because each epoch took about 6 minutes to run. One example of an epoch that I got was Epoch 10. It took 5 minutes and 40 seconds,
with a TrainLoss of 3.270, Train PPL of 26.305, ValLoss of 3.690, and Val PPL of 40.059. 

## Testing 

The website where I got the model from tested their code by typing in one phrase at a time. I found this very time consuming, so I just 
compiled 25 phrases in a text file and ran them in a for loop. Examples of phrases are "write a python program to merge two dictionaries",
"write a function to find factorial", and "function to find the reverse of a string". When I ran 5 epochs and analyzed the results, I 
found that 3/25 inputs created correct programs, with 3 programs that were "almost correct". When I ran 10 epochs, I got 2/24 inputs correct.
The second run only had 24 inputs because I was getting an error with one of the inputs that I was not getting with the 5 epoch run. 

Here is an example of an incorrect, almost correct, and correct output and the inputs that produced them. 

<img width="875" alt="Screen Shot 2021-09-30 at 10 24 14 AM" src="https://user-images.githubusercontent.com/26678552/135473778-3583bfb1-9543-420e-b1dd-9a92c905ac4b.png">

The incorrect program is simply a jumble of letters and symbols, and does not accomplish anything. However, I'd like to point out that most of the 
incorrect programs that I generated did not look like this. They were mostly incomplete programs, programs that just did not make sense, or programs that did not 
work. 

An 'almost correct' program is in the middle square. At first glance, this factorial program looks really good, and I almost counted it as correct. However, there 
is one thing that really changes the program, and that is the if statement. The if statement says "if n == 1:". However, it should be "if n <=0:" or "if n == 0:". 
This is very important, because if we ran this program as is and passed n = 0, it would run infintely. So we needed a condition to handle numbers <=0, which is why 
I counted it as almost correct.

Finally, we have a correct program. I did not count the name of the method when determining incorrectness and correctness, because I did not expect the computer to
understand the complexities of what it should name the method or its variables. So barring that, all of this is correct.

## Future Testing

As my machine was limited in the number of epochs it could run, I would like to use a more powerful machine to run more epochs 
in the future. Additionally, this algorithm is very complex, and I want to study it and understand it more. 

Finally, I would like to try providing
the computer with more complex inputs. The inputs that I tested are very simple, and although they may be useful to write simple programs, I think that this 
algorithm can really help us programmers with writing more complex programs. It would be really cool to create an algorithm that can write complex
programs with just English input. This kind of algorithm would cut down the amount of work that programmers do significantly, allowing them to 
complete more projects with greater efficiency (this algorithm would avoid simple errors caused by humans, such as forgetting parentheses, semicolons, 
brackets, and quotations). 

