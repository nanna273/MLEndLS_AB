# MLEndLS_AB #

This repo contains an updated version of a project undertaken as part of my 2022 MSc in Data Science and Artificial Intelligence at Queen Mary University of London. The project is called MLEnd London Sounds, or MLEndLS. Using my initials, this becomes MLEndLS_AB.

## Background: ##
Students were tasked with making short video recordings of set locations from throughout London, following a set format. The course leader processed the video recordings into audio recordings, and then shared the dataset.

## Problem statement: ##
Build a classifier that can identify if a recording in the dataset was taken inside or outside.

The original notebooks were created in Google Colab, but have been transferred to Jupyter Notebooks for ease of access.

## Files:  ##
The first stage is to download the zip file containing .wav audio files from:  

https://www.kaggle.com/datasets/jesusrequena/mlend-london-sounds  

or  

https://mlenddatasets.github.io/london_sounds/  

These are unzipped and stored in the repository in the folder 'Data/wav_files/'. This is a large file (3.48 GB) and therefore not part of this repo. A gitignore file is included to prevent commits with these files.

## Part A:  ##
The Python notebook called *PartA_Pre-processing.ipynb* contains details of the pre-processing of the data. Features are extracted, and saved to csv files for analysis. An example of the first 5 rows of the tabulated data is shown below.

| file_id  | area         | spot      |	in_out	  | Participant |	duration  |
| -------- | ------------ | --------- | --------- | ----------- | --------  |
| 0001.wav |	british     |	street	  | outdoor   |	S151	      | 9.59      |
| 0002.wav |  kensington  |	dinosaur  |	indoor    |	S127        | 7.04      |
| 0003.wav |	campus      |	square    |	outdoor  	| S18         |	8.85      |
| 0004.wav |	kensington  |	hintze	  | indoor	  | S179        | 7.72      |
| 0005.wav |	campu       |	square	  | outdoor	  | S176	      | 11.42     |

An example of the raw audio data in the .wav files can be seen below.
![Raw audio file representation](figure/1_raw_audio.png)

The raw audio data then undergoes a Short-Time Fourier Transform (STFT) to represent it in in the frequency domain, as shown below.
![STFT](figure/2_STFT.png)

The below features are created by transformations in the librosa library. Domain understanding of the transformations is not part of this ML task, but may be investigated in a future update.

| Feature name     | Number of features  |
| ------------     | ------------------- |
| Power | 1 |
| Pitch mean | 1 |
| Pitch std | 1 |
| Voiced fraction | 1 |
| spectral_contrast | 7 |
| chroma_stft | 13 |
| mfcc | 20 |
| rms | 1  |
| spectral_centroid | 1 |
| spectral_bandwidth | 1 |
| spectral_flatness | 1 |
| spectral_rolloff | 1 |

## Part B:  ##
The Python notebook called *PartB_Feature_Selection_Modelling.ipynb* contains exploratory data analysis, feature selection, and finally modelling.

### Exploratory data analysis and feature selection ###
Boxplots and a PCA plotted to visually investigate features that might give good separation, and therefore be used for modelling. The PCA does not show much useful separation, but 5 features, corresponding to the MFCC transformation, do show some separation.

### Modelling ###

SVM, random forest and logistic regression models are investigated, using a grid search to tune hyperparameters. The models are then validated with sklearn's cross_val_score function, using 5 folds. A Random Forest model is selected, and classifies indoor and outdoor sounds from this dataset with 63 % accuracy. 
