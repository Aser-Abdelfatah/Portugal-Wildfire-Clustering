To re-produce the SOM file, the data located in https://raw.githubusercontent.com/Aser-Abdelfatah/Portugal-Wildfire-Research/main/Portugal_Dataset_Extraction/Datasets/Burned_Data/climatic_and_meteorological_data_after_imputation.csv need to be pre-processed to remove irrelevant columns.
</br> This can be done in either R or Python.</br>  In R, 
```{r}
library(XML)
library(RCurl)
url <- getURL("https://raw.githubusercontent.com/Aser-Abdelfatah/Portugal-Wildfire-Research/main/Portugal_Dataset_Extraction/Datasets/Burned_Data/climatic_and_meteorological_data_after_imputation.csv")
data = read.csv(text = url)
data <- data[-1] # remove index column
drop <- c( 'day_of_the_year', 'month', 'time', 'x_int', 'y_int', 'burned_areas') # remove irrelevant columns
data = data[,!(names(data) %in% drop)] # This pre-processed data is the same as that used in the R file 
```
In Python,
```{r}
SOM = pd.read_csv('https://raw.githubusercontent.com/Aser-Abdelfatah/Portugal-Wildfire-Research/main/Portugal_Dataset_Extraction/Datasets/Burned_Data/climatic_and_meteorological_data_after_imputation.csv', index_col=None)
SOM = SOM.drop(columns=['Unnamed: 0', 'day_of_the_year', 'month', 'time', 'x_int', 'y_int', 'burned_areas'])
SOM.to_csv('C:\\Users\\asera\\Downloads\\Research\\Current\\SOM.csv') # change directory to save to your local directory and use the saved data with SOM
                                                                      # This pre-processed data is the same as that used in the R file 
```
