# **Week 2 Quiz: Information Extraction with NLP**

### **Notice that I only list correct options.**

1. Which of the following is not true about BERT’s inner word representations? 
- **Each unique word can have exactly one vector representation**

Correct!
Explanation: Unlike typical word vectors, BERT uses contextualized word vectors. Therefore, since a given word’s vector depends on the other vectors around it, it in general can correspond to representations. This affords BERT more flexibility, which contributes to its power. 

2. True or False: the start and end vectors are fixed throughout training 
- **False**

Correct!
Explanation: This is false. The start and end vectors, which we dot product with our word vectors to get start and end scores, are in fact learned as well during training. They are fixed at test time, however. 

3. Which of the following is a difference between BERT and LSTM models? 
- **BERT takes entire sequences as input, while LSTM models process words one by one**

Correct!
Explanation: A major difference between BERT and LSTMs is that BERT process an entire sequence of input, while LSTMs only in words one by one. This enables greater parallelization and results in better training among a variety of tasks. 

4. Given the following word vectors and start and end vectors, determine the start and end of the sequence of interest.
- **start: breast, end: cancer**

Correct!
Explanation: The start scores are [the: 0.1, BRCA1: 0.25, gene: -0.3, is: -0.2, associated: -0.5, with: 0.4, breast: 0.5, cancer: -0.4] while the end scores are [the: -0.1, BRCA1: 0.05, gene: -0.5, is: 0.25, associated: 0.01, with: 0.03, breast: 0.12, cancer: 0.6]. The the pair of words which maximize the sum of start and end scores and where the start token is before the end token is start: breast and end: cancer, which corresponds to answer D.

5. You find that a radiology report mentions “edema”. Which of the following can you immediately conclude? 
- **None of the above**

Correct!
Explanation: The correct answer is none of the above, since we are missing negation information about the mention of edema. A is false since the mention could have been preceded by “no”, so we can’t conclude that it is present. For similar reasons, we can’t say that it’s not necessarily not present. Since nothing is mentioned about pneumonia, we can’t say whether its present or not. Therefore the correct answer is none of the above. 

6. Use the following entry in SNOMED CT to help determine the positive labels for this x-ray report.
- **common cold: 1, lesion: 0**

Correct!
Explanation: First, report mentions acute coryza, which we can see from the SNOMED CT cards is a synonym for the common cold. Since it is a positive mention, we can safely say that the patient has a common cold. However, while mass is synonymous mass and lump, which are mentioned, they are negated. Therefore the label should be common cold: 1, lesion: 0.

7. Let’s see why F1 is used instead of the regular mean of precision and recall. Let’s say the mean of precision and recall is at least 0.75. Which of the following could be the true value of the precision?
- **Both**

Correct!
Explanation: Here we see both are possible. If the precision is 0.75, then the recall just could be anything greater than 0.75, and if the precision is 0.5, then the recall could be 1 to keep the average at 0.75. Therefore a relatively high mean still permits quite a low precision. 

8. Now let’s say F1 score is at least 0.75. Now which of the following values of precision are possible?
- **0.75**

Correct!
Explanation: Here it is only A. We see that if we set precision and recall to 0.75, then the F1 score is 2*precision*recall / (precision + recall) = 2*0.75*0.75 / (0.75 + 0.75) = 0.75. Now let’s see if we can use 0.5 for precision. Then the F1 score is 2*0.5*recall / (0.5 + recall) >= 0.75, which implies that recall / (0.5 + recall) >= 0.75, which implies that recall >= 1.5, which is impossible. Therefore a precision of 0.5 is not possible. Here we see that F1 encourages balancing of precision and recall, and therefore is good for tasks where both are important.

9. Compute the F1 score for pneumonia and mass separately based on the following retrieved labels and ground truth:
- **(0.5, 0.8)**

Correct!
Explanation: Let’s begin with pneumonia. Both precision and recall are 0.5. Therefore the F1 score is 2*0.5*0.5 / (0.5 + 0.5) = 0.5. Next let’s do mass. Recall was 2/3, while precision was 1. Computing the F1 score, we get 2*⅔*1 / (1 + 2/3) = 0.8. Therefore the correct answer is B. A was using the arithmetic mean, so be careful!

10. Now compute the F1 score for all labels jointly: 
- **0.66**

Correct!
Explanation: The overall recall is ⅗, while the overall precision is ¾. Therefore the F1 score is 2*⅗*¾ / (⅗ + ¾) = 18/20 /  27/20 = 18/27 ~ 0.66. Therefore the correct answer is  C. Note that it is not B, which is the harmonic mean of the individual class F1 scores, since 2*0.5*0.8 / (0.5 + 0.8) ~ 0.62, and it is not A, which is the arithmetic mean of the overall recall and precision. 
