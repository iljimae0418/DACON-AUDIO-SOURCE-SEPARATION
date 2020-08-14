# DACON-AUDIO-SOURCE-SEPARATION

### Link to competition: https://dacon.io/competitions/official/235616/overview/ 

### Brief overview of the competition
Given a .wav file containing 4 different words pronounced at once, we need to be able to differentiate which words they are. To do so, we output the probability of each of the words given a .wav file containing 4 different words pronounced at once.  

### Final rank 
Top 30% (26th place) 

### Methods
Due to time limitations (only had a few days to work on the competition before it ended) could not attempt a lot of different techniques, but here is a summary.  

1. Used spectrogram data for training the CNN model. Log transformed the spectrogram data then normalised the spectrogram data.  

2. Used librosa library for reading .wav files and used scipy's signal.spectrogram for generating spectrogram data of .wav files. There are other methods of generating spectrograms and I also could have used melspectrograms.  

3. Data augmented the .wav data by adding noise, by shifting the data and by changing pitch. 

4. After augmentation, dataset size become quite large so used a data generator instead of loading the entire dataset at once. 

5. Used selu activation functions with lecun_normal for kernel initialization.  

6. Tried adding combinations of dropout (AlphaDropout) and batchnorm, but dropouts seemed to hurt performance (more experimentations could have been done but I was short of time). 

7. CNN was trained using paperspace NVIDIA Quadro P6000 GPU.  

8. If there was more time, I could have experimented with different (possibly more complex and deeper) neural network structures, tried different ways of generating spectrograms (or use these different methods of generating spectrograms all at once as input data), and try k-fold cross validation (get predictions for each of the models from k-fold and average their results - this tends to perform better judging from prior experience). Also, instead of using spectrogram data, we could have used the actual numpy data read from the .wav files and use 1D-CNN or DenseNet or ResNet on this data.    


