# Find My Next Car Project

## Installations
Please install python (python-3.7.1) and import following packages and libraries: bokeh, Click==7.0, dill==0.2.9, Flask==1.0.2, itsdangerous==1.1.0, Jinja2==2.10
MarkupSafe==1.1.0, numpy==1.16.1, pandas==0.24.1, python-dateutil==2.8.0, pytz==2018.9, scikit-learn==0.20.2, scipy==1.2.1, six==1.12.0
sklearn==0.0, Werkzeug==0.14.1, gunicorn==19.9.0

You should also run "run: pip install -r requirements.txt" in the shell to install all other required packages

Run the following command in the app's directory to run your web app.
    `python app.py`

Then, go to http://127.0.0.1:5000

## Project Screenshots:
![image1](https://github.com/pouyanebrahimi/FindMyNextCar/blob/master/Screenshot.PNG?raw=true)

## Project Motivation
The goal of this project is to employ Data Science to build and deploy a Machine Learning Model that can predict a car price, and ultimately suggest buyers a list of best value used cars they can buy.

## Data Descriptions
Retrieving Data is the important step that should be done in the fastest possible way. For this purpose “BeautifulSoup” was used to scrape information of the listed cars on craigslist.org. The process for this task is quite simple, first we loop over the ads pages in order to collect the ads URLs by incrementing the page number parameter called oin the base URL. Once the URLs is collected, data about the car posted in that ad, such as : ‘Model Year’, ‘Make’, ‘Model’,‘Mileage’, ‘Price’ …, are stored in a SQL database. The next step is the most time consuming in every Data Science process which is Data Preprocessing & Cleansing. Information about 2 Million cars were scraped initially, which around 800,000 healthy pages were retreieved from.

Armed with this information, you can make the necessary changes to your inventory. For example, only cars with a "clean" title were used in the modeling step.

## How to Interact with this project
### Price Prediction

Now we came to the main task in all this process, which is Data Modeling, for this purpose a Multi-layer Perceptron (MLP) regressor Machine Learning models dedicated for Regression problem. r2_score for out-of-sample testing was 0.88.

The price prediction model is trained on various fetures: ‘Model Year’, ‘Make’, ‘Model’,‘Mileage’. The corrolation matrix suggested that,‘Model Year’, not surprisingly, has the most contribution to the price prediction. StandardScalar was used to normalize ‘Model Year’ and ‘Mileage’. In order to make rest of the features numerical, so that they will fit into our model, OneHotEncoder categorical variable transformation was used.

Usually we split our data into three parts : Training , validation and Testing set, but for simplicity we will use only train and test with 20% in test size, and the rest for training.

### Optimization

Once we are done with price prediction, now it is time to decide which used cars are best to buy. In order to do that, the optimizer gets various parameter from the user. First, the avaiable budget and, second, a price margin that defines a range. The model creates a list of all possible selection of used cars using this information. Third and forth are the number miles that the buyers plan to drive the car annually and the number of years that the car is planned to be kept. These parameters help to determine the total cost of keeping the car. Value loss, maitainance costs and repair costs, all contribute to the total cost.

Finally, total cost of keeping the assiciated with each car in the selection of possible cars in the price range will be predicted and given as a sortable list to the user.  

## Licensing
Authors, Acknowledgements, etc. You are more tham welcome to use the code. I appreciate if you refer to my github.
