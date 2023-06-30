# Laptop Price Predictor
Final project of Machine Learning course

## Collecting data
All of the needed data scraped from <a href="https://torob.com/search/?query=%D9%84%D9%BE%20%D8%AA%D8%A7%D9%BE&stock_status=new&available=true&category=99">torob.com</a>

At scraping step, first we used ```selenium``` for getting 1176 laptop samples (picking up laptop link from torob website and write them in a ```.csv``` file). After that, we used ```Requests``` and ```BeautifulSoup``` librarys to openning every 1176 record link (loading every link from last .csv file to get laptops price and features, putting them on from-0-to-1176.csv file), because of these two library was faster than selenium in loading web pages.

## Cleaning
At first we drop non related columns (or unnecessary columns) from last .csv file and then merge related columns together. Then, we make values clean by runing Regex on some columns, and some by hand in google sheet


The finnal cleaned data includes: ```CPU Detail``` ```CPU Manufacturer``` ```CPU Generation``` ```CPU Arc``` ```Core``` ```Cache``` ```RAM``` ```HDD``` ```SSD``` ```Graphic-creator``` ```Graphic RAM``` ```Blore screen``` ```Keyboard light``` ```Battery houre``` ```Battery Cells``` ```Battery Capacity``` ```Size per Inch``` and ```Touch screen``` with ```amount``` lable


## Feature Engineering
the finnal data fream includes many NaN values, so we set them to zero, column's mode or outside value, depends on they belongs to whitch columns. we set them with sklearn Pipeline

At the second step we use ```OneHotEncoder``` and ```StandardScaler``` for categorical and numerical features.

## Training models
Used models:
* ```RandomForestRegressor```
* ```GradientBosstingRegressor```
* ```SVR``` (Regressor type of SVM algorithm)
* ```XGBoost```
* Tow types of LinearRegressions: `Ridge` and `Lasso`
* ```Fully connected```


All of the models above,  tuned with their specific hyper parameters and different cross-validations and K-folds by ```GridSearchCV```