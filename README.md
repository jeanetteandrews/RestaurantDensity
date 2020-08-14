# CMPT 353 Project

### Libraries used  
pandas  
numpy  
fuzzywuzzy  
python-Levenshtein  
matplotlib  
descartes  
geopandas  
shapely  
googlemaps  
sklearn.model_selection  
sklearn.ensemble  
sklearn.preprocessing  
pandas.io.json  


### Project Pipeline
#### Questions Asked:
	Are there some parts of Vancouver with more chain restaurants than others? 
	In particular, how can we use visual, statistical, and machine learning 
	applications to find chains automatically by their density relative to 
	non-chain restaurants?
#### Acquiring, Cleaning, and Preparing Data:
	You will find much of our data acquiring, cleaning and preparation,
	as well as their order of execution in:
      data_cleaning.ipynb
	The above notebook references three other notebooks:
	  find_postal_codes.ipynb 		   - includes googlemaps API requests
	  get_all_restaurant_ratings.ipynb - includes googlemaps API requests
	  label_and_hot_encoding.ipynb 	   - includes LabelEncoder and 
										 OneHotEncoder
	In addition, an R file, postalcodescrap.rmd was created to scrape postal
	codes in the Greater Vancouver area.
#### Analyzing and Presenting Data:
	Data analysis and visualizations can be found in:
	  price_level_analysis.ipynb 	   - predictions on restaurant price levels
	  chain_vs_nonchain_analysis 	   - predictions on whether restaurant is a
										 chain or not
	  heatmap.ipynb 				   - visualizations of restaurant chain 
										 density in Vancouver, real and 
										 predicted values
										 
### Instuctions
    Start with data_cleaning.ipynb. Your end result should be multiple of .csv 
	files. From data_cleaning.ipynb, in order:
	  Expects: amenities-vancouver.json.gz
	  Outputs: complete_resturants.csv
	  References: find_postal_codes.ipynb
		Expects: complete_resturants.csv
		Outputs: complete_resturants_WITH_ADDRESS.csv
	  Expects: complete_resturants_WITH_ADDRESS.ipynb
	           postalcodes.csv (from postalcodescrap.rmd)
	  Outputs: final_restuarants.csv
	  References: get_all_restaurant_ratings.ipynb
	    Expects: final_restuarants.csv
		Outputs: final_restaurants_v2.csv
	  References: label_and_hot_encoding.ipynb
	    Expects: final_restaurants_v2.csv
		Outputs: hot_encoded_rests.csv
	  
	For the remainder of the project we will work with: 
	 final_restuarants.csv, 
	 final_restaurants_v2.csv,
	 and hot_encoded_rests.csv files.
	 
	First we will look at price_level_analysis.ipynb which works with
	final_restuarants.csv and hot_encoded_rests.csv to create a bar graph on
	price levels of restaurants and a random forest classifier to predict
	price levels.
	
	Next take a look at chain_vs_nonchain_analysis.ipynb which works with
	final_restuarants.csv to perform a chi squared test. This tests to find
	whether there is a statistically significant difference between expected
	and observed frequencies of chain restaurants in different neighborhoods.
	In the same notebook, we use, hot_encoded_rests.csv and 
	final_restaurants_v2.csv to work with a random forest classifier in 
	predicting if a restaurant is a chain or not.
	
	Finally, we can take a look at heatmap.ipynb, which utilizes 
	final_restuarants.csv to display two heatmaps to visualize density of chain
	restaurants in Vancouver, real and predicted values.
	