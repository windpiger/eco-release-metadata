
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
#  0.8.3 Release Notes

These release notes cover new developer and user-facing incompatibilities, features, and major improvements.


---

* [KAFKA-2226](https://issues.apache.org/jira/browse/KAFKA-2226) | *Major* | **NullPointerException in TestPurgatoryPerformance**

A NullPointerException sometimes shows up in TimerTaskList.remove while running TestPurgatoryPerformance. I’m on the HEAD of trunk.
{code}
> ./bin/kafka-run-class.sh kafka.TestPurgatoryPerformance --key-space-size 100000 --keys 3 --num 100000 --pct50 50 --pct75 75 --rate 1000 --size 50 --timeout 20
SLF4J: Class path contains multiple SLF4J bindings.
SLF4J: Found binding in [jar:file:/Users/okaraman/code/kafka/core/build/dependant-libs-2.10.5/slf4j-log4j12-1.6.1.jar!/org/slf4j/impl/StaticLoggerBinder.class]
SLF4J: Found binding in [jar:file:/Users/okaraman/code/kafka/core/build/dependant-libs-2.10.5/slf4j-log4j12-1.7.6.jar!/org/slf4j/impl/StaticLoggerBinder.class]
SLF4J: See http://www.slf4j.org/codes.html#multiple\_bindings for an explanation.
SLF4J: Actual binding is of type [org.slf4j.impl.Log4jLoggerFactory]
[2015-05-27 10:02:14,782] ERROR [completion thread], Error due to  (kafka.TestPurgatoryPerformance$CompletionQueue$$anon$1)
java.lang.NullPointerException
  at kafka.utils.timer.TimerTaskList.remove(TimerTaskList.scala:80)
  at kafka.utils.timer.TimerTaskEntry.remove(TimerTaskList.scala:128)
  at kafka.utils.timer.TimerTask$class.cancel(TimerTask.scala:27)
  at kafka.server.DelayedOperation.cancel(DelayedOperation.scala:50)
  at kafka.server.DelayedOperation.forceComplete(DelayedOperation.scala:71)
  at kafka.TestPurgatoryPerformance$CompletionQueue$$anon$1.doWork(TestPurgatoryPerformance.scala:263)
  at kafka.utils.ShutdownableThread.run(ShutdownableThread.scala:60)
{code}


---

* [KAFKA-2189](https://issues.apache.org/jira/browse/KAFKA-2189) | *Blocker* | **Snappy compression of message batches less efficient in 0.8.2.1**

We are using snappy compression and noticed a fairly substantial increase (about 2.25x) in log filesystem space consumption after upgrading a Kafka cluster from 0.8.1.1 to 0.8.2.1. We found that this is caused by messages being seemingly recompressed individually (or possibly with a much smaller buffer or dictionary?) instead of as a batch as sent by producers. We eventually tracked down the change in compression ratio/scope to this [1] commit that updated the snappy version from 1.0.5 to 1.1.1.3. The Kafka client version does not appear to be relevant as we can reproduce this with both the 0.8.1.1 and 0.8.2.1 Producer.

Here are the log files from our troubleshooting that contain the same set of 1000 messages, for batch sizes of 1, 10, 100, and 1000. f9d9b was the last commit with 0.8.1.1-like behavior prior to f5ab8 introducing the issue.

{noformat}
-rw-rw-r-- 1 kafka kafka 404967 May 12 11:45 /var/kafka2/f9d9b-batch-1-0/00000000000000000000.log
-rw-rw-r-- 1 kafka kafka 119951 May 12 11:45 /var/kafka2/f9d9b-batch-10-0/00000000000000000000.log
-rw-rw-r-- 1 kafka kafka  89645 May 12 11:45 /var/kafka2/f9d9b-batch-100-0/00000000000000000000.log
-rw-rw-r-- 1 kafka kafka  88279 May 12 11:45 /var/kafka2/f9d9b-batch-1000-0/00000000000000000000.log

-rw-rw-r-- 1 kafka kafka 402837 May 12 11:41 /var/kafka2/f5ab8-batch-1-0/00000000000000000000.log
-rw-rw-r-- 1 kafka kafka 382437 May 12 11:41 /var/kafka2/f5ab8-batch-10-0/00000000000000000000.log
-rw-rw-r-- 1 kafka kafka 364791 May 12 11:41 /var/kafka2/f5ab8-batch-100-0/00000000000000000000.log
-rw-rw-r-- 1 kafka kafka 380693 May 12 11:41 /var/kafka2/f5ab8-batch-1000-0/00000000000000000000.log
{noformat}

[1] https://github.com/apache/kafka/commit/f5ab8e1780cf80f267906e3259ad4f9278c32d28


---

* [KAFKA-2185](https://issues.apache.org/jira/browse/KAFKA-2185) | *Minor* | **Update to Gradle 2.4**

Gradle 2.4 has been released recently while Kafka is still using Gradle 2.0. There have been a large number of improvements over the various releases (including performance improvements):

https://gradle.org/docs/2.1/release-notes
https://gradle.org/docs/2.2/release-notes
https://gradle.org/docs/2.3/release-notes
http://gradle.org/docs/current/release-notes


---

* [KAFKA-2169](https://issues.apache.org/jira/browse/KAFKA-2169) | *Critical* | **Upgrade to zkclient-0.5**

zkclient-0.5 is released http://mvnrepository.com/artifact/com.101tec/zkclient/0.5 and has the fix for KAFKA-824


---

* [KAFKA-2131](https://issues.apache.org/jira/browse/KAFKA-2131) | *Trivial* | **Update new producer javadocs with correct documentation links**

New producer java docs are referring to old producer documentation.


---

* [KAFKA-2128](https://issues.apache.org/jira/browse/KAFKA-2128) | *Minor* | **kafka.Kafka should return non-zero exit code when caught exception.**

kafka.Kafka Object always return exit code zero.
I think that it should return non-zero exit code when caught exception.
(for example FileNotFoundException caught, since server.properies is not exist)


---

* [KAFKA-2121](https://issues.apache.org/jira/browse/KAFKA-2121) | *Major* | **prevent potential resource leak in KafkaProducer and KafkaConsumer**

On Mon, Apr 13, 2015 at 7:17 PM, Guozhang Wang <wangguoz@gmail.com> wrote:
It is a valid problem and we should correct it as soon as possible, I'm
with Ewen regarding the solution.

On Mon, Apr 13, 2015 at 5:05 PM, Ewen Cheslack-Postava <ewen@confluent.io>
wrote:

> Steven,
>
> Looks like there is even more that could potentially be leaked -- since key
> and value serializers are created and configured at the end, even the IO
> thread allocated by the producer could leak. Given that, I think 1 isn't a
> great option since, as you said, it doesn't really address the underlying
> issue.
>
> 3 strikes me as bad from a user experience perspective. It's true we might
> want to introduce additional constructors to make testing easier, but the
> more components I need to allocate myself and inject into the producer's
> constructor, the worse the default experience is. And since you would have
> to inject the dependencies to get correct, non-leaking behavior, it will
> always be more code than previously (and a backwards incompatible change).
> Additionally, the code creating a the producer would have be more
> complicated since it would have to deal with the cleanup carefully whereas
> it previously just had to deal with the exception. Besides, for testing
> specifically, you can avoid exposing more constructors just for testing by
> using something like PowerMock that let you mock private methods. That
> requires a bit of code reorganization, but doesn't affect the public
> interface at all.
>
> So my take is that a variant of 2 is probably best. I'd probably do two
> things. First, make close() safe to call even if some fields haven't been
> initialized, which presumably just means checking for null fields. (You
> might also want to figure out if all the methods close() calls are
> idempotent and decide whether some fields should be marked non-final and
> cleared to null when close() is called). Second, add the try/catch as you
> suggested, but just use close().
>
> -Ewen
>
>
> On Mon, Apr 13, 2015 at 3:53 PM, Steven Wu <stevenz3wu@gmail.com> wrote:
>
> > Here is the resource leak problem that we have encountered when 0.8.2
> java
> > KafkaProducer failed in constructor. here is the code snippet of
> > KafkaProducer to illustrate the problem.
> >
> > -------------------------------
> > public KafkaProducer(ProducerConfig config, Serializer<K> keySerializer,
> > Serializer<V> valueSerializer) {
> >
> >     // create metrcis reporter via reflection
> >     List<MetricsReporter> reporters =
> >
> >
> config.getConfiguredInstances(ProducerConfig.METRIC\_REPORTER\_CLASSES\_CONFIG,
> > MetricsReporter.class);
> >
> >     // validate bootstrap servers
> >     List<InetSocketAddress> addresses =
> >
> >
> ClientUtils.parseAndValidateAddresses(config.getList(ProducerConfig.BOOTSTRAP\_SERVERS\_CONFIG));
> >
> > }
> > -------------------------------
> >
> > let's say MyMetricsReporter creates a thread in constructor. if hostname
> > validation threw an exception, constructor won't call the close method of
> > MyMetricsReporter to clean up the resource. as a result, we created
> thread
> > leak issue. this becomes worse when we try to auto recovery (i.e. keep
> > creating KafkaProducer again -> failing again -> more thread leaks).
> >
> > there are multiple options of fixing this.
> >
> > 1) just move the hostname validation to the beginning. but this is only
> fix
> > one symtom. it didn't fix the fundamental problem. what if some other
> lines
> > throw an exception.
> >
> > 2) use try-catch. in the catch section, try to call close methods for any
> > non-null objects constructed so far.
> >
> > 3) explicitly declare the dependency in the constructor. this way, when
> > KafkaProducer threw an exception, I can call close method of metrics
> > reporters for releasing resources.
> >     KafkaProducer(..., List<MetricsReporter> reporters)
> > we don't have to dependency injection framework. but generally hiding
> > dependency is a bad coding practice. it is also hard to plug in mocks for
> > dependencies. this is probably the most intrusive change.
> >
> > I am willing to submit a patch. but like to hear your opinions on how we
> > should fix the issue.
> >
> > Thanks,
> > Steven
> >
>
>
>
> --
> Thanks,
> Ewen
>



--
-- Guozhang


---

* [KAFKA-2119](https://issues.apache.org/jira/browse/KAFKA-2119) | *Trivial* | **ConsumerRecord key() and value() methods should not have throws Exception**

There were some leftover throws clauses in ConsumerRecord. It looks like the initial implementation removed errors from the ConsumerRecord but didn't clean up these clauses.

Attaching a trivial patch to remove the clauses.


---

* [KAFKA-2118](https://issues.apache.org/jira/browse/KAFKA-2118) | *Major* | **Cleaner cannot clean after shutdown during replaceSegments**

If a broker shuts down after the cleaner calls replaceSegments with more than one segment, the partition can be left in an uncleanable state. We saw this on a few brokers after doing a rolling update. The sequence of things we saw is:

1) Cleaner cleaned segments with base offsets 0, 1094621529, and 1094831997 into a new segment 0.
2) Cleaner logged "Swapping in cleaned segment 0 for segment(s) 0,1094621529,1094831997 in log xxx-15." and called replaceSegments.
3) 0.cleaned was renamed to 0.swap.
4) Broker shut down before deleting segments 1094621529 and 1094831997.
5) Broker started up and logged "Found log file /mnt/persistent/kafka-logs/xxx-15/00000000000000000000.log.swap from interrupted swap operation, repairing."
6) Cleaner thread died with the exception "kafka.common.InvalidOffsetException: Attempt to append an offset (1094911424) to position 1003 no larger than the last offset appended (1095045873) to /mnt/persistent/kafka-logs/xxx-15/00000000000000000000.index.cleaned."

I think what's happening in #6 is that when the broker started back up and repaired the log, segment 0 ended up with a bunch of messages that were also in segment 1094621529 and 1094831997 (because the new segment 0 was created from cleaning all 3). But segments 1094621529 and 1094831997 were still on disk, so offsets on disk were no longer monotonically increasing, violating the assumption of OffsetIndex. We ended up fixing this by deleting segments 1094621529 and 1094831997 manually, and then removing the line for this partition from the cleaner-offset-checkpoint file (otherwise it would reference the non-existent segment 1094621529).

This can happen even on a clean shutdown (the async deletes in replaceSegments might not happen).

