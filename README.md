# SF_crime_statistics

Q&A:

1. How did changing values on the SparkSession property parameters affect the throughput and latency of the data?
There are several configuration properties that allow you to tweak for example the resources spark uses. This affect directly throughput and latency since they determine for example the way spark allocate the executors to maximize parallelism like dynamic allocation which can reduce latency but a high cost because of overhead is paid.

2. What were the 2-3 most efficient SparkSession property key/value pairs? Through testing multiple variations on values, how can you tell these were the most optimal?
I think one indicator to evaluate the most optimal is the reduction of the duration of a process which is reflected in the progress reporter as the number of rows processed per second and the indicator input Rows Per Second .
I configured the memory properties in the past whose optimum depends on the available resources.  
spark.executor.memory:8g
spark.driver.memory:8g	 
I also modified spark.streaming.receiver.maxRate and spark.streaming.kafka.maxRatePerPartition=(20,10) but I didn't observe any performance improvement.
