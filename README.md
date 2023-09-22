This repositry contains the assignments I completed during the course **CSF441**

Following are the requirements for the assignments:

***Assignment 1***:


For Week of Aug 21: Data acquisition and inspection

    Download pin code data in CSV from data.gov.in (search for all india pincode directory till last month).
    Read and create a data frame.
    Count the number of rows and columns in the data frame.
    List the column names.
    Count the number of rows with missing values, and number of rows with missing values.

For Week of Aug 28: Data cleaning

    Re-read the CSV file with 'Latitude' and "Longitude" columns read as string. Hint: use dtype parameter in read_csv method.
    Remove rows with missing values and reset the indices of the data frame.
    Clean the 'Latitude' and "Longitude" columns and convert them to float type data: Hint: use .astype(float). Check the error during conversion. Clean and retry the conversion. Repeat the process till the conversion goes through.

***Assignment 2***:

  Data Acquisition and Inspection:

  
Read only the Gender and Height ata columns from the attached Excel file. 
df = pd.read_excel(<filename>, usecols=<list of columns>) 
You must install openpyxl package before using Pandas read_excel method. (ex: pip install openpyxl)
Check the exact name of the Height data column.
You may use Pandas function to change the column names to shorten them for convenient of use. 
(For example: df.rename(columns={"A xxxx": "a"}). Note: rename method will change the name of only those columns you specify. Remember that like most pandas methods, rename does not update the original dataframe unless you use inplace=True. or assign it to the same or a different data frame.)
However, the original column name must be used as the label of the axis.

Data Cleaning:
The gender column data may have some non-uniformity on the name.  For example: "Male" may appear as "male" in some rows. Use Pandas function to resolve that problem.

Data Visualization:
Use either of Plotly Express,  Seaborn to create the following distribution plots :

    Histogram pot
    Box plot
    Violin plot

Note that the plots must show distributions of the Male and Female heights separately (may overlap) on the same plot.

(This dataset contains the height, weight and 4 fingerprint measurements (length, width, area and circumference), collected from 200 participants. This data was collected with the intention of performing regression analysis to asses whether a significant relationship exists between fingerprint size and physical stature. The dataset was downloaded from https://repository.lboro.ac.uk/articles/dataset/Height_weight_and_fingerprint_measurements_collected_from_200_participants/7539206)

***Assignment 3***:

Goal: Create a time-series visualization of  local monthly temperatures over a few years.
Data Source URL: https://data.telengana.gov.in/dataset/telengana-temperature-data-2013-2017

Data Acquisition component: You may directly download the Maximum and Minimum data sets from the source URL mentioned above or use the following steps to get the datasets as Pandas dataframes. (see https://data.telangana.gov.in/dataset/62a1cc18-7613-460b-a0b1-4b71c78fa1ce/api)

    Use python api requests and query the metadata from the above mentioned URL as  

           r = requests.get("https://data.telangana.gov.in/api/1/metastore/schemas/dataset/items/62a1cc18-7613-460b-a0b1-4b71c78fa1ce&quot;)
           dataInfo = r.json()

     Use the two URLs listed in the metadata in the distributions item array of dataInfo to read_csv as

            df_max = pd.read_csv(dataInfo["distribution"][0]["downloadURL"])
            df_min = pd.read_csv(

dataInfo["distribution"][1]["downloadURL"])

Data Preparation and Data Cleaning component: Extract the data rows corresponding to Medchal district and Kapra Mandal from the data frames. 
(You may combine the two rows into a single data frame if it helps in creating the visualization.)
Use Pandas transpose (T) operation to transpose the table columns into rows and rows into columns. 
Convert the months and year data to Pandas Datetime format. (to be discussed in Day 2 of week 4 practice session).

Data Visualization component: Create line plots using either of plotly.express and seaborn to show the minimum and maximum temperatures for the months and years available in the dataset.

Sample Visuals from plotly express and seaborn are attached.

***Assignment 4***:

Goal: 
Live access NSE market data using nsepython. Acquire and compare the relative changes of a few NIFTY index data over the last 9 yrs.

Detail:  
Acquire and create visual comparison of percent changes of the following 3 index funds over the last 9 years.

    NIFTY 50
    NIFTY BANK
    NIFTY IT

Data Acquisition Component:
Install nsepython package and use its index_total_returns for the above mentioned funds (symbols of the funds are as written above) to acquire historical index data for the following period (See https://unofficed.com/nse-python/documentation/ for details).
Start Date: "01-May-2014"
End Data: "10-Sept-2023"

Data Cleaning and Data Preparation Component:
For every acquired timeseries index data: Compute the relative percent change in the index return value from the start date. 
It will require you to apply the following calculation at every date:
    100*(Return at the date of interest -  Return at the start date)/Return at the start date

Combine the updated index data to create a single data frame. Rename the columns to distinguish the relative percent change data for the three index funds from each other. 

Data Visualization: 
Use Plotly Express or Seaborn to create line plots of on a single chart.
