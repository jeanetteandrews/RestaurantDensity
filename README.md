# Restaurant Densities in Greater Vancouver

### Repository in progress!

## Project Pipeline

### Question
Are there some parts of Greater Vancouver with more chain restaurants than others? How can we use visual, statistical, and machine learning applications to automatically find chain restaurant densities relative to independent restaurants?

### Dataset
We started with [amenities-vancouver.json.gz](https://github.com/jeanetteandrews/RestaurantDensity/blob/master/amenities-vancouver.json.gz), obtained from [OpenStreetMap](www.openstreetmap.org). This data gave us thousands of facilities and amenities in the Vancouver lower mainland, along with its latitude and longitude, amenity type, OSM tags, and business name.

### Acquiring, Cleaning, and Preparing Data
You will find our data cleaning workflow in:
* [data_cleaning.ipynb](https://github.com/jeanetteandrews/RestaurantDensity/blob/master/data_cleaning.ipynb) <br />

The above notebook references three other notebooks in the [more files](https://github.com/jeanetteandrews/RestaurantDensity/tree/master/more_files) folder:

* [find_postal_codes.ipynb](https://github.com/jeanetteandrews/RestaurantDensity/blob/master/more_files/find_postal_codes.ipynb) – Includes GoogleMaps API requests.
* [get_all_restaurant_ratings.ipynb](https://github.com/jeanetteandrews/RestaurantDensity/blob/master/more_files/get_all_restaurant_ratings.ipynb) – Includes GoogleMaps API requests.
* [label_and_hot_encoding.ipynb](https://github.com/jeanetteandrews/RestaurantDensity/blob/master/more_files/label_and_hot_encoding.ipynb) – Includes LabelEncoder and OneHotEncoder.

Additionally, [postalcodescrape.rmd](https://github.com/jeanetteandrews/RestaurantDensity/blob/master/more_files/postalcodescrape.rmd) scrapes postal codes in the Greater Vancouver area.
      
### Analyzing and Presenting Data
You will find our analyses and visualizations in:

* [price_level_analysis.ipynb](https://github.com/jeanetteandrews/VancouverRestaurantDensity/blob/master/price_level_analysis.ipynb) – Predicts restaurant price levels.
* [chain_vs_nonchain_analysis](https://github.com/jeanetteandrews/VancouverRestaurantDensity/blob/master/chain_vs_nonchain_analysis.ipynb) – Predicts whether or not a restaurant is a chain restuarant.
* [heatmap.ipynb](https://github.com/jeanetteandrews/VancouverRestaurantDensity/blob/master/heatmap.ipynb) – Visualizes restaurant chain density in Vancouver and compares real vs. predicted restaurant plots.

### Results

### Limitations

## Libraries Used  
* pandas
* numpy  
* fuzzywuzzy  
* python-Levenshtein  
* matplotlib  
* descartes  
* geopandas  
* shapely  
* googlemaps  
* sklearn.model_selection  
* sklearn.ensemble  
* sklearn.preprocessing  
* pandas.io.json  

## Team Members
* Jeanette Andrews
* Yu Han Zheng
* Catherine Riopel
										 
## Detailed Instuctions
1. Start with [data_cleaning.ipynb](https://github.com/jeanetteandrews/RestaurantDensity/blob/master/data_cleaning.ipynb). Your end result should be multiple CSV files. 

From [data_cleaning.ipynb](https://github.com/jeanetteandrews/RestaurantDensity/blob/master/data_cleaning.ipynb), in order:

* Expects: [amenities-vancouver.json.gz](https://github.com/jeanetteandrews/RestaurantDensity/blob/master/amenities-vancouver.json.gz)
* Outputs: [complete_resturants.csv](https://github.com/jeanetteandrews/VancouverRestaurantDensity/blob/master/complete_restaurants.csv)
* References: [find_postal_codes.ipynb](https://github.com/jeanetteandrews/RestaurantDensity/blob/master/more_files/find_postal_codes.ipynb)
	* Expects: [complete_resturants.csv](https://github.com/jeanetteandrews/VancouverRestaurantDensity/blob/master/complete_restaurants.csv)
	* Outputs: [complete_resturants_WITH_ADDRESS.csv](https://github.com/jeanetteandrews/VancouverRestaurantDensity/blob/master/complete_restaurants_WITH_ADDRESS.csv)
* Expects: [postalcodes.csv](https://github.com/jeanetteandrews/VancouverRestaurantDensity/blob/master/postalcodes.csv) (from [postalcodescrape.rmd](https://github.com/jeanetteandrews/VancouverRestaurantDensity/blob/master/more_files/postalcodescrape.rmd))
* Outputs: [final_restuarants.csv](https://github.com/jeanetteandrews/VancouverRestaurantDensity/blob/master/final_restaurants.csv)
* References: [get_all_restaurant_ratings.ipynb](https://github.com/jeanetteandrews/RestaurantDensity/blob/master/more_files/get_all_restaurant_ratings.ipynb)
	* Expects: [final_restuarants.csv](https://github.com/jeanetteandrews/VancouverRestaurantDensity/blob/master/final_restaurants.csv)
	* Outputs: [final_restaurants_v2.csv](https://github.com/jeanetteandrews/VancouverRestaurantDensity/blob/master/final_restaurants_v2.csv)
* References: [label_and_hot_encoding.ipynb](https://github.com/jeanetteandrews/RestaurantDensity/blob/master/more_files/label_and_hot_encoding.ipynb)
	* Expects: [final_restaurants_v2.csv](https://github.com/jeanetteandrews/VancouverRestaurantDensity/blob/master/final_restaurants_v2.csv)
	* Outputs: [hot_encoded_rests.csv](https://github.com/jeanetteandrews/VancouverRestaurantDensity/blob/master/hot_encoded_rests.csv)
	  
For the remainder of the project we will work with: 
* [final_restuarants.csv](https://github.com/jeanetteandrews/VancouverRestaurantDensity/blob/master/final_restaurants.csv)
* [final_restaurants_v2.csv](https://github.com/jeanetteandrews/VancouverRestaurantDensity/blob/master/final_restaurants_v2.csv)
* [hot_encoded_rests.csv](https://github.com/jeanetteandrews/VancouverRestaurantDensity/blob/master/hot_encoded_rests.csv)
	 
2. Take a look at [price_level_analysis.ipynb](https://github.com/jeanetteandrews/VancouverRestaurantDensity/blob/master/price_level_analysis.ipynb), which uses [final_restuarants.csv](https://github.com/jeanetteandrews/VancouverRestaurantDensity/blob/master/final_restaurants.csv) and [hot_encoded_rests.csv](https://github.com/jeanetteandrews/VancouverRestaurantDensity/blob/master/hot_encoded_rests.csv) to create a bar graph on restaurant price levels of and a random forest classifier to predict price levels.
	
3. Take a look at [chain_vs_nonchain_analysis](https://github.com/jeanetteandrews/VancouverRestaurantDensity/blob/master/chain_vs_nonchain_analysis.ipynb), which uses [final_restuarants.csv](https://github.com/jeanetteandrews/VancouverRestaurantDensity/blob/master/final_restaurants.csv) to perform a chi squared test. This test determines whether there is a statistically significant difference between expected and observed frequencies of chain restaurants in different neighborhoods. In the same notebook, we use [hot_encoded_rests.csv](https://github.com/jeanetteandrews/VancouverRestaurantDensity/blob/master/hot_encoded_rests.csv) and [final_restaurants_v2.csv](https://github.com/jeanetteandrews/VancouverRestaurantDensity/blob/master/final_restaurants_v2.csv) to predict whether or not a restaurant is a chain or independent restaurant using a random forest classifier.
	
4. Finally, take a look at [heatmap.ipynb](https://github.com/jeanetteandrews/VancouverRestaurantDensity/blob/master/heatmap.ipynb), which uses [final_restuarants.csv](https://github.com/jeanetteandrews/VancouverRestaurantDensity/blob/master/final_restaurants.csv) to display two heatmaps of chain restaurant densities in Vancouver, comparing real and predicted values.
	
