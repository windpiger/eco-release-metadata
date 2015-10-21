
<!---
# Licensed to the Apache Software Foundation (ASF) under one
# or more contributor license agreements.  See the NOTICE file
# distributed with this work for additional information
# regarding copyright ownership.  The ASF licenses this file
# to you under the Apache License, Version 2.0 (the
# "License"); you may not use this file except in compliance
# with the License.  You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
-->
# Apache Spark  1.5.2 Release Notes

These release notes cover new developer and user-facing incompatibilities, important issues, features, and major improvements.


---

* [SPARK-11153](https://issues.apache.org/jira/browse/SPARK-11153) | *Blocker* | **Turns off Parquet filter push-down for string and binary columns**

Due to PARQUET-251, {{BINARY}} columns in existing Parquet files may be written with corrupted statistics information. This information is used by filter push-down optimization. Since Spark 1.5 turns on Parquet filter push-down by default, we may end up with wrong query results. PARQUET-251 has been fixed in parquet-mr 1.8.1, but Spark 1.5 is still using 1.7.0.

Note that this kind of corrupted Parquet files could be produced by any Parquet data models.

This affects all Spark SQL data types that can be mapped to Parquet {{BINARY}}, namely:

- {{StringType}}
- {{BinaryType}}
- {{DecimalType}} (but Spark SQL doesn't support pushing down {{DecimalType}} columns for now.)

To avoid wrong query results, we should disable filter push-down for columns of {{StringType}} and {{BinaryType}} until we upgrade to parquet-mr 1.8.


---

* [SPARK-11135](https://issues.apache.org/jira/browse/SPARK-11135) | *Blocker* | **Exchange sort-planning logic incorrectly avoid sorts when existing ordering is non-empty subset of required ordering**

In Spark SQL, the Exchange planner tries to avoid unnecessary sorts in cases where the data has already been sorted by a superset of the requested sorting columns. For instance, let's say that a query calls for an operator's input to be sorted by `a.asc` and the input happens to already be sorted by `[a.asc, b.asc]`. In this case, we do not need to re-sort the input. The converse, however, is not true: if the query calls for `[a.asc, b.asc]`, then `a.asc` alone will not satisfy the ordering requirements, requiring an additional sort to be planned by Exchange.

However, the current Exchange code gets this wrong and incorrectly skips sorting when the existing output ordering is a subset of the required ordering. This is simple to fix, however.

This bug was introduced in https://github.com/apache/spark/pull/7458, so it affects 1.5.0+.


---

* [SPARK-11126](https://issues.apache.org/jira/browse/SPARK-11126) | *Blocker* | **A memory leak in SQLListener.\_stageIdToStageMetrics**

SQLListener adds all stage infos to \_stageIdToStageMetrics, but only removes  stage infos belonging to SQL executions.

Reported by Terry Hoo in https://www.mail-archive.com/user@spark.apache.org/msg38810.html


---

* [SPARK-11104](https://issues.apache.org/jira/browse/SPARK-11104) | *Major* | **A potential deadlock in StreamingContext.stop and stopOnShutdown**

When the shutdown hook of StreamingContext and StreamingContext.stop are running at the same time (e.g., press CTRL-C when StreamingContext.stop is running), the following deadlock may happen:

{code}
Java stack information for the threads listed above:
===================================================
"Thread-2":
	at org.apache.spark.streaming.StreamingContext.stop(StreamingContext.scala:699)
	- waiting to lock \<0x00000005405a1680\> (a org.apache.spark.streaming.StreamingContext)
	at org.apache.spark.streaming.StreamingContext.org$apache$spark$streaming$StreamingContext$$stopOnShutdown(StreamingContext.scala:729)
	at org.apache.spark.streaming.StreamingContext$$anonfun$start$1.apply$mcV$sp(StreamingContext.scala:625)
	at org.apache.spark.util.SparkShutdownHook.run(ShutdownHookManager.scala:266)
	at org.apache.spark.util.SparkShutdownHookManager$$anonfun$runAll$1$$anonfun$apply$mcV$sp$1.apply$mcV$sp(ShutdownHookManager.scala:236)
	at org.apache.spark.util.SparkShutdownHookManager$$anonfun$runAll$1$$anonfun$apply$mcV$sp$1.apply(ShutdownHookManager.scala:236)
	at org.apache.spark.util.SparkShutdownHookManager$$anonfun$runAll$1$$anonfun$apply$mcV$sp$1.apply(ShutdownHookManager.scala:236)
	at org.apache.spark.util.Utils$.logUncaughtExceptions(Utils.scala:1697)
	at org.apache.spark.util.SparkShutdownHookManager$$anonfun$runAll$1.apply$mcV$sp(ShutdownHookManager.scala:236)
	at org.apache.spark.util.SparkShutdownHookManager$$anonfun$runAll$1.apply(ShutdownHookManager.scala:236)
	at org.apache.spark.util.SparkShutdownHookManager$$anonfun$runAll$1.apply(ShutdownHookManager.scala:236)
	at scala.util.Try$.apply(Try.scala:161)
	at org.apache.spark.util.SparkShutdownHookManager.runAll(ShutdownHookManager.scala:236)
	- locked \<0x00000005405b6a00\> (a org.apache.spark.util.SparkShutdownHookManager)
	at org.apache.spark.util.SparkShutdownHookManager$$anon$2.run(ShutdownHookManager.scala:216)
	at org.apache.hadoop.util.ShutdownHookManager$1.run(ShutdownHookManager.java:54)
"main":
	at org.apache.spark.util.SparkShutdownHookManager.remove(ShutdownHookManager.scala:248)
	- waiting to lock \<0x00000005405b6a00\> (a org.apache.spark.util.SparkShutdownHookManager)
	at org.apache.spark.util.ShutdownHookManager$.removeShutdownHook(ShutdownHookManager.scala:199)
	at org.apache.spark.streaming.StreamingContext.stop(StreamingContext.scala:712)
	- locked \<0x00000005405a1680\> (a org.apache.spark.streaming.StreamingContext)
	at org.apache.spark.streaming.StreamingContext.stop(StreamingContext.scala:684)
	- locked \<0x00000005405a1680\> (a org.apache.spark.streaming.StreamingContext)
	at org.apache.spark.streaming.SessionByKeyBenchmark$.main(SessionByKeyBenchmark.scala:108)
	at org.apache.spark.streaming.SessionByKeyBenchmark.main(SessionByKeyBenchmark.scala)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:497)
	at org.apache.spark.deploy.SparkSubmit$.org$apache$spark$deploy$SparkSubmit$$runMain(SparkSubmit.scala:680)
	at org.apache.spark.deploy.SparkSubmit$.doRunMain$1(SparkSubmit.scala:180)
	at org.apache.spark.deploy.SparkSubmit$.submit(SparkSubmit.scala:205)
	at org.apache.spark.deploy.SparkSubmit$.main(SparkSubmit.scala:120)
	at org.apache.spark.deploy.SparkSubmit.main(SparkSubmit.scala)
{code}


---

* [SPARK-11094](https://issues.apache.org/jira/browse/SPARK-11094) | *Minor* | **Test runner script fails to parse Java version.**

Running {{dev/run-tests}} fails when the local Java version has an extra string appended to the version.
For example, in Debian Stretch (currently testing distribution), {{java -version}} yields "1.8.0\_66-internal" where the extra part "-internal" causes the script to fail.


---

* [SPARK-11066](https://issues.apache.org/jira/browse/SPARK-11066) | *Minor* | **Flaky test o.a.scheduler.DAGSchedulerSuite.misbehavedResultHandler occasionally fails due to j.l.UnsupportedOperationException concerning a finished JobWaiter**

The DAGSchedulerSuite test for the "misbehaved ResultHandler" has an inherent problem: it creates a job for the DAGScheduler comprising multiple (2) tasks, but whilst the job will fail and a SparkDriverExecutionException will be returned, a race condition exists as to whether the first task's (deliberately) thrown exception causes the job to fail - and having its causing exception set to the DAGSchedulerSuiteDummyException that was thrown as the setup of the misbehaving test - or second (and subsequent) tasks who equally end, but have instead the DAGScheduler's legitimate UnsupportedOperationException (a subclass of RuntimeException) returned instead as their causing exception.  This race condition is likely associated with the vagaries of processing quanta, and expense of throwing two exceptions (under interpreter execution) per thread of control; this race is usually 'won' by the first task throwing the DAGSchedulerDummyException, as desired (and expected)... but not always.

The problem for the testcase is that the first assertion is largely concerning the test setup, and doesn't (can't? Sorry, still not a ScalaTest expert) capture all the causes of SparkDriverExecutionException that can legitimately arise from a correctly working (not crashed) DAGScheduler.  Arguably, this assertion might test something of the DAGScheduler... but not all the possible outcomes for a working DAGScheduler.  Nevertheless, this test - when comprising a multiple task job - will report as a failure when in fact the DAGScheduler is working-as-designed (and not crashed ;-).  Furthermore, the test is already failed before it actually tries to use the SparkContext a second time (for an arbitrary processing task), which I think is the real subject of the test?

The solution, I submit, is to ensure that the job is composed of just one task, and that single task will result in the call to the compromised ResultHandler causing the test's deliberate exception to be thrown and exercising the relevant (DAGScheduler) code paths.  Given tasks are scoped by the number of partitions of an RDD, this could be achieved with a single partitioned RDD (indeed, doing so seems to exercise/would test some default parallelism support of the TaskScheduler?); the pull request offered, however, is based on the minimal change of just using a single partition of the 2 (or more) partition parallelized RDD.  This will result in scheduling a job of just one task, one successful task calling the user-supplied compromised ResultHandler function, which results in failing the job and unambiguously wrapping our DAGSchedulerSuiteException inside a SparkDriverExecutionException; there are no other tasks that on running successfully will find the job failed causing the 'undesired' UnsupportedOperationException to be thrown instead.  This, then, satisfies the test's setup assertion.

I have tested this hypothesis having parametised the number of partitions, N, used by the "misbehaved ResultHandler" job and have observed the 1 x DAGSchedulerSuiteException first, followed by the legitimate N-1 x UnsupportedOperationExceptions ... what propagates back from the job seems to simply become the result of the race between task threads and the intermittent failures observed.


---

* [SPARK-11063](https://issues.apache.org/jira/browse/SPARK-11063) | *Critical* | **Spark TaskSetManager doesn't use Receiver's scheduling executors**

The format of RDD's preferredLocations must be hostname but the format of Streaming Receiver's scheduling executors is hostport. So it doesn't work.


---

* [SPARK-11056](https://issues.apache.org/jira/browse/SPARK-11056) | *Minor* | **Improve documentation on how to build Spark efficiently**

Slow build times are a common pain point for new Spark developers.  We should improve the main documentation on building Spark to describe how to make building Spark less painful.


---

* [SPARK-11051](https://issues.apache.org/jira/browse/SPARK-11051) | *Critical* | **NullPointerException when action called on localCheckpointed RDD (that was checkpointed before)**

While toying with {{RDD.checkpoint}} and {{RDD.localCheckpoint}} methods, the following NullPointerException was thrown:

{code}
scala\> lines.count
java.lang.NullPointerException
  at org.apache.spark.rdd.RDD.firstParent(RDD.scala:1587)
  at org.apache.spark.rdd.MapPartitionsRDD.getPartitions(MapPartitionsRDD.scala:35)
  at org.apache.spark.rdd.RDD$$anonfun$partitions$2.apply(RDD.scala:239)
  at org.apache.spark.rdd.RDD$$anonfun$partitions$2.apply(RDD.scala:237)
  at scala.Option.getOrElse(Option.scala:121)
  at org.apache.spark.rdd.RDD.partitions(RDD.scala:237)
  at org.apache.spark.SparkContext.runJob(SparkContext.scala:1927)
  at org.apache.spark.rdd.RDD.count(RDD.scala:1115)
  ... 48 elided
{code}

To reproduce the issue do the following:

{code}
$ ./bin/spark-shell
Welcome to
      \_\_\_\_              \_\_
     / \_\_/\_\_  \_\_\_ \_\_\_\_\_/ /\_\_
    \_\ \/ \_ \/ \_ `/ \_\_/  '\_/
   /\_\_\_/ .\_\_/\\_,\_/\_/ /\_/\\_\   version 1.6.0-SNAPSHOT
      /\_/

Using Scala version 2.11.7 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0\_60)
Type in expressions to have them evaluated.
Type :help for more information.

scala\> val lines = sc.textFile("README.md")
lines: org.apache.spark.rdd.RDD[String] = MapPartitionsRDD[1] at textFile at \<console\>:24

scala\> sc.setCheckpointDir("checkpoints")

scala\> lines.checkpoint

scala\> lines.count
res2: Long = 98

scala\> lines.localCheckpoint
15/10/10 22:59:20 WARN MapPartitionsRDD: RDD was already marked for reliable checkpointing: overriding with local checkpoint.
res4: lines.type = MapPartitionsRDD[1] at textFile at \<console\>:24

scala\> lines.count
java.lang.NullPointerException
  at org.apache.spark.rdd.RDD.firstParent(RDD.scala:1587)
  at org.apache.spark.rdd.MapPartitionsRDD.getPartitions(MapPartitionsRDD.scala:35)
  at org.apache.spark.rdd.RDD$$anonfun$partitions$2.apply(RDD.scala:239)
  at org.apache.spark.rdd.RDD$$anonfun$partitions$2.apply(RDD.scala:237)
  at scala.Option.getOrElse(Option.scala:121)
  at org.apache.spark.rdd.RDD.partitions(RDD.scala:237)
  at org.apache.spark.SparkContext.runJob(SparkContext.scala:1927)
  at org.apache.spark.rdd.RDD.count(RDD.scala:1115)
  ... 48 elided
{code}


---

* [SPARK-11047](https://issues.apache.org/jira/browse/SPARK-11047) | *Critical* | **Internal accumulators miss the internal flag when replaying events in the history server**

Internal accumulators don't write the internal flag to event log. So on the history server Web UI, all accumulators are not internal. This causes incorrect peak execution memory and unwanted accumulator table displayed on the stage page.


---

* [SPARK-11039](https://issues.apache.org/jira/browse/SPARK-11039) | *Trivial* | **Document all UI "retained\*" configurations**

Most are documented except these:
- spark.sql.ui.retainedExecutions
- spark.streaming.ui.retainedBatches

They are really helpful for managing the memory usage of the driver application.


---

* [SPARK-11026](https://issues.apache.org/jira/browse/SPARK-11026) | *Major* | **spark.yarn.user.classpath.first does work for 'spark-submit --jars hdfs://user/foo.jar'**

when spark.yarn.user.classpath.first=true and addJars is on hdfs path, need to add the yarn's linkName of addJars to the system classpath.


---

* [SPARK-11023](https://issues.apache.org/jira/browse/SPARK-11023) | *Major* | **Error initializing SparkContext. java.net.URISyntaxException**

Simliar to SPARK-10326. [https://issues.apache.org/jira/browse/SPARK-10326?page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel&focusedCommentId=14949470#comment-14949470]


C:\WINDOWS\system32\>pyspark --master yarn-client
Python 2.7.10 \|Anaconda 2.3.0 (64-bit)\| (default, Sep 15 2015, 14:26:14) [MSC v.1500 64 bit (AMD64)]
Type "copyright", "credits" or "license" for more information.
IPython 4.0.0 – An enhanced Interactive Python.
? -\> Introduction and overview of IPython's features.
%quickref -\> Quick reference.
help -\> Python's own help system.
object? -\> Details about 'object', use 'object??' for extra details.
15/10/08 09:28:05 WARN MetricsSystem: Using default name DAGScheduler for source because spark.app.id is not set.
15/10/08 09:28:06 WARN : Your hostname, PC-509512 resolves to a loopback/non-reachable address: fe80:0:0:0:0:5efe:a5f:c318%net3, but we couldn't find any external IP address!
15/10/08 09:28:08 WARN BlockReaderLocal: The short-circuit local reads feature cannot be used because UNIX Domain sockets are not available on Windows.
15/10/08 09:28:08 ERROR SparkContext: Error initializing SparkContext.
java.net.URISyntaxException: Illegal character in opaque part at index 2: C:\spark\bin\..\python\lib\pyspark.zip
at java.net.URI$Parser.fail(Unknown Source)
at java.net.URI$Parser.checkChars(Unknown Source)
at java.net.URI$Parser.parse(Unknown Source)
at java.net.URI.\<init\>(Unknown Source)
at org.apache.spark.deploy.yarn.Client$$anonfun$setupLaunchEnv$7.apply(Client.scala:558)
at org.apache.spark.deploy.yarn.Client$$anonfun$setupLaunchEnv$7.apply(Client.scala:557)
at scala.collection.immutable.List.foreach(List.scala:318)
at org.apache.spark.deploy.yarn.Client.setupLaunchEnv(Client.scala:557)
at org.apache.spark.deploy.yarn.Client.createContainerLaunchContext(Client.scala:628)
at org.apache.spark.deploy.yarn.Client.submitApplication(Client.scala:119)
at org.apache.spark.scheduler.cluster.YarnClientSchedulerBackend.start(YarnClientSchedulerBackend.scala:56)
at org.apache.spark.scheduler.TaskSchedulerImpl.start(TaskSchedulerImpl.scala:144)
at org.apache.spark.SparkContext.\<init\>(SparkContext.scala:523)
at org.apache.spark.api.java.JavaSparkContext.\<init\>(JavaSparkContext.scala:61)
at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source)
at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Source)
at java.lang.reflect.Constructor.newInstance(Unknown Source)
at py4j.reflection.MethodInvoker.invoke(MethodInvoker.java:234)
at py4j.reflection.ReflectionEngine.invoke(ReflectionEngine.java:379)
at py4j.Gateway.invoke(Gateway.java:214)
at py4j.commands.ConstructorCommand.invokeConstructor(ConstructorCommand.java:79)
at py4j.commands.ConstructorCommand.execute(ConstructorCommand.java:68)
at py4j.GatewayConnection.run(GatewayConnection.java:207)
at java.lang.Thread.run(Unknown Source)
15/10/08 09:28:08 ERROR Utils: Uncaught exception in thread Thread-2
java.lang.NullPointerException
at org.apache.spark.network.netty.NettyBlockTransferService.close(NettyBlockTransferService.scala:152)
at org.apache.spark.storage.BlockManager.stop(BlockManager.scala:1228)
at org.apache.spark.SparkEnv.stop(SparkEnv.scala:100)
at org.apache.spark.SparkContext$$anonfun$stop$12.apply$mcV$sp(SparkContext.scala:1749)
at org.apache.spark.util.Utils$.tryLogNonFatalError(Utils.scala:1185)
at org.apache.spark.SparkContext.stop(SparkContext.scala:1748)
at org.apache.spark.SparkContext.\<init\>(SparkContext.scala:593)
at org.apache.spark.api.java.JavaSparkContext.\<init\>(JavaSparkContext.scala:61)
at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source)
at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Source)
at java.lang.reflect.Constructor.newInstance(Unknown Source)
at py4j.reflection.MethodInvoker.invoke(MethodInvoker.java:234)
at py4j.reflection.ReflectionEngine.invoke(ReflectionEngine.java:379)
at py4j.Gateway.invoke(Gateway.java:214)
at py4j.commands.ConstructorCommand.invokeConstructor(ConstructorCommand.java:79)
at py4j.commands.ConstructorCommand.execute(ConstructorCommand.java:68)
at py4j.GatewayConnection.run(GatewayConnection.java:207)
at java.lang.Thread.run(Unknown Source)
---------------------------------------------------------------------------
Py4JJavaError Traceback (most recent call last)
C:\spark\bin\..\python\pyspark\shell.py in \<module\>()
41 SparkContext.setSystemProperty("spark.executor.uri", os.environ["SPARK\_EXECUTOR\_URI"])
42
---\> 43 sc = SparkContext(pyFiles=add\_files)
44 atexit.register(lambda: sc.stop())
45
C:\spark\python\pyspark\context.pyc in \_init\_(self, master, appName, sparkHome, pyFiles, environment, batchSize, serializer, conf, gateway, jsc, profiler\_cls)
111 try:
112 self.\_do\_init(master, appName, sparkHome, pyFiles, environment, batchSize, serializer,
--\> 113 conf, jsc, profiler\_cls)
114 except:
115 # If an error occurs, clean up in order to allow future SparkContext creation:
C:\spark\python\pyspark\context.pyc in \_do\_init(self, master, appName, sparkHome, pyFiles, environment, batchSize, serializer, conf, jsc, profiler\_cls)
168
169 # Create the Java SparkContext through Py4J
--\> 170 self.\_jsc = jsc or self.\_initialize\_context(self.\_conf.\_jconf)
171
172 # Create a single Accumulator in Java that we'll send all our updates through;
C:\spark\python\pyspark\context.pyc in \_initialize\_context(self, jconf)
222 Initialize SparkContext in function to allow subclass specific initialization
223 """
--\> 224 return self.\_jvm.JavaSparkContext(jconf)
225
226 @classmethod
C:\spark\python\lib\py4j-0.8.2.1-src.zip\py4j\java\_gateway.py in \_call\_(self, \*args)
699 answer = self.\_gateway\_client.send\_command(command)
700 return\_value = get\_return\_value(answer, self.\_gateway\_client, None,
--\> 701 self.\_fqn)
702
703 for temp\_arg in temp\_args:
C:\spark\python\lib\py4j-0.8.2.1-src.zip\py4j\protocol.py in get\_return\_value(answer, gateway\_client, target\_id, name)
298 raise Py4JJavaError(
299 'An error occurred while calling
{0} {1} {2}
.\n'.
--\> 300 format(target\_id, '.', name), value)
301 else:
302 raise Py4JError(
Py4JJavaError: An error occurred while calling None.org.apache.spark.api.java.JavaSparkContext.
: java.net.URISyntaxException: Illegal character in opaque part at index 2: C:\spark\bin\..\python\lib\pyspark.zip
at java.net.URI$Parser.fail(Unknown Source)
at java.net.URI$Parser.checkChars(Unknown Source)
at java.net.URI$Parser.parse(Unknown Source)
at java.net.URI.\<init\>(Unknown Source)
at org.apache.spark.deploy.yarn.Client$$anonfun$setupLaunchEnv$7.apply(Client.scala:558)
at org.apache.spark.deploy.yarn.Client$$anonfun$setupLaunchEnv$7.apply(Client.scala:557)
at scala.collection.immutable.List.foreach(List.scala:318)
at org.apache.spark.deploy.yarn.Client.setupLaunchEnv(Client.scala:557)
at org.apache.spark.deploy.yarn.Client.createContainerLaunchContext(Client.scala:628)
at org.apache.spark.deploy.yarn.Client.submitApplication(Client.scala:119)
at org.apache.spark.scheduler.cluster.YarnClientSchedulerBackend.start(YarnClientSchedulerBackend.scala:56)
at org.apache.spark.scheduler.TaskSchedulerImpl.start(TaskSchedulerImpl.scala:144)
at org.apache.spark.SparkContext.\<init\>(SparkContext.scala:523)
at org.apache.spark.api.java.JavaSparkContext.\<init\>(JavaSparkContext.scala:61)
at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source)
at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Source)
at java.lang.reflect.Constructor.newInstance(Unknown Source)
at py4j.reflection.MethodInvoker.invoke(MethodInvoker.java:234)
at py4j.reflection.ReflectionEngine.invoke(ReflectionEngine.java:379)
at py4j.Gateway.invoke(Gateway.java:214)
at py4j.commands.ConstructorCommand.invokeConstructor(ConstructorCommand.java:79)
at py4j.commands.ConstructorCommand.execute(ConstructorCommand.java:68)
at py4j.GatewayConnection.run(GatewayConnection.java:207)
at java.lang.Thread.run(Unknown Source)
In [1]:
Reply
  
Marcelo Vanzin added a comment - 10 hours ago
Ah, that's similar but not the same bug; it's a different part of the code that only affects pyspark. Could you file a separate bug for that? This is the 

{code}
    (pySparkArchives ++ pyArchives).foreach { path =\>
      val uri = new URI(path)
{code}


---

* [SPARK-11009](https://issues.apache.org/jira/browse/SPARK-11009) | *Blocker* | **RowNumber in HiveContext returns negative values in cluster mode**

This issue happens when submitting the job into a standalone cluster. Have not tried YARN or MESOS. Repartition df into 1 piece or default parallelism=1 does not fix the issue. Also tried having only one node in the cluster, with same result. Other shuffle configuration changes do not alter the results either.

The issue does NOT happen in --master local[\*].

        val ws = Window.
            partitionBy("client\_id").
            orderBy("date")
 
        val nm = "repeatMe"
        df.select(df.col("\*"), rowNumber().over(ws).as(nm))
 
        df.filter(df("repeatMe").isNotNull).orderBy("repeatMe").take(50).foreach(println(\_))
 
---\>
 
Long, DateType, Int
[219483904822,2006-06-01,-1863462909]
[219483904822,2006-09-01,-1863462909]
[219483904822,2007-01-01,-1863462909]
[219483904822,2007-08-01,-1863462909]
[219483904822,2007-07-01,-1863462909]
[192489238423,2007-07-01,-1863462774]
[192489238423,2007-02-01,-1863462774]
[192489238423,2006-11-01,-1863462774]
[192489238423,2006-08-01,-1863462774]
[192489238423,2007-08-01,-1863462774]
[192489238423,2006-09-01,-1863462774]
[192489238423,2007-03-01,-1863462774]
[192489238423,2006-10-01,-1863462774]
[192489238423,2007-05-01,-1863462774]
[192489238423,2006-06-01,-1863462774]
[192489238423,2006-12-01,-1863462774]


---

* [SPARK-10981](https://issues.apache.org/jira/browse/SPARK-10981) | *Minor* | **R semijoin leads to Java errors, R leftsemi leads to Spark errors**

I am using SparkR from RStudio, and I ran into an error with the join function that I recreated with a smaller example:

{code:title=joinTest.R\|borderStyle=solid}
Sys.setenv(SPARK\_HOME="/Users/liumo1/Applications/spark/")
.libPaths(c(file.path(Sys.getenv("SPARK\_HOME"), "R", "lib"), .libPaths()))
library(SparkR)
sc \<- sparkR.init("local[4]")
sqlContext \<- sparkRSQL.init(sc) 

n = c(2, 3, 5)
s = c("aa", "bb", "cc")
b = c(TRUE, FALSE, TRUE)
df = data.frame(n, s, b)
df1= createDataFrame(sqlContext, df)
showDF(df1)

x = c(2, 3, 10)
t = c("dd", "ee", "ff")
c = c(FALSE, FALSE, TRUE)
dff = data.frame(x, t, c)
df2 = createDataFrame(sqlContext, dff)
showDF(df2)
res = join(df1, df2, df1$n == df2$x, "semijoin")
showDF(res)
{code}

Running this code, I encountered the error:
{panel}
Error in invokeJava(isStatic = FALSE, objId$id, methodName, ...) : 
  java.lang.IllegalArgumentException: Unsupported join type 'semijoin'. Supported join types include: 'inner', 'outer', 'full', 'fullouter', 'leftouter', 'left', 'rightouter', 'right', 'leftsemi'.
{panel}

However, if I changed the joinType to "leftsemi", 
{code}
res = join(df1, df2, df1$n == df2$x, "leftsemi")
{code}

I would get the error:
{panel}
Error in .local(x, y, ...) : 
  joinType must be one of the following types: 'inner', 'outer', 'left\_outer', 'right\_outer', 'semijoin'
{panel}

Since the join function in R appears to invoke a Java method, I went into DataFrame.R and changed the code on line 1374 and line 1378 to change the "semijoin" to "leftsemi" to match the Java function's parameters. These also make the R joinType accepted values match those of Scala's. 

semijoin:
{code:title=DataFrame.R: join(x, y, joinExpr, joinType)\|borderStyle=solid}
if (joinType %in% c("inner", "outer", "left\_outer", "right\_outer", "semijoin")) {
    sdf \<- callJMethod(x@sdf, "join", y@sdf, joinExpr@jc, joinType)
} 
else {
     stop("joinType must be one of the following types: ",
             "'inner', 'outer', 'left\_outer', 'right\_outer', 'semijoin'")
}
{code}

leftsemi:
{code:title=DataFrame.R: join(x, y, joinExpr, joinType)\|borderStyle=solid}
if (joinType %in% c("inner", "outer", "left\_outer", "right\_outer", "leftsemi")) {
    sdf \<- callJMethod(x@sdf, "join", y@sdf, joinExpr@jc, joinType)
} 
else {
     stop("joinType must be one of the following types: ",
             "'inner', 'outer', 'left\_outer', 'right\_outer', 'leftsemi'")
}
{code}

This fixed the issue, but I'm not sure if this solution breaks hive compatibility or causes other issues, but I can submit a pull request to change this


---

* [SPARK-10980](https://issues.apache.org/jira/browse/SPARK-10980) | *Major* | **Create wrong decimal if unscaled \> 1e18 and scale \> 0**

Decimal(1000000000000000000L, 20, 2) will become 1000000000000000000 instead of 10000000000000000.00


---

* [SPARK-10973](https://issues.apache.org/jira/browse/SPARK-10973) | *Major* | **\_\_gettitem\_\_ method throws IndexError exception when we try to access index after the last non-zero entry.**

\\_\\_gettitem\\_\\_ method throws IndexError exception when we try to access  index  after the last non-zero entry.

{code}
from pyspark.mllib.linalg import Vectors
sv = Vectors.sparse(5, {1: 3})
sv[0]
## 0.0
sv[1]
## 3.0
sv[2]
## Traceback (most recent call last):
##   File "\<stdin\>", line 1, in \<module\>
##   File "/python/pyspark/mllib/linalg/\_\_init\_\_.py", line 734, in \_\_getitem\_\_
##     row\_ind = inds[insert\_index]
## IndexError: index out of bounds
{code}


---

* [SPARK-10960](https://issues.apache.org/jira/browse/SPARK-10960) | *Major* | **SQL with windowing function cannot reference column in inner select block**

There seems to be a bug in the Spark SQL parser when I use windowing functions. Specifically, when the SELECT refers to a column from an inner select block, the parser throws an error.

Here is an example:
--------------------------
When I use a windowing function and add a '1' constant to the result, 
{code}
   select Rank() OVER ( ORDER BY D1.c3 ) + 1 as c1
{code}

The Spark SQL parser works. The whole SQL is:
{code}
select Rank() OVER ( ORDER BY D1.c3 ) + 1 as c1,
                         D1.c3 as c3,
                         D1.c4 as c4,
                         D1.c5 as c5
                    from 
                         (select T3671.ROW\_WID as c3,
                                   T3671.CAL\_MONTH as c4,
                                   T3671.CAL\_YEAR as c5,
                                   1 as c6
                              from 
                                   W\_DAY\_D T3671
                         ) D1
{code}

However, if I change the projection so that it refers to a column in an inner select block, D1.C6, whose value is itself a '1' literal, so it is functionally equivalent to the SQL above, Spark SQL will throw an error:
{code}
select Rank() OVER ( ORDER BY D1.c3 ) + D1.C6 as c1,
                         D1.c3 as c3,
                         D1.c4 as c4,
                         D1.c5 as c5
                    from 
                         (select T3671.ROW\_WID as c3,
                                   T3671.CAL\_MONTH as c4,
                                   T3671.CAL\_YEAR as c5,
                                   1 as c6
                              from 
                                   W\_DAY\_D T3671
                         ) D1
{code}

The error message is:
{code}
. . . . . . . . . . . . . . . .\> java.lang.NullPointerException
Error: org.apache.spark.sql.AnalysisException: resolved attribute(s) c6#3386 missing from c5#3390
,c3#3383,c4#3389,\_we0#3461,c3#3388 in operator !Project [c3#3388,c4#3389,c5#3390,c3#3383,\_we0#346
1,(\_we0#3461 + c6#3386) AS c1#3387]; (state=,code=0)
{code}

The above example is a simplified version of the SQL I was testing. The full SQL I was using, which fails with a similar error, is as follows:

{code}
select Case when case D1.c6 when 1 then D1.c3 else NULL end  is not null then Rank() OVER ( ORDER BY case when ( case D1.c6 when 1 then D1.c3 else NULL end  ) is null then 1 else 0 end, case D1.c6 when 1 then D1.c3 else NULL end ) end as c1,
                         Case when case D1.c7 when 1 then D1.c3 else NULL end  is not null then Rank() OVER ( PARTITION BY D1.c4, D1.c5 ORDER BY case when ( case D1.c7 when 1 then D1.c3 else NULL end  ) is null then 1 else 0 end, case D1.c7 when 1 then D1.c3 else NULL end ) end as c2,
                         D1.c3 as c3,
                         D1.c4 as c4,
                         D1.c5 as c5
                    from 
                         (select T3671.ROW\_WID as c3,
                                   T3671.CAL\_MONTH as c4,
                                   T3671.CAL\_YEAR as c5,
                                   ROW\_NUMBER() OVER (PARTITION BY T3671.CAL\_MONTH, T3671.CAL\_YEAR ORDER BY T3671.CAL\_MONTH DESC, T3671.CAL\_YEAR DESC) as c6,
                                   ROW\_NUMBER() OVER (PARTITION BY T3671.CAL\_MONTH, T3671.CAL\_YEAR, T3671.ROW\_WID ORDER BY T3671.CAL\_MONTH DESC, T3671.CAL\_YEAR DESC, T3671.ROW\_WID DESC) as c7
                              from 
                                   W\_DAY\_D T3671
                         ) D1
{code}

Hopefully when fixed, both these sample SQLs should work!


---

* [SPARK-10959](https://issues.apache.org/jira/browse/SPARK-10959) | *Critical* | **PySpark StreamingLogisticRegressionWithSGD does not train with given regParam and convergenceTol parameters**

These parameters are passed into the StreamingLogisticRegressionWithSGD constructor, but do not get transferred to the model to use when training.  Same problem with StreamingLinearRegressionWithSGD and the intercept param is in the wrong  argument place where it is being used as regularization value.


---

* [SPARK-10955](https://issues.apache.org/jira/browse/SPARK-10955) | *Major* | **Warn if dynamic allocation is enabled for Streaming jobs**

Spark streaming can be tricky with dynamic allocation and can lose data if not used properly (with WAL, or with WAL-free solutions like Direct Kafka and Kinesis since 1.5). If dynamic allocation is enabled, we should issue a log4j warning.


---

* [SPARK-10932](https://issues.apache.org/jira/browse/SPARK-10932) | *Major* | **Port two minor changes to release packaging scripts back into Spark repo**

Spark's release packaging scripts used to live in separate repositories. Although these scripts are now part of the Spark repo, there are some patches against the old repos that are missing in Spark's copy of the script. As part of the deprecation of those other repos, we should port those changes into Spark's copy of the script. I'll open a PR to do this.


---

* [SPARK-10914](https://issues.apache.org/jira/browse/SPARK-10914) | *Major* | **UnsafeRow serialization breaks when two machines have different Oops size**

\*Updated description (by rxin on Oct 8, 2015)\*

To reproduce, launch Spark using
{code}
MASTER=local-cluster[2,1,1024] bin/spark-shell --conf "spark.executor.extraJavaOptions=-XX:-UseCompressedOops"
{code}

And then run the following
{code}
scala\> sql("select 1 xx").collect()
{code}

The problem is that UnsafeRow contains 3 pieces of information when pointing to some data in memory (an object, a base offset, and length). When the row is serialized with Java/Kryo serialization, the object layout in memory can change if two machines have different pointer width (Oops in JVM).



\*Original bug report description\*:

Using an inner join, to match together two integer columns, I generally get no results when there should be matches.  But the results vary and depend on whether the dataframes are coming from SQL, JSON, or cached, as well as the order in which I cache things and query them.

This minimal example reproduces it consistently for me in the spark-shell, on new installs of both 1.5.0 and 1.5.1 (pre-built against Hadoop 2.6 from http://spark.apache.org/downloads.html.)

{code}
/\* x is {"xx":1}{"xx":2} and y is just {"yy":1}{"yy:2} \*/
val x = sql("select 1 xx union all select 2") 
val y = sql("select 1 yy union all select 2")

x.join(y, $"xx" === $"yy").count() /\* expect 2, get 0 \*/
/\* If I cache both tables it works: \*/
x.cache()
y.cache()
x.join(y, $"xx" === $"yy").count() /\* expect 2, get 2 \*/

/\* but this still doesn't work: \*/
x.join(y, $"xx" === $"yy").filter("yy=1").count() /\* expect 1, get 0 \*/
{code}


---

* [SPARK-10904](https://issues.apache.org/jira/browse/SPARK-10904) | *Major* | **  select(df, c("col1", "col2")) fails**

The help page for 'select' gives an example of 
  select(df, c("col1", "col2"))

However, this fails with assertion:

java.lang.AssertionError: assertion failed
	at scala.Predef$.assert(Predef.scala:165)
	at org.apache.spark.api.r.SerDe$.readStringBytes(SerDe.scala:92)
	at org.apache.spark.api.r.SerDe$.readString(SerDe.scala:99)
	at org.apache.spark.api.r.SerDe$.readTypedObject(SerDe.scala:63)
	at org.apache.spark.api.r.SerDe$.readObject(SerDe.scala:52)
	at org.apache.spark.api.r.RBackendHandler$$anonfun$readArgs$1.apply(RBackendHandler.scala:182)
	at org.apache.spark.api.r.RBackendHandler$$anonfun$readArgs$1.apply(RBackendHandler.scala:181)

And then none of the functions will work with following error:
\> head(df)
 Error in if (returnStatus != 0) { : argument is of length zero


---

* [SPARK-10901](https://issues.apache.org/jira/browse/SPARK-10901) | *Critical* | **spark.yarn.user.classpath.first doesn't work**

spark.yarn.user.classpath.first doesn't properly add the app jar to the system class path first.  It has some logic there that i believe works for local files but running on yarn using distributed cache to distribute the app jar doesn't put \_\_app\_\_.jar into the classpath at all.

This is a break in backwards compatibility.

Note that in this case the user is trying to use different version of kryo (which used to work in spark 1.2) and the new configs for this: spark.{driver, executor}.userClassPathFirst don't allow this as it errors out with:

User class threw exception: java.lang.LinkageError: loader constraint violation: loader (instance of org/apache/spark/util/ChildFirstURLClassLoader) previously initiated loading for a different type with name "com/esotericsoftware/kryo/Kryo"


---

* [SPARK-10889](https://issues.apache.org/jira/browse/SPARK-10889) | *Minor* | **Upgrade Kinesis Client Library**

Kinesis Client Library added a custom cloudwatch metric in 1.3.0 called MillisBehindLatest. This is very important for capacity planning and alerting.


---

* [SPARK-10885](https://issues.apache.org/jira/browse/SPARK-10885) | *Major* | **Display the failed output op in Streaming UI**

Now if an output operation failed because of an error in the closure of `foreachRDD`, such as, 
{code}
    wordCounts.foreachRDD { rdd =\>
      if (Random.nextInt(2) == 0) {
        throw new RuntimeException("xxx")
      }
    }
{code}

we cannot display the error information.


---

* [SPARK-10871](https://issues.apache.org/jira/browse/SPARK-10871) | *Minor* | **Specify number of failed executors in ApplicationMaster error message**

I ran in to [this\|https://github.com/apache/spark/blob/9b9fe5f7bf55257269d8febcd64e95677075dfb6/yarn/src/main/scala/org/apache/spark/deploy/yarn/ApplicationMaster.scala#L346-L348] error message today while debugging a failed app:

{code}
15/09/29 00:33:20 INFO yarn.ApplicationMaster: Final app status: FAILED, exitCode: 11, (reason: Max number of executor failures reached)
15/09/29 00:33:23 INFO util.ShutdownHookManager: Shutdown hook called
{code}

This app ran with dynamic allocation and I'm not sure what limit was used as the "maximum allowable number of failed executors"; in any case, the error message may as well specify this.


---

* [SPARK-10859](https://issues.apache.org/jira/browse/SPARK-10859) | *Blocker* | **Predicates pushed to InmemoryColumnarTableScan are not evaluated correctly**

{code}
var data01 = sqlContext.sql("select 1 as id, \"{\\\"animal\\\":{\\\"type\\\": \\\"cat\\\"}},{\\\"animal\\\":{\\\"type\\\": \\\"dog\\\"}},{\\\"animal\\\":{\\\"type\\\": \\\"donkey\\\"}},{\\\"animal\\\":{\\\"type\\\": \\\"turkey\\\"}},{\\\"animal\\\":{\\\"type\\\": \\\"cat\\\"}},{\\\"animal\\\":{\\\"NOTANIMAL\\\": \\\"measuring tape\\\"}}\" as field")
case class SubField(fieldling: String)
var data02 = data01.explode(data01("field")){ case Row(field: String) =\> field.split(",").map(SubField(\_))}
  .selectExpr("id","fieldling","get\_json\_object(fieldling,\"$.animal.type\") as animal") 
var data03 = data01.explode(data01("field")){ case Row(field: String) =\> field.split(",").map(SubField(\_))}
  .selectExpr("id","fieldling","get\_json\_object(fieldling,\"$.animal.type\") as animal")
data02.cache()

data02.select($"animal" === "cat").explain
== Physical Plan ==
Project [(animal#25 = cat) AS (animal = cat)#263]
 InMemoryColumnarTableScan [animal#25], (InMemoryRelation [id#20,fieldling#24,animal#25], true, 10000, StorageLevel(true, true, false, true, 1), (TungstenProject [id#20,fieldling#24,get\_json\_object(fieldling#24,$.animal.type) AS animal#25]), None)

data02.select($"animal" === "cat").show
+--------------+
\|(animal = cat)\|
+--------------+
\|          true\|
\|         false\|
\|         false\|
\|         false\|
\|          true\|
\|          null\|
+--------------+

data02.filter($"animal" === "cat").explain
== Physical Plan ==
Filter (animal#25 = cat)
 InMemoryColumnarTableScan [id#20,fieldling#24,animal#25], [(animal#25 = cat)], (InMemoryRelation [id#20,fieldling#24,animal#25], true, 10000, StorageLevel(true, true, false, true, 1), (TungstenProject [id#20,fieldling#24,get\_json\_object(fieldling#24,$.animal.type) AS animal#25]), None)

data02.filter($"animal" === "cat").show
+---+---------+------+
\| id\|fieldling\|animal\|
+---+---------+------+
+---+---------+------+
{code}


---

* [SPARK-10858](https://issues.apache.org/jira/browse/SPARK-10858) | *Minor* | **YARN: archives/jar/files rename with # doesn't work unless scheme given**

The YARN distributed cache feature with --jars, --archives, --files where you can rename the file/archive using a # symbol only works if you explicitly include the scheme in the path:

works:
--jars file:///home/foo/my.jar#renamed.jar

doesn't work:
--jars /home/foo/my.jar#renamed.jar

Exception in thread "main" java.io.FileNotFoundException: File file:/home/foo/my.jar#renamed.jar does not exist
        at org.apache.hadoop.fs.RawLocalFileSystem.deprecatedGetFileStatus(RawLocalFileSystem.java:534)
        at org.apache.hadoop.fs.RawLocalFileSystem.getFileLinkStatusInternal(RawLocalFileSystem.java:747)
        at org.apache.hadoop.fs.RawLocalFileSystem.getFileStatus(RawLocalFileSystem.java:524)
        at org.apache.hadoop.fs.FilterFileSystem.getFileStatus(FilterFileSystem.java:416)
        at org.apache.hadoop.fs.FileUtil.copy(FileUtil.java:337)
        at org.apache.hadoop.fs.FileUtil.copy(FileUtil.java:289)
        at org.apache.spark.deploy.yarn.Client.copyFileToRemote(Client.scala:240)
        at org.apache.spark.deploy.yarn.Client.org$apache$spark$deploy$yarn$Client$$distribute$1(Client.scala:329)
        at org.apache.spark.deploy.yarn.Client$$anonfun$prepareLocalResources$6$$anonfun$apply$2.apply(Client.scala:393)
        at org.apache.spark.deploy.yarn.Client$$anonfun$prepareLocalResources$6$$anonfun$apply$2.apply(Client.scala:392)
        at scala.collection.IndexedSeqOptimized$class.foreach(IndexedSeqOptimized.scala:33)
        at scala.collection.mutable.ArrayOps$ofRef.foreach(ArrayOps.scala:108)


---

* [SPARK-10845](https://issues.apache.org/jira/browse/SPARK-10845) | *Major* | **SQL option "spark.sql.hive.version" doesn't show up in the result of "SET -v"**

When refactoring SQL options from plain strings to the strongly typed {{SQLConfEntry}}, {{spark.sql.hive.version}} wasn't migrated, and doesn't show up in the result of {{SET -v}}, as {{SET -v}} only shows public {{SQLConfEntry}} instances.

This affects compatibility with Simba ODBC driver.


---

* [SPARK-10833](https://issues.apache.org/jira/browse/SPARK-10833) | *Major* | **Inline, organize BSD/MIT licenses in LICENSE**

In the course of https://issues.apache.org/jira/browse/LEGAL-226 it came to light that the guidance at http://www.apache.org/dev/licensing-howto.html#permissive-deps means that permissively-licensed dependencies has a different interpretation than we (er, I) had been operating under. "pointer ... to the license within the source tree" specifically means a copy of the license within Spark's distribution, whereas at the moment, Spark's LICENSE has a pointer to the project's license in the \*other project's\* source tree.

The remedy is simply to inline all such license references (i.e. BSD/MIT licenses) or include their text in "licenses" subdirectory and point to that.

Along the way, we can also treat other BSD/MIT licenses, whose text has been inlined into LICENSE, in the same way.

The LICENSE file can continue to provide a helpful list of BSD/MIT licensed projects and a pointer to their sites. This would be over and above including license text in the distro, which is the essential thing.

I do not think this blocks a current release, since there's a good-faith argument that the current practice satisfies the terms of the third-party licenses as well. (If it didn't, this would be a blocker for any further release.) However, of course it's better to follow the best practice going forward.


---

* [SPARK-10825](https://issues.apache.org/jira/browse/SPARK-10825) | *Critical* | **Flaky test: StandaloneDynamicAllocationSuite**

There are some race conditions in StandaloneDynamicAllocationSuite.
1. It should not assume master and workers start in order.
2. It should not assume master and workers get ready at once
3. It should not assume the application is already registered with master after creating SparkContext.
4. It should not access Master.app which is not thread safe.


---

* [SPARK-10790](https://issues.apache.org/jira/browse/SPARK-10790) | *Major* | **Dynamic Allocation does not request any executors if first stage needs less than or equal to spark.dynamicAllocation.initialExecutors**

If you set spark.dynamicAllocation.initialExecutors \> 0 (or spark.dynamicAllocation.minExecutors, since spark.dynamicAllocation.initialExecutors defaults to spark.dynamicAllocation.minExecutors), and the number of tasks in the first stage of your job is less than or equal to this min/init number of executors, dynamic allocation won't actually request any executors and will just hang indefinitely with the warning "Initial job has not accepted any resources; check your cluster UI to ensure that workers are registered and have sufficient resources".

The cause appears to be that ExecutorAllocationManager does not request any executors while the application is still initializing, but it still sets the initial value of numExecutorsTarget to spark.dynamicAllocation.initialExecutors. Once the job is running and has submitted its first task, if the first task does not need more than spark.dynamicAllocation.initialExecutors, ExecutorAllocationManager.updateAndSyncNumExecutorsTarget() does not think that it needs to request any executors, so it doesn't.


---

* [SPARK-10741](https://issues.apache.org/jira/browse/SPARK-10741) | *Major* | **Hive Query Having/OrderBy against Parquet table is not working**

Failed Query with Having Clause
{code}
  def testParquetHaving() {
    val ddl =
      """CREATE TABLE IF NOT EXISTS test ( c1 string, c2 int ) STORED AS PARQUET"""
    val failedHaving =
      """ SELECT c1, avg ( c2 ) as c\_avg
        \| FROM test
        \| GROUP BY c1
        \| HAVING ( avg ( c2 ) \> 5)  ORDER BY c1""".stripMargin
    TestHive.sql(ddl)
    TestHive.sql(failedHaving).collect
  }

org.apache.spark.sql.AnalysisException: resolved attribute(s) c2#16 missing from c1#17,c2#18 in operator !Aggregate [c1#17], [cast((avg(cast(c2#16 as bigint)) \> cast(5 as double)) as boolean) AS havingCondition#12,c1#17,avg(cast(c2#18 as bigint)) AS c\_avg#9];
	at org.apache.spark.sql.catalyst.analysis.CheckAnalysis$class.failAnalysis(CheckAnalysis.scala:37)
	at org.apache.spark.sql.catalyst.analysis.Analyzer.failAnalysis(Analyzer.scala:44)
	at org.apache.spark.sql.catalyst.analysis.CheckAnalysis$$anonfun$checkAnalysis$1.apply(CheckAnalysis.scala:154)
	at org.apache.spark.sql.catalyst.analysis.CheckAnalysis$$anonfun$checkAnalysis$1.apply(CheckAnalysis.scala:49)

{code}

Failed Query with OrderBy
{code}
  def testParquetOrderBy() {
    val ddl =
      """CREATE TABLE IF NOT EXISTS test ( c1 string, c2 int ) STORED AS PARQUET"""
    val failedOrderBy =
      """ SELECT c1, avg ( c2 ) c\_avg
        \| FROM test
        \| GROUP BY c1
        \| ORDER BY avg ( c2 )""".stripMargin
    TestHive.sql(ddl)
    TestHive.sql(failedOrderBy).collect
  }

org.apache.spark.sql.AnalysisException: resolved attribute(s) c2#33 missing from c1#34,c2#35 in operator !Aggregate [c1#34], [avg(cast(c2#33 as bigint)) AS aggOrder#31,c1#34,avg(cast(c2#35 as bigint)) AS c\_avg#28];
	at org.apache.spark.sql.catalyst.analysis.CheckAnalysis$class.failAnalysis(CheckAnalysis.scala:37)
	at org.apache.spark.sql.catalyst.analysis.Analyzer.failAnalysis(Analyzer.scala:44)
{code}


---

* [SPARK-10619](https://issues.apache.org/jira/browse/SPARK-10619) | *Major* | **Can't sort columns on Executor Page**

I am using spark 1.5 running on yarn and go to the executors page.  It won't allow sorting of the columns. This used to work in Spark 1.4.


---

* [SPARK-10581](https://issues.apache.org/jira/browse/SPARK-10581) | *Minor* | **Groups are not resolved in scaladoc for org.apache.spark.sql.Column**

The Scala API documentation (scaladoc) for [org.apache.spark.sql.Column\|http://people.apache.org/~pwendell/spark-nightly/spark-master-docs/latest/api/scala/index.html#org.apache.spark.sql.Column] does not resolve groups, and they appear unresolved like {{df\_ops}}, {{expr\_ops}}, et al. instead of \_DataFrame functions.\_, \_Expression operators.\_, et al.  

BTW, [DataFrame\|http://people.apache.org/~pwendell/spark-nightly/spark-master-docs/latest/api/scala/index.html#org.apache.spark.sql.DataFrame] and other classes in the [org.apache.spark.sql\|http://people.apache.org/~pwendell/spark-nightly/spark-master-docs/latest/api/scala/index.html#org.apache.spark.sql.package] package seem fine.


---

* [SPARK-10577](https://issues.apache.org/jira/browse/SPARK-10577) | *Major* | **[PySpark] DataFrame hint for broadcast join**

As in https://issues.apache.org/jira/browse/SPARK-8300
there should by possibility to add hint for broadcast join in:
- Pyspark


---

* [SPARK-10389](https://issues.apache.org/jira/browse/SPARK-10389) | *Major* | **support order by non-attribute grouping expression on Aggregate**

For example, we should support "SELECT MAX(value) FROM src GROUP BY key + 1 ORDER BY key + 1".


---

* [SPARK-10058](https://issues.apache.org/jira/browse/SPARK-10058) | *Critical* | **Flaky test: HeartbeatReceiverSuite: normal heartbeat**

https://amplab.cs.berkeley.edu/jenkins/view/Spark-QA-Test/job/Spark-1.5-SBT/116/AMPLAB\_JENKINS\_BUILD\_PROFILE=hadoop2.2,label=spark-test/testReport/junit/org.apache.spark/HeartbeatReceiverSuite/normal\_heartbeat/

{code}
Error Message

3 did not equal 2
Stacktrace

sbt.ForkMain$ForkError: 3 did not equal 2
	at org.scalatest.Assertions$class.newAssertionFailedException(Assertions.scala:500)
	at org.scalatest.FunSuite.newAssertionFailedException(FunSuite.scala:1555)
	at org.scalatest.Assertions$AssertionsHelper.macroAssert(Assertions.scala:466)
	at org.apache.spark.HeartbeatReceiverSuite$$anonfun$2.apply$mcV$sp(HeartbeatReceiverSuite.scala:104)
	at org.apache.spark.HeartbeatReceiverSuite$$anonfun$2.apply(HeartbeatReceiverSuite.scala:97)
	at org.apache.spark.HeartbeatReceiverSuite$$anonfun$2.apply(HeartbeatReceiverSuite.scala:97)
	at org.scalatest.Transformer$$anonfun$apply$1.apply$mcV$sp(Transformer.scala:22)
	at org.scalatest.OutcomeOf$class.outcomeOf(OutcomeOf.scala:85)
	at org.scalatest.OutcomeOf$.outcomeOf(OutcomeOf.scala:104)
	at org.scalatest.Transformer.apply(Transformer.scala:22)
	at org.scalatest.Transformer.apply(Transformer.scala:20)
	at org.scalatest.FunSuiteLike$$anon$1.apply(FunSuiteLike.scala:166)
	at org.apache.spark.SparkFunSuite.withFixture(SparkFunSuite.scala:42)
	at org.scalatest.FunSuiteLike$class.invokeWithFixture$1(FunSuiteLike.scala:163)
	at org.scalatest.FunSuiteLike$$anonfun$runTest$1.apply(FunSuiteLike.scala:175)
	at org.scalatest.FunSuiteLike$$anonfun$runTest$1.apply(FunSuiteLike.scala:175)
	at org.scalatest.SuperEngine.runTestImpl(Engine.scala:306)
	at org.scalatest.FunSuiteLike$class.runTest(FunSuiteLike.scala:175)
	at org.apache.spark.HeartbeatReceiverSuite.org$scalatest$BeforeAndAfterEach$$super$runTest(HeartbeatReceiverSuite.scala:41)
	at org.scalatest.BeforeAndAfterEach$class.runTest(BeforeAndAfterEach.scala:255)
	at org.apache.spark.HeartbeatReceiverSuite.runTest(HeartbeatReceiverSuite.scala:41)
	at org.scalatest.FunSuiteLike$$anonfun$runTests$1.apply(FunSuiteLike.scala:208)
	at org.scalatest.FunSuiteLike$$anonfun$runTests$1.apply(FunSuiteLike.scala:208)
	at org.scalatest.SuperEngine$$anonfun$traverseSubNodes$1$1.apply(Engine.scala:413)
	at org.scalatest.SuperEngine$$anonfun$traverseSubNodes$1$1.apply(Engine.scala:401)
	at scala.collection.immutable.List.foreach(List.scala:318)
	at org.scalatest.SuperEngine.traverseSubNodes$1(Engine.scala:401)
	at org.scalatest.SuperEngine.org$scalatest$SuperEngine$$runTestsInBranch(Engine.scala:396)
	at org.scalatest.SuperEngine.runTestsImpl(Engine.scala:483)
	at org.scalatest.FunSuiteLike$class.runTests(FunSuiteLike.scala:208)
	at org.scalatest.FunSuite.runTests(FunSuite.scala:1555)
	at org.scalatest.Suite$class.run(Suite.scala:1424)
	at org.scalatest.FunSuite.org$scalatest$FunSuiteLike$$super$run(FunSuite.scala:1555)
	at org.scalatest.FunSuiteLike$$anonfun$run$1.apply(FunSuiteLike.scala:212)
	at org.scalatest.FunSuiteLike$$anonfun$run$1.apply(FunSuiteLike.scala:212)
	at org.scalatest.SuperEngine.runImpl(Engine.scala:545)
	at org.scalatest.FunSuiteLike$class.run(FunSuiteLike.scala:212)
	at org.apache.spark.HeartbeatReceiverSuite.org$scalatest$BeforeAndAfterAll$$super$run(HeartbeatReceiverSuite.scala:41)
	at org.scalatest.BeforeAndAfterAll$class.liftedTree1$1(BeforeAndAfterAll.scala:257)
	at org.scalatest.BeforeAndAfterAll$class.run(BeforeAndAfterAll.scala:256)
	at org.apache.spark.HeartbeatReceiverSuite.run(HeartbeatReceiverSuite.scala:41)
	at org.scalatest.tools.Framework.org$scalatest$tools$Framework$$runSuite(Framework.scala:462)
	at org.scalatest.tools.Framework$ScalaTestTask.execute(Framework.scala:671)
	at sbt.ForkMain$Run$2.call(ForkMain.java:294)
	at sbt.ForkMain$Run$2.call(ForkMain.java:284)
	at java.util.concurrent.FutureTask.run(FutureTask.java:262)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1145)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:615)
	at java.lang.Thread.run(Thread.java:745)
{code}

This is really flaky (fail 30%)
https://amplab.cs.berkeley.edu/jenkins/view/Spark-QA-Test/job/Spark-1.5-SBT/116/AMPLAB\_JENKINS\_BUILD\_PROFILE=hadoop2.2,label=spark-test/testReport/junit/org.apache.spark/HeartbeatReceiverSuite/normal\_heartbeat/history/


---

* [SPARK-8386](https://issues.apache.org/jira/browse/SPARK-8386) | *Critical* | **DataFrame and JDBC regression**

I have an ETL app that appends to a JDBC table new results found at each run.  In 1.3.1 I did this:

testResultsDF.insertIntoJDBC(CONNECTION\_URL, TABLE\_NAME, false);

When I do this now in 1.4 it complains that the "object" 'TABLE\_NAME' already exists. I get this even if I switch the overwrite to true.  I also tried this now:

testResultsDF.write().mode(SaveMode.Append).jdbc(CONNECTION\_URL, TABLE\_NAME, connectionProperties);

getting the same error. It works running the first time creating the new table and adding data successfully. But, running it a second time it (the jdbc driver) will tell me that the table already exists. Even SaveMode.Overwrite will give me the same error.


