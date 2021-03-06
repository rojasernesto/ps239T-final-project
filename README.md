## Description
My PS239T final project focused on cleaning crime victimization data from the NCVS and using ggplot I visualized serious violent crimes not reported throughout the United States, more specifically the 40 largest Metropolitan Areas. Additionally, I also visualized the same data but for three other groups, Hispanics, Blacks, and individuals below the poverty line. Once I visualized these results, in an attempt to explain my findings I created an API with the intention of accessing New York Times articles focusing on increased police presence. Having collected these articles I then cleaned my results using dplyr and plyr. Next rather than go through each individual article and making sure it covered strictly the United States, I ran text analysis using the tm package in order to focus on word frequencies so that I could find out what countries other than the U.S. were appearing. Once I found these countries I used the str_detect function to create a logical variable and save it in a new column so that I could subset those articles out. Lastly, now having both a clean ncvs data set and nytimes data set I graphed them together and compared their trends overtime. 

## Dependencies
1. R, version 3.4.4
2. Installed R Packages:
  - cowplot
  - dplyr
  - foreign
  - ggplot
  - ggthemes
  - jsonlite
  - plyr
  - stringr
  - tm
  
## Code
 
 1. [01_data-cleaning](https://github.com/rojasernesto/Ernesto-Rojas-ps239T-final-project/blob/master/Code/01_data-cleaning.Rmd): Here I open the original NCVS data and go through and clean it in order to create data sets 2-5 as listed in the Data section below. 
 
 2. [02_data-visualization](https://github.com/rojasernesto/Ernesto-Rojas-ps239T-final-project/blob/master/Code/02_data-visualization.Rmd): Here I visualize my data which was gathered and cleaned in 01_data-cleaning. 
 
 3. [03_data-api](https://github.com/rojasernesto/Ernesto-Rojas-ps239T-final-project/blob/master/Code/03_data-api.Rmd): Here I create and API that accesses the NYTimes API. Using the API I gathered articles covering increased police presence within the U.S.
 
 4. [04_text-analysis](https://github.com/rojasernesto/Ernesto-Rojas-ps239T-final-project/blob/master/Code/04_text-analysis.Rmd): Here I run text analysis with the goal of combing through the articles I had previously saved in 03_data-api, "nytimes." Using text analysis I search for terms such as countries other than the U.S. in order to delete those articles which covered other nations given that I am focused on crime and policing within the U.S. nytimes_final.csv comes from this file. 
 
 5. [05_text-visualization](https://github.com/rojasernesto/Ernesto-Rojas-ps239T-final-project/blob/master/Code/05_text-visualization.Rmd): Here I visualize my results from my text analysis in 04_text-analysis.Rmd and I compare those results to my initial findings from 02_data-visualization.
 
 
  
## Data
1. "original ncvs" - Refers to the original data collected from the NCVS. The data set was too large to upload but it can be found [here](https://www.icpsr.umich.edu/icpsrweb/NACJD/studies/4576) along with its codebook. This was loaded in [01_data-cleaning](https://github.com/rojasernesto/Ernesto-Rojas-ps239T-final-project/blob/master/Code/01_data-cleaning.Rmd) Part 1. 

2. "clean-ncvs.csv" - Refers to the final NCVS data which was converted to readable data in R, has the variables of interest, and cleaned of missing values. See [01_data-cleaning](https://github.com/rojasernesto/Ernesto-Rojas-ps239T-final-project/blob/master/Code/01_data-cleaning.Rmd) for how this was done. 

3. "clean-ncvs-black.csv" - Refers to data set similar to that found in the "clean-ncvs" file, however, it only focuses on individuals who self identified as Black. See [01_data-cleaning](https://github.com/rojasernesto/Ernesto-Rojas-ps239T-final-project/blob/master/Code/01_data-cleaning.Rmd) for how this was done. 

4. "clean-ncvs-hispanic.csv" - Refers to data set similar to that found in the "clean-ncvs" file, however, it only focuses on individuals who self identified as Hispanic. [01_data-cleaning](https://github.com/rojasernesto/Ernesto-Rojas-ps239T-final-project/blob/master/Code/01_data-cleaning.Rmd) for how this was done. 

5. "clean-ncvs-income.csv" - Refers to data set similar to that found in the "clean-ncvs" file, however, it only focuses on individuals who were below the poverty line. See [01_data-cleaning](https://github.com/rojasernesto/Ernesto-Rojas-ps239T-final-project/blob/master/Code/01_data-cleaning.Rmd) for how this was done. 

6. "nytimes.csv" - Refers to data collected as a result of using the NYTimes API. It includes the columns of interest which were renamed. See [03_data-api](https://github.com/rojasernesto/Ernesto-Rojas-ps239T-final-project/blob/master/Code/03_data-api.Rmd) for how this was done. 

7. "nytimes_final.csv" - Refers to the data set which was cleaned using text analysis on the "nytimes.csv" file. [See 05_text-visualization](https://github.com/rojasernesto/Ernesto-Rojas-ps239T-final-project/blob/master/Code/05_text-visualization.Rmd) for how this was done. 

## Results
1. Final_ComparisonA.jpg - One of two final comparisons where I compare the ncvs nonreporting of serious violent crimes to the number of articles focusing on increased police presence over time. Here I have two separate charts on top of one another, for more information see [05_text-visualization.Rmd](https://github.com/rojasernesto/Ernesto-Rojas-ps239T-final-project/blob/master/Code/05_text-visualization.Rmd) Part 3.  

2. Final_ComparisonB.jpg - One of two final comparisons where I compare the NCVS nonreporting of serious violent crimes to the number of articles focusing on increased police presence over time. Here I have two graphs plotted on one another to show the trends over time for both results more clearly. For more information see [05_text-visualization.Rmd](https://github.com/rojasernesto/Ernesto-Rojas-ps239T-final-project/blob/master/Code/05_text-visualization.Rmd) Part 3.

3. article_not_clean.jpg - Graph that shows the results of the number of articles focusing on increased police presence before excluding non-U.S. countries. This can be found in [03_data-api](https://github.com/rojasernesto/Ernesto-Rojas-ps239T-final-project/blob/master/Code/03_data-api.Rmd) Part 2.

4. black_anaheim_plot.jpg - Initially I was going to analyze not only all 40 MSAs, however, also the three aforementioned groups. This graph depicts the issues I encountered in doing so, in this case, no data for certain groups within specific MSAs during certain years. Based on these results I chose to only look at the U.S. as a whole rather than by specific groups. Here I visualize blacks in the Anaheim metropolitan area. See [02_data-visualization](https://github.com/rojasernesto/Ernesto-Rojas-ps239T-final-project/blob/master/Code/02_data-visualization.Rmd) Part 3 for more information.

5. black_plot.jpg - Depicts the number of serious violent crimes not reported to the police from 1980 to 2002 among individuals who self identified as black throughout all 40 MSAs together. See [02_data-visualization](https://github.com/rojasernesto/Ernesto-Rojas-ps239T-final-project/blob/master/Code/02_data-visualization.Rmd) Part 2 for more information.

6. hispanic_pv_plot.jpg -Initially I was going to analyze not only all 40 MSAs, however, also the three aforementioned groups. This graph depicts the issues I encountered in doing so, in this case, no data for certain groups within specific MSAs during certain years. Based on these results I chose to only look at the U.S. as a whole rather than by specific groups. Here I visualize hispanics in the Portland/Vancouver metropolitan area. See [02_data-visualization](https://github.com/rojasernesto/Ernesto-Rojas-ps239T-final-project/blob/master/Code/02_data-visualization.Rmd) Part 3 for more information.

7. hispanic_plot.jpg - Depicts the number of serious violent crimes not reported to the police from 1980 to 2002 among individuals who self identified as Hispanic throughout all 40mMSAs together. See [02_data-visualization](https://github.com/rojasernesto/Ernesto-Rojas-ps239T-final-project/blob/master/Code/02_data-visualization.Rmd) Part 2 for more information.

8. low_ses_plot.jpg - Depicts the number of serious violent crimes not reported to the police from 1980 to 2002 among individuals who fell below the poverty line throughout all 40MSAs together. See [02_data-visualization](https://github.com/rojasernesto/Ernesto-Rojas-ps239T-final-project/blob/master/Code/02_data-visualization.Rmd)  Part 2 for more information.

9. ncvs_plot - Depicts the number of serious violent crimes not reported to the police from 1980 to 2002 for all individuals throughout all 40MSAs together. See [02_data-visualization](https://github.com/rojasernesto/Ernesto-Rojas-ps239T-final-project/blob/master/Code/02_data-visualization.Rmd) Part 2 for more information.

3. section_visualization.jpg - Barplot used to help visualize and better understand the NyTimes articles I initially collected before doing any cleaning. This chart allowed me to decide what types of news articles I wanted to keep/exclude. See [03_data-api](https://github.com/rojasernesto/Ernesto-Rojas-ps239T-final-project/blob/master/Code/03_data-api.Rmd) Part 3 for more information. 


## More Information
If you have any questions or comments about reproducing the results outlined above, please contact Ernesto Rojas at ernestorojas@berkeley.edu.
