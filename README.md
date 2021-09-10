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
The data for this task consists of pairs of words![formula](https://render.githubusercontent.com/render/math?math=$\left\{\left(s^{(i)}, t^{(i)}\right)\right\}_{i=1}^{N}$) where the *source* $s^{(i)}$
is an English word, and the *target* $t^{(i)}$ is its translation in Pig-Latin. 

The dataset is composed of unique words from the book *Sense and Sensibility*, by Jane Austen. The vocabulary consists of 29 tokens:
the 26 standard alphabet letters (all lowercase), the dash symbol -, and two special tokens `<SOS>`
and `<EOS>` that denote the start and end of a sequence, respectively. The dataset contains 6387
unique (English, Pig-Latin) pairs in total; the first few examples are:

<center> { (the, ethay), (family, amilyfay), (of, ofway), ... } </center>

In order to simplify the processing of *mini-batches* of words, the word pairs are grouped based
on the lengths of the source and target. Thus, in each mini-batch the source words are all the same
length, and the target words are all the same length. This simplifies the code, as we don’t have to
worry about batches of variable-length sequences.

