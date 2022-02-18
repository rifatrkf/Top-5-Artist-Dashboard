# Top-5-Artist-Dashboard in selected Year

## Metabase Dashboard

## SQL Query
 
## Explanation 

# Dataset
https://github.com/fivethirtyeight/data/blob/master/classic-rock/classic-rock-song-list.csv

# Tools
Python (pandas) - data extraction
Postgresql - database engine
Metabase - Data visualization (Dashboard)


The data set is stored in a table named song_list2, 
The clause is used for defining a temporary relation such that the output of this temporary relation is available and is used by the query that is associated with the WITH clause 



Inside T2, it queries a table that contains the number of songs released by the artist per year,and is ordered from the most released songs to the least in the selected year. The output will be:

Important to note that the selected year filter is marked with curly braces in the metabase, so we can change it in the dashboard.

After that, inside t3. we query a list of the top 5 of total released songs by the artist in the selected year, and the output will be:




Thus, our desired output is a table that displays the  top 5 artists and count of released song per year in the selected year . so we join t2 and t3 with right join, because we want to keep rows in t3 regardless of whether a match is found in t2.












And it will result:




Then we pivot the table with pivot column is released by the year and cell column is the count.













# Problem
There is a problem with visualizing through a pivot table, the order of artists in the pivot table is often not the same as the order of artists in the total count of released songs in a selected year. For example:



using “ORDER BY t3.summ, released year DESC” does not solve the problem, but actually if the table not in pivot, the order will be the same as total count table.

Conclusion
In conclusion, we manage to create a metabase dashboard table as the desired output from the dataset given successfully. However, a small problem was encountered in the pivot table. 
