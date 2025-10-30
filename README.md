# 🤖 Projects: Sequence-to-Sequence Models and Attention

## Seq - Seq - Attn (Sequence-to-Sequence with Attention)

### Tokenizer (BPE - Byte Pair Encoding)

1. Take a **vocabulary size**.
2. **Encode the data**.
3. **Count** (token, next\_token) pairs.
4. **Add the best pair** to the vocabulary.
5. **Merge encoding** for the best pair.
6. Repeat till 3-5 you reach vocab size.

### Encode the text

1. **Encode to UTF-8**.
2. **Get all the pairs**.
3. **Check for matching pair** in the vocabulary.
4. merge the matching pair with lowest mapping.
5. Repeat 2-4 until you donot have pairs 

---

## RNN Encoder-Decoder (ENC-DEC) Model

### Model Architecture

* **Embedding**
* **Bidirectional-LSTM** (Encoder)
* **Projection layer** 
* **Decoder Embedding**
* **Decoder**
* **Output**

### Details

* **Embedding**: $\rightarrow D \times V$ Matrix ($D$ is the embedding dimension, $V$ is the vocabulary size).
    * (NN. linear expect OHV, Embedding expect $[w_1, w_2, w_3]$)
* **Bidirectional LSTM** (Encoder): Have future knowledge and can utilize it.
* **Decoder**: $\rightarrow$ **LSTM**.

### **Things to look out for**

* Bidirectional LSTM gives an output of shape $(2 \times \text{num layer} \times h_{\text{out}})$.
* Will need to **concatenate $h_0$** $(\text{num layer} \times 2 \times h_{\text{out}})$ and **project to** $(\text{num layer} \times h_{\text{out}})$.

### Loss Function

* **Loss**: NLL loss (Negative Log-Likelihood loss).

---

## Attention (Attn) Module

* **Dot product** between **decoder hidden state** and **encoder hidden states**.
* **Apply softmax**.

### ENC-DEC Model with Attention

* Similar to the ENC-DEC Model but with **attention**.
* Take the **$h_t$ for the last layer** at each time step.
* **Calculate attention score** by the **attention module**.
* **Calculate a context vector** based on the score.
* **Concatenate the context vector** with the **hidden layer output** to predict.

---

## Beam Search

* Take **top $K$ most probable candidates** (sequences) at each timestamp.
