# Clustering-courses-by-popularity
In this project we are looking at the amount of enrolled grad students in Cornell every year and determine which field should be considered in a scale from 1 to 5 that goes from Very Popular to Very Unpopular. By using clusters we can see that how many fields belong to each category in a strategic way instead of simply using the TOP 20% as very popular and so on. This can help the university understand how popular their most popular fields actually are and could potentially be used as a KPI. An example can be, that the school wants their courses to have more enrollments, therefore if they use clustering they can see if the ranges that each cluster increase than their effort was useful, if not students simply overlapped from one to another. 


# Analysis
I created five categories which are Very popular, popular, average, unpopular and Very unpopular. What we can see is that the average enrolled students for each category are as shown in the nest table. Therefore the most popular field have about 51 students enrolled, whereas the least popular have 1 student. The clustering means that if we were to classifiy classes in the 5 categories (we chose 5 categories) this would be the best courses to "represent" that cluster. In order to do that we minimized the standardized distances of the enrollment from all fields to the cluster field's representative. 
This was done using Excel solver via exploratoy analysis. Since it is exploratory analysis and not a linear programming there could be a best value for the representatives but we are confident that after running the exploration for 5 minutes the results are reliable and useful.


<img src= https://github.com/GuillermoAlcocerDelano/Clustering-courses-by-popularity/blob/master/ClusterTable.png />

# Methodology
  1. We needed to extract the data from Cornell. (source provided at the end of the file)
  2. Since it is a Tableau Dashboard, we clicked on Research Graduates (the area I was interested in analyzing). This would then filter the data and only show this category.
  3. Retrieve into a data sheet. For that you must click in the tabs symbol from the image shown and then select all rows.
  <img src= https://github.com/GuillermoAlcocerDelano/Clustering-courses-by-popularity/blob/master/ExportTableau.png />
  4. Rearrange the data in Excel using Vlookups and Concatenate fields so that you have a column for every year instead of every year making a new row in the data set. For visual understand see the Excel file and compare original data set to rearranged data set sheets.
    Note that I included an identifier for each field, this will be used for all VLOOKUPS and representative numbers.
  5. Determine 5 random course IDs that represent the 5 clusters. Note: the cluster number is only a reference, this does not mean that cluster 1 will mean the most popular courses and so on. That process will be done later on. For simplicity, it is recommended you add the rows (at least 6, since its the 5 clusters and their heading) above your arrange data set.
  6. Standardize each years enrollments using STANDARDIZE for each column (one per year), consider that you must calculate the mean and standadr deviation for each column as well. This can be done via AVERAGE() and STDEV().
  7. Use VLOOKUP to get the value for the standardization of each representative.
  8. Calculate distances using SUMXMY2() where array 1 is your row value, and second array is the cluster representative row (in the recommended rows above the data). In doubt, select the formula in Excel to clarify.
    Note that you must make a column for distance to each representative, in this case, 5 columns.
  9. Create a new column that selects the minimum value from the 5 'new columns'. Additionally have the sum of the values in a cell, preferably on top of the table. This cell will be our objective function.
  10. Minimize the Objective function considering the representatives as the variables. This must have the following constrains:
    Values must be within 1 and 47.
    Values must be integer.
  11. Create summary table with relevant information

# Source


https://tableau.cornell.edu/views/5yrEnrollmentFactsandFigures_0/EnrollmentCounts?iframeSizedToWindow=true&:embed=y&:showAppBanner=false&:display_count=no&:showVizHome=no
