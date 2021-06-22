# Unemployment Project 
By Ank, 

Extraction

This is an ETL Project where I used 3 datasets from the public platform Kaggle and Data World. All of our data was based on county through all the States ranging over various years from 2010 to 2015. These were the most recent ones we could find. The sources for our dataset are as follows
 
Diversity Index from Kaggle.
Unemployment from Kaggle.
Median Income by county from Data World.

Transformation

My first steps in cleaning up the datasets involved figuring out which variables were not relevant. For the Median Income Dataset (Figure 1), we dropped the columns County-State & State and renamed the State Code column to State. 
					
I also split certain columns such as Location from Diversity table into County & State to make it easier to merge and group with the other 2 datasets (Figure 2).

For the unemployment rate dataset, State column was in full name (Figure 3), we needed to abbreviate them to merge with the rest. To do this, a dictionary of states and their abbreviations were used with a loc loop to iterate through the dataset (Figure 4). Finally, we grouped this dataset by State and County and averaged for each County.

After cleaning the datasets and workable, I started merging. To start, the Unemployment dataset and Median Income dataset were merged on State and County, using an inner join. The Diversity dataset was then merged on that by State and County again, using an inner join as well. With all the three datasets combined (Figure 5) into one universal table, the State and County index was reset turning them back into columns, and columns were reordered to a more logical format.


Load

The last step was to transfer our final output into a DataBase. 
I created a extract the data frame into the CSV file and then with the help of boot3 service I upload this into AWS S3 buckuct. On Later stage this data will 
will push to AWS dynmo DB with the help of AWS Datapipe line. 

I inspired by a team of three who worked on the simmilar data set.

Summary
I used these datasets so we could identify the diversity ratio, median income and unemployment rates per county for each state. The final output will help us to recognize which county, state that has the following. 

Most or Least Population. 
Median Household Income
Unemployment Rate
Diversity Index
Race Index 

These indices can be used to identify if any development aid/work are required for areas with high unemployment rate, low median income or with high population. 
If the population is high and if the schools/colleges/educational institutions are less, these indices can be used to build more educational institutions, which in turn create more employment opportunities. It is a cascading effect of more the population, more educational institutions, more employment, more household income.
