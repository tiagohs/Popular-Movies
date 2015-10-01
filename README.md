# Popular Movies Android App

`Popular Movies` is an Android app which helps you to discover the latest popular and top rated movies. You can flip through movie posters, check movie details, watch movie trailers and read other people's reviews. It is designed and optimised for both Android phones and tablets.

This pages documented the technical design of the app. For the functioanl details and screenshots, please visit [Frank's Popular Movies app](http://frank-tan.github.io/Popular-Movies/).

## Data Retrieval Logic

This app retrieves Movie List using a SyncAdapter. It performs an immediate synchronisation when the user opens the app for the first time and when a new version of this app with data schema changes is installed and opened. It performs subsequent synchronisation every 24 hours in the background. The synchronisation retrieves a full genre list and a movie list by popularity and by rating, including movie details such as title, language, poster path, backdrop path, vote count, vote average, genres, etc. 

Movie trailer addresses and reviews are retrieved using an IntentService when movie detail fragment is loaded. 

Movie poster images, backdrop images and trailer thumbnail images are retrieved when the corresponding actvity is loaded. Poster images and backdrop images are retrieved using [Picasso](http://square.github.io/picasso/) and trailer thumbnail is retrieved using [Youtube Android API](https://developers.google.com/youtube/android/player/). 

## Caching and Offline Use

The App saves movie details, genres, trailer address, reviews and favourites in the SQLite database on the device. Movie poster image and backdrop image are cached on the device using OKHttp. So as long as the data are retrieved once, the app can still show saved/cached data and work in an offline mode.

## Data Schema

The diagram shows how the schema of the SQLite database.

![Alt text](content_provider_generator/popular-movies-db.png?raw=true "Database Schema")

The app is developed for [Udacity Android Developer Nanodegree](https://www.udacity.com/course/android-developer-nanodegree--nd801).
