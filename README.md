# free-spoken-digits

### Introduction 
The main objective of this project is to put into practice what you have learned on classification techniques. You will mainly work on audio signals. In particular, you will try to build a classification model that is able to identify which digit was uttered analyzing the content of short audio samples from different speakers.

This work is a part of practice during a.y. 23/24 for the Data Science Lab Course taught at Politecnico di Torino [Link here](https://dbdmg.polito.it/dbdmg_web/2023/data-science-lab-process-and-methods-2023-24/)

____

### 1. Dataset
The dataset for this project has been inspired by the [Free Spoken Digit Dataset.](https://github.com/Jakobovski/free-spoken-digit-dataset)

It is composed of **2,000 recordings** by 4 speakers of numbers from 0 to 9 with English pronunciation.
Thus, each digit has a total of 50 recordings per speaker. Each recording is a mono wav file. The sampling rate is 8 kHz. The recordings are trimmed so that they have near minimal silence at the beginnings and
ends.

The data has been distributed uniformly in two separate collections:

- **Development (dev)**: a collection composed of 1500 recordings with the ground-truth labels. This
collection of data has to be used during the development of the classification model. Each file in this portion of the dataset is a recording named with the following format "{Id}_{Label}.wav"

- **Evaluation (eval)**: a collection composed of 500 recordings without the labels. This collection of
data has to be used to produce the submission file containing the labels predicted for each evaluation
recording, exploiting the previously built model. Each file in this portion of the dataset is a recording
named with the following format "{Id}.wav".

### 2. Work

n this exercise you will build a complete data analytics pipeline to pre-process your audio signals and build
a classification model able to distinguish between the classes available in the dataset. More specifically, you
will load, analyze and prepare the Free Spoken Digit dataset to train and validate a classification model.
Finally, you will be able to upload your classification results and participate to the lab competition.

1. Load the dataset from the root folder. Here the Python’s os module comes to your help. You can use
the os.listdir function to list files in a directory. Furthermore, you can use the wavefile module
from SciPy to read a file in wav format. 

2. Focus now on the data preparation step. You should have noticed that wavfile gives you an array of
floating point values, plus the sampling rate. Before continuing, take you your time to answer these
questions:
- What do these numbers represent?
- Were the audios recorded under the same conditions? (e.g. recording volume, noise, etc.)
- Do the arrays have an equal length? How different lengths could impact on your pre-processing
solution? If it was needed, could you figure a way out to align them to the same length?


Now, in order to train your model, you are required to design and build a vector representation.
This mainly involves extracting several features out of your initial representation. Bear in mind that,
since you are dealing with audio signals, you can work either on the time domain or the frequency
one. In the former case, you might opt, for example, to split the signal into chunks and characterize
them by means of statistical measures (e.g. mean, standard deviation). In the latter case, you can
base your features on the frequencies contained in the signal. This involves reshaping the signal
using a transformation function (e.g. Fourier transform) and work on its spectrum of frequencies
(e.g. spectogram). Data preparation on frequencies can be hard to carry out. To know more about
it, please refer to Camastra and Vinciarelli 2015 and Oppenheim and Schafer 2014, and Presti and
Neri 1992.

3. Once you have your vector representation, choose one classification algorithm of those you know.
Then, perform the classic training-validation pipeline on the Development dataset to identify the best
set of hyper-parameters for your model. we will evaluate your results
on the mean F1 score. Hence, it is a reasonable option trying to optimize it on the Development
dataset.

_____