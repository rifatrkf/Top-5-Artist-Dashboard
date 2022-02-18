# Top-5-Artist-Dashboard in selected Year
Create the Metabase dashboard which consists of Top 5 artists (Song Release) in selected range year, e.g. If you choose the 1980 - 1999 year range, it will display a table of the artist's names with the total count of songs released.


## Metabase Dashboard
![Dashboard Screenshot (1)](https://user-images.githubusercontent.com/70887963/154684260-7be7f240-3534-4c91-baff-bba22c66c54f.png)

## SQL Query
 ![Query Screenshot (2)](https://user-images.githubusercontent.com/70887963/154684195-ef028a94-a022-42f3-b5fa-1542b2a160dd.png)

## Explanation 

### Dataset
https://github.com/fivethirtyeight/data/blob/master/classic-rock/classic-rock-song-list.csv

### Tools
Python (pandas) - data extraction

Postgresql - database engine

Metabase - Data visualization (Dashboard)


The data set is stored in a table named song_list2, 
The clause is used for defining a temporary relation such that the output of this temporary relation is available and is used by the query that is associated with the WITH clause 

![image6](https://user-images.githubusercontent.com/70887963/154685155-cdd4e6af-10bf-4111-b521-00acaaceb997.png)


Inside T2, it queries a table that contains the number of songs released by the artist per year,and is ordered from the most released songs to the least in the selected year. The output will be:

![image1](https://user-images.githubusercontent.com/70887963/154685319-912f4b46-d62f-4041-b90f-737e1789707d.png)


Important to note that the selected year filter is marked with curly braces in the metabase, so we can change it in the dashboard.

![image5](https://user-images.githubusercontent.com/70887963/154685422-b18449b3-9978-4b4e-9033-7da778700855.png)


After that, inside t3. we query a list of the top 5 of total released songs by the artist in the selected year, and the output will be:

![image1](https://user-images.githubusercontent.com/70887963/154685465-421dea04-2051-45ec-ba83-39992b5e38f5.png)



Thus, our desired output is a table that displays the  top 5 artists and count of released song per year in the selected year . so we join t2 and t3 with right join, because we want to keep rows in t3 regardless of whether a match is found in t2.


![image10](https://user-images.githubusercontent.com/70887963/154685535-27e5349b-1c04-4f8c-9aa7-e2aad3d7647d.png)


And it will result:

![image7](https://user-images.githubusercontent.com/70887963/154685600-fa4303f7-a002-4dc9-83fd-920db42a0674.png)



Then we pivot the table with pivot column is released by the year and cell column is the count.


![image2](https://user-images.githubusercontent.com/70887963/154685784-5e77c96f-a98a-49e7-be9d-020ab8b30f1a.png)












### Problem
There is a problem with visualizing through a pivot table, the order of artists in the pivot table is often not the same as the order of artists in the total count of released songs in a selected year. For example:

![image3](https://user-images.githubusercontent.com/70887963/154685805-f042d48e-979f-403a-9e7e-57b633cc8150.png)

![image11](https://user-images.githubusercontent.com/70887963/154685944-69a1d21b-8342-4ab6-a19f-19a5e2a8c90b.png)



using “ORDER BY t3.summ, released year DESC” does not solve the problem, but actually if the table not in pivot, the order will be the same as total count table.

Conclusion
In conclusion, we manage to create a metabase dashboard table as the desired output from the dataset given successfully. However, a small problem was encountered in the pivot table. 
