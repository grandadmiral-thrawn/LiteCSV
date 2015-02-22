# LiteCSV
A quick tool to convert a CSV file on the web to a SQLite3 db using Python.

LiteCSV is a basic python tool that uses Requests and SQLite3 to convert a csv file stored on a webpage into a table in an existing .db in your directory. It is made simply to be a fast way to automate this process, without being too complicated, as it's assumed by me that if you know you want to put a certain csv in a certain database, it's likely you don't need many fancier options.

All the components of the csv file will be read in as TEXT. This includes date strings. Again, this is just a simple fast importer.

Here is example use:

Foxs-MacBook-Pro:february2015 dataRonin$ python litecsv.py "http://andrewsforest.oregonstate.edu/lter/about/weather/portal/UPLMET/data/uplmet_227_5min_2015.csv" fiveUplmet upl227.db

The first arguement is the webpage

The second arguement is the csvfile

The third arguement is the database

When it is done, you will see Finished Transaction on your screen.


To verify it is there,  you can check the .schema in the sqlite3 utility

        SQLite version 3.8.5 2014-08-15 22:37:57
        Enter ".help" for usage hints.
        sqlite> .schema
        CREATE TABLE fiveUplmet (Site TEXT,Date TEXT,RecNum TEXT,Flag_RecNum TEXT,LOGGERID TEXT,Flag_LOGGERID TEXT,PROGID TEXT,Flag_PROGID TEXT,BATTERY_INST TEXT,Flag_BATTERY_INST TEXT,PPT_SA_INST TEXT,Flag_PPT_SA_INST TEXT,PPT_SA_DIFF TEXT,Flag_PPT_SA_DIFF TEXT,ORI_SA_AVG TEXT,Flag_ORI_SA_AVG TEXT,PPT_SH_INST TEXT,Flag_PPT_SH_INST TEXT,PPT_SH_DIFF TEXT,Flag_PPT_SH_DIFF TEXT,ORI_SH_AVG TEXT,Flag_ORI_SH_AVG TEXT,SWE_INST TEXT,Flag_SWE_INST TEXT,SNODEP_INST TEXT,Flag_SNODEP_INST TEXT,SNODEP_MED TEXT,Flag_SNODEP_MED TEXT,LYS_TB_TOT TEXT,Flag_LYS_TB_TOT TEXT);

And here is that database and table "in action"

        sqlite> select SNODEP_INST from fiveUplmet limit 10;
        46.00000
        51.00000
        49.00000
        47.00000
        47.00000
        46.00000
        47.00000
        54.00000
        49.00000
        47.00000

I hope that this will save you some time. 
