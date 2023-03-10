**********
Input data
**********

Before learning how to setup and run the CSTrack Dash application it is important to have at hand the dataset that the app
is going to work with, the database connection and the BERT model needed in order to provide all the visualizations. This information can be
provided through a .env file that needs to placed in the cstrack_dash folder.

=============
Tweet dataset
=============

The CSTrack Dash application reads a .csv file in which the information of the tweets is written. Although we provide a basic
dataset, it can be completed with more tweets or custom datasets may be used too. The name of the .csv file is defined in the variable
TWEET_DATASET of the .env file.

The .csv file must have the following columns:

* Fecha: The date of the tweet.
* Fuente: The source of the tweet.
* Texto: The text of the tweet.
* Enlace: The link of the tweet.
* Marca: The filter used for extracting the tweet.
* Usuario: The username of the person that wrote the tweet.

====================
Database connections
====================

The Geomap visualizations requires from data that is not present in the tweet dataset. This data has been previously stored in a Mongo
database that is accessed by the Dash application in order to create these visualizations. The link of the connection must be supplied
in the MONGODB_CONNECTION variable of the .env file. There needs to be a cstrack database with a "geomap_full" collection in it.
Each document in that collection must contain the following fields:

* lat: The latitude.
* lon: The longitude.
* tweets: The number of tweets.
* followers: The number of followers.
* country_code: The 2 character country code.
* iso_3: The 3 character country code.
* country: The full name of the country.
* continent: The name of the continent.

==========
BERT model
==========

The application preloads a BERT model in order to carry out Topic Modelling tasks. By filtering tweets and training this model
the Dash application creates visualizations that allow you to determine the themes of the discussions in Twitter (Depending on
the tweet dataset). In order to provide this model to the application the variable BERT_MODEL must be supplied to the .env file.


====================
Final considerations
====================

The .env file should look as follows:

.. include:: env.txt
   :literal:
