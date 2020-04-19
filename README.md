# Writing User Defined Functions (UDFs) for Hadoop processing

I present this project after conducting some distinct experiments on batch-processing by Pig Latin. The key focus of the article is on JAVA UDF.

## Section I: Source Data and Metadata Details:

The source data for the first UDF is - baseball_data_sample.csv. The UDF will be able to determine which string(s) is/are the most frequently occurring one(s).
 
Some key metadata on file:
Total characters = 8063747
Total lines = 162771
Size = 7875 KB


## Section II: Writing Pig UDF to calculate most frequently occurring string(s) in DataBag of tuples holding Strings:

The UDF present in Pigscript.txt will be called ‘ModeCalculator’ and will take an argument of a bag with tuples carrying string type values.

UDF is present in file - UDF_ModeCalculator.txt.

## Section III: Load/Store Functions on various types of data formats.

There are various Load/Store functions available in Pig Latin and also API can be used to write our own custom functions. However, this article will be limited by scope on few of the functions only. This article won’t talk about them but instead use them experimentally.

(i)	JsonStorage/JsonLoader:

Given a json file in HDFS (json_sample.png), the script (jsonloader_pig_script.txt) loads data into Pig:

If a JSON data is in nested form as shown in nester_json_sample.png, relevant pig script to load the data is present in nested_json_pig_script.txt.

## Section IV: Other JAVA UDFs I wrote:

The sample data 'heartbeat_sample.png' represents media(or movie) streaming data (I call each line of record as a ‘heartbeat’). The fields are heartbeat id, movie id, movie name, timestamp of heartbeat generation, particular instance id unique to the viewer, state of stream, timestamp representing the end of the streaming-state, device id, and location id.

The Pig Script-hb_pig_script.txt and UDF - eng_duration_UDF.txt will calculate the engagement duration of a particular movie per playback instance id. 

I further took the above application to derive ‘Population Standard Deviation’ from engagement durations for all the movies-'std_dev_pig_script.txt' and UDF - 'std_dev_UDF.txt'

## Section V: End Notes

As a Pig Latin Engineer, I am also interested in other key topics like performance and optimization (http://pig.apache.org/docs/r0.15.0/perf.html ), HDFS architecture (http://hadoop.apache.org/docs/current/hadoop-project-dist/hadoop-hdfs/HdfsUserGuide.html ), MapReduce Program (http://hadoop.apache.org/docs/current/hadoop-mapreduce-client/hadoop-mapreduce-client-core/MapReduceTutorial.html ), YARN Framework (http://hadoop.apache.org/docs/current/hadoop-yarn/hadoop-yarn-site/YARN.html ). 

#### Pig Latin is an awesome MapReduce Programming Language and I Wish You All Good Luck with it.
