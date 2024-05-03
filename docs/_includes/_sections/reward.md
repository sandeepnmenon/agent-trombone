We experimented with two rewards

1. MSE on LogMelSpectogram
![mse](images/mse.png)


2. Cosine similarity on Whisper Embeddings
![cosine](images/cosine.png)

![whisper](images/whisper.png)

The whisper embeddings are obtained by passing the Log-melspectogram of the audio to the encoder block to get the embeddings. The cosine similarity between the embeddings of the target audio and the generated audio is used as the reward.