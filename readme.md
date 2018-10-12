Method 1  : From binary

	* Install java 8
	* No need of maven
	* Download setup file 200MB - https://github.com/brianfrankcooper/YCSB/releases/download/0.5.0/ycsb-0.5.0.tar.gz
	* Extract the tar file
	* Keep only lib/ bin/ mongodb-binding/ workloads/ and delete remaining - 5 MB
	* Run ./bin/ycsb load mongodb-async -s -P workloads/workloada -p recordcount=1000 -threads 10  > outputLoadThreads10.txt
	
		./bin/ycsb load mongodb-async -s -P workloads/workloada -p recordcount=1000 -threads 10  > outputLoadThreads10.txt
		/usr/lib/jvm/java-8-oracle/bin/java -cp /home/akilan/Desktop/ycsb-final/ycsb-0.5.0/mongodb-binding/conf:/home/akilan/Desktop/ycsb-final/ycsb-0.5.0/conf:/home/akilan/Desktop/ycsb-final/ycsb-0.5.0/lib/jackson-mapper-asl-1.9.4.jar:/home/akilan/Desktop/ycsb-final/ycsb-0.5.0/lib/HdrHistogram-2.1.4.jar:/home/akilan/Desktop/ycsb-final/ycsb-0.5.0/lib/core-0.5.0.jar:/home/akilan/Desktop/ycsb-final/ycsb-0.5.0/lib/jackson-core-asl-1.9.4.jar:/home/akilan/Desktop/ycsb-final/ycsb-0.5.0/mongodb-binding/lib/logback-core-1.1.2.jar:/home/akilan/Desktop/ycsb-final/ycsb-0.5.0/mongodb-binding/lib/mongodb-async-driver-2.0.1.jar:/home/akilan/Desktop/ycsb-final/ycsb-0.5.0/mongodb-binding/lib/mongodb-binding-0.5.0.jar:/home/akilan/Desktop/ycsb-final/ycsb-0.5.0/mongodb-binding/lib/slf4j-api-1.6.4.jar:/home/akilan/Desktop/ycsb-final/ycsb-0.5.0/mongodb-binding/lib/mongo-java-driver-3.0.3.jar:/home/akilan/Desktop/ycsb-final/ycsb-0.5.0/mongodb-binding/lib/logback-classic-1.1.2.jar com.yahoo.ycsb.Client -db com.yahoo.ycsb.db.AsyncMongoDbClient -s -P workloads/workloada -p recordcount=1000 -threads 10 -load
		Loading workload...
		Starting test.
		2018-10-12 07:37:40:129 0 sec: 0 operations; est completion in 0 seconds 
		2018-10-12 07:37:40:878 0 sec: 1000 operations; 1333.33 current ops/sec; [CLEANUP: Count=10, Max=2905, Min=1, Avg=292.1, 90=8, 99=2905, 99.9=2905, 99.99=2905] [INSERT: Count=1000, Max=339455, Min=374, Avg=5810.15, 90=6183, 99=24591, 99.9=339199, 99.99=339455] 

	* Check mongodb://example.com/?ssl=true&ssl_ca_certs=/path/to/ca.pem

Method 2 : From source code

	* Install java 8 and maven
	* Download source code from - https://github.com/brianfrankcooper/YCSB/archive/master.zip
	* mvn -pl com.yahoo.ycsb:mongodb-binding -DskipTests -am clean package
	* Following Artifacts created
		binding-parent/datastore-specific-descriptor/target/
		binding-parent/target/
		core/target/
		mongodb/target/
		target/
	* Run ./bin/ycsb load mongodb-async -s -P workloads/workloada -p recordcount=1000 -threads 10  > outputLoadThreads10.txt

		./bin/ycsb load mongodb-async -s -P workloads/workloada -p recordcount=1000 -threads 10  > outputLoadThreads10.txt
		[WARN]  Running against a source checkout. In order to get our runtime dependencies we'll have to invoke Maven. Depending on the state of your system, this may take ~30-45 seconds
		[DEBUG]  Running 'mvn -pl com.yahoo.ycsb:mongodb-binding -am package -DskipTests dependency:build-classpath -DincludeScope=compile -Dmdep.outputFilterFile=true'
		/usr/lib/jvm/java-8-oracle/bin/java -cp /home/akilan/Desktop/ycsb-final/YCSB-master/mongodb/conf:/home/akilan/Desktop/ycsb-final/YCSB-master/mongodb/target/mongodb-binding-0.16.0-SNAPSHOT.jar:/home/akilan/.m2/repository/org/mongodb/mongo-java-driver/3.8.0/mongo-java-driver-3.8.0.jar:/home/akilan/.m2/repository/org/apache/htrace/htrace-core4/4.1.0-incubating/htrace-core4-4.1.0-incubating.jar:/home/akilan/.m2/repository/org/xerial/snappy/snappy-java/1.1.7.1/snappy-java-1.1.7.1.jar:/home/akilan/Desktop/ycsb-final/YCSB-master/core/target/core-0.16.0-SNAPSHOT.jar:/home/akilan/.m2/repository/org/hdrhistogram/HdrHistogram/2.1.4/HdrHistogram-2.1.4.jar:/home/akilan/.m2/repository/org/codehaus/jackson/jackson-mapper-asl/1.9.4/jackson-mapper-asl-1.9.4.jar:/home/akilan/.m2/repository/org/codehaus/jackson/jackson-core-asl/1.9.4/jackson-core-asl-1.9.4.jar:/home/akilan/.m2/repository/com/allanbank/mongodb-async-driver/2.0.1/mongodb-async-driver-2.0.1.jar com.yahoo.ycsb.Client -db com.yahoo.ycsb.db.AsyncMongoDbClient -s -P workloads/workloada -p recordcount=1000 -threads 10 -load
		Command line: -db com.yahoo.ycsb.db.AsyncMongoDbClient -s -P workloads/workloada -p recordcount=1000 -threads 10 -load
		YCSB Client 0.16.0-SNAPSHOT

		Loading workload...
		Starting test.
		2018-10-12 07:28:29:664 0 sec: 0 operations; est completion in 0 second 
		DBWrapper: report latency for each error is false and specific error codes to track for latency are: []
		DBWrapper: report latency for each error is false and specific error codes to track for latency are: []
		DBWrapper: report latency for each error is false and specific error codes to track for latency are: []
		DBWrapper: report latency for each error is false and specific error codes to track for latency are: []
		DBWrapper: report latency for each error is false and specific error codes to track for latency are: []
		DBWrapper: report latency for each error is false and specific error codes to track for latency are: []
		DBWrapper: report latency for each error is false and specific error codes to track for latency are: []
		DBWrapper: report latency for each error is false and specific error codes to track for latency are: []
		DBWrapper: report latency for each error is false and specific error codes to track for latency are: []
		DBWrapper: report latency for each error is false and specific error codes to track for latency are: []
		2018-10-12 07:28:30:274 0 sec: 1000 operations; 1557.63 current ops/sec; [CLEANUP: Count=10, Max=2487, Min=1, Avg=250.4, 90=8, 99=2487, 99.9=2487, 99.99=2487] [INSERT: Count=1000, Max=265471, Min=376, Avg=5031.78, 90=5671, 99=31311, 99.9=265215, 99.99=265471] 

