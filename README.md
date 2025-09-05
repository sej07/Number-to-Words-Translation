## Number to Words Translation using Encoder–Decoder (Seq2Seq)
_This project implements a sequence-to-sequence (Seq2Seq) model with LSTMs to translate numbers into their word equivalents. The project follows the encoder–decoder architecture introduced in the original Seq2Seq research, implemented in TensorFlow and Keras._

#### Dataset Details:
- Source: Custom Dataset 

#### ML Workflow: 
1. Import Libraries: 
    1. TensorFlow, Keras, NumPy, Pandas, Matplotlib, Scikit-learn
2. Creating Dataset 
    1. Generated a synthetic dataset of integers mapped to their word-based representations.
3. Text Preprocessing
    1. Converted text to Lowercase
    2. Removed extra spaces
    3. Formatted the number–word pairs.
4. Text Tokenization
    1. Converted both input (numbers) and output (words) into integer tokens.
5. Padding
    1. Standardized sequence lengths using padding for batch training.
6. Encoder–Decoder Architecture: 
    - The model is built using stacked LSTM encoder–decoder. 
    - Encoder: 
        1. Input Layer – Accepts tokenized number sequences.
        2. Embedding Layer – Maps input tokens into dense vector embeddings.
        3. LSTM Layer 1 – Processes sequence step by step, returning hidden states.
        4. LSTM Layer 2 – Builds a deeper sequence representation and returns the final hidden + cell states.
        5. Encoder States – Final states are passed to the decoder as context.
    - Decoder
        1. Input Layer – Accepts shifted target sequences (teacher forcing)
        2. Embedding Layer – Maps output tokens into embeddings.
        3. LSTM Layer 1 – Uses encoder hidden and cell states as initial state.
        4. LSTM Layer 2 – Further processes decoder sequences.
        5. Dense Layer (Softmax) – Outputs probability distribution over the vocabulary for each time step.
7. Model Training
    1. Trained the model with teacher forcing for 150 epochs, using a validation split of 20%.
    2. Loss function: Sparse Categorical Crossentropy
    3. Optimizer: Adam
8. Making Predictions
    1. Translated unseen number sequences into words.

#### Frameworks:
- Tensorflow and Keras

#### Model Summary:
<img width="753" height="574" alt="Screenshot 2025-09-05 at 4 42 04 PM" src="https://github.com/user-attachments/assets/8f6381ab-39e5-4eeb-b0b5-c3363a103555" />


#### Assumptions
1. Assumed that the dataset vocabulary is fixed and finite (limited range of numbers)

#### Key Observation
1. The embedding layer allowed the model to learn compact semantic representations of digits and words, making the translation more efficient.
2. The encoder–decoder model can successfully learn structured sequence translations even without attention, but struggles as sequence length grows.

