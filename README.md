# Writing User Defined Functions (UDFs) for Hadoop processing

I present this project after conducting some distinct experiments on batch-processing by Pig Latin. The key focus of the article is on JAVA UDF.

### Source Data and Metadata Details

The source data for the first UDF is - baseball_data_sample.csv. The UDF will be able to determine which string(s) is/are the most frequently occurring one(s).
 
Some key metadata on file:
Total characters = 8063747
Total lines = 162771
Size = 7875 KB


### Writing Pig UDF to calculate most frequently occurring string(s)
The UDF present in Pigscript.txt will be called ‘ModeCalculator’ and will take an argument of a bag with tuples carrying string type values.

UDF is present in file - UDF_ModeCalculator.txt.

### Other JAVA UDFs I wrote

The sample data 'heartbeat_sample.png' represents media(or movie) streaming data (I call each line of record as a ‘heartbeat’). The fields are heartbeat id, movie id, movie name, timestamp of heartbeat generation, particular instance id unique to the viewer, state of stream, timestamp representing the end of the streaming-state, device id, and location id.

The Pig Script-hb_pig_script.txt and UDF - eng_duration_UDF.txt will calculate the engagement duration of a particular movie per playback instance id. 

I further took the above application to derive ‘Population Standard Deviation’ from engagement durations for all the movies-'std_dev_pig_script.txt' and UDF - 'std_dev_UDF.txt'.
