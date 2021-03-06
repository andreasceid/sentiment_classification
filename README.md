# Sentiment Classification

![Movie Critics Classification](wordcloud_illustration.png)

In this repository we have implemented a couple of deep learning models for binary sentiment analysis:
* A Dynamic CNN model, also known as [Kim CNN](https://arxiv.org/abs/1408.5882v2): 
    
    This model uses an Embedding Layer to transform all tokens found in a dataset to numerical vectors, forming a matrix. This makes CNN models able to approach the given dataset not as natural language data, but as *images* made of the tokens' vector representations. Hence, CNN models perform spatial analysis of the dataset. To make training more effective, we provide the model with pretrained word embeddings, using [GloVe](https://nlp.stanford.edu/projects/glove/).
* A [Long Short-term Memory](https://doi.org/10.1162/neco.1997.9.8.1735) model:
    
    This model uses a particular RNN cell architecture, called *LSTM cell*. Those cells are able to correlate data patterns and find temporal dependencies. More specifically, LSTMs are explicitly designed to avoid the long-term dependency problem, remembering information for long periods of time. To utilize the full potential of the model, we add [Keras Embedding Layer](https://keras.io/api/layers/core_layers/embedding/) to the model, which implements custom word embeddings. 

Therefore, while the *dynamic CNN* performs spatial analysis, the *LSTM* performs termporal data analysis. Those models were tested under two datasets:
* The [IMDB](https://www.kaggle.com/lakshmi25npathi/imdb-dataset-of-50k-movie-reviews) dataset for binary sentiment classification
* The [Cornell movie review](https://www.cs.cornell.edu/people/pabo/movie-review-data/) dataset for binary sentiment classification

## Installation

To install the project first install [Anaconda](https://docs.anaconda.com/anaconda/install/), and then execute:
* `git clone https://github.com/andreasceid/sentiment_classification.git` to clone the repository
* `cd sentiment_classification` to access the project directory
* `pip install -r requirements.txt` to install all dependencies
* `python cnn.py` to execute the **CNN** model
* `python lstm.py` to execute the **LSTM** model

We recommend to execute both the installation and the scripts as an Administrator. The default training dataset is *Cornell movie review* dataset. To change the default dataset, edit the code with respect to the path of your custom dataset.
   
## Project Structure

The major project files are:
* `cnn.py` and
* `lstm.py`

There are also Jupyter Notebooks that can be used to better explain the thought process of the developers and provide a better understanding of the models:
* `cnn.ipynb` for the **CNN** model
* `lstm.ipynb` for the **LSTM** model

The datasets used to test the models' performance can be found under the `dataset` directory of the project folder, where:
* The `Cornell movie review` dataset is named `MoviesDataset.csv`
* The `IMDB` dataset is named `IMDB.csv`

There is also a directory named docs, where the interested can find the documentation generated using [Sphinx](https://www.sphinx-doc.org/en/master/index.html). The documentation can also be found at the project's [readthedocs](https://sentiment-classification.readthedocs.io/en/latest/index.html).

## Results

The models were tested under 2 datasets. The expected results are shown below.

-------
### Cornell Dataset

-------
|                	|          CNN          	|          LSTM         	|
|:----------------:	|:---------------------:	|:---------------------:	|
|      Device      	|   NVIDIA GTX 1660 Ti  	|  Intel Core i7 9750H  	|
| Number of Epochs 	|         20        	    |         5             	|
| Epoch  Benchmark 	|         2 sec.        	|         7 sec.        	|
|  Loss  Function  	| Binary  Cross Entropy 	| Binary  Cross Entropy 	|
|     Test Loss    	|         0.519         	|         0.7698        	|
|   Test Accuracy  	|        74.57 %        	|        75.34 %        	|

-------
### IMDB Dataset

-------
|                	|          CNN          	|          LSTM         	|
|:----------------:	|:---------------------:	|:---------------------:	|
|      Device      	|   NVIDIA GTX 1660 Ti  	|  AMD Ryzen 5 3600       	|
| Number of Epochs 	|         20        	    |         5             	|
| Epoch  Benchmark 	|         ~19 min.        	|         142 sec.        	|
|  Loss  Function  	| Binary  Cross Entropy 	| Binary  Cross Entropy 	|
|     Test Loss    	|         0.259         	|         0.3021        	|
|   Test Accuracy  	|        90.41 %        	|        89.34 %        	|