Cleaner logs post-startup:
2015-04-12 15:07:56,533 INFO [kafka-log-cleaner-thread-0] kafka.log.LogCleaner - Cleaner 0: Beginning cleaning of log xxx-15.
2015-04-12 15:07:56,533 INFO [kafka-log-cleaner-thread-0] kafka.log.LogCleaner - Cleaner 0: Building offset map for xxx-15...
2015-04-12 15:07:56,595 INFO [kafka-log-cleaner-thread-0] kafka.log.LogCleaner - Cleaner 0: Building offset map for log xxx-15 for 6 segments in offset range [1094621529, 1095924157).
2015-04-12 15:08:01,443 INFO [kafka-log-cleaner-thread-0] kafka.log.LogCleaner - Cleaner 0: Offset map for log xxx-15 complete.
2015-04-12 15:08:01,443 INFO [kafka-log-cleaner-thread-0] kafka.log.LogCleaner - Cleaner 0: Cleaning log xxx-15 (discarding tombstones prior to Sun Apr 12 14:05:37 UTC 2015)...
2015-04-12 15:08:01,443 INFO [kafka-log-cleaner-thread-0] kafka.log.LogCleaner - Cleaner 0: Cleaning segment 0 in log xxx-15 (last modified Sun Apr 12 14:05:38 UTC 2015) into 0, retaining deletes.
2015-04-12 15:08:04,283 INFO [kafka-log-cleaner-thread-0] kafka.log.LogCleaner - Cleaner 0: Cleaning segment 1094621529 in log xxx-15 (last modified Sun Apr 12 13:49:27 UTC 2015) into 0, discarding deletes.
2015-04-12 15:08:05,079 INFO [kafka-log-cleaner-thread-0] kafka.log.LogCleaner - Cleaner 0: Cleaning segment 1094831997 in log xxx-15 (last modified Sun Apr 12 14:04:28 UTC 2015) into 0, discarding deletes.
2015-04-12 15:08:05,157 ERROR [kafka-log-cleaner-thread-0] kafka.log.LogCleaner - [kafka-log-cleaner-thread-0], Error due to
kafka.common.InvalidOffsetException: Attempt to append an offset (1094911424) to position 1003 no larger than the last offset appended (1095045873) to /mnt/persistent/kafka-logs/xxx-15/00000000000000000000.index.
cleaned.
at kafka.log.OffsetIndex$$anonfun$append$1.apply$mcV$sp(OffsetIndex.scala:207)
at kafka.log.OffsetIndex$$anonfun$append$1.apply(OffsetIndex.scala:197)
at kafka.log.OffsetIndex$$anonfun$append$1.apply(OffsetIndex.scala:197)
at kafka.utils.Utils$.inLock(Utils.scala:535)
at kafka.log.OffsetIndex.append(OffsetIndex.scala:197)
at kafka.log.LogSegment.append(LogSegment.scala:81)
at kafka.log.Cleaner.cleanInto(LogCleaner.scala:427)
at kafka.log.Cleaner$$anonfun$cleanSegments$1.apply(LogCleaner.scala:358)
at kafka.log.Cleaner$$anonfun$cleanSegments$1.apply(LogCleaner.scala:354)
at scala.collection.immutable.List.foreach(List.scala:318)
at kafka.log.Cleaner.cleanSegments(LogCleaner.scala:354)
at kafka.log.Cleaner$$anonfun$clean$4.apply(LogCleaner.scala:321)
at kafka.log.Cleaner$$anonfun$clean$4.apply(LogCleaner.scala:320)
at scala.collection.immutable.List.foreach(List.scala:318)
at kafka.log.Cleaner.clean(LogCleaner.scala:320)
at kafka.log.LogCleaner$CleanerThread.cleanOrSleep(LogCleaner.scala:221)
at kafka.log.LogCleaner$CleanerThread.doWork(LogCleaner.scala:199)
at kafka.utils.ShutdownableThread.run(ShutdownableThread.scala:60)
2015-04-12 15:08:05,157 INFO [kafka-log-cleaner-thread-0] kafka.log.LogCleaner - [kafka-log-cleaner-thread-0], Stopped


---

* [KAFKA-2117](https://issues.apache.org/jira/browse/KAFKA-2117) | *Major* | **OffsetManager uses incorrect field for metadata**

java.lang.ClassCastException: java.lang.Long cannot be cast to
java.lang.String

at
kafka.server.OffsetManager$.kafka$server$OffsetManager$$readMessageValue(OffsetManager.scala:576)

at
kafka.server.OffsetManager$$anonfun$kafka$server$OffsetManager$$loadOffsets$1$2.apply(OffsetManager.scala:388)

at
kafka.server.OffsetManager$$anonfun$kafka$server$OffsetManager$$loadOffsets$1$2.apply(OffsetManager.scala:377)

at scala.collection.Iterator$class.foreach(Iterator.scala:727)

at kafka.utils.IteratorTemplate.foreach(IteratorTemplate.scala:32)

at scala.collection.IterableLike$class.foreach(IterableLike.scala:72)

at kafka.message.MessageSet.foreach(MessageSet.scala:67)

at
kafka.server.OffsetManager.kafka$server$OffsetManager$$loadOffsets$1(OffsetManager.scala:377)

at
kafka.server.OffsetManager$$anonfun$loadOffsetsFromLog$1.apply$mcV$sp(OffsetManager.scala:358)

at
Saw the following exception.

kafka.utils.KafkaScheduler$$anonfun$1.apply$mcV$sp(KafkaScheduler.scala:108)

at kafka.utils.CoreUtils$$anon$1.run(CoreUtils.scala:60)

at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:471)

at java.util.concurrent.FutureTask.run(FutureTask.java:262)

at
java.util.concurrent.ScheduledThreadPoolExecutor$ScheduledFutureTask.access$201(ScheduledThreadPoolExecutor.java:178)

at
java.util.concurrent.ScheduledThreadPoolExecutor$ScheduledFutureTask.run(ScheduledThreadPoolExecutor.java:292)

at
java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1145)

at
java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:615)

at java.lang.Thread.run(Thread.java:744)


---

