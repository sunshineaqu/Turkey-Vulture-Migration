# Turkey-Vulture-Migration


![alt text](https://proxy.duckduckgo.com/iu/?u=http%3A%2F%2Fwww.sfzoo.org%2Fimages%2Fgallery%2Fturkeyvulture%2Fimg_turkeyvulture_mh_large.jpg&f=1)

## Turkey Vulture Migration Project Report

## Team members: Winnie Wu, Lei Qin, and Rob Seaberg

## Project Purpose: To demonstrate ETL process.  


## Work Flow:
# 1.	Extract:
For this project we chose to focus on a theme relating to environmental studies.  From data.world that we found the data from a study which tracked the migration patterns of Turkey Vultures in North and South America ([here](https://data.world/makeovermonday/2018-w-4-turkey-vulture-migration-in-north-and-south-america)).  We chose this set because we saw the potential to link the study results to other sources such as historical climate and population data for what may be interesting insights.  
	This original data set is an excel file with 220,000 point-in-time location recordings for 19 unique turkey vultures who were tracked by satellite as they migrated between North and South America during 2003 to 2012.  After some research, we found more data sets from this same study on movebank.com, a publicly available repository of academically verified animal tracking datasets.  Here also were detailed definitions of each data attricute used in our study data.  Interesting to us was an additional excel file ([here](https://www.datarepository.movebank.org/discover?query=Cathartes+aura&filtertype=*&filter=&submit_search-filter-controls_add=Add&rpp=20&sort_by=score&order=DESC&location=l2) which gave detailed information for each vulture tracked, such as: name, life stage, mass, and study site.   We also used an excel file Vultures Acopian Center USA which listed additional comments, subspecies, and additional birds to the previous file and found from the same source. 
	Additional sources include the google maps api for converting geographic coordinates into city and state names as well as the openweathermap api to obtain temperature data for each location, as detailed below. 

# 2.	Transform: 
Using jupyter notebook, we imported our migratory point-in-time location recordings. Originally, we converted the excel sheet to a csv file, but after a long importing wait, we found that it was faster to import the large file in the original excel form.  We then imported the information to a pandas data frame and dropped irrelevant and repetitive columns.  We next completed a series of validation checks such as entry counts per column, and dropping incomplete entries.   However, this data was pretty clean already and no changes were necessary.  We also added a column for taxonomical name and filled in all values as "Cathartes aura," since we knew from our second data set that all birds in this study were of this genus and species.  The reasoning was that if we wish to compare this data to migratory patterns of other species, then this column will be useful.  
For our next data set, we imported it as a csv into a pandas data frame and followed a similar process, such as dropping unnecessary columns and validation.  We noted that unfortunately not all birds had a mass listed, but we did not make any changes to this column.  Next a connection was set up to a sqlite database.  The primary key for our original data set was changed to “event-id” because this value indicates a unique recording for each entry.  
Next, we extracted the latitude and longitude points from our migration data set.  First, using citypy, we obtained a list of all the unique cities which the birds migrated traveled over.  However, because citypy only gave us the city name, we tried google maps api next.  Google was able to give us city and state names which correlated to all of our geographic coordinates.  




Additional Movebank Information:
1.	How to use Movebank to download data needed: [here](https://www.hawkmountain.org/science/learn-to-use-tracking-maps/page.aspx?id=4515)
2.	Additional detail on the vulture study: [here](https://www.makeovermonday.co.uk/week4-2018/)
3.	An interactive map of other animal tracking studies: [here](https://www.movebank.org/panel_embedded_movebank_webapp)



