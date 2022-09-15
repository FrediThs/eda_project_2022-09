# ds-project-2022-09-14

Documentation for the King County House prices.

## Environment
Please make sure you have forked the repo and set up a new virtual environment. For this purpose you can use the following commands:

```sh
pyenv local 3.9.8
python -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
```

## Setup

When using this notebook please make sure to follow the following steps:

* setting the python version locally to 3.9.8
* creating a virtual environment using the `venv` module
* activating your newly created environment 
* upgrading `pip` (This step is not absolutely necessary, but will save you trouble when installing some packages.)
* installing the required packages via `pip`

To make sure you have all the necessary packages a requirements.txt has been added. Please make sure to use the one attached here. In case you want a different one use this command:

```bash
pip freeze > requirements.txt
```

## Data cleaning + Notebook order

The dataset has been adapted to the needs of the stakeholder and additional information has been added for geolcation. It is therefore important to run the notebooks in the right order. 

- 1st notebook contains the data cleaning + documentation
- 2nd notebookd contains the vizuals

## Column Names and descriptions for King County Data Set

For further reference of the maeaning of column names, please check below.

## Orginal columns
- **id** - unique identified for a house
- **dateDate** - house was sold
- **pricePrice** - is prediction target
- **bedroomsNumber** - # of bedrooms
- **bathroomsNumber** - # of bathrooms
- **sqft_livingsquare** - footage of the home
- **sqft_lotsquare** - footage of the lot
- **floorsTotal** - floors (levels) in house
- **waterfront** - House which has a view to a waterfront
- **view** - An index from 0 to 4 of how good the view of the property was: 0 = No view, 1 = Fair 2 = Average, 3 = Good, 4 = Excellent
- **condition** - An index from 1 to 5 on the condition of the apartment. 1 = Poor- Worn out, 2 = Fair- Badly worn, 3 = Average, 4 = Good, 5= Very Good
- **grade** -  An index from 1 to 13, where 1-3 falls short of building construction and design, 7 has an average level of construction and design, and 11-13 have a high quality level of construction and design.
- **sqft_above** - square footage of house apart from basement
- **sqft_basement** - square footage of the basement
- **yr_built** - Built Year
- **yr_renovated** - Year when house was renovated
- **zipcode** - zip
- **lat** - Latitude coordinate
- **long** - Longitude coordinate
- **sqft_living15** - The square footage of interior housing living space for the nearest 15 neighbors
- **sqft_lot15** - The square footage of the land lots of the nearest 15 neighbors 

# Added columns
- **city** - joined using a csv containing the zip
- **classification** - Overall usage of zip code: 'Island', 'Has Shore', 'Richie rich', 'City ', 'Forest', 'Poor dogs', 'City', 'Belle', 'Wide land', 'Outskirt'
- **price_per_sqft_house** - Predicted 'price' divided by 'sqft_living'
- **price_per_sqft_lot** - Predicted 'price' divided by 'sqft_lot'
- **price_tag_house** - if price_per_sqft_house > 90% quantile = Top 10, if price_per_sqft_house between 50% and 90% quantile = Above average, below 50% quantile below average
- **price_tag_lot** - if price_per_sqft_lot > 90% quantile = Top 10, if price_per_sqft_lot between 50% and 90% quantile = Above average, below 50% quantile below average
- **renovation_indicator** - shows the renovation status - is not usable because the classification is to rough
- **view_eval** - string to show in words how good the view is
- **condition_eval** - string to show in words how good the condition is
- **grade_eval** - string to show in words how good the property is
- **sqft_basement_cleaned** - cleaned basement size using the sqft_livingsquare - sqft_above
- **basement_to_rest_ratio**  - sqft_basement_cleaned divided by sqft_above to show how much of the property is below ground
- **basement_sizes_string** - ranging from xsmall: to 25% quantile, small: to 50% quantile, medium: to 75% quantile, large: to 90% quantile, xlarge: 90% quantile +
- **basement_sizes_int** corresponding ints to basement_sizes_string for sorting purposes
- **has_secret_storage** - boolean to indicate properties where the basement size is officially unkknown
