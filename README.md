---

---






# Model Card for Deep Learning Network for Predicting Music Genre and Energy Level

<!-- Provide a quick summary of what the model is/does. [Optional] -->
With the high quantity of music being released in this digital age, Music Genre Recognition (MGR) has become an increasingly important task. Many existing MGR models using deep learning have demonstrated success in classifying songs from their audio files. However, we wanted to create a deep learning model that would not only be limited to MGR, but can also predict the energy rating of a song. We believe that such a network could have an additional practical use regarding user recommendations, as the combination of genre and energy level can be an important factor of one’s choice of music.




#  Table of Contents

- [Model Card for Deep Learning Network for Predicting Music Genre and Energy Level](#model-card-for--model_id-)
- [Table of Contents](#table-of-contents)
- [Table of Contents](#table-of-contents-1)
- [Model Details](#model-details)
  - [Model Description](#model-description)
- [Uses](#uses)
  - [Direct Use](#direct-use)
  - [Out-of-Scope Use](#out-of-scope-use)
- [Bias, Risks, and Limitations](#bias-risks-and-limitations)
  - [Recommendations](#recommendations)
- [Training Details](#training-details)
  - [Training Data](#training-data)
  - [Training Procedure](#training-procedure)
    - [Preprocessing](#preprocessing)
    - [Speeds, Sizes, Times](#speeds-sizes-times)
- [Evaluation](#evaluation)
  - [Testing Data, Factors & Metrics](#testing-data-factors--metrics)
    - [Testing Data](#testing-data)
    - [Factors](#factors)
    - [Metrics](#metrics)
  - [Results](#results)
- [Model Examination](#model-examination)
- [Technical Specifications](#technical-specifications-optional)
  - [Model Architecture and Objective](#model-architecture-and-objective)
  - [Compute Infrastructure](#compute-infrastructure)
    - [Hardware](#hardware)
    - [Software](#software)
- [Model Card Authors](#model-card-authors-optional)


# Model Details

## Model Description

<!-- Provide a longer summary of what this model is/does. -->
With the high quantity of music being released in this digital age, Music Genre Recognition (MGR) has become an increasingly important task. Many existing MGR models using deep learning have demonstrated success in classifying songs from their audio files. However, we wanted to create a deep learning model that would not only be limited to MGR, but can also predict the energy rating of a song. We believe that such a network could have an additional practical use regarding user recommendations, as the combination of genre and energy level can be an important factor of one’s choice of music.

- **Developed by:**
    - Anaya Mehta
    - Brandon Kelly
    - Yun Luk Liu
    - Wenhan Lee
- **Model type:** Audio Classification & Energy Prediction model
- **Language(s) (NLP):** en
- **License:** Creative Commons Attribution-NonCommercial-NoDerivatives (cc-by-nc-nd-4.0)
- **Resources for more information:**
    - [FMA's GitHub Repo](https://github.com/mdeff/fma)
    - [FMA's Associated Paper](https://arxiv.org/abs/1612.01840)

# Uses

<!-- Address questions around how the model is intended to be used, including the foreseeable users of the model and those affected by the model. -->

## Direct Use

<!-- This section is for the model use without fine-tuning or plugging into a larger ecosystem/app. -->
<!-- If the user enters content, print that. If not, but they enter a task in the list, use that. If neither, say "more info needed." -->

This model could be used in music recommendation systems, music curation and organization, music synchronization, genre and energy-level-based music categorization, and more.

## Out-of-Scope Use

<!-- This section addresses misuse, malicious use, and uses that the model will not work well for. -->
<!-- If the user enters content, print that. If not, but they enter a task in the list, use that. If neither, say "more info needed." -->

Audio recognition outside of music, generating new audio, music identification, non-audio data processing, and other similar task.


# Bias, Risks, and Limitations

<!-- This section is meant to convey both technical and sociotechnical limitations. -->
### Bias
- Uneven representation of genres since some subsets of the data have more genres in common than others.
- Data was not fully complete and some songs by Echonest were not analyzed.
- Genres and Energy are both subjective.
- Biases are from Echonest's analysis of the data. Since we are not completely sure how or what Echonest used to obtain energy levels of the songs with different factors, it could be more one sides to certain genres versus others.

### Risks
- The model may have potentially overfitted due to the size of the dataset used.
- Biases in the data.
- Limited generalizability since we only used the FMA dataset to train the model.
- Data quality issues since some of the data had NaN values and were not analyzed for energy or some missing energy analyization by Echonest.

## Recommendations
<!-- This section is meant to convey recommendations with respect to the bias, risk, and technical limitations. -->
- Combine the FMA dataset with other music datasets to create a broader and diverse dataset that covers more genres and other features.

# Training Details
![Training graph](https://github.com/brand-kelly/predicting_music_genres/blob/main/best_model.png)
## Training Data

<!-- This should link to a Data Card, perhaps with a short stub of information on what the training data is all about as well as documentation related to data pre-processing or additional filtering. -->

The training data used was from Free Music Archive&#39;s open dataset GitHub page.



## Training Procedure

<!-- This relates heavily to the Technical Specifications. Content here should link to that section when it is relevant to the training procedure. -->

### Preprocessing

The preprocessing of the FMA dataset involved several key steps to prepare the data for the audio genre classification and energy level prediction model. The primary focus was on selecting data with corresponding genre labels and energy levels, as well as handling missing values. The following is a description of the preprocessing steps:

   1. Data selection: The first step in preprocessing the FMA dataset was to identify the music tracks that had both genre labels and energy levels associated with them. This was crucial for ensuring that the model could be trained on relevant data with the required target variables. To achieve this, we filtered the dataset to retain only those records that contained information about the track's genre and energy level.

  2. Handling missing values: After selecting the relevant records, we inspected the dataset for missing values, also known as NaN (Not a Number) values. These missing values can adversely impact the model's performance and lead to inaccuracies in predictions. To address this issue, we removed records containing NaN values in either the genre label or energy level. This step ensured that the model would be trained on a clean and complete dataset, improving the overall quality of the predictions.

By focusing on data selection and handling missing values, we effectively preprocessed the FMA dataset for use in the audio genre classification and energy level prediction model. This preprocessing stage was essential for optimizing the model's performance and ensuring accurate results.

In addition, FMA's dataset also provided subsets of the data that was already split into training, validation, and test splits.

This data can now be accessed directly through Spotify's API and a new update will soon be done to increase the data size.

### Speeds, Sizes, Times

<!-- This section provides information about throughput, start/end time, checkpoint size if relevant, etc. -->


 
# Evaluation

<!-- This section describes the evaluation protocols and provides the results. -->

## Testing Data, Factors & Metrics

### Testing Data

<!-- This should link to a Data Card if possible. -->

Testing data was supplied by FMA's dataset which was predifined by the dataset. The testing data had the associated track_id and the top_level genres to compare the true and pred values with cross entropy loss.

During training, the model was also used with cross-validation.

### Factors

<!-- These are the things the evaluation is disaggregating by, e.g., subpopulations or domains. -->
#### Input features
- MFCCs
- Echonest energy attributes

#### Model Architecture
- 1D CNN layer
- LSTM layer
- Fully connected layers
- 1D Maxpool Layers


#### Hyperparameters
- Learning rate: 1e-3
- Number of LSTM layers: 1

#### Regularization
- Dropout: p=0.50
- Early Stopping
- Batch normalization


### Metrics

<!-- These are the evaluation metrics being used, ideally with a description of why. -->
#### Classification Metrics
- accuracy and Cross-Entropy Loss

#### Regression Metrics
- accuracy and Mean Squared Error


## Results 

### Performance on Test Data
- Loss: 1.22
- Accuracy: 59.48%

### Performance on Validation Data
- Loss 1.35
- Accuracy: 58.71%


# Model Examination
![SGD Computational Experiment](https://github.com/brand-kelly/predicting_music_genres/blob/main/comp_exp_sgd.png)
![Weight Decay Computational Experiment](https://github.com/brand-kelly/predicting_music_genres/blob/main/comp_exp_wd.png)

## Model Architecture and Objective

Multi-layered Convolutional Recurrent Neural Network.

## Compute Infrastructure

### Hardware
- CPU: Google Colab's provided base CPU
- RAM: Google Colab's provided base 12GB RAM

### Software
- Jupyter Notebook
- PyTorch
- NumPy
- Pandas
- SciPy
- Librosa
- Matplotlib
- IPython
- Sklearn

# Model Card Authors

<!-- This section provides another layer of transparency and accountability. Whose views is this model card representing? How many voices were included in its construction? Etc. -->

  - Brandon Kelly
