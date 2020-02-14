# Total_Pig_Latin

I present this project after conducting some distinct experiments on batch-processing by Pig Latin. The article doesn’t simply describe theory and facts on Pig Latin that a reader could find somewhere else. The article actually covers some experimental and practical mapreduce tasks improvised by myself using a single node Hortonworks cluster implementing YARN framework. I will be writing some JAVA UDFs to process batch data and running it to produce result in a single node cluster. The key focus of the article is on JAVA UDFs and JSON load/store function.

##Section I: Source Data and Metadata Details:

The source data for the first UDF was chosen to be baseball data holding fielding data of various players (baseball_data_sample.csv). I will be writing a UDF that takes ‘DataBag’ as an input. The ‘DataBag’ will hold ‘Tuples’ filled with single ‘Chararray’ fields. The UDF will be able to determine which string(s) is/are the most frequently occurring ones in millions of tuples. Following is the list of data field elements:

playerID – unique identifier of a player,                                                                                             yearID – year of games played,                                                                                                         stint – duration,                                                                                                                       teamID – unique identifier of team name,                                                                                                  lgID – League ID, POS - player position, G – Games played, GS – Games Started, InnOuts – amount of innings played multiplied by 3,     PO – PutOuts,E - Error, DP – Double Plays, PB – Passed Balls, WP – Wild Pitches, SB – Stolen Bases, CS – Caught Stealing, ZR – Zone Rating

 
Some key metadata on file:
Total characters = 8063747
Total lines = 162771
Size = 7875 KB


##Section II: Writing Pig UDF to calculate most frequently occurring string(s) in DataBag of tuples holding Strings:

/* I first wrote a Python code snippet to model the functionality of the UDF using a python list. This was done so that similar logic could be modeled while writing JAVA API for Pig Latin UDF*/ (please see Python.png)
 

Before writing Pig UDF, it was essential to make sure the input was a bag with tuples carrying single field-value. Hence, following Pig Script was written: (see Pigscript.txt)

The UDF present in Pigscript.txt will be called ‘ModeCalculator’ and will take an argument of a bag with tuples carrying string type values. The result will be – ‘a list of teamID’s with most number of players analyzed’ in the source file.

UDF is present in file - UDF_ModeCalculator.txt.
Resulting mode of above program was ---   ((CHN))

##Section III: Load/Store Functions on various types of data formats.

There are various Load/Store functions available in Pig Latin and also API can be used to write our own custom functions. However, this article will be limited by scope on few of the functions only. This article won’t talk about them but instead use them experimentally.

(i)	JsonStorage/JsonLoader:

Given a json file in HDFS (json_sample.png), the script (jsonloader_pig_script.txt) loads data into Pig:

If a JSON data is in nested form as shown in nester_json_sample.png, relevant pig script to load the data is present in nested_json_pig_script.txt.

##Section IV: Other JAVA UDFs I wrote:

The sample data 'heartbeat_sample.png' represents media(or movie) streaming data (I call each line of record as a ‘heartbeat’). The fields are heartbeat id, movie id, movie name, timestamp of heartbeat generation, particular instance id unique to the viewer, state of stream, timestamp representing the end of the streaming-state, device id, and location id.

The Pig Script-hb_pig_script.txt and UDF - eng_duration_UDF.txt will calculate the engagement duration of a particular movie per playback instance id. 

I further took the above application to derive ‘Population Standard Deviation’ from engagement durations for all the movies-'std_dev_pig_script.txt' and UDF - 'std_dev_UDF.txt'

##Section V: End Notes

As a Pig Latin Engineer, I am also interested in other key topics like performance and optimization (http://pig.apache.org/docs/r0.15.0/perf.html ), HDFS architecture (http://hadoop.apache.org/docs/current/hadoop-project-dist/hadoop-hdfs/HdfsUserGuide.html ), MapReduce Program (http://hadoop.apache.org/docs/current/hadoop-mapreduce-client/hadoop-mapreduce-client-core/MapReduceTutorial.html ), YARN Framework (http://hadoop.apache.org/docs/current/hadoop-yarn/hadoop-yarn-site/YARN.html ). 

####Pig Latin is an awesome MapReduce Programming Language and I Wish You All Good Luck with it.
