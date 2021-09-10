# Neural-Machine-Translation

In this project, we train a few attention-based neural machine translation (NMT) models to
translate words from English to Pig-Latin. Along the way, we explore several
important concepts in NMT, including gated *recurrent neural networks* and *attention*.

##Pig-Latin Crash Course
Pig Latin is a simple transformation of English based on the following rules (applied on a per-word
basis):
1. If the first letter of a word is a *consonant*, then the letter is moved to the end of the word,
and the letters “ay” are added to the end: 

  `team → eamtay`.
2. If the first letter is a *vowel*, then the word is left unchanged and the letters “way” are added
to the end: 
  
  `impress → impressway`.

3. In addition, some consonant pairs, such as “sh”, are treated as a block and are moved to the end of the string together: 
  
  `shopping → oppingshay`.

To translate a whole sentence from English to Pig-Latin, we simply apply these rules to each word
independently:
<br>
`i went shopping → iway entway oppingshay`
