# Neural-Machine-Translation

In this project, we train a few attention-based neural machine translation (NMT) models to
translate words from English to Pig-Latin. Along the way, we explore several
important concepts in NMT, including gated *recurrent neural networks* and *attention*.

## Pig-Latin Crash Course
Pig Latin is a simple transformation of English based on the following rules (applied on a per-word
basis):
1. If the first letter of a word is a *consonant*, then the letter is moved to the end of the word,
and the letters “ay” are added to the end: 

  `team → eamtay`<p align="center">
  
2. If the first letter is a *vowel*, then the word is left unchanged and the letters “way” are added
to the end: 
  
  `impress → impressway`

3. In addition, some consonant pairs, such as “sh”, are treated as a block and are moved to the end of the string together: 
  
  `shopping → oppingshay`

To translate a whole sentence from English to Pig-Latin, we simply apply these rules to each word
independently:
<br>
`i went shopping → iway entway oppingshay`

## Data
The data for this task consists of pairs of words <a href="https://www.codecogs.com/eqnedit.php?latex=\left\{\left(s^{(i)},&space;t^{(i)}\right)\right\}_{i=1}^{N}" target="_blank"><img src="https://latex.codecogs.com/png.latex?\left\{\left(s^{(i)},&space;t^{(i)}\right)\right\}_{i=1}^{N}" title="\left\{\left(s^{(i)}, t^{(i)}\right)\right\}_{i=1}^{N}" /></a> where the *source* <a href="https://www.codecogs.com/eqnedit.php?latex=s^{(i)}" target="_blank"><img src="https://latex.codecogs.com/png.latex?s^{(i)}" title="s^{(i)}" /></a>
is an English word, and the *target* <a href="https://www.codecogs.com/eqnedit.php?latex=t^{(i)}" target="_blank"><img src="https://latex.codecogs.com/png.latex?t^{(i)}" title="t^{(i)}" /></a> is its translation in Pig-Latin. 

The dataset is composed of unique words from the book *Sense and Sensibility*, by Jane Austen. The vocabulary consists of 29 tokens:
the 26 standard alphabet letters (all lowercase), the dash symbol -, and two special tokens `<SOS>`
and `<EOS>` that denote the start and end of a sequence, respectively. The dataset contains 6387
unique (English, Pig-Latin) pairs in total; the first few examples are:

<p align="center"> { (the, ethay), (family, amilyfay), (of, ofway), ... } </p>
 <br> 
In order to simplify the processing of _mini-batches_ of words, the word pairs are grouped based
on the lengths of the source and target. Thus, in each mini-batch the source words are all the same
length, and the target words are all the same length. This simplifies the code, as we don’t have to
worry about batches of variable-length sequences.
  
## Project Outline

Throughout this project, we implement some attention-based neural machine
translation models, and finally train the models and examine the results. We begin with first implementing the three main building blocks: gated recurrent unit (GRU), additive attention, and scaled dot-product attention. Using these building blocks, we implement two encoders (RNN and transformer encoders) and three decoders (RNN, RNN+additive attention and transformer decoders). The project is split into three parts, each of which investigating a unique encoder-decoder combination from the ones described:

* Part 1: (RNN encoder) + (RNN decoder)
* Part 2: (RNN encoder) + (RNN decoder with additive attention)
* Part 3: (Transformer encoder) + (Transformer decoder)

