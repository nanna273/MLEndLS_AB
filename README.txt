# MLEndLS_AB #

This repo contains an updated version of a project undertaken as part of my 2022 MSc in Data Science and Artificial Intelligence at Queen Mary University of London. The project is called MLEnd London Sounds, or MLEndLS. Using my initials, this becomes MLEndLS_AB.

Background:
Students were tasked with making short video recordings of set locations from throughout London, following a set format. The course leader processed the video recordings into audio recordings, and then shared the dataset.

Problem statement:
Build a classifier that can identify if a recording in the dataset was taken inside or outside.

The original notebooks were created in Google Colab, but have been transferred to Jupyter Notebooks for ease of access.

Files:
The first stage is to download the zip file containing .wav audio files from:

https://www.kaggle.com/datasets/jesusrequena/mlend-london-sounds

or

https://mlenddatasets.github.io/london_sounds/

These are unzipped and stored in the repository in the folder 'Data/wav_files/'. This is a large file (3.48 GB) and therefore not part of this repo. A gitignore file is included to prevent commits with these files.