# CS224N-2019

My notes and solutions for CS224N 2019

## Course links
- Course page [CS224N](http://cs224n.stanford.edu)
- Lecture videos 2019 [Youtube](https://www.youtube.com/playlist?list=PLoROMvodv4rOhcuXMZkNm7j3fVwBBY42z)
- [Stanford online hub](http://onlinehub.stanford.edu/cs224)



## Detailed Course Lectures:

### 13 - Contextual Word Embeddings:

#### [ELMo](https://youtu.be/S-CspeZ8FHc?t=1906)
- 2 biLSTM LM
- Character representation of words to build initial representation. 2048 char n-gram filters and 2 highway layers, 512 dim projection
- 4096 dim hidden/cell LSTM states with 512 dim projection to next input
- Residual connections
- Learns task-specific combinations of biLM representations
- Uses all levels of hiddend layers of the LM (unlike tagLM that just uses the middle layer) for representation
- The **pre-trained LM model is kept frozen. A new model is fine tuned.**

#### [ULMfit](https://youtu.be/S-CspeZ8FHc?t=2516)
 - Universal LM for text classification
 - Pre-trained LM on big corpus
 - Then fine-tune the pre-trained LM on specific domain
 - So it uses **the same pre-trained model for the end task**
 - Finally, uses the same LM with text classification objective. Freezes the LM final softmax and introduces a new classification layer.
 - Different learning rates for each layer
 - Slanted Triagular Learning Rate Schedule (STLR)

#### [Transformer](https://youtu.be/S-CspeZ8FHc?t=3074)
- Aim for parallelism. RNN are sequencial.
- [The Annotated Tranformer](https://youtu.be/S-CspeZ8FHc?t=3261)
- Only Attention. Attention everywhere.
- Multihead attention. Q, K, V have dimension reduced by apply W matrixes and then concatenate multiple attentions and pipe through linear layer.
- Transformer Block
	- Multihead
	- 2-layer FF NNet
- [LayerNorm](https://youtu.be/S-CspeZ8FHc?t=3533)
- Bidirectional
	- GPT is left-to-right
	- ELMo is bidirectional LM, but trained separatedly (no attention between models)
	- BERT bidirectional with attention
- Objective:
	- Predict masked words
	- Second loss function. Next sentence prediction (classification: Given SentA and SentB IsSentBNexSentence: Yes/No)