* [KAFKA-2115](https://issues.apache.org/jira/browse/KAFKA-2115) | *Major* | **Error updating metrics in RequestChannel**

Reported by [~jkreps] on the mailing list:

{code}
    kafka.common.KafkaException: Wrong request type 12
    
    at kafka.api.RequestKeys$.nameForKey(RequestKeys.scala:55)
    
    at
    kafka.network.RequestChannel$Request.updateRequestMetrics(RequestChannel.scala:85)
    
    at kafka.network.Processor.write(SocketServer.scala:514)
    
    at kafka.network.Processor.run(SocketServer.scala:379)
    
    at java.lang.Thread.run(Thread.java:744)
    
    [2015-04-12 12:54:52,077] INFO [Kafka Coordinator 0]: Registered consumer
my-group-24 for group my-group (kafka.coordinator.ConsumerCoordinator)
    
    [2015-04-12 12:54:52,080] INFO [Kafka Coordinator 0]: Handled join-group
    from consumer  to group my-group (kafka.coordinator.ConsumerCoordinator)

    [2015-04-12 12:54:52,081] ERROR Closing socket for /10.0.0.220 because of
    error (kafka.network.Processor)
    
    kafka.common.KafkaException: Wrong request type 11
    
    at kafka.api.RequestKeys$.nameForKey(RequestKeys.scala:55)
    
    at
    kafka.network.RequestChannel$Request.updateRequestMetrics(RequestChannel.scala:85)
    
    at kafka.network.Processor.write(SocketServer.scala:514)
    
    at kafka.network.Processor.run(SocketServer.scala:379)
    
     at java.lang.Thread.run(Thread.java:744)
{code}

This a result of KAFKA-2044 - we moved few Requests out
of RequestKeys to the newer ApiKeys, but didn't update the metrics
code.


---

* [KAFKA-2114](https://issues.apache.org/jira/browse/KAFKA-2114) | *Major* | **Unable to change min.insync.replicas default**

Following the comment here[1] I was unable to change the min.insync.replicas default value. I tested this by setting up a 3 node cluster, wrote to a topic with a replication factor of 3, using request.required.acks=-1 and setting min.insync.replicas=2 on the broker's server.properties. I then shutdown 2 brokers but I was still able to write successfully. Only after running the alter topic command setting min.insync.replicas=2 on the topic did I see write failures.

[1] - http://mail-archives.apache.org/mod\_mbox/kafka-users/201504.mbox/%3CCANZ-JHF71yqKE6%2BKKhWe2EGUJv6R3bTpoJnYck3u1-M35sobgg%40mail.gmail.com%3E


---

* [KAFKA-2113](https://issues.apache.org/jira/browse/KAFKA-2113) | *Major* | **TestPurgatoryPerformance does not compile using IBM JDK**

TestPurgatoryPerformance uses a class from the com.sun package that is not available in the IBM JDK.

The code does handle the class not found exception at runtime if run with an IBM JRE (and prints out -1 as CPU time). But as a result of the direct reference to the com.sun.management.OperatingSystemMXBean class, Kafka core project no longer compiles with an IBM JDK. 

{quote}
:core:compileTestScala/kafka/core/src/test/scala/other/kafka/TestPurgatoryPerformance.scala:88: type OperatingSystemMXBean is not a member of package com.sun.management
      Some(ManagementFactory.getOperatingSystemMXBean().asInstanceOf[com.sun.management.OperatingSystemMXBean])
                                                                                        ^
one error found
 FAILED
{quote}

The JRE-specific class should be dynamically loaded to enable the class to be compiled as well as run with any JDK.


---

* [KAFKA-2112](https://issues.apache.org/jira/browse/KAFKA-2112) | *Major* | **make overflowWheel volatile**

overflowWheel in TimingWheel needs to be volatile due to the issue of Double-Checked Locking pattern with JVM.

http://www.cs.umd.edu/~pugh/java/memoryModel/DoubleCheckedLocking.html


---

* [KAFKA-2110](https://issues.apache.org/jira/browse/KAFKA-2110) | *Trivial* | **Doc: Clarify that max number of consumer instances is per consumer group**

Suggest to modify in the Introduction, section "Consumers" to clarify that the maximum amount of consumer instances is *per consumer group*:

"Note however that there cannot be more consumer instances than partitions."
=>
"Note however that there cannot be more consumer instances in a consumer group than partitions."

and

"... though this will mean only one consumer process." 
=>
"... though this will mean only one consumer process per consumer group."


---

* [KAFKA-2109](https://issues.apache.org/jira/browse/KAFKA-2109) | *Minor* | **Support retries in KafkaLog4jAppender**

KafkaProducer has a "retries" config parameter but this isn't exposed by KafkaLog4jAppender. It would be useful to have this available.


---

* [KAFKA-2104](https://issues.apache.org/jira/browse/KAFKA-2104) | *Major* | ** testDuplicateListeners()  has a typo**

[~onurkaraman] caught a problem introduced in KAFKA-1809:

In testDuplicateListeners() from KafkaConfigTest, your property key has a typo(the comma should be a dot):
{code}
props.put("advertised,listeners", "PLAINTEXT://localhost:9091,TRACE://localhost:9091")
{code}
should be:
{code}
props.put("advertised.listeners", "PLAINTEXT://localhost:9091,TRACE://localhost:9091")
{code}


---

* [KAFKA-2099](https://issues.apache.org/jira/browse/KAFKA-2099) | *Major* | **BrokerEndPoint file, methods and object names should match**

[~harsha\_ch] commented on KAFKA-1809:
We've BrokerEndPoint.scala but internally object called "object BrokerEndpoint" with a smallcase "p" and method createBrokerEndPoint . If possible can we get these consistent in another JIRA.


---

* [KAFKA-2096](https://issues.apache.org/jira/browse/KAFKA-2096) | *Critical* | **Enable keepalive socket option for broker to prevent socket leak**

We run a Kafka 0.8.2.1 cluster in AWS with large number of producers (> 10000). Also the number of producer instances scale up and down significantly on a daily basis.

The issue we found is that after 10 days, the open file descriptor count will approach the limit of 32K. An investigation of these open file descriptors shows that a significant portion of these are from client instances that are terminated during scaling down. Somehow they still show as "ESTABLISHED" in netstat. We suspect that the AWS firewall between the client and broker causes this issue.

We attempted to use "keepalive" socket option to reduce this socket leak on broker and it appears to be working. Specifically, we added this line to kafka.network.Acceptor.accept():

      socketChannel.socket().setKeepAlive(true)

It is confirmed during our experiment of this change that entries in netstat where the client instance is terminated were probed as configured in operating system. After configured number of probes, the OS determined that the peer is no longer alive and the entry is removed, possibly after an error in Kafka to read from the channel and closing the channel. Also, our experiment shows that after a few days, the instance was able to keep a stable low point of open file descriptor count, compared with other instances where the low point keeps increasing day to day.


---

* [KAFKA-2090](https://issues.apache.org/jira/browse/KAFKA-2090) | *Minor* | **Remove duplicate check to metadataFetchInProgress**

In the NetworkClient class on a call to poll() there are three checks (timeToNextMetadataUpdate, timeToNextReconnectAttempt, waitForMetadataFetch) made to see if a metadata update should be made. If all of these == 0 then an update is performed.

However, in the if block a second check is made to metadataFetchInProgress. This only make sense in a multithreaded environment. However, as the variable is not volatile I suspect this is not the case.


---

* [KAFKA-2088](https://issues.apache.org/jira/browse/KAFKA-2088) | *Minor* | **kafka-console-consumer.sh should not create zookeeper path when no brokers found and chroot was set in zookeeper.connect**

1. set server.properties
server.properties:
zookeeper.connect = 192.168.0.10:2181,192.168.0.10:2181,192.168.0.10:2181/kafka

2 default zookeeepr path:
[zk: 192.168.0.10:2181(CONNECTED) 10] ls /
[zookeeper, kafka, storm]

3.start console consumer use a not exist topic and zookeeper address without chroot.
[root@stream client\_0402]# kafka-console-consumer.sh --zookeeper 192.168.0.10:2181 --topic test --from-beginning
[2015-04-03 18:15:28,599] WARN [console-consumer-63060\_stream-1428056127990-d35ca648], no brokers found when trying to rebalance. (kafka.consumer.ZookeeperConsumerConnector)


4.then "/consumer" and "/brokers" path was create in zookeeper.

[zk: 192.168.0.10:2181(CONNECTED) 2] ls /
[zookeeper, consumers, kafka, storm, brokers]

so it is a bug. consumer should not create "/consumer" and "/brokers" path .


---

* [KAFKA-2056](https://issues.apache.org/jira/browse/KAFKA-2056) | *Major* | **PartitionAssignorTest.testRangePartitionAssignor transient failure**

{code}
unit.kafka.consumer.PartitionAssignorTest > testRangePartitionAssignor FAILED
    java.lang.NullPointerException
        at unit.kafka.consumer.PartitionAssignorTest$$anonfun$unit$kafka$consumer$PartitionAssignorTest$$assignAndVerify$1.apply(PartitionAssignorTest.scala:173)
        at unit.kafka.consumer.PartitionAssignorTest$$anonfun$unit$kafka$consumer$PartitionAssignorTest$$assignAndVerify$1.apply(PartitionAssignorTest.scala:172)
        at scala.collection.immutable.List.foreach(List.scala:318)
        at unit.kafka.consumer.PartitionAssignorTest$.unit$kafka$consumer$PartitionAssignorTest$$assignAndVerify(PartitionAssignorTest.scala:172)
        at unit.kafka.consumer.PartitionAssignorTest$$anonfun$testRangePartitionAssignor$1.apply$mcVI$sp(PartitionAssignorTest.scala:79)
        at scala.collection.immutable.Range.foreach$mVc$sp(Range.scala:141)
        at unit.kafka.consumer.PartitionAssignorTest.testRangePartitionAssignor(PartitionAssignorTest.scala:60)
{code}


---

* [KAFKA-2044](https://issues.apache.org/jira/browse/KAFKA-2044) | *Major* | **Support requests and responses from o.a.k.common in KafkaApis**

As groundwork for KIP-4 and for KAFKA-1927, we'll add some plumbing to support handling of requests and responses from o.a.k.common in KafkaApis.

This will allow us to add new Api calls just in o.a.k.conmon and to gradually migrate existing requests and responses.


---

* [KAFKA-2043](https://issues.apache.org/jira/browse/KAFKA-2043) | *Minor* | **CompressionType is passed in each RecordAccumulator append**

Currently org.apache.kafka.clients.producer.internals.RecordAccumulator append method accepts the compressionType on a per record basis. It looks like the code would only work on a per batch basis because the CompressionType is only used when creating a new RecordBatch. My understanding is this should only support setting per batch at most. 

    public RecordAppendResult append(TopicPartition tp, byte[] key, byte[] value, CompressionType compression, Callback callback) throws InterruptedException;

The compression type is a producer
level config. Instead of passing it in for each append, we probably should
just pass it in once during the creation RecordAccumulator.


---

* [KAFKA-2042](https://issues.apache.org/jira/browse/KAFKA-2042) | *Blocker* | **New producer metadata update always get all topics.**

The new java producer metadata.topics is initially empty so the producer sends TMR with empty topic set. The broker takes the empty requested topic set as all topics, so metadata.cluster contains all topic metadata. Later on, when a new topic was produced, it gets added into the metadata.topics. The next metadata update will only contain the meta data for this new topic, so the metadata.cluster will only have this topic. Since there are a lot of messages are still in the accumulator but has no metadata in metadata.cluster, if a caller thread do a flush(), the caller thread will block forever because the messages sitting in accumulator without metadata will never be ready to send.
We should add check for the metadata.topics, if it is empty, no TMR should be sent.


---

* [KAFKA-2039](https://issues.apache.org/jira/browse/KAFKA-2039) | *Minor* | **Update Scala to 2.10.5 and 2.11.6**

Scala 2.10.5 (the last release of the 2.10.x series) is binary compatible with 2.10.4  and Scala 2.11.6 is binary compatible with 2.11.5. For details of the changes in each release, see:

* http://www.scala-lang.org/news/2.10.5
* http://www.scala-lang.org/news/2.11.6


---

* [KAFKA-2033](https://issues.apache.org/jira/browse/KAFKA-2033) | *Major* | **Small typo in documentation**

The javadoc still mentions "metadata.broker.list" in the consumer config.


---

* [KAFKA-2016](https://issues.apache.org/jira/browse/KAFKA-2016) | *Major* | **RollingBounceTest takes long**

RollingBounceTest.testRollingBounce() currently takes about 48 secs. This is a bit too long.


---

* [KAFKA-2013](https://issues.apache.org/jira/browse/KAFKA-2013) | *Trivial* | **benchmark test for the purgatory**

We need a micro benchmark test for measuring the purgatory performance.


---

* [KAFKA-2009](https://issues.apache.org/jira/browse/KAFKA-2009) | *Major* | **Fix UncheckedOffset.removeOffset synchronization and trace logging issue in mirror maker**

This ticket is to fix the mirror maker problem on current trunk which is introduced in KAFKA-1650.


---

* [KAFKA-2001](https://issues.apache.org/jira/browse/KAFKA-2001) | *Major* | **OffsetCommitTest hang during setup**

OffsetCommitTest seems to hang in trunk reliably. The following is the stacktrace. It seems to hang during setup.

"Test worker" prio=5 tid=7fb5ab154800 nid=0x11198e000 waiting on condition [11198c000]
   java.lang.Thread.State: TIMED\_WAITING (sleeping)
        at java.lang.Thread.sleep(Native Method)
        at kafka.server.OffsetCommitTest$$anonfun$setUp$2.apply(OffsetCommitTest.scala:59)
        at kafka.server.OffsetCommitTest$$anonfun$setUp$2.apply(OffsetCommitTest.scala:58)
        at scala.collection.immutable.Stream.dropWhile(Stream.scala:825)
        at kafka.server.OffsetCommitTest.setUp(OffsetCommitTest.scala:58)
        at junit.framework.TestCase.runBare(TestCase.java:132)
        at junit.framework.TestResult$1.protect(TestResult.java:110)
        at junit.framework.TestResult.runProtected(TestResult.java:128)
        at junit.framework.TestResult.run(TestResult.java:113)
        at junit.framework.TestCase.run(TestCase.java:124)
        at junit.framework.TestSuite.runTest(TestSuite.java:232)
        at junit.framework.TestSuite.run(TestSuite.java:227)
        at org.junit.internal.runners.JUnit38ClassRunner.run(JUnit38ClassRunner.java:91)
        at org.gradle.api.internal.tasks.testing.junit.JUnitTestClassExecuter.runTestClass(JUnitTestClassExecuter.java:86)
        at org.gradle.api.internal.tasks.testing.junit.JUnitTestClassExecuter.execute(JUnitTestClassExecuter.java:49)
        at org.gradle.api.internal.tasks.testing.junit.JUnitTestClassProcessor.processTestClass(JUnitTestClassProcessor.java:69)
        at org.gradle.api.internal.tasks.testing.SuiteTestClassProcessor.processTestClass(SuiteTestClassProcessor.java:48)


---

* [KAFKA-1999](https://issues.apache.org/jira/browse/KAFKA-1999) | *Major* | **Fix failing unit-test: kafka.api.ProducerFailureHandlingTest \> testNotEnoughReplicasAfterBrokerShutdown**

The test checks for just one out of two possible exceptions.


---

* [KAFKA-1994](https://issues.apache.org/jira/browse/KAFKA-1994) | *Major* | **Evaluate performance effect of chroot check on Topic creation**

KAFKA-1664 adds check for chroot while creating a node in ZK. ZkPath checks if namespace exists before trying to create a path in ZK. This raises a concern that checking namespace for each path creation might be unnecessary and can potentially make creations expensive.


---

* [KAFKA-1992](https://issues.apache.org/jira/browse/KAFKA-1992) | *Major* | **Following KAFKA-1697, checkEnoughReplicasReachOffset doesn't need to get requiredAcks**

Follow up from Jun's review:

"Should we just remove requiredAcks completely since checkEnoughReplicasReachOffset() will only be called when requiredAcks is -1?"

Answer is: Yes, we should :)


---

* [KAFKA-1990](https://issues.apache.org/jira/browse/KAFKA-1990) | *Major* | **Add unlimited time-based log retention**

Currently you can set
  log.retention.bytes = -1
to disable size based retention (in fact that is the default). However, there is no equivalent for time based retention. You can set time based retention to something really big like 2147483647 hours, which in practical terms is forever, but it is kind of silly to require this.


---

* [KAFKA-1989](https://issues.apache.org/jira/browse/KAFKA-1989) | *Critical* | **New purgatory design**

This is a new design of purgatory based on Hierarchical Timing Wheels.

https://cwiki.apache.org/confluence/display/KAFKA/Purgatory+Redesign+Proposal


---

* [KAFKA-1988](https://issues.apache.org/jira/browse/KAFKA-1988) | *Blocker* | **org.apache.kafka.common.utils.Utils.abs method returns wrong value for negative numbers.**

org.apache.kafka.common.utils.Utils.abs method returns wrong value for negative numbers. The method only returns intended value for positive numbers. All negative numbers except the Integer.Min\_Value will be returned an unsigned integer.


---

* [KAFKA-1986](https://issues.apache.org/jira/browse/KAFKA-1986) | *Major* | **Producer request failure rate should not include InvalidMessageSizeException and OffsetOutOfRangeException**

InvalidMessageSizeException and OffsetOutOfRangeException should not be counted a failedProduce and failedFetch requests since they are client side errors. They should be treated similarly to UnknownTopicOrPartitionException or NotLeaderForPartitionException


---

* [KAFKA-1982](https://issues.apache.org/jira/browse/KAFKA-1982) | *Major* | **change kafka.examples.Producer to use the new java producer**

We need to change the example to use the new java producer.


---

* [KAFKA-1973](https://issues.apache.org/jira/browse/KAFKA-1973) | *Major* | **Remove the accidentally created LogCleanerManager.scala.orig**

It seems there is a LogCleanerManager.scala.orig in the trunk now. Need to remove it.


---

* [KAFKA-1969](https://issues.apache.org/jira/browse/KAFKA-1969) | *Major* | **NPE in unit test for new consumer**

{code}
kafka.api.ConsumerTest > testConsumptionWithBrokerFailures FAILED
    java.lang.NullPointerException
        at org.apache.kafka.clients.consumer.KafkaConsumer.ensureCoordinatorReady(KafkaConsumer.java:1238)
        at org.apache.kafka.clients.consumer.KafkaConsumer.initiateCoordinatorRequest(KafkaConsumer.java:1189)
        at org.apache.kafka.clients.consumer.KafkaConsumer.commit(KafkaConsumer.java:777)
        at org.apache.kafka.clients.consumer.KafkaConsumer.commit(KafkaConsumer.java:816)
        at org.apache.kafka.clients.consumer.KafkaConsumer.poll(KafkaConsumer.java:704)
        at kafka.api.ConsumerTest.consumeWithBrokerFailures(ConsumerTest.scala:167)
        at kafka.api.ConsumerTest.testConsumptionWithBrokerFailures(ConsumerTest.scala:152)
{code}


---

* [KAFKA-1965](https://issues.apache.org/jira/browse/KAFKA-1965) | *Trivial* | **Leaner DelayedItem**

In DelayedItem, which is a superclass of DelayedOperation, both the creation timestamp and the length delay are stored. However, all it needs is one timestamp that is the due of the item.


---

* [KAFKA-1960](https://issues.apache.org/jira/browse/KAFKA-1960) | *Minor* | **.gitignore does not exclude test generated files and folders.**

gradle test can create quite few folders, .gitignore should exclude these files for an easier git submit.


---

* [KAFKA-1959](https://issues.apache.org/jira/browse/KAFKA-1959) | *Major* | **Class CommitThread overwrite group of Thread class causing compile errors**

class CommitThread(id: Int, partitionCount: Int, commitIntervalMs: Long, zkClient: ZkClient)
        extends ShutdownableThread("commit-thread")
        with KafkaMetricsGroup {

    private val group = "group-" + id

group overwrite class Thread group member, causing the following compile error:

overriding variable group in class Thread of type ThreadGroup;  value group has weaker access privileges; it should not be private


---

* [KAFKA-1957](https://issues.apache.org/jira/browse/KAFKA-1957) | *Trivial* | **code doc typo**

There are doc typo in kafka.server.KafkaConfig.scala, SO\_SNDBUFF should be SO\_SNDBUF and SO\_RCVBUFF should be SO\_RCVBUF


---

* [KAFKA-1953](https://issues.apache.org/jira/browse/KAFKA-1953) | *Major* | **Disambiguate metrics from different purgatories**

After the purgatory refactoring, all the different purgatories map to the same metric names. We need to disambiguate.


---

* [KAFKA-1948](https://issues.apache.org/jira/browse/KAFKA-1948) | *Major* | **kafka.api.consumerTests are hanging**

Noticed today that very often when I run the full test suite, it hangs on kafka.api.consumerTest (not always same test though). It doesn't reproduce 100% of the time, but enough to be very annoying.

I also saw it happening on trunk after KAFKA-1333:
https://builds.apache.org/view/All/job/Kafka-trunk/389/


---

* [KAFKA-1947](https://issues.apache.org/jira/browse/KAFKA-1947) | *Major* | **can't explicitly set replica-assignment when add partitions**

When create topic, the replicaAssignmentOpt should not appear with partitions.
But when add partitions,  they should can appear together,  from the code below, you can see when alter topic, and has partitions in arguments, it try get "replica-assignment"
https://git1-us-west.apache.org/repos/asf?p=kafka.git;a=blob;f=core/src/main/scala/kafka/admin/TopicCommand.scala;h=285c0333ff43543d3e46444c1cd9374bb883bb59;hb=HEAD#l114 

The root cause is below code:
CommandLineUtils.checkInvalidArgs(parser, options, replicaAssignmentOpt,
 305         allTopicLevelOpts -- Set(alterOpt, createOpt) + partitionsOpt + replicationFactorOpt)

https://git1-us-west.apache.org/repos/asf?p=kafka.git;a=blob;f=core/src/main/scala/kafka/admin/TopicCommand.scala;h=285c0333ff43543d3e46444c1cd9374bb883bb59;hb=HEAD#l304

Related:  
https://issues.apache.org/jira/browse/KAFKA-1052


---

* [KAFKA-1943](https://issues.apache.org/jira/browse/KAFKA-1943) | *Major* | **Producer request failure rate should not include MessageSetSizeTooLarge and MessageSizeTooLargeException**

If MessageSetSizeTooLargeException or MessageSizeTooLargeException is thrown from Log, then ReplicaManager counts it as a failed produce request. My understanding is that this metric should only count failures as a result of broker issues and not bad requests sent by the clients.

If the message or message set is too large, then it is a client side error and should not be reported. (similar to NotLeaderForPartitionException, UnknownTopicOrPartitionException).


---

* [KAFKA-1940](https://issues.apache.org/jira/browse/KAFKA-1940) | *Major* | **Initial checkout and build failing**

when performing `gradle wrapper` and `gradlew build` as a "new" developer, I get an exception: 
{code}
C:\development\git\kafka>gradlew build --stacktrace
<...>
FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':core:compileScala'.
> com.typesafe.zinc.Setup.create(Lcom/typesafe/zinc/ScalaLocation;Lcom/typesafe/zinc/SbtJars;Ljava/io/File;)Lcom/typesaf
e/zinc/Setup;
{code}

Details: https://gist.github.com/mlem/ddff83cc8a25b040c157

Current Commit:
{code}
C:\development\git\kafka>git rev-parse --verify HEAD
71602de0bbf7727f498a812033027f6cbfe34eb8
{code}

I am evaluating kafka for my company and wanted to run some tests with it, but couldn't due to this error. I know gradle can be tricky and it's not easy to setup everything correct, but this kind of bugs turns possible commiters/users off.


---

* [KAFKA-1938](https://issues.apache.org/jira/browse/KAFKA-1938) | *Trivial* | **[doc] Quick start example should reference appropriate Kafka version**

Kafka 0.8.2.0 documentation, quick start example on https://kafka.apache.org/documentation.html#quickstart in step 1 links and instructs reader to download Kafka 0.8.1.1.


---

* [KAFKA-1926](https://issues.apache.org/jira/browse/KAFKA-1926) | *Major* | **Replace kafka.utils.Utils with o.a.k.common.utils.Utils**

There is currently a lot of duplication between the Utils class in common and the one in core.

Our plan has been to deprecate duplicate code in the server and replace it with the new common code.

As such we should evaluate each method in the scala Utils and do one of the following:
1. Migrate it to o.a.k.common.utils.Utils if it is a sensible general purpose utility in active use that is not Kafka-specific. If we migrate it we should really think about the API and make sure there is some test coverage. A few things in there are kind of funky and we shouldn't just blindly copy them over.
2. Create a new class ServerUtils or ScalaUtils in kafka.utils that will hold any utilities that really need to make use of Scala features to be convenient.
3. Delete it if it is not used, or has a bad api.


---

* [KAFKA-1925](https://issues.apache.org/jira/browse/KAFKA-1925) | *Critical* | **Coordinator Node Id set to INT\_MAX breaks coordinator metadata updates**

KafkaConsumer used INT\_MAX to mimic a new socket for coordinator (details can be found in KAFKA-1760). However, this behavior breaks the coordinator as the underlying NetworkClient only used the node id to determine when to initiate a new connection:

{code}
if (connectionStates.canConnect(node.id(), now))
            // if we are interested in sending to a node and we don't have a connection to it, initiate one
            initiateConnect(node, now);
{code}


---

* [KAFKA-1915](https://issues.apache.org/jira/browse/KAFKA-1915) | *Minor* | **Integrate checkstyle for java code**

There are a lot of little style and layering problems that tend to creep into our code, especially with external patches and lax reviewers.

These are the usual style suspects--capitalization, spacing, bracket placement,  etc.

My personal pet peave is a lack of clear thinking about layers. These layering problems crept in quite fast, and sad to say a number of them were accidentally caused by me. This is things like o.a.k.common depending on o.a.k.clients or the consumer depending on the producer.

I have a patch that integrates checkstyle to catch these issues at build time, and which corrects the known problems. There are a fair number of very small changes in this patch, all trivial.

Checkstyle can be slightly annoying, not least of which because it has a couple minor bugs around anonymous inner class formatting, but I find it is 98% real style issues so mostly worth it.


---

* [KAFKA-1914](https://issues.apache.org/jira/browse/KAFKA-1914) | *Major* | **Count TotalProduceRequestRate and TotalFetchRequestRate in BrokerTopicMetrics**

Currently the BrokerTopicMetrics only counts the failedProduceRequestRate and the failedFetchRequestRate. We should add 2 metrics to count the overall produce/fetch request rates.


---

* [KAFKA-1910](https://issues.apache.org/jira/browse/KAFKA-1910) | *Major* | **Refactor KafkaConsumer**

KafkaConsumer now contains all the logic on the consumer side, making it a very huge class file, better re-factoring it to have multiple layers on top of KafkaClient.


---

* [KAFKA-1896](https://issues.apache.org/jira/browse/KAFKA-1896) | *Major* | **Record size funcition of record in mirror maker hit NPE when the message value is null.**

The byte bounded queue should not assume the message value is not null. For compacted topics, the tombstone message will have a null value, which lead to an NPE.


---

* [KAFKA-1891](https://issues.apache.org/jira/browse/KAFKA-1891) | *Major* | **MirrorMaker hides consumer exception - making troubleshooting challenging**

When MirrorMaker encounters an issue creating a consumer, it gives a generic "unable to create stream" error, while hiding the actual issue.

We should print the original exception too, so users can resolve whatever issue prevents MirrorMaker from creating a stream.


---

* [KAFKA-1890](https://issues.apache.org/jira/browse/KAFKA-1890) | *Blocker* | **Fix bug preventing Mirror Maker from successful rebalance.**

Follow-up patch for KAFKA-1650


---

* [KAFKA-1885](https://issues.apache.org/jira/browse/KAFKA-1885) | *Major* | **Allow test methods in "core" to be individually run from outside of the IDE**

Gradle in combination with Java plugin allows test "filtering" which lets users run select test classes or even select test methods from the command line. See "Test filtering" section here http://www.gradle.org/docs/2.0/userguide/java\_plugin.html#sec:java\_test which has examples of the commands. Currently we have this working in the "clients" and I can run something like:

{code}
./gradlew clients:test --tests org.apache.kafka.clients.producer.MetadataTest.testMetadataUpdateWaitTime
{code}

and that command then only runs that specific test method (testMetadataUpdateWaitTime) from the MetadataTest class.

{code}
To honour the JVM settings for this build a new JVM will be forked. Please consider using the daemon: http://gradle.org/docs/2.0/userguide/gradle\_daemon.html.
Building project 'core' with Scala version 2.10.4
:clients:compileJava UP-TO-DATE
:clients:processResources UP-TO-DATE
:clients:classes UP-TO-DATE
:clients:compileTestJava UP-TO-DATE
:clients:processTestResources UP-TO-DATE
:clients:testClasses UP-TO-DATE
:clients:test

org.apache.kafka.clients.producer.MetadataTest > testMetadataUpdateWaitTime PASSED

BUILD SUCCESSFUL

Total time: 12.714 secs
{code}

I've found this useful when I need to do some quick tests and also reproduce issues that aren't noticed sometimes if the whole test class is run.

This currently only works for the "clients" and not for "core" --because the "core" doesn't have the Java plugin applied to it in the gradle build--. I've a patch which does that (and one other related thing) which then allowed me to run individual test methods even for the core tests. I will create a review request for it.

Edit: I was wrong about the java plugin not being applied to "core". It is indeed already applied but my attempt to get test methods running individually for "core" were failing for a different reason related to JUnit version dependency. I'll be addressing that in the patch and uploading for review.


---

* [KAFKA-1884](https://issues.apache.org/jira/browse/KAFKA-1884) | *Major* | **Print metadata response errors**

Print metadata response errors.

producer logs:

DEBUG [2015-01-20 12:46:13,406] NetworkClient: maybeUpdateMetadata(): Trying to send metadata request to node -1
DEBUG [2015-01-20 12:46:13,406] NetworkClient: maybeUpdateMetadata(): Sending metadata request ClientRequest(expectResponse=true, payload=null, request=RequestSend(header={api\_key=3,api\_version=0,correlation\_id=50845,client\_id=my-producer}, body={topics=[TOPIC=]})) to node -1
TRACE [2015-01-20 12:46:13,416] NetworkClient: handleMetadataResponse(): Ignoring empty metadata response with correlation id 50845.
DEBUG [2015-01-20 12:46:13,417] NetworkClient: maybeUpdateMetadata(): Trying to send metadata request to node -1
DEBUG [2015-01-20 12:46:13,417] NetworkClient: maybeUpdateMetadata(): Sending metadata request ClientRequest(expectResponse=true, payload=null, request=RequestSend(header={api\_key=3,api\_version=0,correlation\_id=50846,client\_id=my-producer}, body={topics=[TOPIC=]})) to node -1
TRACE [2015-01-20 12:46:13,417] NetworkClient: handleMetadataResponse(): Ignoring empty metadata response with correlation id 50846.
DEBUG [2015-01-20 12:46:13,417] NetworkClient: maybeUpdateMetadata(): Trying to send metadata request to node -1
DEBUG [2015-01-20 12:46:13,418] NetworkClient: maybeUpdateMetadata(): Sending metadata request ClientRequest(expectResponse=true, payload=null, request=RequestSend(header={api\_key=3,api\_version=0,correlation\_id=50847,client\_id=my-producer}, body={topics=[TOPIC=]})) to node -1
TRACE [2015-01-20 12:46:13,418] NetworkClient: handleMetadataResponse(): Ignoring empty metadata response with correlation id 50847.

Broker logs:

[2015-01-20 12:46:14,074] ERROR [KafkaApi-0] error when handling request Name: TopicMetadataRequest; Version: 0; CorrelationId: 51020; ClientId: my-producer; Topics: TOPIC= (kafka.server.KafkaApis)
kafka.common.InvalidTopicException: topic name TOPIC= is illegal, contains a character other than ASCII alphanumerics, '.', '\_' and '-'
	at kafka.common.Topic$.validate(Topic.scala:42)
	at kafka.admin.AdminUtils$.createOrUpdateTopicPartitionAssignmentPathInZK(AdminUtils.scala:186)
	at kafka.admin.AdminUtils$.createTopic(AdminUtils.scala:177)
	at kafka.server.KafkaApis$$anonfun$5.apply(KafkaApis.scala:367)
	at kafka.server.KafkaApis$$anonfun$5.apply(KafkaApis.scala:350)
	at scala.collection.TraversableLike$$anonfun$map$1.apply(TraversableLike.scala:244)
	at scala.collection.TraversableLike$$anonfun$map$1.apply(TraversableLike.scala:244)
	at scala.collection.immutable.Set$Set1.foreach(Set.scala:74)
	at scala.collection.TraversableLike$class.map(TraversableLike.scala:244)
	at scala.collection.AbstractSet.scala$collection$SetLike$$super$map(Set.scala:47)
	at scala.collection.SetLike$class.map(SetLike.scala:93)
	at scala.collection.AbstractSet.map(Set.scala:47)
	at kafka.server.KafkaApis.getTopicMetadata(KafkaApis.scala:350)
	at kafka.server.KafkaApis.handleTopicMetadataRequest(KafkaApis.scala:389)
	at kafka.server.KafkaApis.handle(KafkaApis.scala:57)
	at kafka.server.KafkaRequestHandler.run(KafkaRequestHandler.scala:59)
	at java.lang.Thread.run(Thread.java:722)


---

* [KAFKA-1883](https://issues.apache.org/jira/browse/KAFKA-1883) | *Major* | **NullPointerException in RequestSendThread**

I often see the following exception while running some tests
(ProducerFailureHandlingTest.testNoResponse is one such instance):

{code}
[2015-01-19 22:30:24,257] ERROR [Controller-0-to-broker-1-send-thread],
Controller 0 fails to send a request to broker
id:1,host:localhost,port:56729 (kafka.controller.RequestSendThread:103)
java.lang.NullPointerException
    at kafka.controller.RequestSendThread.doWork(ControllerChannelManager.
scala:150)
    at kafka.utils.ShutdownableThread.run(ShutdownableThread.scala:60)

{code}

Looking at that code in question, I can see that the NPE can be triggered
when the "receive" is null which can happen if the "isRunning" is false
(i.e a shutdown has been requested).


---

* [KAFKA-1881](https://issues.apache.org/jira/browse/KAFKA-1881) | *Major* | **transient unit test failure in testDeleteTopicWithCleaner due to OOME**

kafka.admin.DeleteTopicTest > testDeleteTopicWithCleaner FAILED
    java.lang.OutOfMemoryError: Java heap space
        at java.nio.HeapByteBuffer.<init>(HeapByteBuffer.java:39)
        at java.nio.ByteBuffer.allocate(ByteBuffer.java:312)
        at kafka.log.SkimpyOffsetMap.<init>(OffsetMap.scala:42)
        at kafka.log.LogCleaner$CleanerThread.<init>(LogCleaner.scala:177)
        at kafka.log.LogCleaner$$anonfun$1.apply(LogCleaner.scala:86)
        at kafka.log.LogCleaner$$anonfun$1.apply(LogCleaner.scala:86)
        at scala.collection.TraversableLike$$anonfun$map$1.apply(TraversableLike.scala:244)
        at scala.collection.TraversableLike$$anonfun$map$1.apply(TraversableLike.scala:244)
        at scala.collection.immutable.Range.foreach(Range.scala:141)
        at scala.collection.TraversableLike$class.map(TraversableLike.scala:244)
        at scala.collection.AbstractTraversable.map(Traversable.scala:105)
        at kafka.log.LogCleaner.<init>(LogCleaner.scala:86)
        at kafka.log.LogManager.<init>(LogManager.scala:64)
        at kafka.server.KafkaServer.createLogManager(KafkaServer.scala:337)
        at kafka.server.KafkaServer.startup(KafkaServer.scala:85)
        at kafka.utils.TestUtils$.createServer(TestUtils.scala:134)
        at kafka.admin.DeleteTopicTest$$anonfun$10.apply(DeleteTopicTest.scala:272)
        at kafka.admin.DeleteTopicTest$$anonfun$10.apply(DeleteTopicTest.scala:272)
        at scala.collection.TraversableLike$$anonfun$map$1.apply(TraversableLike.scala:244)
        at scala.collection.TraversableLike$$anonfun$map$1.apply(TraversableLike.scala:244)
        at scala.collection.immutable.List.foreach(List.scala:318)
        at scala.collection.TraversableLike$class.map(TraversableLike.scala:244)
        at scala.collection.AbstractTraversable.map(Traversable.scala:105)
        at kafka.admin.DeleteTopicTest.createTestTopicAndCluster(DeleteTopicTest.scala:272)
        at kafka.admin.DeleteTopicTest.testDeleteTopicWithCleaner(DeleteTopicTest.scala:241)


---

* [KAFKA-1878](https://issues.apache.org/jira/browse/KAFKA-1878) | *Major* | **ProducerFailureHandlingTest.testCannotSendToInternalTopic fails with TimeoutException while trying to fetch metadata for topic**

The testCannotSendToInternalTopic test method in ProducerFailureHandlingTest fails consistently with the following exception:

{code}
Unexpected exception while seding to an invalid topic org.apache.kafka.common.errors.TimeoutException: Failed to update metadata after 3000 ms.
java.lang.AssertionError: Unexpected exception while seding to an invalid topic org.apache.kafka.common.errors.TimeoutException: Failed to update metadata after 3000 ms.
	at org.junit.Assert.fail(Assert.java:91)
	at org.junit.Assert.assertTrue(Assert.java:43)
	at kafka.api.test.ProducerFailureHandlingTest.testCannotSendToInternalTopic(ProducerFailureHandlingTest.scala:317)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:601)
	at junit.framework.TestCase.runTest(TestCase.java:168)
	at junit.framework.TestCase.runBare(TestCase.java:134)
	at junit.framework.TestResult$1.protect(TestResult.java:110)
	at junit.framework.TestResult.runProtected(TestResult.java:128)
	at junit.framework.TestResult.run(TestResult.java:113)
	at junit.framework.TestCase.run(TestCase.java:124)
	at org.scalatest.junit.JUnit3Suite.run(JUnit3Suite.scala:321)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:601)
	at org.jetbrains.plugins.scala.testingSupport.scalaTest.ScalaTestRunner.runSingleTest(ScalaTestRunner.java:245)
	at org.jetbrains.plugins.scala.testingSupport.scalaTest.ScalaTestRunner.runScalaTest1(ScalaTestRunner.java:213)
	at org.jetbrains.plugins.scala.testingSupport.scalaTest.ScalaTestRunner.main(ScalaTestRunner.java:30)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:601)
	at com.intellij.rt.execution.application.AppMain.main(AppMain.java:134)
{code}
This failure appears like it's intermittent when the ProducerFailureHandlingTest is run as whole because it hides the timing issue involved in the testCannotSendToInternalTopic test method. Running only that testCannotSendToInternalTopic test method (I did it from IntelliJ IDE) consistently reproduces this failure.

The real issue is that the initialization of the  \_\_consumer\_offset topic (being accessed in the testCannotSendToInternalTopic test method) is time consuming because that topic is backed by 50 partitions (default) and it takes a while for each of them to be assigned a leader and do other initialization. This times out the metadata fetch (3 seconds) being done by the producer during a send(), which causes the test method to fail.

I've a patch to fix that test method which I'll send shortly.


---

* [KAFKA-1867](https://issues.apache.org/jira/browse/KAFKA-1867) | *Major* | **liveBroker list not updated on a cluster with no topics**

Currently, when there is no topic in a cluster, the controller doesn't send any UpdateMetadataRequest to the broker when it starts up. As a result, the liveBroker list in metadataCache is empty. This means that we will return incorrect broker list in TopicMetatadataResponse.


---

* [KAFKA-1866](https://issues.apache.org/jira/browse/KAFKA-1866) | *Major* | **LogStartOffset gauge throws exceptions after log.delete()**

The LogStartOffset gauge does "logSegments.head.baseOffset", which throws NoSuchElementException on an empty list, which can occur after a delete() of the log. This makes life harder for custom MetricsReporters, since they have to deal with .value() possibly throwing an exception.

Locally we're dealing with this by having Log.delete() also call removeMetric on all the gauges. That also has the benefit of not having a bunch of metrics floating around for logs that the broker is not actually handling.


---

* [KAFKA-1865](https://issues.apache.org/jira/browse/KAFKA-1865) | *Major* | **Add a flush() call to the new producer API**

The postconditions of this would be that any record enqueued prior to flush() would have completed being sent (either successfully or not).

An open question is whether you can continue sending new records while this call is executing (on other threads).

We should only do this if it doesn't add inefficiencies for people who don't use it.


---

* [KAFKA-1856](https://issues.apache.org/jira/browse/KAFKA-1856) | *Major* | **Add PreCommit Patch Testing**

h1. Kafka PreCommit Patch Testing - *Don't wait for it to break*

h2. Motivation
*With great power comes great responsibility* - Uncle Ben. As Kafka user list is growing, mechanism to ensure quality of the product is required. Quality becomes hard to measure and maintain in an open source project, because of a wide community of contributors. Luckily, Kafka is not the first open source project and can benefit from learnings of prior projects.

PreCommit tests are the tests that are run for each patch that gets attached to an open JIRA. Based on tests results, test execution framework, test bot, +1 or -1 the patch. Having PreCommit tests take the load off committers to look at or test each patch.

h2. Tests in Kafka
h3. Unit and Integraiton Tests
[Unit and Integration tests|https://cwiki.apache.org/confluence/display/KAFKA/Kafka+0.9+Unit+and+Integration+Tests] are cardinal to help contributors to avoid breaking existing functionalities while adding new functionalities or fixing older ones. These tests, atleast the ones relevant to the changes, must be run by contributors before attaching a patch to a JIRA.

h3. System Tests
[System tests|https://cwiki.apache.org/confluence/display/KAFKA/Kafka+System+Tests] are much wider tests that, unlike unit tests, focus on end-to-end scenarios and not some specific method or class.

h2. Apache PreCommit tests
Apache provides a mechanism to automatically build a project and run a series of tests whenever a patch is uploaded to a JIRA. Based on test execution, the test framework will comment with a +1 or -1 on the JIRA.

You can read more about the framework here:
http://wiki.apache.org/general/PreCommitBuilds

h2. Plan
# Create a test-patch.py script (similar to the one used in Flume, Sqoop and other projects) that will take a jira as a parameter, apply on the appropriate branch, build the project, run tests and report results. This script should be committed into the Kafka code-base. To begin with, this will only run unit tests. We can add code sanity checks, system\_tests, etc in the future.
# Create a jenkins job for running the test (as described in http://wiki.apache.org/general/PreCommitBuilds) and validate that it works manually. This must be done by a committer with Jenkins access.
# Ask someone with access to https://builds.apache.org/job/PreCommit-Admin/ to add Kafka to the list of projects PreCommit-Admin triggers.


---

* [KAFKA-1854](https://issues.apache.org/jira/browse/KAFKA-1854) | *Major* | **Allow the JIRA username and password to be prompted during patch submission**

The current patch submission process involves using the kafka-patch-review.py python script which expects a jira.ini file to contain the user's username and password for JIRA authentication. I'm one of those who doesn't like storing passwords in files :) It would be good to (optionally) allow the username/password to be prompted by the patch submission script.

I've a patch which I can submit for this enhancement.


---

* [KAFKA-1852](https://issues.apache.org/jira/browse/KAFKA-1852) | *Major* | **OffsetCommitRequest can commit offset on unknown topic**

Currently, we allow an offset to be committed to Kafka, even when the topic/partition for the offset doesn't exist. We probably should disallow that and send an error back in that case.


---

* [KAFKA-1848](https://issues.apache.org/jira/browse/KAFKA-1848) | *Major* | **Checking shutdown during each iteration of ZookeeperConsumerConnector**

In ZookeeperConsumerConnector the syncedRebalance() method checks the isShuttingDown flag before it triggers a rebalance. However, it does not recheck the same value between successive retries which is possible if the consumer is shutting down.

This acquires the rebalanceLock and blocks shutdown from completing.


---

* [KAFKA-1845](https://issues.apache.org/jira/browse/KAFKA-1845) | *Major* | **KafkaConfig should use ConfigDef**

ConfigDef is already used for the new producer and for TopicConfig. 
Will be nice to standardize and use one configuration and validation library across the board.


---

* [KAFKA-1836](https://issues.apache.org/jira/browse/KAFKA-1836) | *Minor* | **metadata.fetch.timeout.ms set to zero blocks forever**

You can easily work around this by setting the timeout value to 1ms, but 0ms should mean 0ms or at least have the behavior documented.


---

* [KAFKA-1824](https://issues.apache.org/jira/browse/KAFKA-1824) | *Major* | **in ConsoleProducer - properties key.separator and parse.key no longer work**

Looks like the change in kafka-1711 breaks them accidentally.

reader.init is called with readerProps which is initialized with commandline properties as defaults.

the problem is that reader.init checks:
    if(props.containsKey("parse.key"))
and defaults don't return true in this case.


---

* [KAFKA-1818](https://issues.apache.org/jira/browse/KAFKA-1818) | *Trivial* | **Code cleanup in ReplicationUtils including unit test**

Code in getLeaderIsrAndEpochForPartition() and parseLeaderAndIsr() was essentially reimplementing the flatMap function on the Option type.  The attached patch refactors that code to more idiomatic Scala and provides a unit test over the affected code.


---

* [KAFKA-1815](https://issues.apache.org/jira/browse/KAFKA-1815) | *Minor* | **ServerShutdownTest fails in trunk.**

I ran into these failures consistently when trying to build Kafka locally:

kafka.server.ServerShutdownTest > testCleanShutdown FAILED
    java.lang.NullPointerException
        at kafka.server.ServerShutdownTest$$anonfun$verifyNonDaemonThreadsStatus$2.apply(ServerShutdownTest.scala:147)
        at kafka.server.ServerShutdownTest$$anonfun$verifyNonDaemonThreadsStatus$2.apply(ServerShutdownTest.scala:147)
        at scala.collection.TraversableOnce$$anonfun$count$1.apply(TraversableOnce.scala:114)
        at scala.collection.TraversableOnce$$anonfun$count$1.apply(TraversableOnce.scala:113)
        at scala.collection.IndexedSeqOptimized$class.foreach(IndexedSeqOptimized.scala:33)
        at scala.collection.mutable.ArrayOps$ofRef.foreach(ArrayOps.scala:105)
        at scala.collection.TraversableOnce$class.count(TraversableOnce.scala:113)
        at scala.collection.mutable.ArrayOps$ofRef.count(ArrayOps.scala:105)
        at kafka.server.ServerShutdownTest.verifyNonDaemonThreadsStatus(ServerShutdownTest.scala:147)
        at kafka.server.ServerShutdownTest.testCleanShutdown(ServerShutdownTest.scala:101)

kafka.server.ServerShutdownTest > testCleanShutdownWithDeleteTopicEnabled FAILED
    java.lang.NullPointerException
        at kafka.server.ServerShutdownTest$$anonfun$verifyNonDaemonThreadsStatus$2.apply(ServerShutdownTest.scala:147)
        at kafka.server.ServerShutdownTest$$anonfun$verifyNonDaemonThreadsStatus$2.apply(ServerShutdownTest.scala:147)
        at scala.collection.TraversableOnce$$anonfun$count$1.apply(TraversableOnce.scala:114)
        at scala.collection.TraversableOnce$$anonfun$count$1.apply(TraversableOnce.scala:113)
        at scala.collection.IndexedSeqOptimized$class.foreach(IndexedSeqOptimized.scala:33)
        at scala.collection.mutable.ArrayOps$ofRef.foreach(ArrayOps.scala:105)
        at scala.collection.TraversableOnce$class.count(TraversableOnce.scala:113)
        at scala.collection.mutable.ArrayOps$ofRef.count(ArrayOps.scala:105)
        at kafka.server.ServerShutdownTest.verifyNonDaemonThreadsStatus(ServerShutdownTest.scala:147)
        at kafka.server.ServerShutdownTest.testCleanShutdownWithDeleteTopicEnabled(ServerShutdownTest.scala:114)

kafka.server.ServerShutdownTest > testCleanShutdownAfterFailedStartup FAILED
    java.lang.NullPointerException
        at kafka.server.ServerShutdownTest$$anonfun$verifyNonDaemonThreadsStatus$2.apply(ServerShutdownTest.scala:147)
        at kafka.server.ServerShutdownTest$$anonfun$verifyNonDaemonThreadsStatus$2.apply(ServerShutdownTest.scala:147)
        at scala.collection.TraversableOnce$$anonfun$count$1.apply(TraversableOnce.scala:114)
        at scala.collection.TraversableOnce$$anonfun$count$1.apply(TraversableOnce.scala:113)
        at scala.collection.IndexedSeqOptimized$class.foreach(IndexedSeqOptimized.scala:33)
        at scala.collection.mutable.ArrayOps$ofRef.foreach(ArrayOps.scala:105)
        at scala.collection.TraversableOnce$class.count(TraversableOnce.scala:113)
        at scala.collection.mutable.ArrayOps$ofRef.count(ArrayOps.scala:105)
        at kafka.server.ServerShutdownTest.verifyNonDaemonThreadsStatus(ServerShutdownTest.scala:147)
        at kafka.server.ServerShutdownTest.testCleanShutdownAfterFailedStartup(ServerShutdownTest.scala:141)

It looks like Jenkins also had issues with these tests:

https://builds.apache.org/job/Kafka-trunk/351/console

I would like to provide a patch that fixes this.


---

* [KAFKA-1813](https://issues.apache.org/jira/browse/KAFKA-1813) | *Minor* | **Build fails for scala 2.9.2**

Currently, in trunk, the 2.9.2 build fails with the following error:

MirrorMaker.scala:507 overloaded method value commitOffsets with alternatives:
  (isAutoCommit: Boolean,topicPartitionOffsets: scala.collection.immutable.Map[kafka.common.TopicAndPartition,kafka.common.OffsetAndMetadata])Unit <and>
  (isAutoCommit: Boolean)Unit <and>
  => Unit
 cannot be applied to (isAutoCommit: Boolean, scala.collection.immutable.Map[kafka.common.TopicAndPartition,kafka.common.OffsetAndMetadata])
        connector.commitOffsets(isAutoCommit = false, offsetsToCommit)

It looks like the 2.9.2 compiler cannot resolve an overloaded method when mixing named and ordered parameters.

I ran into this when I cloned the repo and ran ./gradlew test.


---

* [KAFKA-1812](https://issues.apache.org/jira/browse/KAFKA-1812) | *Minor* | ** Allow IpV6 in configuration with parseCsvMap**

The current implementation of parseCsvMap in Utils expects k:v,k:v. This modifies that function to accept a string with multiple ":" characters and splitting on the last occurrence per pair. 

This limitation is noted in the Reviewboard comments for KAFKA-1512


---

* [KAFKA-1809](https://issues.apache.org/jira/browse/KAFKA-1809) | *Major* | **Refactor brokers to allow listening on multiple ports and IPs**

The goal is to eventually support different security mechanisms on different ports. 
Currently brokers are defined as host+port pair, and this definition exists throughout the code-base, therefore some refactoring is needed to support multiple ports for a single broker.

The detailed design is here: https://cwiki.apache.org/confluence/display/KAFKA/Multiple+Listeners+for+Kafka+Brokers


---

* [KAFKA-1807](https://issues.apache.org/jira/browse/KAFKA-1807) | *Minor* | **Improve accuracy of ProducerPerformance target throughput**

The code in ProducerPerformance that tries to match a target throughput is very inaccurate because it doesn't account for time spent sending messages. Since we have to get the current time to timestamp the messages, we can be much more accurate by computing the current rate over the entire run and only add to the sleep deficit if we're above the target rate.


---

* [KAFKA-1803](https://issues.apache.org/jira/browse/KAFKA-1803) | *Major* | **UncleanLeaderElectionEnableProp in LogConfig should be of boolean**

Now that KAFKA-1798 is fixed, we should define UncleanLeaderElectionEnableProp as a boolean, instead of String in LogConfig and get rid of the customized validation for boolean.


---

* [KAFKA-1801](https://issues.apache.org/jira/browse/KAFKA-1801) | *Trivial* | **Remove non-functional variable definition in log4j.properties**

In log4j.properties, a property kafka.logs.dir is defined. However, modifying this property has no effect because log4j will always use the system property defined in kafka-run-class.sh before using the locally defined property in log4j.properties. Therefore, its probably less confusing to simply remove this property from here.

See http://logging.apache.org/log4j/1.2/apidocs/org/apache/log4j/PropertyConfigurator.html for the property search order (system property first, locally defined property second).

An alternative solution: remove the system property from kafka-run-class.sh and keep the one here.


---

* [KAFKA-1798](https://issues.apache.org/jira/browse/KAFKA-1798) | *Major* | **ConfigDef.parseType() should throw exception on invalid boolean value**

ConfigDef.parseType() currently uses Boolean.parseBoolean(trimmed) to parse boolean value from a String. However, it simply returns false for anything that's not "true". It would be better if we throw an exception if the input string is not either "true" or "false".


---

* [KAFKA-1762](https://issues.apache.org/jira/browse/KAFKA-1762) | *Major* | **Update max-inflight-request doc string**

The new Producer client introduces a config for the max # of inFlight messages. When it is set > 1 on MirrorMaker, however, there is a risk for data loss even with KAFKA-1650 because the offsets recorded in the MM's offset map is no longer continuous.

Another issue is that when this value is set > 1, there is a risk of message re-ordering in the producer

Changes:
    1. Set max # of inFlight messages = 1 in MM
    2. Leave comments explaining what the risks are of changing


---

* [KAFKA-1760](https://issues.apache.org/jira/browse/KAFKA-1760) | *Major* | **Implement new consumer client**

Implement a consumer client.


---

* [KAFKA-1757](https://issues.apache.org/jira/browse/KAFKA-1757) | *Minor* | **Can not delete Topic index on Windows**

When running the Kafka 0.8.2-Beta (Scala 2.10) on Windows, an attempt to delete the Topic throwed an error:

ERROR [KafkaApi-1] error when handling request Name: StopReplicaRequest; Version: 0; CorrelationId: 38; ClientId: ; DeletePartitions: true; ControllerId: 0; ControllerEpoch: 3; Partitions: [test,0] (kafka.server.KafkaApis)
kafka.common.KafkaStorageException: Delete of index 00000000000000000000.index failed.
        at kafka.log.LogSegment.delete(LogSegment.scala:283)
        at kafka.log.Log$$anonfun$delete$1.apply(Log.scala:608)
        at kafka.log.Log$$anonfun$delete$1.apply(Log.scala:608)
        at scala.collection.Iterator$class.foreach(Iterator.scala:727)
        at scala.collection.AbstractIterator.foreach(Iterator.scala:1157)
        at scala.collection.IterableLike$class.foreach(IterableLike.scala:72)
        at scala.collection.AbstractIterable.foreach(Iterable.scala:54)
        at kafka.log.Log.delete(Log.scala:608)
        at kafka.log.LogManager.deleteLog(LogManager.scala:375)
        at kafka.cluster.Partition$$anonfun$delete$1.apply$mcV$sp(Partition.scala:144)
        at kafka.cluster.Partition$$anonfun$delete$1.apply(Partition.scala:139)
        at kafka.cluster.Partition$$anonfun$delete$1.apply(Partition.scala:139)
        at kafka.utils.Utils$.inLock(Utils.scala:535)
        at kafka.utils.Utils$.inWriteLock(Utils.scala:543)
        at kafka.cluster.Partition.delete(Partition.scala:139)
        at kafka.server.ReplicaManager.stopReplica(ReplicaManager.scala:158)
        at kafka.server.ReplicaManager$$anonfun$stopReplicas$3.apply(ReplicaManager.scala:191)
        at kafka.server.ReplicaManager$$anonfun$stopReplicas$3.apply(ReplicaManager.scala:190)
        at scala.collection.immutable.Set$Set1.foreach(Set.scala:74)
        at kafka.server.ReplicaManager.stopReplicas(ReplicaManager.scala:190)
        at kafka.server.KafkaApis.handleStopReplicaRequest(KafkaApis.scala:96)
        at kafka.server.KafkaApis.handle(KafkaApis.scala:59)
        at kafka.server.KafkaRequestHandler.run(KafkaRequestHandler.scala:59)
        at java.lang.Thread.run(Thread.java:744)



When I have investigated the issue I figured out that the index file (in my environment it was C:\tmp\kafka-logs\00000000-0000-0000-0000-000000000014-0\00000000000000000000.index) was locked by the kafka process and the OS did not allow to delete that file.

I tried to fix the problem in source codes and when I added close() method call into LogSegment.delete(), the Topic deletion started to work.

I will add here (not sure how to upload the file during issue creation) a diff with the changes I have made so You can take a look on that whether it is reasonable or not. It would be perfect if it could make it into the product...

In the end I would like to say that on Linux the deletion works just fine...


---

* [KAFKA-1747](https://issues.apache.org/jira/browse/KAFKA-1747) | *Major* | **TestcaseEnv improperly shares state between instances**

TestcaseEnv in system tests uses class variables instead of instance variables for a bunch of state. This causes the data to persist between tests. In some cases this can cause tests to break (e.g. there will be state from a service running in a previous test that doesn't exist in the current test; trying to look up state about that service raises an exception or produces invalid data).


---

* [KAFKA-1746](https://issues.apache.org/jira/browse/KAFKA-1746) | *Major* | **System tests don't handle errors well**

The system test scripts don't handle errors well. A couple of key issues:

* Unexpected exceptions during tests are just ignored and the tests appear to be successful in the reports.
* The scripts exit code is always 0, even if tests fail.
* Almost no subprocess calls are checked. In a lot of cases this is ok, and sometimes it's not possible (e.g. after starting a long-running remote process), but in some cases such as calls to DumpLogSegments, the tests can miss that the tools is exiting with an exception and the test appears to be successful even though no data was verified.


---

* [KAFKA-1739](https://issues.apache.org/jira/browse/KAFKA-1739) | *Major* | **Remove testComplexCompressDecompress in MessageCompressionTest**

As discussed on the mailing list, we would not support nested compression in Kafka, and hence could remove this test case.


---

* [KAFKA-1733](https://issues.apache.org/jira/browse/KAFKA-1733) | *Major* | **Producer.send will block indeterminately when broker is unavailable.**

This is a follow up to the conversation here:

https://mail-archives.apache.org/mod\_mbox/kafka-dev/201409.mbox/%3CCAOG\_4QYMoEJHKbo0N31+A-UjX0z5unSiSD5WbrmN-XtX7giP-Q@mail.gmail.com%3E

During ClientUtils.fetchTopicMetadata, if the broker is unavailable, socket.connect will block indeterminately. Any retry policy (message.send.max.retries) further increases the time spent waiting for the socket to connect.

The root fix is to add a connection timeout value to the BlockingChannel's socket configuration, like so:

{noformat}
-channel.socket.connect(new InetSocketAddress(host, port))
+channel.socket.connect(new InetSocketAddress(host, port), connectTimeoutMs)
{noformat}

The simplest thing to do here would be to have a constant, default value that would be applied to every socket configuration. 

Is that acceptable?


---

* [KAFKA-1727](https://issues.apache.org/jira/browse/KAFKA-1727) | *Trivial* | **Fix comment about message format**

The comment in Message.scala says the value of "magic" identifier is 2,

 bq. 2. 1 byte "magic" identifier to allow format changes, value is 2 currently

but the actual current "magic" value is 0.

{code}
  /**
   * The current "magic" value
   */
  val CurrentMagicValue: Byte = 0
{code}


---

* [KAFKA-1724](https://issues.apache.org/jira/browse/KAFKA-1724) | *Major* | **Errors after reboot in single node setup**

In a single node setup, after reboot, Kafka logs show the following:
{code}
[2014-10-22 16:37:22,206] INFO [Controller 0]: Controller starting up (kafka.controller.KafkaController)
[2014-10-22 16:37:22,419] INFO [Controller 0]: Controller startup complete (kafka.controller.KafkaController)
[2014-10-22 16:37:22,554] INFO conflict in /brokers/ids/0 data: {"jmx\_port":-1,"timestamp":"1413995842465","host":"ip-10-91-142-54.eu-west-1.compute.internal","version":1,"port":9092} stored data: {"jmx\_port":-1,"timestamp":"1413994171579","host":"ip-10-91-142-54.eu-west-1.compute.internal","version":1,"port":9092} (kafka.utils.ZkUtils$)
[2014-10-22 16:37:22,736] INFO I wrote this conflicted ephemeral node [{"jmx\_port":-1,"timestamp":"1413995842465","host":"ip-10-91-142-54.eu-west-1.compute.internal","version":1,"port":9092}] at /brokers/ids/0 a while back in a different session, hence I will backoff for this node to be deleted by Zookeeper and retry (kafka.utils.ZkUtils$)
[2014-10-22 16:37:25,010] ERROR Error handling event ZkEvent[Data of /controller changed sent to kafka.server.ZookeeperLeaderElector$LeaderChangeListener@a6af882] (org.I0Itec.zkclient.ZkEventThread)
java.lang.IllegalStateException: Kafka scheduler has not been started
        at kafka.utils.KafkaScheduler.ensureStarted(KafkaScheduler.scala:114)
        at kafka.utils.KafkaScheduler.shutdown(KafkaScheduler.scala:86)
        at kafka.controller.KafkaController.onControllerResignation(KafkaController.scala:350)
        at kafka.controller.KafkaController$$anonfun$2.apply$mcV$sp(KafkaController.scala:162)
        at kafka.server.ZookeeperLeaderElector$LeaderChangeListener$$anonfun$handleDataDeleted$1.apply$mcZ$sp(ZookeeperLeaderElector.scala:138)
        at kafka.server.ZookeeperLeaderElector$LeaderChangeListener$$anonfun$handleDataDeleted$1.apply(ZookeeperLeaderElector.scala:134)
        at kafka.server.ZookeeperLeaderElector$LeaderChangeListener$$anonfun$handleDataDeleted$1.apply(ZookeeperLeaderElector.scala:134)
        at kafka.utils.Utils$.inLock(Utils.scala:535)
        at kafka.server.ZookeeperLeaderElector$LeaderChangeListener.handleDataDeleted(ZookeeperLeaderElector.scala:134)
        at org.I0Itec.zkclient.ZkClient$6.run(ZkClient.java:549)
        at org.I0Itec.zkclient.ZkEventThread.run(ZkEventThread.java:71)
[2014-10-22 16:37:28,757] INFO Registered broker 0 at path /brokers/ids/0 with address ip-10-91-142-54.eu-west-1.compute.internal:9092. (kafka.utils.ZkUtils$)
[2014-10-22 16:37:28,849] INFO [Kafka Server 0], started (kafka.server.KafkaServer)
[2014-10-22 16:38:56,718] INFO Closing socket connection to /127.0.0.1. (kafka.network.Processor)
[2014-10-22 16:38:56,850] INFO Closing socket connection to /127.0.0.1. (kafka.network.Processor)
[2014-10-22 16:38:56,985] INFO Closing socket connection to /127.0.0.1. (kafka.network.Processor)
{code}
The last log line repeats forever and is correlated with errors on the app side.
Restarting Kafka fixes the errors.

Steps to reproduce (with help from the mailing list):
# start zookeeper
# start kafka-broker
# create topic or start a producer writing to a topic
# stop zookeeper
# stop kafka-broker( kafka broker shutdown goes into  WARN Session
0x14938d9dc010001 for server null, unexpected error, closing socket connection and attempting reconnect (org.apache.zookeeper.ClientCnxn) java.net.ConnectException: Connection refused)
# kill -9 kafka-broker
# restart zookeeper and than kafka-broker leads into the the error above


---

* [KAFKA-1711](https://issues.apache.org/jira/browse/KAFKA-1711) | *Major* | **WARN Property topic is not valid when running console producer**

bin/kafka-console-producer.sh --broker-list localhost:9092 --topic test 
[2014-10-17 09:54:23,984] WARN Property topic is not valid (kafka.utils.VerifiableProperties)

It would be good if we can get rid of the warning.


---

* [KAFKA-1702](https://issues.apache.org/jira/browse/KAFKA-1702) | *Major* | **Messages silently Lost by producer**


Hello,

we lost millions of messages because of this {{try/catch}} in  the producer {{DefaultEventHandler}}:
https://github.com/apache/kafka/blob/0.8.1/core/src/main/scala/kafka/producer/async/DefaultEventHandler.scala#L114-L116

If a Throwable is caught by this {{try/catch}}, the retry policy will have no effect and all yet-to-be-sent messages are lost (the error will break the loop over the broker list).
This issue is very hard to detect because: the producer (async or sync) cannot even catch the error, and *all* the metrics are updated as if everything was fine.

Only the abnormal drop in the producers network I/O, or the incoming message rate on the brokers; or the alerting on errors in producer logs could have revealed the issue. 

This behavior was introduced by KAFKA-300. I can't see a good reason for it, so here is a patch that will let the retry-policy do its job when such a {{Throwable}} occurs.

Thanks in advance for your help.

Alexis

ps: you might wonder how could this {{try/catch}} ever caught something? {{DefaultEventHandler#groupMessagesToSet}} looks so harmless. 

Here are the details:
We use Snappy compression. When the native snappy library is not installed on the host, Snappy, during the initialization of class {{org.xerial.snappy.Snappy}}  will [write a C library|https://github.com/xerial/snappy-java/blob/1.1.0/src/main/java/org/xerial/snappy/SnappyLoader.java#L312] in the JVM temp directory {{java.io.tmpdir}}.

In our scenario, {{java.io.tmpdir}} was a subdirectory of {{/tmp}}. After an instance reboot (thank you [AWS|https://twitter.com/hashtag/AWSReboot?src=hash]!), the JVM temp directory was removed. The JVM was then running with a non-existing temp dir. Snappy class would be impossible to initialize and the following message would be silently logged:

{code}
ERROR [2014-10-07 22:23:56,530] kafka.producer.async.DefaultEventHandler: Failed to send messages
! java.lang.NoClassDefFoundError: Could not initialize class org.xerial.snappy.Snappy
{code}


---

* [KAFKA-1700](https://issues.apache.org/jira/browse/KAFKA-1700) | *Minor* | **examples directory - README and shell scripts are out of date**

sbt build files were removed during resolution of KAFKA-1254, so the README under the examples directory should no longer make reference to sbt.

Also, the paths added to CLASSPATH variable in the example shell script are no longer correct.


---

* [KAFKA-1698](https://issues.apache.org/jira/browse/KAFKA-1698) | *Major* | **Validator.ensureValid() only validates default config value**

We should use it to validate the actual configured value.


---

* [KAFKA-1697](https://issues.apache.org/jira/browse/KAFKA-1697) | *Major* | **remove code related to ack\>1 on the broker**

We removed the ack>1 support from the producer client in kafka-1555. We can completely remove the code in the broker that supports ack>1.

Also, we probably want to make NotEnoughReplicasAfterAppend a non-retriable exception and let the client decide what to do.


---

* [KAFKA-1668](https://issues.apache.org/jira/browse/KAFKA-1668) | *Minor* | **TopicCommand doesn't warn if --topic argument doesn't match any topics**

Running {{kafka-topics.sh --alter}} with an invalid {{--topic}} argument produces no output and exits with 0, indicating success.

{code}
$ bin/kafka-topics.sh --topic does-not-exist --alter --config invalid=xxx --zookeeper zkhost:2181
$ echo $?
0
{code}

An invalid topic name or a regular expression that matches 0 topics should at least print a warning.


---

* [KAFKA-1667](https://issues.apache.org/jira/browse/KAFKA-1667) | *Major* | ** topic-level configuration not validated**

I was able to set the configuration for a topic to these invalid values:

{code}
Topic:topic-config-test  PartitionCount:1        ReplicationFactor:2     Configs:min.cleanable.dirty.ratio=-30.2,segment.bytes=-1,retention.ms=-12,cleanup.policy=lol
{code}

It seems that the values are saved as long as they are the correct type, but are not validated like the corresponding broker-level properties.


---

* [KAFKA-1661](https://issues.apache.org/jira/browse/KAFKA-1661) | *Trivial* | **Move MockConsumer and MockProducer from src/main to src/test**

The MockConsumer and MockProducer are currently in src/main although they belong in src/test.


---

* [KAFKA-1654](https://issues.apache.org/jira/browse/KAFKA-1654) | *Major* | **Provide a way to override server configuration from command line**

I've been recently playing with Kafka and I found the current way of server configuration quite inflexible. All the configuration options have to be inside a properties file and there is no way how they can be overridden for execution.  In order to temporarily change one property I had to copy the config file and change the property there. Hence, I'm wondering if people would be open to provide a way how to specify and override the configs from the command line when starting Kafka?

Something like:

{code}
./bin/kafka-server-start.sh -Dmy.cool.property=X kafka.properties
{code}

or 

{code}
./bin/kafka-server-start.sh --set my.cool.property=X kafka.properties
{code}

I'm more than happy to take a stab at it, but I would like to see if there is an interest for such capability?


---

* [KAFKA-1650](https://issues.apache.org/jira/browse/KAFKA-1650) | *Major* | **Mirror Maker could lose data on unclean shutdown.**

Currently if mirror maker got shutdown uncleanly, the data in the data channel and buffer could potentially be lost. With the new producer's callback, this issue could be solved.


---

* [KAFKA-1648](https://issues.apache.org/jira/browse/KAFKA-1648) | *Major* | **Round robin consumer balance throws an NPE when there are no topics**

If you use the roundrobin rebalance method with a wildcard consumer, and there are no topics in the cluster, rebalance throws a NullPointerException in the consumer and fails. It retries the rebalance, but will continue to throw the NPE.

2014/09/23 17:51:16.147 [ZookeeperConsumerConnector] [kafka-audit\_lva1-app0007.corp-1411494404908-4e620544], Cleared all relevant queues for this fetcher
2014/09/23 17:51:16.147 [ZookeeperConsumerConnector] [kafka-audit\_lva1-app0007.corp-1411494404908-4e620544], Cleared the data chunks in all the consumer message iterators
2014/09/23 17:51:16.148 [ZookeeperConsumerConnector] [kafka-audit\_lva1-app0007.corp-1411494404908-4e620544], Committing all offsets after clearing the fetcher queues
2014/09/23 17:51:46.148 [ZookeeperConsumerConnector] [kafka-audit\_lva1-app0007.corp-1411494404908-4e620544], begin rebalancing consumer kafka-audit\_lva1-app0007.corp-1411494404908-4e620544 try #0
2014/09/23 17:51:46.148 ERROR [OffspringServletRuntime] [main] [kafka-console-audit] [] Boot listener com.linkedin.kafkaconsoleaudit.KafkaConsoleAuditBootListener failed
kafka.common.ConsumerRebalanceFailedException: kafka-audit\_lva1-app0007.corp-1411494404908-4e620544 can't rebalance after 10 retries
	at kafka.consumer.ZookeeperConsumerConnector$ZKRebalancerListener.syncedRebalance(ZookeeperConsumerConnector.scala:630)
	at kafka.consumer.ZookeeperConsumerConnector.kafka$consumer$ZookeeperConsumerConnector$$reinitializeConsumer(ZookeeperConsumerConnector.scala:897)
	at kafka.consumer.ZookeeperConsumerConnector$WildcardStreamsHandler.<init>(ZookeeperConsumerConnector.scala:931)
	at kafka.consumer.ZookeeperConsumerConnector.createMessageStreamsByFilter(ZookeeperConsumerConnector.scala:159)
	at kafka.javaapi.consumer.ZookeeperConsumerConnector.createMessageStreamsByFilter(ZookeeperConsumerConnector.scala:101)
	at com.linkedin.tracker.consumer.TrackingConsumerImpl.initWildcardIterators(TrackingConsumerImpl.java:88)
	at com.linkedin.tracker.consumer.TrackingConsumerImpl.getWildcardIterators(TrackingConsumerImpl.java:116)
	at com.linkedin.kafkaconsoleaudit.KafkaConsoleAudit.createAuditThreads(KafkaConsoleAudit.java:59)
	at com.linkedin.kafkaconsoleaudit.KafkaConsoleAudit.initializeAudit(KafkaConsoleAudit.java:50)
	at com.linkedin.kafkaconsoleaudit.KafkaConsoleAuditFactory.createInstance(KafkaConsoleAuditFactory.java:125)
	at com.linkedin.kafkaconsoleaudit.KafkaConsoleAuditFactory.createInstance(KafkaConsoleAuditFactory.java:20)
	at com.linkedin.util.factory.SimpleSingletonFactory.createInstance(SimpleSingletonFactory.java:20)
	at com.linkedin.util.factory.SimpleSingletonFactory.createInstance(SimpleSingletonFactory.java:14)
	at com.linkedin.util.factory.Generator.doGetBean(Generator.java:337)
	at com.linkedin.util.factory.Generator.getBean(Generator.java:270)
	at com.linkedin.kafkaconsoleaudit.KafkaConsoleAuditBootListener.onBoot(KafkaConsoleAuditBootListener.java:16)
	at com.linkedin.offspring.servlet.OffspringServletRuntime.startGenerator(OffspringServletRuntime.java:147)
	at com.linkedin.offspring.servlet.OffspringServletRuntime.start(OffspringServletRuntime.java:73)
	at com.linkedin.offspring.servlet.OffspringServletContextListener.contextInitialized(OffspringServletContextListener.java:28)
	at org.eclipse.jetty.server.handler.ContextHandler.callContextInitialized(ContextHandler.java:771)
	at org.eclipse.jetty.servlet.ServletContextHandler.callContextInitialized(ServletContextHandler.java:424)
	at org.eclipse.jetty.server.handler.ContextHandler.startContext(ContextHandler.java:763)
	at org.eclipse.jetty.servlet.ServletContextHandler.startContext(ServletContextHandler.java:249)
	at org.eclipse.jetty.webapp.WebAppContext.startContext(WebAppContext.java:1250)
	at org.eclipse.jetty.server.handler.ContextHandler.doStart(ContextHandler.java:706)
	at org.eclipse.jetty.webapp.WebAppContext.doStart(WebAppContext.java:492)
	at org.eclipse.jetty.util.component.AbstractLifeCycle.start(AbstractLifeCycle.java:64)
	at com.linkedin.emweb.ContextBasedHandlerImpl.doStart(ContextBasedHandlerImpl.java:105)
	at org.eclipse.jetty.util.component.AbstractLifeCycle.start(AbstractLifeCycle.java:64)
	at com.linkedin.emweb.WebappDeployerImpl.start(WebappDeployerImpl.java:333)
	at com.linkedin.emweb.WebappDeployerImpl.deploy(WebappDeployerImpl.java:187)
	at com.linkedin.emweb.StateKeeperWebappDeployer.deploy(StateKeeperWebappDeployer.java:75)
	at com.linkedin.emweb.StateKeeperWebappDeployer.restore(StateKeeperWebappDeployer.java:62)
	at com.linkedin.emweb.WebappRunner.restoreServerState(WebappRunner.java:171)
	at com.linkedin.emweb.BaseRunner.start(BaseRunner.java:96)
	at com.linkedin.spring.cmdline.ServerCmdLineApp.start(ServerCmdLineApp.java:86)
	at com.linkedin.spring.cmdline.ServerCmdLineApp.doRun(ServerCmdLineApp.java:102)
	at com.linkedin.spring.cmdline.CmdLineAppRunner.run(CmdLineAppRunner.java:246)
	at com.linkedin.spring.cmdline.CmdLineAppRunner.main(CmdLineAppRunner.java:480)

(note - the com.linkedin stuff in the stack trace is from the container we run our applications in and does not affect the operation of the rebalance)


---

* [KAFKA-1644](https://issues.apache.org/jira/browse/KAFKA-1644) | *Major* | **Inherit FetchResponse from RequestOrResponse**

Unlike all other Kafka API responses {{FetchResponse}} is not a subclass of RequestOrResponse, which requires handling it as a special case while processing responses.


---

* [KAFKA-1641](https://issues.apache.org/jira/browse/KAFKA-1641) | *Major* | **Log cleaner exits if last cleaned offset is lower than earliest offset**

Encountered this recently: the log cleaner exited a while ago (I think because the topic had compressed messages). That issue was subsequently addressed by having the producer only send uncompressed. However, on a subsequent restart of the broker we see this:

In this scenario I think it is reasonable to just emit a warning and have the cleaner round up its first dirty offset to the base offset of the first segment.

{code}
[kafka-server] [] [kafka-log-cleaner-thread-0], Error due to 
java.lang.IllegalArgumentException: requirement failed: Last clean offset is 54770438 but segment base offset is 382844024 for log testtopic-0.
        at scala.Predef$.require(Predef.scala:145)
        at kafka.log.Cleaner.buildOffsetMap(LogCleaner.scala:491)
        at kafka.log.Cleaner.clean(LogCleaner.scala:288)
        at kafka.log.LogCleaner$CleanerThread.cleanOrSleep(LogCleaner.scala:202)
        at kafka.log.LogCleaner$CleanerThread.doWork(LogCleaner.scala:187)
        at kafka.utils.ShutdownableThread.run(ShutdownableThread.scala:51)
{code}


---

* [KAFKA-1634](https://issues.apache.org/jira/browse/KAFKA-1634) | *Blocker* | **Improve semantics of timestamp in OffsetCommitRequests and update documentation**

From the mailing list -

following up on this -- I think the online API docs for OffsetCommitRequest
still incorrectly refer to client-side timestamps:

https://cwiki.apache.org/confluence/display/KAFKA/A+Guide+To+The+Kafka+Protocol#AGuideToTheKafkaProtocol-OffsetCommitRequest

Wasn't that removed and now always handled server-side now?  Would one of
the devs mind updating the API spec wiki?


---

* [KAFKA-1583](https://issues.apache.org/jira/browse/KAFKA-1583) | *Major* | **Kafka API Refactoring**

This is the next step of KAFKA-1430. Details can be found at this page:

https://cwiki.apache.org/confluence/display/KAFKA/Kafka+API+Refactoring


---

* [KAFKA-1546](https://issues.apache.org/jira/browse/KAFKA-1546) | *Major* | **Automate replica lag tuning**

Currently, there is no good way to tune the replica lag configs to automatically account for high and low volume topics on the same cluster. 
For the low-volume topic it will take a very long time to detect a lagging
replica, and for the high-volume topic it will have false-positives.
One approach to making this easier would be to have the configuration
be something like replica.lag.max.ms and translate this into a number
of messages dynamically based on the throughput of the partition.


---

* [KAFKA-1517](https://issues.apache.org/jira/browse/KAFKA-1517) | *Trivial* | **Messages is a required argument to Producer Performance Test**

When running the producer performance test without providing a messages argument, you get an error:

{noformat}
$bin/kafka-producer-perf-test.sh --topics mirrormirror --broker-list kafka-dc21:9092
Missing required argument "[messages]"

Option                                  Description
------                                  -----------
......
--messages <Long: count>                The number of messages to send or
                                          consume (default:
                                          9223372036854775807)
{noformat}

However the [shell command documentation|https://github.com/apache/kafka/blob/c66e408b244de52f1c5c5bbd7627aa1f028f9a87/perf/src/main/scala/kafka/perf/PerfConfig.scala#L25] doesn't say that this is required and implies that [2^63-1|http://en.wikipedia.org/wiki/9223372036854775807] (Long.MaxValue) messages will be sent. It should probably look like the [ConsoleProducer|https://github.com/apache/kafka/blob/c66e408b244de52f1c5c5bbd7627aa1f028f9a87/core/src/main/scala/kafka/producer/ConsoleProducer.scala#L32] and prefix the documentation with REQUIRED. Or should we make this a non-required argument and set the default value to something sane like 100,000 messages.

Which option is preferable for this?


---

* [KAFKA-1499](https://issues.apache.org/jira/browse/KAFKA-1499) | *Major* | **Broker-side compression configuration**

A given topic can have messages in mixed compression codecs. i.e., it can
also have a mix of uncompressed/compressed messages.

It will be useful to support a broker-side configuration to recompress
messages to a specific compression codec. i.e., all messages (for all
topics) on the broker will be compressed to this codec. We could have
per-topic overrides as well.


---

* [KAFKA-1481](https://issues.apache.org/jira/browse/KAFKA-1481) | *Critical* | **Stop using dashes AND underscores as separators in MBean names**

MBeans should not use dashes or underscores as separators because these characters are allowed in hostnames, topics, group and consumer IDs, etc., and these are embedded in MBeans names making it impossible to parse out individual bits from MBeans.

Perhaps a pipe character should be used to avoid the conflict. 

This looks like a major blocker because it means nobody can write Kafka 0.8.x monitoring tools unless they are doing it for themselves AND do not use dashes AND do not use underscores.

See: http://search-hadoop.com/m/4TaT4lonIW


---

* [KAFKA-1476](https://issues.apache.org/jira/browse/KAFKA-1476) | *Major* | **Get a list of consumer groups**

It would be useful to have a way to get a list of consumer groups currently active via some tool/script that ships with kafka. This would be helpful so that the system tools can be explored more easily.

For example, when running the ConsumerOffsetChecker, it requires a group option

bin/kafka-run-class.sh kafka.tools.ConsumerOffsetChecker --topic test --group ?

But, when just getting started with kafka, using the console producer and consumer, it is not clear what value to use for the group option.  If a list of consumer groups could be listed, then it would be clear what value to use.

Background:
http://mail-archives.apache.org/mod\_mbox/kafka-users/201405.mbox/%3cCAOq\_b1w=SLZe5jRNAkxvaK0Gu9cTDKPaZaK1G4DygVqZbSgUyg@mail.gmail.com%3e


---

* [KAFKA-1461](https://issues.apache.org/jira/browse/KAFKA-1461) | *Major* | **Replica fetcher thread does not implement any back-off behavior**

The current replica fetcher thread will retry in a tight loop if any error occurs during the fetch call. For example, we've seen cases where the fetch continuously throws a connection refused exception leading to several replica fetcher threads that spin in a pretty tight loop.

To a much lesser degree this is also an issue in the consumer fetcher thread, although the fact that erroring partitions are removed so a leader can be re-discovered helps some.


---

* [KAFKA-1374](https://issues.apache.org/jira/browse/KAFKA-1374) | *Major* | **LogCleaner (compaction) does not support compressed topics**

This is a known issue, but opening a ticket to track.

If you try to compact a topic that has compressed messages you will run into
various exceptions - typically because during iteration we advance the
position based on the decompressed size of the message. I have a bunch of
stack traces, but it should be straightforward to reproduce.


---

* [KAFKA-1173](https://issues.apache.org/jira/browse/KAFKA-1173) | *Major* | **Using Vagrant to get up and running with Apache Kafka**

Vagrant has been getting a lot of pickup in the tech communities.  I have found it very useful for development and testing and working with a few clients now using it to help virtualize their environments in repeatable ways.

Using Vagrant to get up and running.

For 0.8.0 I have a patch on github https://github.com/stealthly/kafka

1) Install Vagrant [http://www.vagrantup.com/](http://www.vagrantup.com/)
2) Install Virtual Box [https://www.virtualbox.org/](https://www.virtualbox.org/)

In the main kafka folder

1) ./sbt update
2) ./sbt package
3) ./sbt assembly-package-dependency
4) vagrant up

once this is done 
* Zookeeper will be running 192.168.50.5
* Broker 1 on 192.168.50.10
* Broker 2 on 192.168.50.20
* Broker 3 on 192.168.50.30

When you are all up and running you will be back at a command brompt.  

If you want you can login to the machines using vagrant shh <machineName> but you don't need to.

You can access the brokers and zookeeper by their IP

e.g.

bin/kafka-console-producer.sh --broker-list 192.168.50.10:9092,192.168.50.20:9092,192.168.50.30:9092 --topic sandbox

bin/kafka-console-consumer.sh --zookeeper 192.168.50.5:2181 --topic sandbox --from-beginning


---

* [KAFKA-1109](https://issues.apache.org/jira/browse/KAFKA-1109) | *Major* | **Need to fix GC log configuration code, not able to override KAFKA\_GC\_LOG\_OPTS**

kafka-run-class.sh contains GC log code:

# GC options
GC\_FILE\_SUFFIX='-gc.log'
GC\_LOG\_FILE\_NAME=''
if [ "$1" = "daemon" ] && [ -z "$KAFKA\_GC\_LOG\_OPTS"] ; then
  shift
  GC\_LOG\_FILE\_NAME=$1$GC\_FILE\_SUFFIX
  shift
  KAFKA\_GC\_LOG\_OPTS="-Xloggc:$LOG\_DIR/$GC\_LOG\_FILE\_NAME -verbose:gc -XX:+PrintGCDetails -XX:+PrintGCDateStamps -XX:+PrintGCTimeStamps "
fi

So when in my scripts I start kafka and want to override KAFKA\_GC\_LOG\_OPTS by exporting new values I get:

Exception in thread "main" java.lang.NoClassDefFoundError: daemon
Caused by: java.lang.ClassNotFoundException: daemon

That's because shift is not done when KAFKA\_GC\_LOG\_OPTS is set and "daemon" is passed as main class.

I suggest to replace it with this code:

# GC options
GC\_FILE\_SUFFIX='-gc.log'
GC\_LOG\_FILE\_NAME=''
if [ "$1" = "daemon" ] && [ -z "$KAFKA\_GC\_LOG\_OPTS" ] ; then
  shift
  GC\_LOG\_FILE\_NAME=$1$GC\_FILE\_SUFFIX
  shift
  KAFKA\_GC\_LOG\_OPTS="-Xloggc:$LOG\_DIR/$GC\_LOG\_FILE\_NAME -verbose:gc -XX:+PrintGCDetails -XX:+PrintGCDateStamps -XX:+PrintGCTimeStamps "
else
    if [ "$1" = "daemon" ] && [ "$KAFKA\_GC\_LOG\_OPTS" != "" ] ; then
      shift 2
    fi
fi


---

* [KAFKA-1070](https://issues.apache.org/jira/browse/KAFKA-1070) | *Major* | **Auto-assign node id**

It would be nice to have Kafka brokers auto-assign node ids rather than having that be a configuration. Having a configuration is irritating because (1) you have to generate a custom config for each broker and (2) even though it is in configuration, changing the node id can cause all kinds of bad things to happen.


---

* [KAFKA-1057](https://issues.apache.org/jira/browse/KAFKA-1057) | *Major* | **Trim whitespaces from user specified configs**

Whitespaces in configs are a common problem that leads to config errors. It will be nice if Kafka can trim the whitespaces from configs automatically


---

* [KAFKA-766](https://issues.apache.org/jira/browse/KAFKA-766) | *Major* | **Isr shrink/expand check is fragile**

Currently the isr check is coupled tightly with the produce batch size. For example, if the producer batch size is 10000 messages and isr check is 4000 messages, we continuously oscillate between shrinking isr and expanding isr every second. This is because a single produce request throws the replica out of the isr. This results in hundreds of calls to ZK (we still dont have multi write). This can be alleviated by making the producer batch size smaller than the isr check size. 

Going forward, we should try to not have this coupling. It is worth investigating if we can make the check more robust under such scenarios.


---

* [KAFKA-742](https://issues.apache.org/jira/browse/KAFKA-742) | *Major* | **Existing directories under the Kafka data directory without any data cause process to not start**

I incorrectly setup the configuration file to have the metrics go to /var/kafka/metrics while the logs were in /var/kafka. On startup I received the following error then the daemon exited:

30   [main] INFO  kafka.log.LogManager  - [Log Manager on Broker 0] Loading log 'metrics'
32   [main] FATAL kafka.server.KafkaServerStartable  - Fatal error during KafkaServerStable startup. Prepare to shutdown
java.lang.StringIndexOutOfBoundsException: String index out of range: -1
        at java.lang.String.substring(String.java:1937)
        at kafka.log.LogManager.kafka$log$LogManager$$parseTopicPartitionName(LogManager.scala:335)
        at kafka.log.LogManager$$anonfun$loadLogs$1$$anonfun$apply$3.apply(LogManager.scala:112)
        at kafka.log.LogManager$$anonfun$loadLogs$1$$anonfun$apply$3.apply(LogManager.scala:109)
        at scala.collection.IndexedSeqOptimized$class.foreach(IndexedSeqOptimized.scala:34)
        at scala.collection.mutable.ArrayOps.foreach(ArrayOps.scala:34)
        at kafka.log.LogManager$$anonfun$loadLogs$1.apply(LogManager.scala:109)
        at kafka.log.LogManager$$anonfun$loadLogs$1.apply(LogManager.scala:101)
        at scala.collection.IndexedSeqOptimized$class.foreach(IndexedSeqOptimized.scala:34)
        at scala.collection.mutable.WrappedArray.foreach(WrappedArray.scala:32)
        at kafka.log.LogManager.loadLogs(LogManager.scala:101)
        at kafka.log.LogManager.<init>(LogManager.scala:62)
        at kafka.server.KafkaServer.startup(KafkaServer.scala:59)
        at kafka.server.KafkaServerStartable.startup(KafkaServerStartable.scala:34)
        at kafka.Kafka$.main(Kafka.scala:46)
        at kafka.Kafka.main(Kafka.scala)
34   [main] INFO  kafka.server.KafkaServer  - [Kafka Server 0], shutting down

This was on a brand new cluster so no data or metrics logs existed yet.

Moving the metrics to their own directory (not a child of the logs) allowed the daemon to start.

Took a few minutes to figure out what was wrong.


---

* [KAFKA-328](https://issues.apache.org/jira/browse/KAFKA-328) | *Major* | **Write unit test for kafka server startup and shutdown API**

Background discussion in KAFKA-320

People often try to embed KafkaServer in an application that ends up calling startup() and shutdown() repeatedly and sometimes in odd ways. To ensure this works correctly we have to be very careful about cleaning up resources. This is a good practice for making unit tests reliable anyway.

A good first step would be to add some unit tests on startup and shutdown to cover various cases:
1. A Kafka server can startup if it is not already starting up, if it is not currently being shutdown, or if it hasn't been already started
2. A Kafka server can shutdown if it is not already shutting down, if it is not currently starting up, or if it hasn't been already shutdown.


