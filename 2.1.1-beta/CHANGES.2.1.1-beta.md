# Hadoop Changelog

## Release 2.1.1-beta - 2013-09-16

### INCOMPATIBLE CHANGES:

| JIRA | Description | Priority | Component | Reporter | Contributor |
|:---- |:---- | :--- |:---- |:---- |:---- |
| [HADOOP-9944](https://issues.apache.org/jira/browse/HADOOP-9944) | RpcRequestHeaderProto defines callId as uint32 while ipc.Client.CONNECTION\_CONTEXT\_CALL\_ID is signed (-3) |  Blocker | . | Arun C Murthy | Arun C Murthy |
| [YARN-1170](https://issues.apache.org/jira/browse/YARN-1170) | yarn proto definitions should specify package as 'hadoop.yarn' |  Blocker | . | Arun C Murthy | Binglin Chang |
| [YARN-707](https://issues.apache.org/jira/browse/YARN-707) | Add user info in the YARN ClientToken |  Blocker | . | Bikas Saha | Jason Lowe |


### NEW FEATURES:

| JIRA | Description | Priority | Component | Reporter | Contributor |
|:---- |:---- | :--- |:---- |:---- |:---- |
| [HADOOP-9789](https://issues.apache.org/jira/browse/HADOOP-9789) | Support server advertised kerberos principals |  Critical | ipc, security | Daryn Sharp | Daryn Sharp |
| [HDFS-5118](https://issues.apache.org/jira/browse/HDFS-5118) | Provide testing support for DFSClient to drop RPC responses |  Major | . | Jing Zhao | Jing Zhao |
| [HDFS-5076](https://issues.apache.org/jira/browse/HDFS-5076) | Add MXBean methods to query NN's transaction information and JournalNode's journal status |  Minor | . | Jing Zhao | Jing Zhao |


### IMPROVEMENTS:

| JIRA | Description | Priority | Component | Reporter | Contributor |
|:---- |:---- | :--- |:---- |:---- |:---- |
| [HADOOP-9962](https://issues.apache.org/jira/browse/HADOOP-9962) | in order to avoid dependency divergence within Hadoop itself lets enable DependencyConvergence |  Major | build | Roman Shaposhnik | Roman Shaposhnik |
| [HADOOP-9945](https://issues.apache.org/jira/browse/HADOOP-9945) | HAServiceState should have a state for stopped services |  Minor | ha | Karthik Kambatla | Karthik Kambatla |
| [HADOOP-9918](https://issues.apache.org/jira/browse/HADOOP-9918) | Add addIfService() to CompositeService |  Minor | . | Karthik Kambatla | Karthik Kambatla |
| [HADOOP-9886](https://issues.apache.org/jira/browse/HADOOP-9886) | Turn warning message in RetryInvocationHandler to debug |  Minor | . | Arpit Gupta | Arpit Gupta |
| [HADOOP-9879](https://issues.apache.org/jira/browse/HADOOP-9879) | Move the version info of zookeeper dependencies to hadoop-project/pom |  Minor | build | Karthik Kambatla | Karthik Kambatla |
| [HADOOP-9833](https://issues.apache.org/jira/browse/HADOOP-9833) | move slf4j to version 1.7.5 |  Minor | build | Steve Loughran | Kousuke Saruta |
| [HADOOP-9831](https://issues.apache.org/jira/browse/HADOOP-9831) | Make checknative shell command accessible on Windows. |  Minor | bin | Chris Nauroth | Chris Nauroth |
| [HADOOP-9821](https://issues.apache.org/jira/browse/HADOOP-9821) | ClientId should have getMsb/getLsb methods |  Minor | . | Tsuyoshi Ozawa | Tsuyoshi Ozawa |
| [HADOOP-9803](https://issues.apache.org/jira/browse/HADOOP-9803) | Add generic type parameter to RetryInvocationHandler |  Minor | ipc | Tsz Wo Nicholas Sze | Tsz Wo Nicholas Sze |
| [HADOOP-9802](https://issues.apache.org/jira/browse/HADOOP-9802) | Support Snappy codec on Windows. |  Major | io | Chris Nauroth | Chris Nauroth |
| [HADOOP-9686](https://issues.apache.org/jira/browse/HADOOP-9686) | Easy access to final parameters in Configuration |  Major | conf | Jason Lowe | Jason Lowe |
| [HADOOP-9672](https://issues.apache.org/jira/browse/HADOOP-9672) | Upgrade Avro dependency to 1.7.4 |  Major | . | Sandy Ryza | Sandy Ryza |
| [HADOOP-9669](https://issues.apache.org/jira/browse/HADOOP-9669) | Reduce the number of byte array creations and copies in XDR data manipulation |  Major | nfs | Tsz Wo Nicholas Sze | Haohui Mai |
| [HADOOP-9446](https://issues.apache.org/jira/browse/HADOOP-9446) | Support Kerberos HTTP SPNEGO authentication for non-SUN JDK |  Major | security | Yu Gao | Yu Gao |
| [HADOOP-8814](https://issues.apache.org/jira/browse/HADOOP-8814) | Inefficient comparison with the empty string. Use isEmpty() instead |  Minor | conf, fs, fs/s3, ha, io, metrics, performance, record, security, util | Brandon Li | Brandon Li |
| [HDFS-5128](https://issues.apache.org/jira/browse/HDFS-5128) | Allow multiple net interfaces to be used with HA namenode RPC server |  Critical | . | Kihwal Lee | Kihwal Lee |
| [HDFS-5061](https://issues.apache.org/jira/browse/HDFS-5061) | Make FSNameSystem#auditLoggers an unmodifiable list |  Major | namenode | Arpit Agarwal | Arpit Agarwal |
| [HDFS-5045](https://issues.apache.org/jira/browse/HDFS-5045) | Add more unit tests for retry cache to cover all AtMostOnce methods |  Minor | . | Jing Zhao | Jing Zhao |
| [HDFS-4926](https://issues.apache.org/jira/browse/HDFS-4926) | namenode webserver's page has a tooltip that is inconsistent with the datanode HTML link |  Trivial | namenode | Joseph Lorenzini | Vivek Ganesan |
| [HDFS-4905](https://issues.apache.org/jira/browse/HDFS-4905) | Add appendToFile command to "hdfs dfs" |  Minor | tools | Arpit Agarwal | Arpit Agarwal |
| [HDFS-4513](https://issues.apache.org/jira/browse/HDFS-4513) | Clarify WebHDFS REST API that all JSON respsonses may contain additional properties |  Minor | documentation, webhdfs | Tsz Wo Nicholas Sze | Tsz Wo Nicholas Sze |
| [HDFS-3245](https://issues.apache.org/jira/browse/HDFS-3245) | Add metrics and web UI for cluster version summary |  Major | namenode | Todd Lipcon | Ravi Prakash |
| [MAPREDUCE-5478](https://issues.apache.org/jira/browse/MAPREDUCE-5478) | TeraInputFormat unnecessarily defines its own FileSplit subclass |  Minor | examples | Sandy Ryza | Sandy Ryza |
| [MAPREDUCE-5379](https://issues.apache.org/jira/browse/MAPREDUCE-5379) | Include token tracking ids in jobconf |  Major | job submission, security | Sandy Ryza | Karthik Kambatla |
| [MAPREDUCE-5367](https://issues.apache.org/jira/browse/MAPREDUCE-5367) | Local jobs all use same local working directory |  Major | . | Sandy Ryza | Sandy Ryza |
| [MAPREDUCE-1981](https://issues.apache.org/jira/browse/MAPREDUCE-1981) | Improve getSplits performance by using listLocatedStatus |  Major | job submission | Hairong Kuang | Hairong Kuang |
| [YARN-1137](https://issues.apache.org/jira/browse/YARN-1137) | Add support whitelist for system users to Yarn container-executor.c |  Major | nodemanager | Alejandro Abdelnur | Roman Shaposhnik |
| [YARN-1117](https://issues.apache.org/jira/browse/YARN-1117) | Improve help message for $ yarn applications and $yarn node |  Major | client | Tassapol Athiapinya | Xuan Gong |
| [YARN-1081](https://issues.apache.org/jira/browse/YARN-1081) | Minor improvement to output header for $ yarn node -list |  Minor | client | Tassapol Athiapinya | Akira AJISAKA |
| [YARN-1080](https://issues.apache.org/jira/browse/YARN-1080) | Improve help message for $ yarn logs |  Major | client | Tassapol Athiapinya | Xuan Gong |
| [YARN-1074](https://issues.apache.org/jira/browse/YARN-1074) | Clean up YARN CLI app list to show only running apps. |  Major | client | Tassapol Athiapinya | Xuan Gong |
| [YARN-910](https://issues.apache.org/jira/browse/YARN-910) | Allow auxiliary services to listen for container starts and completions |  Major | nodemanager | Sandy Ryza | Alejandro Abdelnur |
| [YARN-758](https://issues.apache.org/jira/browse/YARN-758) | Augment MockNM to use multiple cores |  Minor | . | Bikas Saha | Karthik Kambatla |
| [YARN-696](https://issues.apache.org/jira/browse/YARN-696) | Enable multiple states to to be specified in Resource Manager apps REST call |  Major | resourcemanager | Trevor Lorimer | Trevor Lorimer |
| [YARN-589](https://issues.apache.org/jira/browse/YARN-589) | Expose a REST API for monitoring the fair scheduler |  Major | scheduler | Sandy Ryza | Sandy Ryza |


### BUG FIXES:

| JIRA | Description | Priority | Component | Reporter | Contributor |
|:---- |:---- | :--- |:---- |:---- |:---- |
| [HADOOP-9977](https://issues.apache.org/jira/browse/HADOOP-9977) | Hadoop services won't start with different keypass and keystorepass when https is enabled |  Major | security | Yesha Vora | Chris Nauroth |
| [HADOOP-9961](https://issues.apache.org/jira/browse/HADOOP-9961) | versions of a few transitive dependencies diverged between hadoop subprojects |  Minor | build | Roman Shaposhnik | Roman Shaposhnik |
| [HADOOP-9960](https://issues.apache.org/jira/browse/HADOOP-9960) | Upgrade Jersey version to 1.9 |  Blocker | . | Brock Noland | Karthik Kambatla |
| [HADOOP-9958](https://issues.apache.org/jira/browse/HADOOP-9958) | Add old constructor back to DelegationTokenInformation to unbreak downstream builds |  Major | . | Andrew Wang | Andrew Wang |
| [HADOOP-9932](https://issues.apache.org/jira/browse/HADOOP-9932) | Improper synchronization in RetryCache |  Blocker | . | Kihwal Lee | Kihwal Lee |
| [HADOOP-9924](https://issues.apache.org/jira/browse/HADOOP-9924) | FileUtil.createJarWithClassPath() does not generate relative classpath correctly |  Major | fs | shanyu zhao | shanyu zhao |
| [HADOOP-9916](https://issues.apache.org/jira/browse/HADOOP-9916) | Race condition in ipc.Client causes TestIPC timeout |  Minor | . | Binglin Chang | Binglin Chang |
| [HADOOP-9910](https://issues.apache.org/jira/browse/HADOOP-9910) | proxy server start and stop documentation wrong |  Minor | . | André Kelpe |  |
| [HADOOP-9906](https://issues.apache.org/jira/browse/HADOOP-9906) | Move HAZKUtil to o.a.h.util.ZKUtil and make inner-classes public |  Minor | ha | Karthik Kambatla | Karthik Kambatla |
| [HADOOP-9899](https://issues.apache.org/jira/browse/HADOOP-9899) | Remove the debug message added by HADOOP-8855 |  Minor | security | Tsz Wo Nicholas Sze | Tsz Wo Nicholas Sze |
| [HADOOP-9880](https://issues.apache.org/jira/browse/HADOOP-9880) | SASL changes from HADOOP-9421 breaks Secure HA NN |  Blocker | . | Kihwal Lee | Daryn Sharp |
| [HADOOP-9868](https://issues.apache.org/jira/browse/HADOOP-9868) | Server must not advertise kerberos realm |  Blocker | ipc | Daryn Sharp | Daryn Sharp |
| [HADOOP-9858](https://issues.apache.org/jira/browse/HADOOP-9858) | Remove unused private RawLocalFileSystem#execCommand method from branch-2. |  Trivial | fs | Chris Nauroth | Chris Nauroth |
| [HADOOP-9857](https://issues.apache.org/jira/browse/HADOOP-9857) | Tests block and sometimes timeout on Windows due to invalid entropy source. |  Major | build, test | Chris Nauroth | Chris Nauroth |
| [HADOOP-9806](https://issues.apache.org/jira/browse/HADOOP-9806) | PortmapInterface should check if the procedure is out-of-range |  Major | nfs | Brandon Li | Brandon Li |
| [HADOOP-9801](https://issues.apache.org/jira/browse/HADOOP-9801) | Configuration#writeXml uses platform defaulting encoding, which may mishandle multi-byte characters. |  Major | conf | Chris Nauroth | Chris Nauroth |
| [HADOOP-9774](https://issues.apache.org/jira/browse/HADOOP-9774) | RawLocalFileSystem.listStatus() return absolute paths when input path is relative on Windows |  Major | fs | shanyu zhao | shanyu zhao |
| [HADOOP-9768](https://issues.apache.org/jira/browse/HADOOP-9768) | chown and chgrp reject users and groups with spaces on platforms where spaces are otherwise acceptable |  Major | fs | Chris Nauroth | Chris Nauroth |
| [HADOOP-9757](https://issues.apache.org/jira/browse/HADOOP-9757) | Har metadata cache can grow without limit |  Major | fs | Jason Lowe | Cristina L. Abad |
| [HADOOP-9557](https://issues.apache.org/jira/browse/HADOOP-9557) | hadoop-client excludes commons-httpclient |  Major | build | Lohit Vijayarenu | Lohit Vijayarenu |
| [HADOOP-9435](https://issues.apache.org/jira/browse/HADOOP-9435) | Support building the JNI code against the IBM JVM |  Major | build | Tian Hong Wang | Tian Hong Wang |
| [HADOOP-9381](https://issues.apache.org/jira/browse/HADOOP-9381) | Document dfs cp -f option |  Trivial | . | Keegan Witt | Keegan Witt |
| [HADOOP-9315](https://issues.apache.org/jira/browse/HADOOP-9315) | Port HADOOP-9249 hadoop-maven-plugins Clover fix to branch-2 to fix build failures |  Major | build | Dennis Y | Chris Nauroth |
| [HDFS-5231](https://issues.apache.org/jira/browse/HDFS-5231) | Fix broken links in the document of HDFS Federation |  Minor | . | Haohui Mai | Haohui Mai |
| [HDFS-5219](https://issues.apache.org/jira/browse/HDFS-5219) | Add configuration keys for retry policy in WebHDFSFileSystem |  Major | webhdfs | Haohui Mai | Haohui Mai |
| [HDFS-5192](https://issues.apache.org/jira/browse/HDFS-5192) | NameNode may fail to start when dfs.client.test.drop.namenode.response.number is set |  Minor | . | Jing Zhao | Jing Zhao |
| [HDFS-5159](https://issues.apache.org/jira/browse/HDFS-5159) | Secondary NameNode fails to checkpoint if error occurs downloading edits on first checkpoint |  Major | namenode | Aaron T. Myers | Aaron T. Myers |
| [HDFS-5150](https://issues.apache.org/jira/browse/HDFS-5150) | Allow per NN SPN for internal SPNEGO. |  Blocker | . | Kihwal Lee | Kihwal Lee |
| [HDFS-5140](https://issues.apache.org/jira/browse/HDFS-5140) | Too many safemode monitor threads being created in the standby namenode causing it to fail with out of memory error |  Blocker | ha | Arpit Gupta | Jing Zhao |
| [HDFS-5132](https://issues.apache.org/jira/browse/HDFS-5132) | Deadlock in NameNode between SafeModeMonitor#run and DatanodeManager#handleHeartbeat |  Blocker | namenode | Arpit Gupta | Kihwal Lee |
| [HDFS-5124](https://issues.apache.org/jira/browse/HDFS-5124) | DelegationTokenSecretManager#retrievePassword can cause deadlock in NameNode |  Blocker | namenode | Deepesh Khandelwal | Daryn Sharp |
| [HDFS-5111](https://issues.apache.org/jira/browse/HDFS-5111) | Remove duplicated error message for snapshot commands when processing invalid arguments |  Minor | snapshots | Jing Zhao | Jing Zhao |
| [HDFS-5106](https://issues.apache.org/jira/browse/HDFS-5106) | TestDatanodeBlockScanner fails on Windows due to incorrect path format |  Minor | test | Chuan Liu | Chuan Liu |
| [HDFS-5105](https://issues.apache.org/jira/browse/HDFS-5105) | TestFsck fails on Windows |  Minor | . | Chuan Liu | Chuan Liu |
| [HDFS-5103](https://issues.apache.org/jira/browse/HDFS-5103) | TestDirectoryScanner fails on Windows |  Minor | test | Chuan Liu | Chuan Liu |
| [HDFS-5102](https://issues.apache.org/jira/browse/HDFS-5102) | Snapshot names should not be allowed to contain slash characters |  Major | snapshots | Aaron T. Myers | Jing Zhao |
| [HDFS-5100](https://issues.apache.org/jira/browse/HDFS-5100) | TestNamenodeRetryCache fails on Windows due to incorrect cleanup |  Minor | test | Chuan Liu | Chuan Liu |
| [HDFS-5099](https://issues.apache.org/jira/browse/HDFS-5099) | Namenode#copyEditLogSegmentsToSharedDir should close EditLogInputStreams upon finishing |  Major | namenode | Chuan Liu | Chuan Liu |
| [HDFS-5091](https://issues.apache.org/jira/browse/HDFS-5091) | Support for spnego keytab separate from the JournalNode keytab for secure HA |  Minor | . | Jing Zhao | Jing Zhao |
| [HDFS-5080](https://issues.apache.org/jira/browse/HDFS-5080) | BootstrapStandby not working with QJM when the existing NN is active |  Major | ha, qjm | Jing Zhao | Jing Zhao |
| [HDFS-5077](https://issues.apache.org/jira/browse/HDFS-5077) | NPE in FSNamesystem.commitBlockSynchronization() |  Major | namenode | Konstantin Shvachko | Plamen Jeliazkov |
| [HDFS-5055](https://issues.apache.org/jira/browse/HDFS-5055) | nn fails to download checkpointed image from snn in some setups |  Blocker | namenode | Allen Wittenauer | Vinayakumar B |
| [HDFS-5047](https://issues.apache.org/jira/browse/HDFS-5047) | Supress logging of full stack trace of quota and lease exceptions |  Major | namenode | Kihwal Lee | Robert Parker |
| [HDFS-5043](https://issues.apache.org/jira/browse/HDFS-5043) | For HdfsFileStatus, set default value of childrenNum to -1 instead of 0 to avoid confusing applications |  Major | . | Brandon Li | Brandon Li |
| [HDFS-5028](https://issues.apache.org/jira/browse/HDFS-5028) | LeaseRenewer throw java.util.ConcurrentModificationException when timeout |  Major | . | zhaoyunjiong | zhaoyunjiong |
| [HDFS-4993](https://issues.apache.org/jira/browse/HDFS-4993) | fsck can fail if a file is renamed or deleted |  Major | . | Kihwal Lee | Robert Parker |
| [HDFS-4898](https://issues.apache.org/jira/browse/HDFS-4898) | BlockPlacementPolicyWithNodeGroup.chooseRemoteRack() fails to properly fallback to local rack |  Minor | namenode | Eric Sirianni | Tsz Wo Nicholas Sze |
| [HDFS-4680](https://issues.apache.org/jira/browse/HDFS-4680) | Audit logging of delegation tokens for MR tracing |  Major | namenode, security | Andrew Wang | Andrew Wang |
| [HDFS-4632](https://issues.apache.org/jira/browse/HDFS-4632) | globStatus using backslash for escaping does not work on Windows |  Major | test | Chris Nauroth | Chuan Liu |
| [HDFS-4594](https://issues.apache.org/jira/browse/HDFS-4594) | WebHDFS open sets Content-Length header to what is specified by length parameter rather than how much data is actually returned. |  Minor | webhdfs | Arpit Gupta | Chris Nauroth |
| [HDFS-2994](https://issues.apache.org/jira/browse/HDFS-2994) | If lease soft limit is recovered successfully the append can fail |  Major | . | Todd Lipcon | Tao Luo |
| [MAPREDUCE-5497](https://issues.apache.org/jira/browse/MAPREDUCE-5497) | '5s sleep'  in MRAppMaster.shutDownJob is only needed before stopping ClientService |  Major | . | Jian He | Jian He |
| [MAPREDUCE-5493](https://issues.apache.org/jira/browse/MAPREDUCE-5493) | In-memory map outputs can be leaked after shuffle completes |  Blocker | mrv2 | Jason Lowe | Jason Lowe |
| [MAPREDUCE-5483](https://issues.apache.org/jira/browse/MAPREDUCE-5483) | revert MAPREDUCE-5357 |  Major | distcp | Alejandro Abdelnur | Robert Kanter |
| [MAPREDUCE-5475](https://issues.apache.org/jira/browse/MAPREDUCE-5475) | MRClientService does not verify ACLs properly |  Blocker | mr-am, mrv2 | Jason Lowe | Jason Lowe |
| [MAPREDUCE-5470](https://issues.apache.org/jira/browse/MAPREDUCE-5470) | LocalJobRunner does not work on Windows. |  Major | . | Chris Nauroth | Sandy Ryza |
| [MAPREDUCE-5468](https://issues.apache.org/jira/browse/MAPREDUCE-5468) | AM recovery does not work for map only jobs |  Blocker | . | Yesha Vora | Vinod Kumar Vavilapalli |
| [MAPREDUCE-5454](https://issues.apache.org/jira/browse/MAPREDUCE-5454) | TestDFSIO fails intermittently on JDK7 |  Major | test | Karthik Kambatla | Karthik Kambatla |
| [MAPREDUCE-5446](https://issues.apache.org/jira/browse/MAPREDUCE-5446) | TestJobHistoryEvents and TestJobHistoryParsing have race conditions |  Major | mrv2, test | Jason Lowe | Jason Lowe |
| [MAPREDUCE-5440](https://issues.apache.org/jira/browse/MAPREDUCE-5440) | TestCopyCommitter Fails on JDK7 |  Major | mrv2 | Robert Parker | Robert Parker |
| [MAPREDUCE-5428](https://issues.apache.org/jira/browse/MAPREDUCE-5428) | HistoryFileManager doesn't stop threads when service is stopped |  Major | jobhistoryserver, mrv2 | Jason Lowe | Karthik Kambatla |
| [MAPREDUCE-5425](https://issues.apache.org/jira/browse/MAPREDUCE-5425) | Junit in TestJobHistoryServer failing in jdk 7 |  Major | jobhistoryserver | Ashwin Shankar | Robert Parker |
| [MAPREDUCE-5414](https://issues.apache.org/jira/browse/MAPREDUCE-5414) | TestTaskAttempt fails jdk7 with NullPointerException |  Major | test | Nemon Lou | Nemon Lou |
| [MAPREDUCE-5385](https://issues.apache.org/jira/browse/MAPREDUCE-5385) | JobContext cache files api are broken |  Blocker | . | Omkar Vinit Joshi | Omkar Vinit Joshi |
| [MAPREDUCE-5358](https://issues.apache.org/jira/browse/MAPREDUCE-5358) | MRAppMaster throws invalid transitions for JobImpl |  Major | mr-am | Devaraj K | Devaraj K |
| [MAPREDUCE-5317](https://issues.apache.org/jira/browse/MAPREDUCE-5317) | Stale files left behind for failed jobs |  Major | mrv2 | Ravi Prakash | Ravi Prakash |
| [MAPREDUCE-5251](https://issues.apache.org/jira/browse/MAPREDUCE-5251) | Reducer should not implicate map attempt if it has insufficient space to fetch map output |  Major | mrv2 | Jason Lowe | Ashwin Shankar |
| [MAPREDUCE-5164](https://issues.apache.org/jira/browse/MAPREDUCE-5164) | command  "mapred job" and "mapred queue" omit HADOOP\_CLIENT\_OPTS |  Major | . | Nemon Lou | Nemon Lou |
| [MAPREDUCE-5020](https://issues.apache.org/jira/browse/MAPREDUCE-5020) | Compile failure with JDK8 |  Major | client | Trevor Robinson | Trevor Robinson |
| [MAPREDUCE-5001](https://issues.apache.org/jira/browse/MAPREDUCE-5001) | LocalJobRunner has race condition resulting in job failures |  Major | . | Brock Noland | Sandy Ryza |
| [MAPREDUCE-3193](https://issues.apache.org/jira/browse/MAPREDUCE-3193) | FileInputFormat doesn't read files recursively in the input path dir |  Major | mrv1, mrv2 | Ramgopal N | Devaraj K |
| [YARN-1194](https://issues.apache.org/jira/browse/YARN-1194) | TestContainerLogsPage fails with native builds |  Minor | nodemanager | Roman Shaposhnik | Roman Shaposhnik |
| [YARN-1189](https://issues.apache.org/jira/browse/YARN-1189) | NMTokenSecretManagerInNM is not being told when applications have finished |  Blocker | . | Jason Lowe | Omkar Vinit Joshi |
| [YARN-1176](https://issues.apache.org/jira/browse/YARN-1176) | RM web services ClusterMetricsInfo total nodes doesn't include unhealthy nodes |  Critical | resourcemanager | Thomas Graves | Jonathan Eagles |
| [YARN-1152](https://issues.apache.org/jira/browse/YARN-1152) | Invalid key to HMAC computation error when getting application report for completed app attempt |  Blocker | resourcemanager | Jason Lowe | Jason Lowe |
| [YARN-1144](https://issues.apache.org/jira/browse/YARN-1144) | Unmanaged AMs registering a tracking URI should not be proxy-fied |  Critical | resourcemanager | Alejandro Abdelnur | Alejandro Abdelnur |
| [YARN-1124](https://issues.apache.org/jira/browse/YARN-1124) | By default yarn application -list should display all the applications in a state other than FINISHED / FAILED |  Blocker | . | Omkar Vinit Joshi | Xuan Gong |
| [YARN-1120](https://issues.apache.org/jira/browse/YARN-1120) | Make ApplicationConstants.Environment.USER definition OS neutral |  Minor | . | Chuan Liu | Chuan Liu |
| [YARN-1107](https://issues.apache.org/jira/browse/YARN-1107) | Job submitted with Delegation token in secured environment causes RM to fail during RM restart |  Blocker | resourcemanager | Arpit Gupta | Omkar Vinit Joshi |
| [YARN-1101](https://issues.apache.org/jira/browse/YARN-1101) | Active nodes can be decremented below 0 |  Major | resourcemanager | Robert Parker | Robert Parker |
| [YARN-1094](https://issues.apache.org/jira/browse/YARN-1094) | RM restart throws Null pointer Exception in Secure Env |  Blocker | . | Yesha Vora | Vinod Kumar Vavilapalli |
| [YARN-1093](https://issues.apache.org/jira/browse/YARN-1093) | Corrections to Fair Scheduler documentation |  Major | documentation | Wing Yew Poon |  |
| [YARN-1083](https://issues.apache.org/jira/browse/YARN-1083) | ResourceManager should fail when yarn.nm.liveness-monitor.expiry-interval-ms is set less than heartbeat interval |  Major | resourcemanager | Yesha Vora | Zhijie Shen |
| [YARN-1082](https://issues.apache.org/jira/browse/YARN-1082) | Secure RM with recovery enabled and rm state store on hdfs fails with gss exception |  Blocker | resourcemanager | Arpit Gupta | Vinod Kumar Vavilapalli |
| [YARN-1078](https://issues.apache.org/jira/browse/YARN-1078) | TestNodeManagerResync, TestNodeManagerShutdown, and TestNodeStatusUpdater fail on Windows |  Minor | . | Chuan Liu | Chuan Liu |
| [YARN-1077](https://issues.apache.org/jira/browse/YARN-1077) | TestContainerLaunch fails on Windows |  Minor | . | Chuan Liu | Chuan Liu |
| [YARN-1025](https://issues.apache.org/jira/browse/YARN-1025) | ResourceManager and NodeManager do not load native libraries on Windows. |  Major | nodemanager, resourcemanager | Chris Nauroth | Chris Nauroth |
| [YARN-1008](https://issues.apache.org/jira/browse/YARN-1008) | MiniYARNCluster with multiple nodemanagers, all nodes have same key for allocations |  Major | nodemanager | Alejandro Abdelnur | Alejandro Abdelnur |
| [YARN-1006](https://issues.apache.org/jira/browse/YARN-1006) | Nodes list web page on the RM web UI is broken |  Major | . | Jian He | Xuan Gong |
| [YARN-994](https://issues.apache.org/jira/browse/YARN-994) | HeartBeat thread in AMRMClientAsync does not handle runtime exception correctly |  Major | . | Xuan Gong | Xuan Gong |
| [YARN-981](https://issues.apache.org/jira/browse/YARN-981) | YARN/MR2/Job-history /logs link does not have correct content |  Major | . | Xuan Gong | Jian He |
| [YARN-966](https://issues.apache.org/jira/browse/YARN-966) | The thread of ContainerLaunch#call will fail without any signal if getLocalizedResources() is called when the container is not at LOCALIZED |  Major | . | Zhijie Shen | Zhijie Shen |
| [YARN-957](https://issues.apache.org/jira/browse/YARN-957) | Capacity Scheduler tries to reserve the memory more than what node manager reports. |  Blocker | . | Omkar Vinit Joshi | Omkar Vinit Joshi |
| [YARN-948](https://issues.apache.org/jira/browse/YARN-948) | RM should validate the release container list before actually releasing them |  Major | . | Omkar Vinit Joshi | Omkar Vinit Joshi |
| [YARN-942](https://issues.apache.org/jira/browse/YARN-942) | In Fair Scheduler documentation, inconsistency on which properties have prefix |  Major | scheduler | Sandy Ryza | Akira AJISAKA |
| [YARN-903](https://issues.apache.org/jira/browse/YARN-903) | DistributedShell throwing Errors in logs after successfull completion |  Major | applications/distributed-shell | Abhishek Kapoor | Omkar Vinit Joshi |
| [YARN-881](https://issues.apache.org/jira/browse/YARN-881) | Priority#compareTo method seems to be wrong. |  Major | . | Jian He | Jian He |
| [YARN-643](https://issues.apache.org/jira/browse/YARN-643) | WHY appToken is removed both in BaseFinalTransition and AMUnregisteredTransition AND clientToken is removed in FinalTransition and not BaseFinalTransition |  Major | . | Jian He | Xuan Gong |
| [YARN-602](https://issues.apache.org/jira/browse/YARN-602) | NodeManager should mandatorily set some Environment variables into every containers that it launches |  Major | . | Xuan Gong | Kenji Kikushima |
| [YARN-337](https://issues.apache.org/jira/browse/YARN-337) | RM handles killed application tracking URL poorly |  Major | resourcemanager | Jason Lowe | Jason Lowe |
| [YARN-107](https://issues.apache.org/jira/browse/YARN-107) | ClientRMService.forceKillApplication() should handle the non-RUNNING applications properly |  Major | resourcemanager | Devaraj K | Xuan Gong |


### TESTS:

| JIRA | Description | Priority | Component | Reporter | Contributor |
|:---- |:---- | :--- |:---- |:---- |:---- |


### OTHER:

| JIRA | Description | Priority | Component | Reporter | Contributor |
|:---- |:---- | :--- |:---- |:---- |:---- |
| [YARN-1034](https://issues.apache.org/jira/browse/YARN-1034) | Remove "experimental" in the Fair Scheduler documentation |  Trivial | documentation, scheduler | Sandy Ryza | Karthik Kambatla |
| [YARN-1001](https://issues.apache.org/jira/browse/YARN-1001) | YARN should provide per application-type and state statistics |  Blocker | api | Srimanth Gunturi | Zhijie Shen |

