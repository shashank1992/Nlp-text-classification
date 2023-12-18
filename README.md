**Training an NLP **

**Classical Machine Learning **

2. logistic regression for an imbalanced data set , with 0.06 % true rate. The toxic classification nlp problem with this scenario, gives the following performance. 
1 if px(1) > 0.6 	 F1 score 52 
1 if px(1) > 0.5	48

We can see it's the base level performance. Even with the class weights added, the score for 
	        precision	recall	f1-score	support
0	        0.947531	0.835920	0.888233	294089
1	        0.106771	0.297611	0.157160	19381
accuracy	0.802638	0.802638	0.802638	0
macro avg	0.527151	0.566766	0.522697	313470
weighted avg	0.895549	0.802638	0.843033	313470

**Deeplearning Models**

**Experimenting with tokenizations**
  Used , TFId vectorisation for this. Along with cleaning text. Performance wasn't satisfactory
  
  Used Glove 200d vectors.
  
3. Using the tokenizer from the keras preprocessing , about a lakh words are not in the vacabulary. Due to being very old, and not being able to accommodate new words. Need a tokenizer that can break the words, and correct spellings. 
    1. Proceeding to train the model of bidirectional gpu and a dense layer, gave an f1 score of 76. 
    2. This problem is called, oov. or out of vocabulary problem. 
    3. One way to deal with them is to use, the word piece toeknizer or the byte pair tokenizer to actually breakdown and combine the words to form the desired vocabulary for the corpus. ( to be explored with Bert) 
    4. Another way that also helps to solve the oov, is to use a spell checker , or a separate model to correct spellings based on context. (to be explored)
    5. Another idea, is to search on a treebased vocabulary for words which are oov, in the following way. (implemented)
  
**Impact of preprocessing**

4. Used, bi directional GRU, and 2 dense layers, to shoot up the performance to 81. 
    1. used threshold probability as 0.4. 
5. using, CNV + LSTM  + Dense, the performance, came up to 78. 
    1. used threshold probability, as 0.9.
 	        precision	recall	f1-score	support
0	        0.973275	0.974089	0.973682	196059
1	        0.601787	0.594149	0.597944	12921
accuracy	0.950598	0.950598	0.950598	0
macro avg	0.787531	0.784119	0.785813	208980
weighted avg	0.950307	0.950598	0.950451	208980

observations:  the cnn + lstm increases the precision. 

How drop out affects performance. 
How the padding should be chosen  ? Whether, the pre padding or post padding affects the type of model, eg. bidirectional GRU vs, LSTM ( in single direction)  How long to train, how many epochs. probability is > 0.8
				
 		precision	recall		f1-score	support
    0	    	0.981546	0.952524	0.966818	196059
    1	    	0.502725	0.728272	0.594835	12921
accuracy	0.938659	0.938659	0.938659	0
macro avg	0.742136	0.840398	0.780827	208980
weighted avg	0.951941	0.938659	0.943819	208980

 **impact of reducing the max seq. length : **

After , reducing the sequence size. a simple , GRU + deep gives, 78 for px(x=1) > 0.8 . 


**impact of number of epochs :**

Batch size  ( keep max) 	Epochs 	Px (x==1) >	F1 score
256	12	0.8	78
256	25	0.8	78

After increasing the padding sequence to 30 

   
   
