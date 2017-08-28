# Data from Allocine

We had web scrape (see [the script here](https://github.com/ibmw/Allocine-project/webscraping)) the data from the AlloCiné website. AlloCiné is a company which provides information on French cinema and provide ratings from the press and from their users for a large number of movies.

## Description of the data
We provide the dataset in two version :
- A one csv files format (brut and clean version) : [allocine_dataset.zip](http://olivier-maillot.fr/wp-content/uploads/2017/08/allocine_dataset.zip)
- A multiple csv files format (clean version only): [allocine_rel-dataset.zip](http://olivier-maillot.fr/wp-content/uploads/2017/08/allocine_rel-dataset.zip)

The brut file contains **59 966 movies**, but only **10 424 movies** have both press and users ratings.
If you decide to use the clean version, you directly start with the **10 424 movies** and if you decide to use the multiple csv files, you don't have to use ast library (see Getting Started).

### The Columns :
- `movie_title` : the movies title (in french)
- `release_date`: the original release date
- `re_release_date`: the re-release date
- `duration`: the movies length
- `genre` : the movies types (as an array, up to three different types)
- `directors` : movies directors (as an array)
- `actors` : main movie characters (as an array)
- `nationality`: nationality of the movies (as an array)
- `press_rating`: press ratings (from 0 to 5 stars)
- `nber_press_vote`: number of press votes
- `user_rating`:  AlloCiné users ratings (from 0 to 5 stars)
- `nber_user_vote`: number of users votes

## Getting Started

We save the Pandas DataFrame as a csv file and several columns store Arrays, but the csv file keep it as a string. So, we need to call `ast.literal_eval()` function on these columns.

Example :

```
import pandas as pd
import ast

allocine = pd.read_csv("allocine.csv")

allocine["actors"] = allocine["actors"].apply(ast.literal_eval)
allocine["directors"] = allocine["directors"].apply(ast.literal_eval)
allocine["genre"] = allocine["genre"].apply(ast.literal_eval)
```

# Authors

* **Olivier Maillot** - *Initial work* - [Allociné Project](https://github.com/ibmw/Allocine-project) - [Blog Post](http://wp.me/p8Ffnw-4U)

# Licence

This project is free. Have fun.
