
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
#  1.3.2 Release Notes

These release notes cover new developer and user-facing incompatibilities, features, and major improvements.


---

* [SPARK-6781](https://issues.apache.org/jira/browse/SPARK-6781) | *Critical* | **sqlCtx -\> sqlContext in pyspark shell**

We should be consistent across languages in the default names of things we add to the shells.


---

* [SPARK-6767](https://issues.apache.org/jira/browse/SPARK-6767) | *Trivial* | **Documentation error in Spark SQL Readme file**

Error in Spark SQL Documentation file . The sample script for SQL DSL   throwing below error

scala> query.where('key > 30).select(avg('key)).collect()
<console>:43: error: value > is not a member of Symbol
              query.where('key > 30).select(avg('key)).collect()


---

* [SPARK-6753](https://issues.apache.org/jira/browse/SPARK-6753) | *Minor* | **Unit test for SPARK-3426 (in ShuffleSuite) doesn't correctly clone the SparkConf**

As a result, that test always uses the default shuffle settings, rather than using the shuffle manager / other settings set by tests that extend ShuffleSuite.


---

* [SPARK-6636](https://issues.apache.org/jira/browse/SPARK-6636) | *Minor* | **Use public DNS hostname everywhere in spark\_ec2.py**

The spark\_ec2.py script uses public\_dns\_name everywhere in the script except for testing ssh availability, which is done using the public ip address of the instances. This breaks the script for users who are deploying the cluster with a private-network-only security group. The fix is to use public\_dns\_name in the remaining place.

I am submitting a pull-request alongside this bug report.


---

* [SPARK-6506](https://issues.apache.org/jira/browse/SPARK-6506) | *Major* | **python support yarn cluster mode requires SPARK\_HOME to be set**

We added support for python running in yarn cluster mode in https://issues.apache.org/jira/browse/SPARK-5173, but it requires that SPARK\_HOME be set in the environment variables for application master and executor.  It doesn't have to be set to anything real but it fails if its not set.  See the command at the end of: https://github.com/apache/spark/pull/3976


---

* [SPARK-6343](https://issues.apache.org/jira/browse/SPARK-6343) | *Minor* | **Make doc more explicit regarding network connectivity requirements**

As a new user of Spark, I read through the official documentation before attempting to stand-up my own cluster and write my own driver application. But only after attempting to run my app remotely against my cluster did I realize that full network connectivity (layer 3) is necessary between my driver program and worker nodes (i.e., my driver was *listening* for connections from my workers).

I returned to the documentation to see how I had missed this requirement. On a second read-through, I saw that the doc hints at it in a few places (e.g., [driver config|http://spark.apache.org/docs/1.2.0/configuration.html#networking], [submitting applications suggestion|http://spark.apache.org/docs/1.2.0/submitting-applications.html], [cluster overview|http://spark.apache.org/docs/1.2.0/cluster-overview.html])  but never outright says it.

I think it would help would-be users better understand how Spark works to state the network connectivity requirements right up-front in the overview section of the doc. I suggest revising the diagram and accompanying text found on the [overview page|http://spark.apache.org/docs/1.2.0/cluster-overview.html]:

!http://spark.apache.org/docs/1.2.0/img/cluster-overview.png!

so that it depicts at least the directionality of the network connections initiated (perhaps like so):

!http://i.imgur.com/2dqGbCr.png!

and states that the driver must listen for and accept connections from other Spark components on a variety of ports.

Please treat my diagram and text as strawmen: I expect more experienced Spark users and developers will have better ideas on how to convey these requirements.


---

* [SPARK-6205](https://issues.apache.org/jira/browse/SPARK-6205) | *Minor* | **UISeleniumSuite fails for Hadoop 2.x test with NoClassDefFoundError**

{code}
mvn -DskipTests -Pyarn -Phive -Phadoop-2.4 -Dhadoop.version=2.6.0 clean install
mvn -Pyarn -Phive -Phadoop-2.4 -Dhadoop.version=2.6.0 test -DwildcardSuites=org.apache.spark.ui.UISeleniumSuite -Dtest=none -pl core/ 
{code}

will produce:

{code}
UISeleniumSuite:
*** RUN ABORTED ***
  java.lang.NoClassDefFoundError: org/w3c/dom/ElementTraversal
  ...
{code}

It doesn't seem to happen without the various profiles set above.

The fix is simple, although sounds weird; Selenium's dependency on {{xml-apis:xml-apis}} must be manually included in core's test dependencies. This probably has something to do with Hadoop 2 vs 1 dependency changes and the fact that Maven test deps aren't transitive, AFAIK.

PR coming...


