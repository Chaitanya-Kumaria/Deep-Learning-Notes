# Week 9 
## Major Points of the week
- One Hot Representation Of words
- Co-occurence matirix
- SVD for learning word representations
- Continuous Bag of words Model
- Skip Gram Model
- Hierarchical Softmax
- GLove Representation
- Relation between SVD and Word2Vec

 ## SVD for Learning word representation
[This is the link for required collb](SVD_For_Word_Embeddings.ipynb)

## Continuos Bag Of Words
The continuous bag-of-words (CBOW) model is a neural network for natural language processing tasks such as language translation and text classification. It is based on predicting a target word given the context of the surrounding words. The CBOW model takes a window of surrounding words as input and tries to predict the target word in the center of the window. The model is trained on a large text dataset and learns to predict the target word based on the patterns it observes in the input data. The CBOW model is often combined with other natural language processing techniques and models, such as the skip-gram model, to improve the performance of natural language processing tasks.

![image](https://user-images.githubusercontent.com/64345863/232458486-f77e6fcb-27a5-4a9d-8ea5-f7e8f56c8cec.png)

CBOW (Continuous Bag of Words) model predicts a target word based on the context of the surrounding words in a sentence or text. It is trained using a feedforward neural network where the input is a set of context words, and the output is the target word. The model learns to adjust the weights of the neurons in the hidden layer to produce an output that is most likely to be the target word.

Major areas of use: 
  - Sentiment Analysis
  - Language Translation
  - Text Classification

 Python Implementation: [Continuos_Bag_of_words](Continuos_Bag_of_words.ipynb)
 
 
 ## Skip Gram Model
 The Skip-gram model architecture usually tries to achieve the reverse of what the CBOW model does. It tries to predict the source context words (surrounding words) given a target word (the center word). Considering our simple sentence from earlier, “the quick brown fox jumps over the lazy dog”. If we used the CBOW model, we get pairs of (context_window, target_word)where if we consider a context window of size 2, we have examples like ([quick, fox], brown), ([the, brown], quick), ([the, dog], lazy) and so on. Now considering that the skip-gram model’s aim is to predict the context from the target word, the model typically inverts the contexts and targets, and tries to predict each context word from its target word. Hence the task becomes to predict the context [quick, fox] given target word ‘brown’ or [the, brown] given target word ‘quick’ and so on. Thus the model tries to predict the context_window words based on the target_word.
   
 ![image](https://user-images.githubusercontent.com/64345863/232462543-805828ee-20ee-4616-a5e5-2b41baf96fbf.png)
 
 ![image](https://user-images.githubusercontent.com/64345863/232463578-3cb1e72b-19a5-42ac-8f47-34ef7fe6c170.png)

## Hierarchical Softmax
- Hierarchical softmax is a replacement for softmax which is must faster to evaluate. While softmax is  O(n) time, hierarchical softmax is  O(logn) time
- You can view the softmax function as a tree, where the root node is the hidden layer activations (or context vector C), and the leaves are the probabilities of each word.

![image](https://user-images.githubusercontent.com/64345863/232464803-cf78cba1-c2dc-4a69-999e-b32089a3d69a.png)

- Note that to find the probability of a given word, you must compute all of the terminal leaves.

### Hierarchical Softmax

A hierarchical softmax instead computes the values of the leaves with a multi-layer tree.
![image](https://user-images.githubusercontent.com/64345863/232465188-8a1a8818-ee1c-4695-a5de-bdf21e4b079d.png)
To evaluate the probability of a given word, take the product of the probabilities of each edge on the path to that node:
$P(I'm|C) = 0.57∗0.68∗0.72=0.28$
Now, in the case of a binary tree, this can provide an exponential speedup. In the case of 1 million words, the computation involves $log(1,000,000) =20 $ multiplications
