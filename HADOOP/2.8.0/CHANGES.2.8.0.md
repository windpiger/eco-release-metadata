
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
# Apache Hadoop Changelog

## Release 2.8.0 - Unreleased (as of 2016-03-01)

### INCOMPATIBLE CHANGES:

| JIRA | Summary | Priority | Component | Reporter | Contributor |
|:---- |:---- | :--- |:---- |:---- |:---- |
| [HADOOP-12552](https://issues.apache.org/jira/browse/HADOOP-12552) | Fix undeclared/unused dependency to httpclient |  Minor | build | Masatake Iwasaki | Masatake Iwasaki |
| [HADOOP-12416](https://issues.apache.org/jira/browse/HADOOP-12416) | Trash messages should be handled by Logger instead of being delivered on System.out |  Major | trash | Ashutosh Chauhan | Mingliang Liu |
| [HADOOP-11772](https://issues.apache.org/jira/browse/HADOOP-11772) | RPC Invoker relies on static ClientCache which has synchronized(this) blocks |  Major | ipc, performance | Gopal V | Haohui Mai |
| [HADOOP-11746](https://issues.apache.org/jira/browse/HADOOP-11746) | rewrite test-patch.sh |  Major | build, test | Allen Wittenauer | Allen Wittenauer |
| [HADOOP-11731](https://issues.apache.org/jira/browse/HADOOP-11731) | Rework the changelog and releasenotes |  Major | documentation | Allen Wittenauer | Allen Wittenauer |
| [HDFS-9047](https://issues.apache.org/jira/browse/HDFS-9047) | Retire libwebhdfs |  Major | webhdfs | Allen Wittenauer | Haohui Mai |
| [HDFS-8900](https://issues.apache.org/jira/browse/HDFS-8900) | Compact XAttrs to optimize memory footprint. |  Major | namenode | Yi Liu | Yi Liu |
| [HDFS-7933](https://issues.apache.org/jira/browse/HDFS-7933) | fsck should also report decommissioning replicas. |  Major | namenode | Jitendra Nath Pandey | Xiaoyu Yao |
| [HDFS-6564](https://issues.apache.org/jira/browse/HDFS-6564) | Use slf4j instead of common-logging in hdfs-client |  Major | build | Haohui Mai | Rakesh R |
| [MAPREDUCE-6427](https://issues.apache.org/jira/browse/MAPREDUCE-6427) | Fix typo in JobHistoryEventHandler |  Minor | . | Brahma Reddy Battula | Ray Chiang |
| [YARN-3241](https://issues.apache.org/jira/browse/YARN-3241) | FairScheduler handles "invalid" queue names inconsistently |  Major | fairscheduler | zhihai xu | zhihai xu |
| [YARN-2336](https://issues.apache.org/jira/browse/YARN-2336) | Fair scheduler REST api returns a missing '[' bracket JSON for deep queue tree |  Major | fairscheduler | Kenji Kikushima | Akira AJISAKA |
| [YARN-41](https://issues.apache.org/jira/browse/YARN-41) | The RM should handle the graceful shutdown of the NM. |  Major | nodemanager, resourcemanager | Ravi Teja Ch N V | Devaraj K |


### IMPORTANT ISSUES:

| JIRA | Summary | Priority | Component | Reporter | Contributor |
|:---- |:---- | :--- |:---- |:---- |:---- |
| [HADOOP-12081](https://issues.apache.org/jira/browse/HADOOP-12081) | Fix UserGroupInformation.java to support 64-bit zLinux |  Major | security | Adam Roberts | Akira AJISAKA |


### NEW FEATURES:

| JIRA | Summary | Priority | Component | Reporter | Contributor |
|:---- |:---- | :--- |:---- |:---- |:---- |
| [HADOOP-12691](https://issues.apache.org/jira/browse/HADOOP-12691) | Add CSRF Filter for REST APIs to Hadoop Common |  Major | security | Larry McCay | Larry McCay |
| [HADOOP-12657](https://issues.apache.org/jira/browse/HADOOP-12657) | Add a option to skip newline on empty files with getMerge -nl |  Minor | . | Jan Filipiak | Kanaka Kumar Avvaru |
| [HADOOP-12635](https://issues.apache.org/jira/browse/HADOOP-12635) | Adding Append API support for WASB |  Major | azure | Dushyanth | Dushyanth |
| [HADOOP-12548](https://issues.apache.org/jira/browse/HADOOP-12548) | Read s3a creds from a Credential Provider |  Major | fs/s3 | Allen Wittenauer | Larry McCay |
| [HADOOP-12426](https://issues.apache.org/jira/browse/HADOOP-12426) | Add Entry point for Kerberos health check |  Minor | security | Steve Loughran | Steve Loughran |
| [HADOOP-12366](https://issues.apache.org/jira/browse/HADOOP-12366) | expose calculated paths |  Major | . | Allen Wittenauer | Allen Wittenauer |
| [HADOOP-12360](https://issues.apache.org/jira/browse/HADOOP-12360) | Create StatsD metrics2 sink |  Minor | metrics | Dave Marion | Dave Marion |
| [HADOOP-11843](https://issues.apache.org/jira/browse/HADOOP-11843) | Make setting up the build environment easier |  Major | build | Niels Basjes | Niels Basjes |
| [HADOOP-10971](https://issues.apache.org/jira/browse/HADOOP-10971) | Add -C flag to make `hadoop fs -ls` print filenames only |  Major | fs | Ryan Williams | Kengo Seki |
| [HADOOP-9477](https://issues.apache.org/jira/browse/HADOOP-9477) | Add posixGroups support for LDAP groups mapping service |  Major | . | Kai Zheng | Dapeng Sun |
| [HADOOP-8934](https://issues.apache.org/jira/browse/HADOOP-8934) | Shell command ls should include sort options |  Minor | fs | Jonathan Allen | Jonathan Allen |
| [HADOOP-5732](https://issues.apache.org/jira/browse/HADOOP-5732) | Add SFTP FileSystem |  Minor | fs | Íñigo Goiri | ramtin |
| [HDFS-9711](https://issues.apache.org/jira/browse/HDFS-9711) | Integrate CSRF prevention filter in WebHDFS. |  Major | datanode, namenode, webhdfs | Chris Nauroth | Chris Nauroth |
| [HDFS-9244](https://issues.apache.org/jira/browse/HDFS-9244) | Support nested encryption zones |  Major | encryption | Xiaoyu Yao | Zhe Zhang |
| [HDFS-8622](https://issues.apache.org/jira/browse/HDFS-8622) | Implement GETCONTENTSUMMARY operation for WebImageViewer |  Major | . | Jagadesh Kiran N | Jagadesh Kiran N |
| [HDFS-8608](https://issues.apache.org/jira/browse/HDFS-8608) | Merge HDFS-7912 to trunk and branch-2 (track BlockInfo instead of Block in UnderReplicatedBlocks and PendingReplicationBlocks) |  Major | . | Zhe Zhang | Zhe Zhang |
| [HDFS-8487](https://issues.apache.org/jira/browse/HDFS-8487) | Generalize BlockInfo in preparation of merging HDFS-7285 into trunk and branch-2 |  Major | namenode | Zhe Zhang | Zhe Zhang |
| [HDFS-8155](https://issues.apache.org/jira/browse/HDFS-8155) | Support OAuth2 in WebHDFS |  Major | webhdfs | Jakob Homan | Jakob Homan |
| [HDFS-8009](https://issues.apache.org/jira/browse/HDFS-8009) | Signal congestion on the DataNode |  Major | datanode | Haohui Mai | Haohui Mai |
| [HDFS-8008](https://issues.apache.org/jira/browse/HDFS-8008) | Support client-side back off when the datanodes are congested |  Major | hdfs-client | Haohui Mai | Haohui Mai |
| [HDFS-7891](https://issues.apache.org/jira/browse/HDFS-7891) | A block placement policy with best rack failure tolerance |  Minor | namenode | Walter Su | Walter Su |
| [MAPREDUCE-6415](https://issues.apache.org/jira/browse/MAPREDUCE-6415) | Create a tool to combine aggregated logs into HAR files |  Major | . | Robert Kanter | Robert Kanter |
| [MAPREDUCE-6364](https://issues.apache.org/jira/browse/MAPREDUCE-6364) | Add a "Kill" link to Task Attempts page |  Minor | applicationmaster | Ryu Kobayashi | Ryu Kobayashi |
| [MAPREDUCE-6304](https://issues.apache.org/jira/browse/MAPREDUCE-6304) | Specifying node labels when submitting MR jobs |  Major | . | Jian Fang | Naganarasimha G R |
| [MAPREDUCE-6284](https://issues.apache.org/jira/browse/MAPREDUCE-6284) | Add Task Attempt State API to MapReduce Application Master REST API |  Minor | . | Ryu Kobayashi | Ryu Kobayashi |
| [YARN-4349](https://issues.apache.org/jira/browse/YARN-4349) | Support CallerContext in YARN |  Major | . | Wangda Tan | Wangda Tan |
| [YARN-3623](https://issues.apache.org/jira/browse/YARN-3623) | We should have a config to indicate the Timeline Service version |  Major | timelineserver | Zhijie Shen | Xuan Gong |
| [YARN-3458](https://issues.apache.org/jira/browse/YARN-3458) | CPU resource monitoring in Windows |  Minor | nodemanager | Inigo Goiri | Inigo Goiri |
| [YARN-2901](https://issues.apache.org/jira/browse/YARN-2901) | Add errors and warning metrics page to RM, NM web UI |  Major | nodemanager, resourcemanager | Varun Vasudev | Varun Vasudev |
| [YARN-261](https://issues.apache.org/jira/browse/YARN-261) | Ability to fail AM attempts |  Major | api | Jason Lowe | Rohith Sharma K S |


### IMPROVEMENTS:

| JIRA | Summary | Priority | Component | Reporter | Contributor |
|:---- |:---- | :--- |:---- |:---- |:---- |
| [HADOOP-12828](https://issues.apache.org/jira/browse/HADOOP-12828) | Print user when services are started |  Trivial | . | Brandon Li | Wei-Chiu Chuang |
| [HADOOP-12824](https://issues.apache.org/jira/browse/HADOOP-12824) | Collect network and disk usage on the node running Windows |  Major | . | Inigo Goiri | Inigo Goiri |
| [HADOOP-12805](https://issues.apache.org/jira/browse/HADOOP-12805) | Annotate CanUnbuffer with @InterfaceAudience.Public |  Major | . | Ted Yu | Ted Yu |
| [HADOOP-12794](https://issues.apache.org/jira/browse/HADOOP-12794) | Support additional compression levels for GzipCodec |  Major | io | Ravi Mutyala | Ravi Mutyala |
| [HADOOP-12788](https://issues.apache.org/jira/browse/HADOOP-12788) | OpensslAesCtrCryptoCodec should log which random number generator is used. |  Minor | . | Wei-Chiu Chuang | Wei-Chiu Chuang |
| [HADOOP-12776](https://issues.apache.org/jira/browse/HADOOP-12776) | Remove getaclstatus call for non-acl commands in getfacl. |  Major | . | Brahma Reddy Battula | Brahma Reddy Battula |
| [HADOOP-12764](https://issues.apache.org/jira/browse/HADOOP-12764) | Increase default value of KMS maxHttpHeaderSize and make it configurable |  Minor | . | Zhe Zhang | Zhe Zhang |
| [HADOOP-12758](https://issues.apache.org/jira/browse/HADOOP-12758) | Extend CSRF Filter with UserAgent Checks |  Major | security | Larry McCay | Larry McCay |
| [HADOOP-12731](https://issues.apache.org/jira/browse/HADOOP-12731) | Remove useless boxing/unboxing code |  Minor | performance | Kousuke Saruta | Kousuke Saruta |
| [HADOOP-12686](https://issues.apache.org/jira/browse/HADOOP-12686) | Update FileSystemShell documentation to mention the meaning of each columns of fs -du |  Minor | documentation, fs | Daisuke Kobayashi | Daisuke Kobayashi |
| [HADOOP-12668](https://issues.apache.org/jira/browse/HADOOP-12668) | Support excluding weak Ciphers in HttpServer2 through ssl-server.conf |  Critical | security | Vijay Singh | Vijay Singh |
| [HADOOP-12639](https://issues.apache.org/jira/browse/HADOOP-12639) | Imrpove JavaDoc for getTrimmedStrings |  Trivial | util | BELUGA BEHR | BELUGA BEHR |
| [HADOOP-12600](https://issues.apache.org/jira/browse/HADOOP-12600) | FileContext and AbstractFileSystem should be annotated as a Stable interface. |  Blocker | fs | Chris Nauroth | Chris Nauroth |
| [HADOOP-12575](https://issues.apache.org/jira/browse/HADOOP-12575) | Add build instruction for docker toolbox instead of boot2docker |  Trivial | documentation | Kai Sasaki | Kai Sasaki |
| [HADOOP-12570](https://issues.apache.org/jira/browse/HADOOP-12570) | HDFS Secure Mode Documentation updates |  Major | documentation | Arpit Agarwal | Arpit Agarwal |
| [HADOOP-12568](https://issues.apache.org/jira/browse/HADOOP-12568) | Update core-default.xml to describe posixGroups support |  Minor | documentation | Wei-Chiu Chuang | Wei-Chiu Chuang |
| [HADOOP-12562](https://issues.apache.org/jira/browse/HADOOP-12562) | Make hadoop dockerfile usable by Yetus |  Major | build | Allen Wittenauer | Allen Wittenauer |
| [HADOOP-12555](https://issues.apache.org/jira/browse/HADOOP-12555) | WASB to read credentials from a credential provider |  Minor | azure | Chris Nauroth | Larry McCay |
| [HADOOP-12535](https://issues.apache.org/jira/browse/HADOOP-12535) | Run FileSystem contract tests with hadoop-azure. |  Major | azure, test | Chris Nauroth | madhumita chakraborty |
| [HADOOP-12520](https://issues.apache.org/jira/browse/HADOOP-12520) | Use XInclude in hadoop-azure test configuration to isolate Azure Storage account keys for service integration tests. |  Major | azure, test | Chris Nauroth | Chris Nauroth |
| [HADOOP-12481](https://issues.apache.org/jira/browse/HADOOP-12481) | JWTRedirectAuthenticationHandler doesn't Retain Original Query String |  Major | security | Larry McCay | Larry McCay |
| [HADOOP-12472](https://issues.apache.org/jira/browse/HADOOP-12472) | Make GenericTestUtils.assertExceptionContains robust |  Minor | test | Steve Loughran | Steve Loughran |
| [HADOOP-12460](https://issues.apache.org/jira/browse/HADOOP-12460) | Add overwrite option for 'get' shell command |  Major | . | Keegan Witt | Jagadesh Kiran N |
| [HADOOP-12458](https://issues.apache.org/jira/browse/HADOOP-12458) | Retries is typoed to spell Retires in parts of hadoop-yarn and hadoop-common |  Minor | documentation | Neelesh Srinivas Salian | Neelesh Srinivas Salian |
| [HADOOP-12450](https://issues.apache.org/jira/browse/HADOOP-12450) | UserGroupInformation should not log at WARN level if no groups are found |  Minor | security | Elliott Clark | Elliott Clark |
| [HADOOP-12442](https://issues.apache.org/jira/browse/HADOOP-12442) | Display help if the  command option to "hdfs dfs " is not valid |  Minor | . | nijel | nijel |
| [HADOOP-12428](https://issues.apache.org/jira/browse/HADOOP-12428) | Fix inconsistency between log-level guards and statements |  Minor | . | Jackie Chang | Jagadesh Kiran N |
| [HADOOP-12420](https://issues.apache.org/jira/browse/HADOOP-12420) | While trying to access Amazon S3 through hadoop-aws(Spark basically) I was getting Exception in thread "main" java.lang.NoSuchMethodError: com.amazonaws.services.s3.transfer.TransferManagerConfiguration.setMultipartUploadThreshold(I)V |  Minor | fs/s3 | Tariq Mohammad | Tariq Mohammad |
| [HADOOP-12404](https://issues.apache.org/jira/browse/HADOOP-12404) | Disable caching for JarURLConnection to avoid sharing JarFile with other users when loading resource from URL in Configuration class. |  Minor | conf | zhihai xu | zhihai xu |
| [HADOOP-12384](https://issues.apache.org/jira/browse/HADOOP-12384) | Add "-direct" flag option for fs copy so that user can choose not to create ".\_COPYING\_" file |  Major | fs | Chen He | J.Andreina |
| [HADOOP-12369](https://issues.apache.org/jira/browse/HADOOP-12369) | Point hadoop-project/pom.xml java.security.krb5.conf within target folder |  Minor | . | Andrew Wang | Andrew Wang |
| [HADOOP-12368](https://issues.apache.org/jira/browse/HADOOP-12368) | Mark ViewFileSystemBaseTest and ViewFsBaseTest as abstract |  Trivial | . | Andrew Wang | Andrew Wang |
| [HADOOP-12367](https://issues.apache.org/jira/browse/HADOOP-12367) | Move TestFileUtil's test resources to resources folder |  Minor | . | Andrew Wang | Andrew Wang |
| [HADOOP-12358](https://issues.apache.org/jira/browse/HADOOP-12358) | Add -safely flag to rm to prompt when deleting many files |  Major | fs | Xiaoyu Yao | Xiaoyu Yao |
| [HADOOP-12350](https://issues.apache.org/jira/browse/HADOOP-12350) | WASB Logging: Improve WASB Logging around deletes, reads and writes |  Major | tools | Dushyanth | Dushyanth |
| [HADOOP-12344](https://issues.apache.org/jira/browse/HADOOP-12344) | Improve validateSocketPathSecurity0 error message |  Trivial | net | Casey Brotherton | Casey Brotherton |
| [HADOOP-12334](https://issues.apache.org/jira/browse/HADOOP-12334) | Change Mode Of Copy Operation of HBase WAL Archiving to bypass Azure Storage Throttling after retries |  Major | tools | Gaurav Kanade | Gaurav Kanade |
| [HADOOP-12325](https://issues.apache.org/jira/browse/HADOOP-12325) | RPC Metrics : Add the ability track and log slow RPCs |  Major | ipc, metrics | Anu Engineer | Anu Engineer |
| [HADOOP-12324](https://issues.apache.org/jira/browse/HADOOP-12324) | Better exception reporting in SaslPlainServer |  Minor | security | Mike Yoder | Mike Yoder |
| [HADOOP-12318](https://issues.apache.org/jira/browse/HADOOP-12318) | Expose underlying LDAP exceptions in SaslPlainServer |  Minor | security | Mike Yoder | Mike Yoder |
| [HADOOP-12295](https://issues.apache.org/jira/browse/HADOOP-12295) | Improve NetworkTopology#InnerNode#remove logic |  Major | . | Yi Liu | Yi Liu |
| [HADOOP-12284](https://issues.apache.org/jira/browse/HADOOP-12284) | UserGroupInformation doAs can throw misleading exception |  Trivial | security | Aaron Dossett | Aaron Dossett |
| [HADOOP-12271](https://issues.apache.org/jira/browse/HADOOP-12271) | Hadoop Jar Error Should Be More Explanatory |  Minor | . | Jesse Anderson | Josh Elser |
| [HADOOP-12259](https://issues.apache.org/jira/browse/HADOOP-12259) | Utility to Dynamic port allocation |  Major | test, util | Brahma Reddy Battula | Brahma Reddy Battula |
| [HADOOP-12214](https://issues.apache.org/jira/browse/HADOOP-12214) | Parse 'HadoopArchive' commandline using cli Options. |  Minor | . | Vinayakumar B | Vinayakumar B |
| [HADOOP-12211](https://issues.apache.org/jira/browse/HADOOP-12211) | Collect disks usages on the node |  Major | . | Robert Grandl | Robert Grandl |
| [HADOOP-12210](https://issues.apache.org/jira/browse/HADOOP-12210) | Collect network usage on the node |  Major | . | Robert Grandl | Robert Grandl |
| [HADOOP-12195](https://issues.apache.org/jira/browse/HADOOP-12195) | Add annotation to package-info.java file to workaround MCOMPILER-205 |  Trivial | . | Andrew Wang | Andrew Wang |
| [HADOOP-12194](https://issues.apache.org/jira/browse/HADOOP-12194) | Support for incremental generation in the protoc plugin |  Major | . | Andrew Wang | Andrew Wang |
| [HADOOP-12193](https://issues.apache.org/jira/browse/HADOOP-12193) | Rename Touchz.java to Touch.java |  Trivial | . | Andrew Wang | Andrew Wang |
| [HADOOP-12189](https://issues.apache.org/jira/browse/HADOOP-12189) | Improve CallQueueManager#swapQueue to make queue elements drop nearly impossible. |  Major | ipc, test | zhihai xu | zhihai xu |
| [HADOOP-12185](https://issues.apache.org/jira/browse/HADOOP-12185) | NetworkTopology is not efficient adding/getting/removing nodes |  Major | . | Inigo Goiri | Inigo Goiri |
| [HADOOP-12183](https://issues.apache.org/jira/browse/HADOOP-12183) | Annotate the HTrace span created by FsShell with the command-line arguments passed by the user |  Minor | tracing | Masatake Iwasaki | Masatake Iwasaki |
| [HADOOP-12180](https://issues.apache.org/jira/browse/HADOOP-12180) | Move ResourceCalculatorPlugin from YARN to Common |  Major | util | Chris Douglas | Chris Douglas |
| [HADOOP-12172](https://issues.apache.org/jira/browse/HADOOP-12172) | FsShell mkdir -p makes an unnecessary check for the existence of the parent. |  Minor | fs | Chris Nauroth | Chris Nauroth |
| [HADOOP-12161](https://issues.apache.org/jira/browse/HADOOP-12161) | Add getStoragePolicy API to the FileSystem interface |  Major | . | Arpit Agarwal | Brahma Reddy Battula |
| [HADOOP-12158](https://issues.apache.org/jira/browse/HADOOP-12158) | Improve error message in TestCryptoStreamsWithOpensslAesCtrCryptoCodec when OpenSSL is not installed |  Trivial | test | Andrew Wang | Andrew Wang |
| [HADOOP-12135](https://issues.apache.org/jira/browse/HADOOP-12135) | cleanup releasedocmaker |  Major | yetus | Allen Wittenauer | Allen Wittenauer |
| [HADOOP-12059](https://issues.apache.org/jira/browse/HADOOP-12059) | S3Credentials should support use of CredentialProvider |  Major | fs/s3 | Sean Busbey | Sean Busbey |
| [HADOOP-12055](https://issues.apache.org/jira/browse/HADOOP-12055) | Deprecate usage of NativeIO#link |  Major | native | Andrew Wang | Andrew Wang |
| [HADOOP-12050](https://issues.apache.org/jira/browse/HADOOP-12050) | Enable MaxInactiveInterval for hadoop http auth token |  Major | security | Benoy Antony | hzlu |
| [HADOOP-12049](https://issues.apache.org/jira/browse/HADOOP-12049) | Control http authentication cookie persistence via configuration |  Major | security | Benoy Antony | hzlu |
| [HADOOP-12045](https://issues.apache.org/jira/browse/HADOOP-12045) | Enable LocalFileSystem#setTimes to change atime |  Minor | fs | Kazuho Fujii | Kazuho Fujii |
| [HADOOP-12043](https://issues.apache.org/jira/browse/HADOOP-12043) | Display warning if defaultFs is not set when running fs commands. |  Minor | fs | Lei (Eddy) Xu | Lei (Eddy) Xu |
| [HADOOP-11995](https://issues.apache.org/jira/browse/HADOOP-11995) | Make jetty version configurable from the maven command line |  Trivial | build, ld | sriharsha devineni | sriharsha devineni |
| [HADOOP-11984](https://issues.apache.org/jira/browse/HADOOP-11984) | Enable parallel JUnit tests in pre-commit. |  Major | build, scripts, test | Chris Nauroth | Chris Nauroth |
| [HADOOP-11971](https://issues.apache.org/jira/browse/HADOOP-11971) | Move test utilities for tracing from hadoop-hdfs to hadoop-common |  Minor | tracing | Masatake Iwasaki | Masatake Iwasaki |
| [HADOOP-11970](https://issues.apache.org/jira/browse/HADOOP-11970) | Replace uses of ThreadLocal\<Random\> with JDK7 ThreadLocalRandom |  Major | . | Sean Busbey | Sean Busbey |
| [HADOOP-11960](https://issues.apache.org/jira/browse/HADOOP-11960) | Enable Azure-Storage Client Side logging. |  Major | tools | Dushyanth | Dushyanth |
| [HADOOP-11950](https://issues.apache.org/jira/browse/HADOOP-11950) | Add cli option to test-patch to set the project-under-test |  Minor | . | Sean Busbey | Sean Busbey |
| [HADOOP-11948](https://issues.apache.org/jira/browse/HADOOP-11948) | test-patch's issue matching regex should be configurable. |  Major | . | Sean Busbey | Sean Busbey |
| [HADOOP-11939](https://issues.apache.org/jira/browse/HADOOP-11939) | Deprecate DistCpV1 and Logalyzer |  Major | . | Brahma Reddy Battula | Brahma Reddy Battula |
| [HADOOP-11925](https://issues.apache.org/jira/browse/HADOOP-11925) | backport trunk's smart-apply-patch.sh to branch-2 |  Major | scripts | Allen Wittenauer | Allen Wittenauer |
| [HADOOP-11911](https://issues.apache.org/jira/browse/HADOOP-11911) | test-patch should allow configuration of default branch |  Minor | . | Sean Busbey | Sean Busbey |
| [HADOOP-11901](https://issues.apache.org/jira/browse/HADOOP-11901) | BytesWritable fails to support 2G chunks due to integer overflow |  Major | . | Reynold Xin | Reynold Xin |
| [HADOOP-11894](https://issues.apache.org/jira/browse/HADOOP-11894) | Bump the version of Apache HTrace to 3.2.0-incubating |  Major | . | Masatake Iwasaki | Masatake Iwasaki |
| [HADOOP-11893](https://issues.apache.org/jira/browse/HADOOP-11893) | Mark org.apache.hadoop.security.token.Token as @InterfaceAudience.Public |  Major | security | Steve Loughran | Brahma Reddy Battula |
| [HADOOP-11827](https://issues.apache.org/jira/browse/HADOOP-11827) | Speed-up distcp buildListing() using threadpool |  Major | tools/distcp | Zoran Dimitrijevic | Zoran Dimitrijevic |
| [HADOOP-11813](https://issues.apache.org/jira/browse/HADOOP-11813) | releasedocmaker.py should use today's date instead of unreleased |  Minor | build | Allen Wittenauer | Darrell Taylor |
| [HADOOP-11807](https://issues.apache.org/jira/browse/HADOOP-11807) | add a lint mode to releasedocmaker |  Minor | build, documentation, yetus | Allen Wittenauer | ramtin |
| [HADOOP-11785](https://issues.apache.org/jira/browse/HADOOP-11785) | Reduce number of listStatus operation in distcp buildListing() |  Minor | tools/distcp | Zoran Dimitrijevic | Zoran Dimitrijevic |
| [HADOOP-11741](https://issues.apache.org/jira/browse/HADOOP-11741) | Add LOG.isDebugEnabled() guard for some LOG.debug() |  Major | . | Walter Su | Walter Su |
| [HADOOP-11737](https://issues.apache.org/jira/browse/HADOOP-11737) | mockito's version in hadoop-nfs’ pom.xml shouldn't be specified |  Minor | nfs | Kengo Seki | Kengo Seki |
| [HADOOP-11719](https://issues.apache.org/jira/browse/HADOOP-11719) | [Fsshell] Remove bin/hadoop reference from GenericOptionsParser default help text |  Minor | scripts | Brahma Reddy Battula | Brahma Reddy Battula |
| [HADOOP-11717](https://issues.apache.org/jira/browse/HADOOP-11717) | Add Redirecting WebSSO behavior with JWT Token in Hadoop Auth |  Major | security | Larry McCay | Larry McCay |
| [HADOOP-11713](https://issues.apache.org/jira/browse/HADOOP-11713) | ViewFileSystem should support snapshot methods. |  Major | fs | Chris Nauroth | Rakesh R |
| [HADOOP-11711](https://issues.apache.org/jira/browse/HADOOP-11711) | Provide a default value for AES/CTR/NoPadding CryptoCodec classes |  Minor | . | Andrew Wang | Andrew Wang |
| [HADOOP-11709](https://issues.apache.org/jira/browse/HADOOP-11709) | Time.NANOSECONDS\_PER\_MILLISECOND - use class-level final constant instead of method variable |  Trivial | . | Ajith S | Ajith S |
| [HADOOP-11692](https://issues.apache.org/jira/browse/HADOOP-11692) | Improve authentication failure WARN message to avoid user confusion |  Major | ipc | Yongjun Zhang | Yongjun Zhang |
| [HADOOP-11660](https://issues.apache.org/jira/browse/HADOOP-11660) | Add support for hardware crc of HDFS checksums on ARM aarch64 architecture |  Minor | native | Edward Nevill | Edward Nevill |
| [HADOOP-11659](https://issues.apache.org/jira/browse/HADOOP-11659) | o.a.h.fs.FileSystem.Cache#remove should use a single hash map lookup |  Minor | fs | Gera Shegalov | Brahma Reddy Battula |
| [HADOOP-11594](https://issues.apache.org/jira/browse/HADOOP-11594) | Improve the readability of site index of documentation |  Minor | documentation | Masatake Iwasaki | Masatake Iwasaki |
| [HADOOP-11447](https://issues.apache.org/jira/browse/HADOOP-11447) | Add a more meaningful toString method to SampleStat and MutableStat |  Minor | metrics | Karthik Kambatla | Karthik Kambatla |
| [HADOOP-11357](https://issues.apache.org/jira/browse/HADOOP-11357) | Print information of the build enviornment in test-patch.sh |  Minor | scripts | Haohui Mai | Allen Wittenauer |
| [HADOOP-11242](https://issues.apache.org/jira/browse/HADOOP-11242) | Record the time of calling in tracing span of IPC server |  Minor | ipc | Masatake Iwasaki | Masatake Iwasaki |
| [HADOOP-11226](https://issues.apache.org/jira/browse/HADOOP-11226) | Add a configuration to set ipc.Client's traffic class with IPTOS\_LOWDELAY\|IPTOS\_RELIABILITY |  Major | ipc | Gopal V | Gopal V |
| [HADOOP-11104](https://issues.apache.org/jira/browse/HADOOP-11104) | org.apache.hadoop.metrics2.lib.MetricsRegistry needs numerical parameter checking |  Minor | . | Ray Chiang | Ray Chiang |
| [HADOOP-11103](https://issues.apache.org/jira/browse/HADOOP-11103) | Clean up RemoteException |  Trivial | ipc | Sean Busbey | Sean Busbey |
| [HADOOP-11031](https://issues.apache.org/jira/browse/HADOOP-11031) | Design Document for Credential Provider API |  Major | site | Larry McCay | Larry McCay |
| [HADOOP-10865](https://issues.apache.org/jira/browse/HADOOP-10865) | Add a Crc32 chunked verification benchmark for both directly and non-directly buffer cases |  Minor | util | Tsz Wo Nicholas Sze | Tsz Wo Nicholas Sze |
| [HADOOP-10775](https://issues.apache.org/jira/browse/HADOOP-10775) | Shell operations to fail with meaningful errors on windows if winutils.exe not found |  Minor | util | Steve Loughran | Steve Loughran |
| [HADOOP-10555](https://issues.apache.org/jira/browse/HADOOP-10555) | Add offset support to MurmurHash |  Trivial | . | Sergey Shelukhin | Sergey Shelukhin |
| [HADOOP-10465](https://issues.apache.org/jira/browse/HADOOP-10465) | Fix use of generics within SortedMapWritable |  Minor | . | Bertrand Dechoux | Bertrand Dechoux |
| [HADOOP-10366](https://issues.apache.org/jira/browse/HADOOP-10366) | Add whitespaces between the classes for values in core-default.xml to fit better in browser |  Minor | documentation | Chengwei Yang | Kanaka Kumar Avvaru |
| [HADOOP-10068](https://issues.apache.org/jira/browse/HADOOP-10068) | Improve log4j regex in testFindContainingJar |  Trivial | . | Robert Rati | Robert Rati |
| [HADOOP-10035](https://issues.apache.org/jira/browse/HADOOP-10035) | Cleanup TestFilterFileSystem |  Major | . | Suresh Srinivas | Suresh Srinivas |
| [HADOOP-9805](https://issues.apache.org/jira/browse/HADOOP-9805) | Refactor RawLocalFileSystem#rename for improved testability. |  Minor | fs, test | Chris Nauroth | Jean-Pierre Matsumoto |
| [HADOOP-9737](https://issues.apache.org/jira/browse/HADOOP-9737) | JarFinder#getJar should delete the jar file upon destruction of the JVM |  Major | util | Esteban Gutierrez | Jean-Baptiste Onofré |
| [HADOOP-9723](https://issues.apache.org/jira/browse/HADOOP-9723) | Improve error message when hadoop archive output path already exists |  Trivial | . | Stephen Chu | Yongjun Zhang |
| [HADOOP-7713](https://issues.apache.org/jira/browse/HADOOP-7713) | dfs -count -q should label output column |  Trivial | . | Nigel Daley | Jonathan Allen |
| [HADOOP-7266](https://issues.apache.org/jira/browse/HADOOP-7266) | Deprecate metrics v1 |  Blocker | metrics | Luke Lu | Akira AJISAKA |
| [HADOOP-6842](https://issues.apache.org/jira/browse/HADOOP-6842) | "hadoop fs -text" does not give a useful text representation of MapWritable objects |  Major | io | Steven Wong | Akira AJISAKA |
| [HADOOP-1540](https://issues.apache.org/jira/browse/HADOOP-1540) | Support file exclusion list in distcp |  Minor | util | Senthil Subramanian | Rich Haase |
| [HDFS-9854](https://issues.apache.org/jira/browse/HDFS-9854) | Log cipher suite negotiation more verbosely |  Major | . | Wei-Chiu Chuang | Wei-Chiu Chuang |
| [HDFS-9843](https://issues.apache.org/jira/browse/HDFS-9843) | Document distcp options required for copying between encrypted locations |  Major | distcp, documentation, encryption | Xiaoyu Yao | Xiaoyu Yao |
| [HDFS-9831](https://issues.apache.org/jira/browse/HDFS-9831) | Document webhdfs retry configuration keys introduced by HDFS-5219/HDFS-5122 |  Major | documentation, webhdfs | Xiaoyu Yao | Xiaobing Zhou |
| [HDFS-9797](https://issues.apache.org/jira/browse/HDFS-9797) | Log Standby exceptions thrown by RequestHedgingProxyProvider at DEBUG Level |  Minor | hdfs-client | Inigo Goiri | Inigo Goiri |
| [HDFS-9768](https://issues.apache.org/jira/browse/HDFS-9768) | Reuse objectMapper instance in HDFS to improve the performance |  Major | performance | Lin Yiqun | Lin Yiqun |
| [HDFS-9726](https://issues.apache.org/jira/browse/HDFS-9726) | Refactor IBR code to a new class |  Minor | datanode | Tsz Wo Nicholas Sze | Tsz Wo Nicholas Sze |
| [HDFS-9721](https://issues.apache.org/jira/browse/HDFS-9721) | Allow Delimited PB OIV tool to run upon fsimage that contains INodeReference |  Major | . | Xiao Chen | Xiao Chen |
| [HDFS-9715](https://issues.apache.org/jira/browse/HDFS-9715) | Check storage ID uniqueness on datanode startup |  Major | datanode | Lei (Eddy) Xu | Lei (Eddy) Xu |
| [HDFS-9710](https://issues.apache.org/jira/browse/HDFS-9710) | Change DN to send block receipt IBRs in batches |  Major | datanode | Tsz Wo Nicholas Sze | Tsz Wo Nicholas Sze |
| [HDFS-9706](https://issues.apache.org/jira/browse/HDFS-9706) | Log more details in debug logs in BlockReceiver's constructor |  Minor | . | Xiao Chen | Xiao Chen |
| [HDFS-9700](https://issues.apache.org/jira/browse/HDFS-9700) | DFSClient and DFSOutputStream should set TCP\_NODELAY on sockets for DataTransferProtocol |  Major | hdfs-client | Gary Helmling | Gary Helmling |
| [HDFS-9686](https://issues.apache.org/jira/browse/HDFS-9686) | Remove useless boxing/unboxing code |  Minor | performance | Kousuke Saruta | Kousuke Saruta |
| [HDFS-9653](https://issues.apache.org/jira/browse/HDFS-9653) | Expose the number of blocks pending deletion through dfsadmin report command |  Major | hdfs-client, tools | Weiwei Yang | Weiwei Yang |
| [HDFS-9644](https://issues.apache.org/jira/browse/HDFS-9644) | Update encryption documentation to reflect nested EZs |  Major | documentation, encryption | Zhe Zhang | Zhe Zhang |
| [HDFS-9638](https://issues.apache.org/jira/browse/HDFS-9638) | Improve DistCp Help and documentation |  Minor | distcp | Wei-Chiu Chuang | Wei-Chiu Chuang |
| [HDFS-9630](https://issues.apache.org/jira/browse/HDFS-9630) | DistCp minor refactoring and clean up |  Minor | distcp | Kai Zheng | Kai Zheng |
| [HDFS-9629](https://issues.apache.org/jira/browse/HDFS-9629) | Update the footer of Web UI to show year 2016 |  Major | . | Xiao Chen | Xiao Chen |
| [HDFS-9566](https://issues.apache.org/jira/browse/HDFS-9566) | Remove expensive 'BlocksMap#getStorages(Block b, final DatanodeStorage.State state)' method |  Major | namenode | Daryn Sharp | Daryn Sharp |
| [HDFS-9557](https://issues.apache.org/jira/browse/HDFS-9557) | Reduce object allocation in PB conversion |  Major | hdfs-client | Daryn Sharp | Daryn Sharp |
| [HDFS-9552](https://issues.apache.org/jira/browse/HDFS-9552) | Document types of permission checks performed for HDFS operations. |  Major | documentation | Chris Nauroth | Chris Nauroth |
| [HDFS-9532](https://issues.apache.org/jira/browse/HDFS-9532) | Detailed exception info is lost in reportTo method of ErrorReportAction and ReportBadBlockAction |  Trivial | datanode | Yongjun Zhang | Yongjun Zhang |
| [HDFS-9528](https://issues.apache.org/jira/browse/HDFS-9528) | Cleanup namenode audit/log/exception messages |  Minor | namenode | Tsz Wo Nicholas Sze | Tsz Wo Nicholas Sze |
| [HDFS-9527](https://issues.apache.org/jira/browse/HDFS-9527) | The return type of FSNamesystem.getBlockCollection should be changed to INodeFile |  Minor | namenode | Tsz Wo Nicholas Sze | Tsz Wo Nicholas Sze |
| [HDFS-9490](https://issues.apache.org/jira/browse/HDFS-9490) | MiniDFSCluster should change block generation stamp via FsDatasetTestUtils |  Minor | test | Tony Wu | Tony Wu |
| [HDFS-9485](https://issues.apache.org/jira/browse/HDFS-9485) | Make BlockManager#removeFromExcessReplicateMap accept BlockInfo instead of Block |  Minor | namenode | Mingliang Liu | Mingliang Liu |
| [HDFS-9474](https://issues.apache.org/jira/browse/HDFS-9474) | TestPipelinesFailover should not fail when printing debug message |  Major | . | Yongjun Zhang | John Zhuge |
| [HDFS-9472](https://issues.apache.org/jira/browse/HDFS-9472) | concat() API does not give proper exception messages on ./reserved relative path |  Major | namenode | Rakesh R | Rakesh R |
| [HDFS-9439](https://issues.apache.org/jira/browse/HDFS-9439) | Include status of closeAck into exception message in DataNode#run |  Trivial | . | Xiao Chen | Xiao Chen |
| [HDFS-9436](https://issues.apache.org/jira/browse/HDFS-9436) | Make NNThroughputBenchmark$BlockReportStats run with 10 datanodes by default |  Minor | test | Mingliang Liu | Mingliang Liu |
| [HDFS-9425](https://issues.apache.org/jira/browse/HDFS-9425) | Expose number of blocks per volume as a metric |  Major | . | Brahma Reddy Battula | Brahma Reddy Battula |
| [HDFS-9415](https://issues.apache.org/jira/browse/HDFS-9415) | Document dfs.cluster.administrators and dfs.permissions.superusergroup |  Major | documentation | Arpit Agarwal | Xiaobing Zhou |
| [HDFS-9402](https://issues.apache.org/jira/browse/HDFS-9402) | Switch DataNode.LOG to use slf4j |  Minor | . | Walter Su | Walter Su |
| [HDFS-9398](https://issues.apache.org/jira/browse/HDFS-9398) | Make ByteArraryManager log message in one-line format |  Minor | hdfs-client | Mingliang Liu | Mingliang Liu |
| [HDFS-9379](https://issues.apache.org/jira/browse/HDFS-9379) | Make NNThroughputBenchmark$BlockReportStats support more than 10 datanodes |  Major | test | Mingliang Liu | Mingliang Liu |
| [HDFS-9369](https://issues.apache.org/jira/browse/HDFS-9369) | Use ctest to run tests for hadoop-hdfs-native-client |  Minor | . | Haohui Mai | Haohui Mai |
| [HDFS-9363](https://issues.apache.org/jira/browse/HDFS-9363) | Add fetchReplica() to FsDatasetTestUtils to return FsDataset-agnostic Replica. |  Minor | test | Tony Wu | Tony Wu |
| [HDFS-9331](https://issues.apache.org/jira/browse/HDFS-9331) | Modify TestNameNodeMXBean#testNameNodeMXBeanInfo() to account for filesystem entirely allocated for DFS use |  Trivial | test | Tony Wu | Tony Wu |
| [HDFS-9314](https://issues.apache.org/jira/browse/HDFS-9314) | Improve BlockPlacementPolicyDefault's picking of excess replicas |  Major | . | Ming Ma | Xiao Chen |
| [HDFS-9312](https://issues.apache.org/jira/browse/HDFS-9312) | Fix TestReplication to be FsDataset-agnostic. |  Minor | . | Lei (Eddy) Xu | Lei (Eddy) Xu |
| [HDFS-9311](https://issues.apache.org/jira/browse/HDFS-9311) | Support optional offload of NameNode HA service health checks to a separate RPC server. |  Major | ha, namenode | Chris Nauroth | Chris Nauroth |
| [HDFS-9308](https://issues.apache.org/jira/browse/HDFS-9308) | Add truncateMeta() and deleteMeta() to MiniDFSCluster |  Minor | test | Tony Wu | Tony Wu |
| [HDFS-9307](https://issues.apache.org/jira/browse/HDFS-9307) | fuseConnect should be private to fuse\_connect.c |  Trivial | fuse-dfs | Colin Patrick McCabe | Mingliang Liu |
| [HDFS-9299](https://issues.apache.org/jira/browse/HDFS-9299) | Give ReplicationMonitor a readable thread name |  Trivial | namenode | Staffan Friberg | Staffan Friberg |
| [HDFS-9297](https://issues.apache.org/jira/browse/HDFS-9297) | Update TestBlockMissingException to use corruptBlockOnDataNodesByDeletingBlockFile() |  Trivial | test | Tony Wu | Tony Wu |
| [HDFS-9292](https://issues.apache.org/jira/browse/HDFS-9292) | Make TestFileConcorruption independent to underlying FsDataset Implementation. |  Minor | . | Lei (Eddy) Xu | Lei (Eddy) Xu |
| [HDFS-9291](https://issues.apache.org/jira/browse/HDFS-9291) | Fix TestInterDatanodeProtocol to be FsDataset-agnostic. |  Minor | test | Lei (Eddy) Xu | Lei (Eddy) Xu |
| [HDFS-9282](https://issues.apache.org/jira/browse/HDFS-9282) | Make data directory count and storage raw capacity related tests FsDataset-agnostic |  Minor | test | Tony Wu | Tony Wu |
| [HDFS-9280](https://issues.apache.org/jira/browse/HDFS-9280) | Document NFS gateway export point parameter |  Trivial | documentation | Zhe Zhang | Xiao Chen |
| [HDFS-9269](https://issues.apache.org/jira/browse/HDFS-9269) | Update the documentation and wrapper for fuse-dfs |  Minor | fuse-dfs | Wei-Chiu Chuang | Wei-Chiu Chuang |
| [HDFS-9264](https://issues.apache.org/jira/browse/HDFS-9264) | Minor cleanup of operations on FsVolumeList#volumes |  Minor | . | Walter Su | Walter Su |
| [HDFS-9259](https://issues.apache.org/jira/browse/HDFS-9259) | Make SO\_SNDBUF size configurable at DFSClient side for hdfs write scenario |  Major | . | Ming Ma | Mingliang Liu |
| [HDFS-9257](https://issues.apache.org/jira/browse/HDFS-9257) | improve error message for "Absolute path required" in INode.java to contain the rejected path |  Trivial | namenode | Marcell Szabo | Marcell Szabo |
| [HDFS-9255](https://issues.apache.org/jira/browse/HDFS-9255) | Consolidate block recovery related implementation into a single class |  Minor | datanode | Walter Su | Walter Su |
| [HDFS-9253](https://issues.apache.org/jira/browse/HDFS-9253) | Refactor tests of libhdfs into a directory |  Major | . | Haohui Mai | Haohui Mai |
| [HDFS-9252](https://issues.apache.org/jira/browse/HDFS-9252) | Change TestFileTruncate to use FsDatasetTestUtils to get block file size and genstamp. |  Major | . | Lei (Eddy) Xu | Lei (Eddy) Xu |
| [HDFS-9251](https://issues.apache.org/jira/browse/HDFS-9251) | Refactor TestWriteToReplica and TestFsDatasetImpl to avoid explicitly creating Files in tests code. |  Major | test | Lei (Eddy) Xu | Lei (Eddy) Xu |
| [HDFS-9250](https://issues.apache.org/jira/browse/HDFS-9250) | Add Precondition check to LocatedBlock#addCachedLoc |  Major | namenode | Xiao Chen | Xiao Chen |
| [HDFS-9238](https://issues.apache.org/jira/browse/HDFS-9238) | Update TestFileCreation#testLeaseExpireHardLimit() to avoid using DataNodeTestUtils#getFile() |  Trivial | test | Tony Wu | Tony Wu |
| [HDFS-9234](https://issues.apache.org/jira/browse/HDFS-9234) | WebHdfs : getContentSummary() should give quota for storage types |  Major | webhdfs | Surendra Singh Lilhore | Surendra Singh Lilhore |
| [HDFS-9229](https://issues.apache.org/jira/browse/HDFS-9229) | Expose size of NameNode directory as a metric |  Minor | namenode | Zhe Zhang | Surendra Singh Lilhore |
| [HDFS-9205](https://issues.apache.org/jira/browse/HDFS-9205) | Do not schedule corrupt blocks for replication |  Minor | namenode | Tsz Wo Nicholas Sze | Tsz Wo Nicholas Sze |
| [HDFS-9198](https://issues.apache.org/jira/browse/HDFS-9198) | Coalesce IBR processing in the NN |  Major | namenode | Daryn Sharp | Daryn Sharp |
| [HDFS-9188](https://issues.apache.org/jira/browse/HDFS-9188) | Make block corruption related tests FsDataset-agnostic. |  Major | test | Lei (Eddy) Xu | Lei (Eddy) Xu |
| [HDFS-9181](https://issues.apache.org/jira/browse/HDFS-9181) | Better handling of exceptions thrown during upgrade shutdown |  Minor | . | Wei-Chiu Chuang | Wei-Chiu Chuang |
| [HDFS-9175](https://issues.apache.org/jira/browse/HDFS-9175) | Change scope of 'AccessTokenProvider.getAccessToken()' and 'CredentialBasedAccessTokenProvider.getCredential()' abstract methods to public |  Major | webhdfs | Santhosh G Nayak | Santhosh G Nayak |
| [HDFS-9151](https://issues.apache.org/jira/browse/HDFS-9151) | Mover should print the exit status/reason on console like balancer tool. |  Minor | balancer & mover | Archana T | Surendra Singh Lilhore |
| [HDFS-9148](https://issues.apache.org/jira/browse/HDFS-9148) | Incorrect assert message in TestWriteToReplica#testWriteToTemporary |  Trivial | test | Tony Wu | Tony Wu |
| [HDFS-9145](https://issues.apache.org/jira/browse/HDFS-9145) | Tracking methods that hold FSNamesytemLock for too long |  Major | namenode | Jing Zhao | Mingliang Liu |
| [HDFS-9139](https://issues.apache.org/jira/browse/HDFS-9139) | Enable parallel JUnit tests for HDFS Pre-commit |  Major | test | Vinayakumar B | Vinayakumar B |
| [HDFS-9132](https://issues.apache.org/jira/browse/HDFS-9132) | Pass genstamp to ReplicaAccessorBuilder |  Major | hdfs-client | Colin Patrick McCabe | Colin Patrick McCabe |
| [HDFS-9112](https://issues.apache.org/jira/browse/HDFS-9112) | Improve error message for Haadmin when multiple name service IDs are configured |  Major | tools | Anu Engineer | Anu Engineer |
| [HDFS-9110](https://issues.apache.org/jira/browse/HDFS-9110) | Use Files.walkFileTree in NNUpgradeUtil#doPreUpgrade for better efficiency |  Minor | . | Charlie Helin | Charlie Helin |
| [HDFS-9082](https://issues.apache.org/jira/browse/HDFS-9082) | Change the log level in WebHdfsFileSystem.initialize() from INFO to DEBUG |  Minor | webhdfs | Santhosh G Nayak | Santhosh G Nayak |
| [HDFS-9065](https://issues.apache.org/jira/browse/HDFS-9065) | Include commas on # of files, blocks, total filesystem objects in NN Web UI |  Minor | namenode | Daniel Templeton | Daniel Templeton |
| [HDFS-9024](https://issues.apache.org/jira/browse/HDFS-9024) | Deprecate the TotalFiles metric |  Major | . | Akira AJISAKA | Akira AJISAKA |
| [HDFS-9021](https://issues.apache.org/jira/browse/HDFS-9021) | Use a yellow elephant rather than a blue one in diagram |  Minor | . | Andrew Wang | Andrew Wang |
| [HDFS-9019](https://issues.apache.org/jira/browse/HDFS-9019) | Adding informative message to sticky bit permission denied exception |  Minor | security | Thejas M Nair | Xiaoyu Yao |
| [HDFS-8988](https://issues.apache.org/jira/browse/HDFS-8988) | Use LightWeightHashSet instead of LightWeightLinkedSet in BlockManager#excessReplicateMap |  Major | . | Yi Liu | Yi Liu |
| [HDFS-8983](https://issues.apache.org/jira/browse/HDFS-8983) | NameNode support for protected directories |  Major | namenode | Arpit Agarwal | Arpit Agarwal |
| [HDFS-8974](https://issues.apache.org/jira/browse/HDFS-8974) | Convert docs in xdoc format to markdown |  Minor | documentation | Masatake Iwasaki | Masatake Iwasaki |
| [HDFS-8965](https://issues.apache.org/jira/browse/HDFS-8965) | Harden edit log reading code against out of memory errors |  Major | . | Colin Patrick McCabe | Colin Patrick McCabe |
| [HDFS-8953](https://issues.apache.org/jira/browse/HDFS-8953) | DataNode Metrics logging |  Major | . | Kanaka Kumar Avvaru | Kanaka Kumar Avvaru |
| [HDFS-8946](https://issues.apache.org/jira/browse/HDFS-8946) | Improve choosing datanode storage for block placement |  Major | namenode | Yi Liu | Yi Liu |
| [HDFS-8945](https://issues.apache.org/jira/browse/HDFS-8945) | Update the description about replica placement in HDFS Architecture documentation |  Minor | documentation | Masatake Iwasaki | Masatake Iwasaki |
| [HDFS-8929](https://issues.apache.org/jira/browse/HDFS-8929) | Add a metric to expose the timestamp of the last journal |  Major | journal-node | Akira AJISAKA | Surendra Singh Lilhore |
| [HDFS-8928](https://issues.apache.org/jira/browse/HDFS-8928) | Improvements for BlockUnderConstructionFeature: ReplicaUnderConstruction as a separate class and replicas as an array |  Minor | namenode | Zhe Zhang | Jing Zhao |
| [HDFS-8924](https://issues.apache.org/jira/browse/HDFS-8924) | Add pluggable interface for reading replicas in DFSClient |  Major | hdfs-client | Colin Patrick McCabe | Colin Patrick McCabe |
| [HDFS-8917](https://issues.apache.org/jira/browse/HDFS-8917) | Cleanup BlockInfoUnderConstruction from comments and tests |  Minor | namenode | Zhe Zhang | Zhe Zhang |
| [HDFS-8911](https://issues.apache.org/jira/browse/HDFS-8911) | NameNode Metric : Add Editlog counters as a JMX metric |  Major | namenode | Anu Engineer | Anu Engineer |
| [HDFS-8887](https://issues.apache.org/jira/browse/HDFS-8887) | Expose storage type and storage ID in BlockLocation |  Major | . | Andrew Wang | Andrew Wang |
| [HDFS-8884](https://issues.apache.org/jira/browse/HDFS-8884) | Fail-fast check in BlockPlacementPolicyDefault#chooseTarget |  Major | . | Yi Liu | Yi Liu |
| [HDFS-8883](https://issues.apache.org/jira/browse/HDFS-8883) | NameNode Metrics : Add FSNameSystem lock Queue Length |  Major | namenode | Anu Engineer | Anu Engineer |
| [HDFS-8880](https://issues.apache.org/jira/browse/HDFS-8880) | NameNode metrics logging |  Major | namenode | Arpit Agarwal | Arpit Agarwal |
| [HDFS-8873](https://issues.apache.org/jira/browse/HDFS-8873) | Allow the directoryScanner to be rate-limited |  Major | datanode | Nathan Roberts | Daniel Templeton |
| [HDFS-8865](https://issues.apache.org/jira/browse/HDFS-8865) | Improve quota initialization performance |  Major | . | Kihwal Lee | Kihwal Lee |
| [HDFS-8860](https://issues.apache.org/jira/browse/HDFS-8860) | Remove unused Replica copyOnWrite code |  Major | . | Lei (Eddy) Xu | Lei (Eddy) Xu |
| [HDFS-8859](https://issues.apache.org/jira/browse/HDFS-8859) | Improve DataNode ReplicaMap memory footprint to save about 45% |  Major | datanode | Yi Liu | Yi Liu |
| [HDFS-8831](https://issues.apache.org/jira/browse/HDFS-8831) | Trash Support for deletion in HDFS encryption zone |  Major | encryption | Xiaoyu Yao | Xiaoyu Yao |
| [HDFS-8829](https://issues.apache.org/jira/browse/HDFS-8829) | Make SO\_RCVBUF and SO\_SNDBUF size configurable for DataTransferProtocol sockets and allow configuring auto-tuning |  Major | datanode | He Tianyi | He Tianyi |
| [HDFS-8828](https://issues.apache.org/jira/browse/HDFS-8828) | Utilize Snapshot diff report to build diff copy list in distcp |  Major | distcp, snapshots | Yufei Gu | Yufei Gu |
| [HDFS-8822](https://issues.apache.org/jira/browse/HDFS-8822) | Add SSD storagepolicy tests in TestBlockStoragePolicy#testDefaultPolicies |  Major | . | Vinayakumar B | Vinayakumar B |
| [HDFS-8821](https://issues.apache.org/jira/browse/HDFS-8821) | Explain message "Operation category X is not supported in state standby" |  Minor | . | Gautam Gopalakrishnan | Gautam Gopalakrishnan |
| [HDFS-8816](https://issues.apache.org/jira/browse/HDFS-8816) | Improve visualization for the Datanode tab in the NN UI |  Major | . | Haohui Mai | Haohui Mai |
| [HDFS-8815](https://issues.apache.org/jira/browse/HDFS-8815) | DFS getStoragePolicy implementation using single RPC call |  Major | hdfs-client | Arpit Agarwal | Surendra Singh Lilhore |
| [HDFS-8811](https://issues.apache.org/jira/browse/HDFS-8811) | Move BlockStoragePolicy name's constants from HdfsServerConstants.java to HdfsConstants.java |  Major | . | Vinayakumar B | Vinayakumar B |
| [HDFS-8808](https://issues.apache.org/jira/browse/HDFS-8808) | dfs.image.transfer.bandwidthPerSec should not apply to -bootstrapStandby |  Major | . | Gautam Gopalakrishnan | Zhe Zhang |
| [HDFS-8735](https://issues.apache.org/jira/browse/HDFS-8735) | Inotify : All events classes should implement toString() API. |  Major | hdfs-client | Surendra Singh Lilhore | Surendra Singh Lilhore |
| [HDFS-8713](https://issues.apache.org/jira/browse/HDFS-8713) | Convert DatanodeDescriptor to use SLF4J logging |  Trivial | . | Andrew Wang | Andrew Wang |
| [HDFS-8712](https://issues.apache.org/jira/browse/HDFS-8712) | Remove "public" and "abstract" modifiers in FsVolumeSpi and FsDatasetSpi |  Trivial | . | Lei (Eddy) Xu | Lei (Eddy) Xu |
| [HDFS-8711](https://issues.apache.org/jira/browse/HDFS-8711) | setSpaceQuota command should print the available storage type when input storage type is wrong |  Major | hdfs-client | Surendra Singh Lilhore | Surendra Singh Lilhore |
| [HDFS-8709](https://issues.apache.org/jira/browse/HDFS-8709) | Clarify automatic sync in FSEditLog#logEdit |  Minor | . | Andrew Wang | Andrew Wang |
| [HDFS-8703](https://issues.apache.org/jira/browse/HDFS-8703) | Merge refactor of DFSInputStream from ErasureCoding branch |  Major | . | Vinayakumar B | Vinayakumar B |
| [HDFS-8696](https://issues.apache.org/jira/browse/HDFS-8696) | Make the lower and higher watermark in the DN Netty server configurable |  Major | webhdfs | Xiaobing Zhou | Xiaobing Zhou |
| [HDFS-8653](https://issues.apache.org/jira/browse/HDFS-8653) | Code cleanup for DatanodeManager, DatanodeDescriptor and DatanodeStorageInfo |  Major | . | Zhe Zhang | Zhe Zhang |
| [HDFS-8647](https://issues.apache.org/jira/browse/HDFS-8647) | Abstract BlockManager's rack policy into BlockPlacementPolicy |  Major | . | Ming Ma | Brahma Reddy Battula |
| [HDFS-8640](https://issues.apache.org/jira/browse/HDFS-8640) | Make reserved RBW space visible through JMX |  Major | . | Kanaka Kumar Avvaru | Kanaka Kumar Avvaru |
| [HDFS-8639](https://issues.apache.org/jira/browse/HDFS-8639) | Option for HTTP port of NameNode by MiniDFSClusterManager |  Minor | test | Kai Sasaki | Kai Sasaki |
| [HDFS-8606](https://issues.apache.org/jira/browse/HDFS-8606) | Cleanup DFSOutputStream by removing unwanted changes |  Minor | hdfs-client | Rakesh R | Rakesh R |
| [HDFS-8605](https://issues.apache.org/jira/browse/HDFS-8605) | Merge Refactor of DFSOutputStream from HDFS-7285 branch |  Major | . | Vinayakumar B | Vinayakumar B |
| [HDFS-8589](https://issues.apache.org/jira/browse/HDFS-8589) | Fix unused imports in BPServiceActor and BlockReportLeaseManager |  Trivial | . | Colin Patrick McCabe | Colin Patrick McCabe |
| [HDFS-8582](https://issues.apache.org/jira/browse/HDFS-8582) | Support getting a list of reconfigurable config properties and do not generate spurious reconfig warnings |  Minor | datanode, hdfs-client | Lei (Eddy) Xu | Lei (Eddy) Xu |
| [HDFS-8573](https://issues.apache.org/jira/browse/HDFS-8573) | Move creation of restartMeta file logic from BlockReceiver to ReplicaInPipeline |  Major | datanode | Lei (Eddy) Xu | Lei (Eddy) Xu |
| [HDFS-8553](https://issues.apache.org/jira/browse/HDFS-8553) | Document hdfs class path options |  Major | documentation | Xiaoyu Yao | Brahma Reddy Battula |
| [HDFS-8549](https://issues.apache.org/jira/browse/HDFS-8549) | Abort the balancer if an upgrade is in progress |  Major | balancer & mover | Andrew Wang | Andrew Wang |
| [HDFS-8546](https://issues.apache.org/jira/browse/HDFS-8546) | Use try with resources in DataStorage and Storage |  Minor | datanode | Andrew Wang | Andrew Wang |
| [HDFS-8545](https://issues.apache.org/jira/browse/HDFS-8545) | Refactor FS#getUsed() to use ContentSummary and add an API to fetch the total file length from a specific path |  Minor | . | J.Andreina | J.Andreina |
| [HDFS-8535](https://issues.apache.org/jira/browse/HDFS-8535) | Clarify that dfs usage in dfsadmin -report output includes all block replicas. |  Minor | documentation | Lei (Eddy) Xu | Lei (Eddy) Xu |
| [HDFS-8532](https://issues.apache.org/jira/browse/HDFS-8532) | Make the visibility of DFSOutputStream#streamer member variable to private |  Trivial | . | Rakesh R | Rakesh R |
| [HDFS-8512](https://issues.apache.org/jira/browse/HDFS-8512) | WebHDFS : GETFILESTATUS should return LocatedBlock with storage type info |  Major | webhdfs | Sumana Sathish | Xiaoyu Yao |
| [HDFS-8490](https://issues.apache.org/jira/browse/HDFS-8490) | Typo in trace enabled log in ExceptionHandler of WebHDFS |  Trivial | webhdfs | Jakob Homan | Archana T |
| [HDFS-8462](https://issues.apache.org/jira/browse/HDFS-8462) | Implement GETXATTRS and LISTXATTRS operations for WebImageViewer |  Major | . | Akira AJISAKA | Jagadesh Kiran N |
| [HDFS-8443](https://issues.apache.org/jira/browse/HDFS-8443) | Document dfs.namenode.service.handler.count in hdfs-site.xml |  Major | documentation | Akira AJISAKA | J.Andreina |
| [HDFS-8435](https://issues.apache.org/jira/browse/HDFS-8435) | Support CreateFlag in WebHdfs |  Major | webhdfs | Vinoth Sathappan | Jakob Homan |
| [HDFS-8432](https://issues.apache.org/jira/browse/HDFS-8432) | Introduce a minimum compatible layout version to allow downgrade in more rolling upgrade use cases. |  Major | namenode, rolling upgrades | Chris Nauroth | Chris Nauroth |
| [HDFS-8397](https://issues.apache.org/jira/browse/HDFS-8397) | Refactor the error handling code in DataStreamer |  Minor | hdfs-client | Tsz Wo Nicholas Sze | Tsz Wo Nicholas Sze |
| [HDFS-8394](https://issues.apache.org/jira/browse/HDFS-8394) | Move getAdditionalBlock() and related functionalities into a separate class |  Major | . | Haohui Mai | Haohui Mai |
| [HDFS-8357](https://issues.apache.org/jira/browse/HDFS-8357) | Consolidate parameters of INode.CleanSubtree() into a parameter objects. |  Major | . | Haohui Mai | Li Lu |
| [HDFS-8350](https://issues.apache.org/jira/browse/HDFS-8350) | Remove old webhdfs.xml and other outdated documentation stuff |  Major | documentation | Akira AJISAKA | Brahma Reddy Battula |
| [HDFS-8327](https://issues.apache.org/jira/browse/HDFS-8327) | Simplify quota calculations for snapshots and truncate |  Major | . | Haohui Mai | Haohui Mai |
| [HDFS-8284](https://issues.apache.org/jira/browse/HDFS-8284) | Update documentation about how to use HTrace with HDFS |  Major | documentation | Masatake Iwasaki | Masatake Iwasaki |
| [HDFS-8283](https://issues.apache.org/jira/browse/HDFS-8283) | DataStreamer cleanup and some minor improvement |  Minor | hdfs-client | Tsz Wo Nicholas Sze | Tsz Wo Nicholas Sze |
| [HDFS-8280](https://issues.apache.org/jira/browse/HDFS-8280) | Code Cleanup in DFSInputStream |  Minor | . | Jing Zhao | Jing Zhao |
| [HDFS-8255](https://issues.apache.org/jira/browse/HDFS-8255) | Rename getBlockReplication to getPreferredBlockReplication |  Major | . | Zhe Zhang | Zhe Zhang |
| [HDFS-8215](https://issues.apache.org/jira/browse/HDFS-8215) | Refactor NamenodeFsck#check method |  Minor | namenode | Takanobu Asanuma | Takanobu Asanuma |
| [HDFS-8209](https://issues.apache.org/jira/browse/HDFS-8209) | Support different number of datanode directories in MiniDFSCluster. |  Minor | test | Surendra Singh Lilhore | Surendra Singh Lilhore |
| [HDFS-8207](https://issues.apache.org/jira/browse/HDFS-8207) | Improper log message when blockreport interval compared with initial delay |  Minor | . | Brahma Reddy Battula | Brahma Reddy Battula |
| [HDFS-8200](https://issues.apache.org/jira/browse/HDFS-8200) | Refactor FSDirStatAndListingOp |  Major | . | Haohui Mai | Haohui Mai |
| [HDFS-8180](https://issues.apache.org/jira/browse/HDFS-8180) | AbstractFileSystem Implementation for WebHdfs |  Major | webhdfs | Santhosh G Nayak | Santhosh G Nayak |
| [HDFS-8176](https://issues.apache.org/jira/browse/HDFS-8176) | Record from/to snapshots in audit log for snapshot diff report |  Minor | snapshots | J.Andreina | J.Andreina |
| [HDFS-8152](https://issues.apache.org/jira/browse/HDFS-8152) | Refactoring of lazy persist storage cases |  Major | test | Arpit Agarwal | Arpit Agarwal |
| [HDFS-8144](https://issues.apache.org/jira/browse/HDFS-8144) | Split TestLazyPersistFiles into multiple tests |  Major | test | Arpit Agarwal | Arpit Agarwal |
| [HDFS-8133](https://issues.apache.org/jira/browse/HDFS-8133) | Improve readability of deleted block check |  Major | namenode | Daryn Sharp | Daryn Sharp |
| [HDFS-8131](https://issues.apache.org/jira/browse/HDFS-8131) | Implement a space balanced block placement policy |  Minor | namenode | Liu Shaohui | Liu Shaohui |
| [HDFS-8117](https://issues.apache.org/jira/browse/HDFS-8117) | More accurate verification in SimulatedFSDataset: replace DEFAULT\_DATABYTE with patterned data |  Major | . | Zhe Zhang | Zhe Zhang |
| [HDFS-8116](https://issues.apache.org/jira/browse/HDFS-8116) | Cleanup uncessary if LOG.isDebugEnabled() from RollingWindowManager |  Trivial | namenode | Xiaoyu Yao | Brahma Reddy Battula |
| [HDFS-8108](https://issues.apache.org/jira/browse/HDFS-8108) | Fsck should provide the info on mandatory option to be used along with "-blocks , -locations and -racks" |  Trivial | documentation | J.Andreina | J.Andreina |
| [HDFS-8101](https://issues.apache.org/jira/browse/HDFS-8101) | DFSClient use of non-constant DFSConfigKeys pulls in WebHDFS classes at runtime |  Minor | hdfs-client | Sean Busbey | Sean Busbey |
| [HDFS-8076](https://issues.apache.org/jira/browse/HDFS-8076) | Code cleanup for DFSInputStream: use offset instead of LocatedBlock when possible |  Major | . | Zhe Zhang | Zhe Zhang |
| [HDFS-8073](https://issues.apache.org/jira/browse/HDFS-8073) | Split BlockPlacementPolicyDefault.chooseTarget(..) so it can be easily overrided. |  Trivial | namenode | Walter Su | Walter Su |
| [HDFS-8056](https://issues.apache.org/jira/browse/HDFS-8056) | Decommissioned dead nodes should continue to be counted as dead after NN restart |  Major | . | Ming Ma | Ming Ma |
| [HDFS-8035](https://issues.apache.org/jira/browse/HDFS-8035) | Move checkBlocksProperlyReplicated() in FSNamesystem to BlockManager |  Minor | namenode | Haohui Mai | Haohui Mai |
| [HDFS-8004](https://issues.apache.org/jira/browse/HDFS-8004) | Use KeyProviderCryptoExtension#warmUpEncryptedKeys when creating an encryption zone |  Trivial | encryption | Andrew Wang | Andrew Wang |
| [HDFS-7988](https://issues.apache.org/jira/browse/HDFS-7988) | Replace usage of ExactSizeInputStream with LimitInputStream. |  Minor | . | Chris Nauroth | Walter Su |
| [HDFS-7979](https://issues.apache.org/jira/browse/HDFS-7979) | Initialize block report IDs with a random number |  Minor | datanode | Andrew Wang | Andrew Wang |
| [HDFS-7978](https://issues.apache.org/jira/browse/HDFS-7978) | Add LOG.isDebugEnabled() guard for some LOG.debug(..) |  Major | . | Walter Su | Walter Su |
| [HDFS-7944](https://issues.apache.org/jira/browse/HDFS-7944) | Minor cleanup of BlockPoolManager#getAllNamenodeThreads |  Minor | . | Arpit Agarwal | Arpit Agarwal |
| [HDFS-7928](https://issues.apache.org/jira/browse/HDFS-7928) | Scanning blocks from disk during rolling upgrade startup takes a lot of time if disks are busy |  Major | datanode | Rushabh S Shah | Rushabh S Shah |
| [HDFS-7890](https://issues.apache.org/jira/browse/HDFS-7890) | Improve information on Top users for metrics in RollingWindowsManager and lower log level |  Major | . | J.Andreina | J.Andreina |
| [HDFS-7888](https://issues.apache.org/jira/browse/HDFS-7888) | Change DataStreamer/DFSOutputStream/DFSPacket for convenience of subclassing |  Minor | hdfs-client | Li Bo | Li Bo |
| [HDFS-7875](https://issues.apache.org/jira/browse/HDFS-7875) | Improve log message when wrong value configured for dfs.datanode.failed.volumes.tolerated |  Trivial | datanode | nijel | nijel |
| [HDFS-7863](https://issues.apache.org/jira/browse/HDFS-7863) | Missing description of some methods and parameters in javadoc of FSDirDeleteOp |  Minor | . | Yongjun Zhang | Brahma Reddy Battula |
| [HDFS-7858](https://issues.apache.org/jira/browse/HDFS-7858) | Improve HA Namenode Failover detection on the client |  Major | hdfs-client | Arun Suresh | Arun Suresh |
| [HDFS-7835](https://issues.apache.org/jira/browse/HDFS-7835) | make initial sleeptime in locateFollowingBlock configurable for DFSClient. |  Major | hdfs-client | zhihai xu | zhihai xu |
| [HDFS-7829](https://issues.apache.org/jira/browse/HDFS-7829) | Code clean up for LocatedBlock |  Minor | . | Jing Zhao | Takanobu Asanuma |
| [HDFS-7793](https://issues.apache.org/jira/browse/HDFS-7793) | Refactor DFSOutputStream separating DataStreamer out |  Major | hdfs-client | Kai Zheng | Li Bo |
| [HDFS-7770](https://issues.apache.org/jira/browse/HDFS-7770) | Need document for storage type label of data node storage locations under dfs.datanode.data.dir |  Major | documentation | Xiaoyu Yao | Xiaoyu Yao |
| [HDFS-7758](https://issues.apache.org/jira/browse/HDFS-7758) | Retire FsDatasetSpi#getVolumes() and use FsDatasetSpi#getVolumeRefs() instead |  Major | datanode | Lei (Eddy) Xu | Lei (Eddy) Xu |
| [HDFS-7671](https://issues.apache.org/jira/browse/HDFS-7671) | hdfs user guide should point to the common rack awareness doc |  Major | documentation | Allen Wittenauer | Kai Sasaki |
| [HDFS-7649](https://issues.apache.org/jira/browse/HDFS-7649) | Multihoming docs should emphasize using hostnames in configurations |  Major | documentation | Arpit Agarwal | Brahma Reddy Battula |
| [HDFS-7433](https://issues.apache.org/jira/browse/HDFS-7433) | Optimize performance of DatanodeManager's node map |  Critical | namenode | Daryn Sharp | Daryn Sharp |
| [HDFS-7397](https://issues.apache.org/jira/browse/HDFS-7397) | Add more detail to the documentation for the conf key "dfs.client.read.shortcircuit.streams.cache.size" |  Minor | hdfs-client | Tsz Wo Nicholas Sze | Brahma Reddy Battula |
| [HDFS-7284](https://issues.apache.org/jira/browse/HDFS-7284) | Add more debug info to BlockInfoUnderConstruction#setGenerationStampAndVerifyReplicas |  Major | namenode | Hu Liu, | Wei-Chiu Chuang |
| [HDFS-7116](https://issues.apache.org/jira/browse/HDFS-7116) | Add a command to get the balancer bandwidth |  Major | balancer & mover | Akira AJISAKA | Rakesh R |
| [HDFS-7087](https://issues.apache.org/jira/browse/HDFS-7087) | Ability to list /.reserved |  Major | . | Andrew Wang | Xiao Chen |
| [HDFS-6888](https://issues.apache.org/jira/browse/HDFS-6888) | Allow selectively audit logging ops |  Major | . | Kihwal Lee | Chen He |
| [HDFS-6757](https://issues.apache.org/jira/browse/HDFS-6757) | Simplify lease manager with INodeID |  Major | . | Haohui Mai | Haohui Mai |
| [HDFS-6407](https://issues.apache.org/jira/browse/HDFS-6407) | Add sorting and pagination in the datanode tab of the NN Web UI |  Critical | namenode | Nathan Roberts | Haohui Mai |
| [HDFS-6200](https://issues.apache.org/jira/browse/HDFS-6200) | Create a separate jar for hdfs-client |  Major | build | Haohui Mai | Haohui Mai |
| [HDFS-6184](https://issues.apache.org/jira/browse/HDFS-6184) | Capture NN's thread dump when it fails over |  Major | namenode | Ming Ma | Ming Ma |
| [HDFS-6054](https://issues.apache.org/jira/browse/HDFS-6054) | MiniQJMHACluster should not use static port to avoid binding failure in unit test |  Major | test | Brandon Li | Yongjun Zhang |
| [HDFS-5795](https://issues.apache.org/jira/browse/HDFS-5795) | RemoteBlockReader2#checkSuccess() shoud print error status |  Trivial | . | Brandon Li | Xiao Chen |
| [HDFS-5640](https://issues.apache.org/jira/browse/HDFS-5640) | Add snapshot methods to FileContext. |  Major | hdfs-client, snapshots | Chris Nauroth | Rakesh R |
| [HDFS-5574](https://issues.apache.org/jira/browse/HDFS-5574) | Remove buffer copy in BlockReader.skip |  Trivial | . | Binglin Chang | Binglin Chang |
| [HDFS-4396](https://issues.apache.org/jira/browse/HDFS-4396) | Add START\_MSG/SHUTDOWN\_MSG for ZKFC |  Major | auto-failover, ha, tools | Liang Xie | Liang Xie |
| [HDFS-4383](https://issues.apache.org/jira/browse/HDFS-4383) | Document the lease limits |  Minor | . | Eli Collins | Arshad Mohammad |
| [HDFS-4185](https://issues.apache.org/jira/browse/HDFS-4185) | Add a metric for number of active leases |  Major | namenode | Kihwal Lee | Rakesh R |
| [HDFS-4015](https://issues.apache.org/jira/browse/HDFS-4015) | Safemode should count and report orphaned blocks |  Major | namenode | Todd Lipcon | Anu Engineer |
| [HDFS-3918](https://issues.apache.org/jira/browse/HDFS-3918) | EditLogTailer shouldn't log WARN when other node is in standby mode |  Major | ha | Todd Lipcon | Todd Lipcon |
| [HDFS-3302](https://issues.apache.org/jira/browse/HDFS-3302) | Review and improve HDFS trash documentation |  Major | documentation | Harsh J | Harsh J |
| [HDFS-2390](https://issues.apache.org/jira/browse/HDFS-2390) | dfsadmin -setBalancerBandwidth doesnot validate -ve value |  Minor | balancer & mover | Rajit Saha | Gautam Gopalakrishnan |
| [HDFS-2360](https://issues.apache.org/jira/browse/HDFS-2360) | Ugly stacktrace when quota exceeds |  Minor | hdfs-client | Rajit Saha | Harsh J |
| [HDFS-328](https://issues.apache.org/jira/browse/HDFS-328) | Improve fs -setrep error message for invalid replication factors |  Major | namenode | Tsz Wo Nicholas Sze | Daniel Templeton |
| [MAPREDUCE-6626](https://issues.apache.org/jira/browse/MAPREDUCE-6626) | Reuse ObjectMapper instance in MapReduce |  Minor | performance | Lin Yiqun | Lin Yiqun |
| [MAPREDUCE-6584](https://issues.apache.org/jira/browse/MAPREDUCE-6584) | Remove trailing whitespaces from mapred-default.xml |  Major | documentation | Akira AJISAKA | Akira AJISAKA |
| [MAPREDUCE-6566](https://issues.apache.org/jira/browse/MAPREDUCE-6566) | Add retry support to mapreduce CLI tool |  Major | . | Varun Vasudev | Varun Vasudev |
| [MAPREDUCE-6499](https://issues.apache.org/jira/browse/MAPREDUCE-6499) | Add elapsed time for retired job in JobHistoryServer WebUI |  Major | webapps | Lin Yiqun | Lin Yiqun |
| [MAPREDUCE-6489](https://issues.apache.org/jira/browse/MAPREDUCE-6489) | Fail fast rogue tasks that write too much to local disk |  Major | task | Maysam Yabandeh | Maysam Yabandeh |
| [MAPREDUCE-6479](https://issues.apache.org/jira/browse/MAPREDUCE-6479) | Add missing mapred job command options in mapreduce document |  Major | documentation | nijel | nijel |
| [MAPREDUCE-6478](https://issues.apache.org/jira/browse/MAPREDUCE-6478) | Add an option to skip cleanupJob stage or ignore cleanup failure during commitJob(). |  Major | . | Junping Du | Junping Du |
| [MAPREDUCE-6473](https://issues.apache.org/jira/browse/MAPREDUCE-6473) | Job submission can take a long time during Cluster initialization |  Major | performance | Kuhu Shukla | Kuhu Shukla |
| [MAPREDUCE-6471](https://issues.apache.org/jira/browse/MAPREDUCE-6471) | Document distcp incremental copy |  Major | distcp | Arpit Agarwal | Neelesh Srinivas Salian |
| [MAPREDUCE-6443](https://issues.apache.org/jira/browse/MAPREDUCE-6443) | Add JvmPauseMonitor to Job History Server |  Major | jobhistoryserver | Robert Kanter | Robert Kanter |
| [MAPREDUCE-6436](https://issues.apache.org/jira/browse/MAPREDUCE-6436) | JobHistory cache issue |  Blocker | . | Ryu Kobayashi | Kai Sasaki |
| [MAPREDUCE-6408](https://issues.apache.org/jira/browse/MAPREDUCE-6408) | Queue name and user name should be printed on the job page |  Major | applicationmaster | Siqi Li | Siqi Li |
| [MAPREDUCE-6395](https://issues.apache.org/jira/browse/MAPREDUCE-6395) | Improve the commit failure messages in MRAppMaster recovery |  Major | applicationmaster | Gera Shegalov | Brahma Reddy Battula |
| [MAPREDUCE-6392](https://issues.apache.org/jira/browse/MAPREDUCE-6392) | Document mapred class path options |  Major | documentation | Brahma Reddy Battula | Brahma Reddy Battula |
| [MAPREDUCE-6384](https://issues.apache.org/jira/browse/MAPREDUCE-6384) | Add the last reporting reducer info for too many fetch failure diagnostics |  Major | . | Chang Li | Chang Li |
| [MAPREDUCE-6383](https://issues.apache.org/jira/browse/MAPREDUCE-6383) | Pi job (QuasiMonteCarlo) should not try to read the results file if its job fails |  Major | examples | Harsh J | Harsh J |
| [MAPREDUCE-6354](https://issues.apache.org/jira/browse/MAPREDUCE-6354) | ShuffleHandler should be able to log shuffle connections |  Major | . | Chang Li | Chang Li |
| [MAPREDUCE-6316](https://issues.apache.org/jira/browse/MAPREDUCE-6316) | Task Attempt List entries should link to the task overview |  Major | . | Siqi Li | Siqi Li |
| [MAPREDUCE-6307](https://issues.apache.org/jira/browse/MAPREDUCE-6307) | Remove property mapreduce.tasktracker.taskmemorymanager.monitoringinterval |  Minor | . | Akira AJISAKA | J.Andreina |
| [MAPREDUCE-6305](https://issues.apache.org/jira/browse/MAPREDUCE-6305) | AM/Task log page should be able to link back to the job |  Major | . | Siqi Li | Siqi Li |
| [MAPREDUCE-6297](https://issues.apache.org/jira/browse/MAPREDUCE-6297) | Task Id of the failed task in diagnostics should link to the task page |  Minor | jobhistoryserver | Siqi Li | Siqi Li |
| [MAPREDUCE-6291](https://issues.apache.org/jira/browse/MAPREDUCE-6291) | Correct mapred queue usage command |  Minor | client | Brahma Reddy Battula | Brahma Reddy Battula |
| [MAPREDUCE-6287](https://issues.apache.org/jira/browse/MAPREDUCE-6287) | Deprecated methods in org.apache.hadoop.examples.Sort |  Minor | examples | Chao Zhang | Chao Zhang |
| [MAPREDUCE-6282](https://issues.apache.org/jira/browse/MAPREDUCE-6282) | Reuse historyFileAbsolute.getFileSystem in CompletedJob#loadFullHistoryData for code optimization. |  Trivial | jobhistoryserver | zhihai xu | zhihai xu |
| [MAPREDUCE-6279](https://issues.apache.org/jira/browse/MAPREDUCE-6279) | AM should explicity exit JVM after all services have stopped |  Major | . | Jason Lowe | Eric Payne |
| [MAPREDUCE-6239](https://issues.apache.org/jira/browse/MAPREDUCE-6239) | Consolidate TestJobConf classes in hadoop-mapreduce-client-jobclient and hadoop-mapreduce-client-core |  Minor | client | Varun Saxena | Varun Saxena |
| [MAPREDUCE-6192](https://issues.apache.org/jira/browse/MAPREDUCE-6192) | Create unit test to automatically compare MR related classes and mapred-default.xml |  Minor | . | Ray Chiang | Ray Chiang |
| [MAPREDUCE-6174](https://issues.apache.org/jira/browse/MAPREDUCE-6174) | Combine common stream code into parent class for InMemoryMapOutput and OnDiskMapOutput. |  Major | mrv2 | Eric Payne | Eric Payne |
| [MAPREDUCE-6105](https://issues.apache.org/jira/browse/MAPREDUCE-6105) | Inconsistent configuration in property mapreduce.reduce.shuffle.merge.percent |  Trivial | . | Dongwook Kwon | Ray Chiang |
| [MAPREDUCE-6100](https://issues.apache.org/jira/browse/MAPREDUCE-6100) | replace "mapreduce.job.credentials.binary" with MRJobConfig.MAPREDUCE\_JOB\_CREDENTIALS\_BINARY for better readability. |  Trivial | mrv2 | zhihai xu | zhihai xu |
| [MAPREDUCE-6079](https://issues.apache.org/jira/browse/MAPREDUCE-6079) | Rename JobImpl#username to reporterUserName |  Major | . | Tsuyoshi Ozawa | Tsuyoshi Ozawa |
| [MAPREDUCE-5981](https://issues.apache.org/jira/browse/MAPREDUCE-5981) | Log levels of certain MR logs can be changed to DEBUG |  Major | . | Varun Saxena | Varun Saxena |
| [MAPREDUCE-5870](https://issues.apache.org/jira/browse/MAPREDUCE-5870) | Support for passing Job priority through Application Submission Context in Mapreduce Side |  Major | client | Sunil G | Sunil G |
| [MAPREDUCE-5762](https://issues.apache.org/jira/browse/MAPREDUCE-5762) | Port MAPREDUCE-3223 and MAPREDUCE-4695 (Remove MRv1 config from mapred-default.xml) to branch-2 |  Minor | documentation | Akira AJISAKA | Akira AJISAKA |
| [MAPREDUCE-5755](https://issues.apache.org/jira/browse/MAPREDUCE-5755) | MapTask.MapOutputBuffer#compare/swap should have @Override annotation |  Trivial | . | Tsuyoshi Ozawa | Tsuyoshi Ozawa |
| [MAPREDUCE-5485](https://issues.apache.org/jira/browse/MAPREDUCE-5485) | Allow repeating job commit by extending OutputCommitter API |  Critical | . | Nemon Lou | Junping Du |
| [MAPREDUCE-5465](https://issues.apache.org/jira/browse/MAPREDUCE-5465) | Tasks are often killed before they exit on their own |  Major | mr-am, mrv2 | Radim Kolar | Ming Ma |
| [MAPREDUCE-5248](https://issues.apache.org/jira/browse/MAPREDUCE-5248) | Let NNBenchWithoutMR specify the replication factor for its test |  Minor | client, test | Erik Paulson | Erik Paulson |
| [MAPREDUCE-5232](https://issues.apache.org/jira/browse/MAPREDUCE-5232) | log classpath and other key properties on child JVM start |  Major | mrv1, mrv2 | Sangjin Lee | Sangjin Lee |
| [MAPREDUCE-5190](https://issues.apache.org/jira/browse/MAPREDUCE-5190) | Unnecessary condition test in RandomSampler |  Minor | mrv2 | Jingguo Yao | Jingguo Yao |
| [MAPREDUCE-4653](https://issues.apache.org/jira/browse/MAPREDUCE-4653) | TestRandomAlgorithm has an unused "import" statement |  Trivial | contrib/gridmix | Amir Sanjar | Amir Sanjar |
| [MAPREDUCE-4414](https://issues.apache.org/jira/browse/MAPREDUCE-4414) | Add main methods to JobConf and YarnConfiguration, for debug purposes |  Major | client | Harsh J | Plamen Jeliazkov |
| [MAPREDUCE-579](https://issues.apache.org/jira/browse/MAPREDUCE-579) | Streaming "slowmatch" documentation |  Trivial | contrib/streaming | Bo Adler | Harsh J |
| [YARN-4720](https://issues.apache.org/jira/browse/YARN-4720) | Skip unnecessary NN operations in log aggregation |  Major | . | Ming Ma | Jun Gong |
| [YARN-4690](https://issues.apache.org/jira/browse/YARN-4690) | Skip object allocation in FSAppAttempt#getResourceUsage when possible |  Major | . | Ming Ma | Ming Ma |
| [YARN-4682](https://issues.apache.org/jira/browse/YARN-4682) | AMRM client to log when AMRM token updated |  Major | client | Steve Loughran | Prabhu Joseph |
| [YARN-4662](https://issues.apache.org/jira/browse/YARN-4662) | Document some newly added metrics |  Major | . | Jian He | Jian He |
| [YARN-4582](https://issues.apache.org/jira/browse/YARN-4582) | Label-related invalid resource request exception should be able to properly handled by application |  Major | scheduler | Bibin A Chundatt | Bibin A Chundatt |
| [YARN-4544](https://issues.apache.org/jira/browse/YARN-4544) | All the log messages about rolling monitoring interval are shown with WARN level |  Minor | log-aggregation, nodemanager | Takashi Ohnishi | Takashi Ohnishi |
| [YARN-4480](https://issues.apache.org/jira/browse/YARN-4480) | Clean up some inappropriate imports |  Major | . | Kai Zheng | Kai Zheng |
| [YARN-4400](https://issues.apache.org/jira/browse/YARN-4400) | AsyncDispatcher.waitForDrained should be final |  Trivial | yarn | Daniel Templeton | Daniel Templeton |
| [YARN-4371](https://issues.apache.org/jira/browse/YARN-4371) | "yarn application -kill" should take multiple application ids |  Major | . | Tsuyoshi Ozawa | Sunil G |
| [YARN-4310](https://issues.apache.org/jira/browse/YARN-4310) | FairScheduler: Log skipping reservation messages at DEBUG level |  Minor | fairscheduler | Arun Suresh | Arun Suresh |
| [YARN-4290](https://issues.apache.org/jira/browse/YARN-4290) | Add -showDetails option to YARN Nodes CLI to print all nodes reports information |  Major | client | Wangda Tan | Sunil G |
| [YARN-4287](https://issues.apache.org/jira/browse/YARN-4287) | Capacity Scheduler: Rack Locality improvement |  Major | capacityscheduler | Nathan Roberts | Nathan Roberts |
| [YARN-4285](https://issues.apache.org/jira/browse/YARN-4285) | Display resource usage as percentage of queue and cluster in the RM UI |  Major | resourcemanager | Varun Vasudev | Varun Vasudev |
| [YARN-4279](https://issues.apache.org/jira/browse/YARN-4279) | Mark ApplicationId and ApplicationAttemptId static methods as @Public, @Unstable |  Minor | client | Steve Loughran | Steve Loughran |
| [YARN-4253](https://issues.apache.org/jira/browse/YARN-4253) | Standardize on using PrivilegedOperationExecutor for all invocations of container-executor in LinuxContainerExecutor |  Major | . | Sidharta Seethana | Sidharta Seethana |
| [YARN-4252](https://issues.apache.org/jira/browse/YARN-4252) | Log container-executor invocation details when exit code is non-zero |  Minor | nodemanager | Sidharta Seethana | Sidharta Seethana |
| [YARN-4228](https://issues.apache.org/jira/browse/YARN-4228) | FileSystemRMStateStore use IOUtils#close instead of fs#close |  Minor | . | Bibin A Chundatt | Bibin A Chundatt |
| [YARN-4207](https://issues.apache.org/jira/browse/YARN-4207) | Add a non-judgemental YARN app completion status |  Major | . | Sergey Shelukhin | Rich Haase |
| [YARN-4149](https://issues.apache.org/jira/browse/YARN-4149) | yarn logs -am should provide an option to fetch all the log files |  Major | client, nodemanager | Varun Vasudev | Varun Vasudev |
| [YARN-4145](https://issues.apache.org/jira/browse/YARN-4145) | Make RMHATestBase abstract so its not run when running all tests under that namespace |  Minor | . | Anubhav Dhoot | Anubhav Dhoot |
| [YARN-4135](https://issues.apache.org/jira/browse/YARN-4135) | Improve the assertion message in MockRM while failing after waiting for the state. |  Trivial | . | nijel | nijel |
| [YARN-4132](https://issues.apache.org/jira/browse/YARN-4132) | Separate configs for nodemanager to resourcemanager connection timeout and retries |  Major | nodemanager | Chang Li | Chang Li |
| [YARN-4095](https://issues.apache.org/jira/browse/YARN-4095) | Avoid sharing AllocatorPerContext object in LocalDirAllocator between ShuffleHandler and LocalDirsHandlerService. |  Major | nodemanager | zhihai xu | zhihai xu |
| [YARN-4086](https://issues.apache.org/jira/browse/YARN-4086) | Allow Aggregated Log readers to handle HAR files |  Major | . | Robert Kanter | Robert Kanter |
| [YARN-4057](https://issues.apache.org/jira/browse/YARN-4057) | If ContainersMonitor is not enabled, only print related log info one time |  Minor | nodemanager | Jun Gong | Jun Gong |
| [YARN-4055](https://issues.apache.org/jira/browse/YARN-4055) | Report node resource utilization in heartbeat |  Major | nodemanager | Inigo Goiri | Inigo Goiri |
| [YARN-4024](https://issues.apache.org/jira/browse/YARN-4024) | YARN RM should avoid unnecessary resolving IP when NMs doing heartbeat |  Major | resourcemanager | Wangda Tan | Hong Zhiguo |
| [YARN-4019](https://issues.apache.org/jira/browse/YARN-4019) | Add JvmPauseMonitor to ResourceManager and NodeManager |  Major | nodemanager, resourcemanager | Robert Kanter | Robert Kanter |
| [YARN-3965](https://issues.apache.org/jira/browse/YARN-3965) | Add startup timestamp to nodemanager UI |  Minor | nodemanager | Hong Zhiguo | Hong Zhiguo |
| [YARN-3961](https://issues.apache.org/jira/browse/YARN-3961) | Expose pending, running and reserved containers of a queue in REST api and yarn top |  Major | capacityscheduler, fairscheduler, webapp | Anubhav Dhoot | Anubhav Dhoot |
| [YARN-3950](https://issues.apache.org/jira/browse/YARN-3950) | Add unique YARN\_SHELL\_ID environment variable to DistributedShell |  Major | applications/distributed-shell | Robert Kanter | Robert Kanter |
| [YARN-3943](https://issues.apache.org/jira/browse/YARN-3943) | Use separate threshold configurations for disk-full detection and disk-not-full detection. |  Critical | nodemanager | zhihai xu | zhihai xu |
| [YARN-3834](https://issues.apache.org/jira/browse/YARN-3834) | Scrub debug logging of tokens during resource localization. |  Major | nodemanager | Chris Nauroth | Chris Nauroth |
| [YARN-3789](https://issues.apache.org/jira/browse/YARN-3789) | Improve logs for LeafQueue#activateApplications() |  Minor | resourcemanager | Bibin A Chundatt | Bibin A Chundatt |
| [YARN-3786](https://issues.apache.org/jira/browse/YARN-3786) | Document yarn class path options |  Major | documentation | Brahma Reddy Battula | Brahma Reddy Battula |
| [YARN-3722](https://issues.apache.org/jira/browse/YARN-3722) | Merge multiple TestWebAppUtils into o.a.h.yarn.webapp.util.TestWebAppUtils |  Minor | test | Masatake Iwasaki | Masatake Iwasaki |
| [YARN-3713](https://issues.apache.org/jira/browse/YARN-3713) | Remove duplicate function call storeContainerDiagnostics in ContainerDiagnosticsUpdateTransition |  Minor | nodemanager | zhihai xu | zhihai xu |
| [YARN-3613](https://issues.apache.org/jira/browse/YARN-3613) | TestContainerManagerSecurity should init and start Yarn cluster in setup instead of individual methods |  Minor | test | Karthik Kambatla | nijel |
| [YARN-3547](https://issues.apache.org/jira/browse/YARN-3547) | FairScheduler: Apps that have no resource demand should not participate scheduling |  Major | fairscheduler | Xianyin Xin | Xianyin Xin |
| [YARN-3528](https://issues.apache.org/jira/browse/YARN-3528) | Tests with 12345 as hard-coded port break jenkins |  Blocker | . | Steve Loughran | Brahma Reddy Battula |
| [YARN-3513](https://issues.apache.org/jira/browse/YARN-3513) | Remove unused variables in ContainersMonitorImpl and add debug log for overall resource usage by all containers |  Trivial | nodemanager | Naganarasimha G R | Naganarasimha G R |
| [YARN-3511](https://issues.apache.org/jira/browse/YARN-3511) | Add errors and warnings page to ATS |  Major | timelineserver | Varun Vasudev | Varun Vasudev |
| [YARN-3503](https://issues.apache.org/jira/browse/YARN-3503) | Expose disk utilization percentage and bad local and log dir counts on NM via JMX |  Major | nodemanager | Varun Vasudev | Varun Vasudev |
| [YARN-3494](https://issues.apache.org/jira/browse/YARN-3494) | Expose AM resource limit and usage in QueueMetrics |  Major | . | Jian He | Rohith Sharma K S |
| [YARN-3491](https://issues.apache.org/jira/browse/YARN-3491) | PublicLocalizer#addResource is too slow. |  Critical | nodemanager | zhihai xu | zhihai xu |
| [YARN-3467](https://issues.apache.org/jira/browse/YARN-3467) | Expose allocatedMB, allocatedVCores, and runningContainers metrics on running Applications in RM Web UI |  Minor | webapp, yarn | Anthony Rojas | Anubhav Dhoot |
| [YARN-3456](https://issues.apache.org/jira/browse/YARN-3456) | Improve handling of incomplete TimelineEntities |  Minor | timelineserver | Steve Loughran | Varun Saxena |
| [YARN-3451](https://issues.apache.org/jira/browse/YARN-3451) | Add start time and Elapsed in ApplicationAttemptReport and display the same in RMAttemptBlock WebUI |  Major | api, webapp | Rohith Sharma K S | Rohith Sharma K S |
| [YARN-3428](https://issues.apache.org/jira/browse/YARN-3428) | Debug log resources to be localized for a container |  Trivial | nodemanager | Karthik Kambatla | Karthik Kambatla |
| [YARN-3424](https://issues.apache.org/jira/browse/YARN-3424) | Change logs for ContainerMonitorImpl's resourse monitoring from info to debug |  Major | nodemanager | Anubhav Dhoot | Anubhav Dhoot |
| [YARN-3412](https://issues.apache.org/jira/browse/YARN-3412) | RM tests should use MockRM where possible |  Major | resourcemanager, test | Karthik Kambatla | Karthik Kambatla |
| [YARN-3410](https://issues.apache.org/jira/browse/YARN-3410) | YARN admin should be able to remove individual application records from RMStateStore |  Critical | resourcemanager, yarn | Wangda Tan | Rohith Sharma K S |
| [YARN-3406](https://issues.apache.org/jira/browse/YARN-3406) | Display count of running containers in the RM's Web UI |  Minor | . | Ryu Kobayashi | Ryu Kobayashi |
| [YARN-3404](https://issues.apache.org/jira/browse/YARN-3404) | View the queue name to YARN Application page |  Minor | . | Ryu Kobayashi | Ryu Kobayashi |
| [YARN-3381](https://issues.apache.org/jira/browse/YARN-3381) | Fix typo InvalidStateTransitonException |  Minor | api | Xiaoshuang LU | Brahma Reddy Battula |
| [YARN-3363](https://issues.apache.org/jira/browse/YARN-3363) | add localization and container launch time to ContainerMetrics at NM to show these timing information for each active container. |  Major | nodemanager | zhihai xu | zhihai xu |
| [YARN-3360](https://issues.apache.org/jira/browse/YARN-3360) | Add JMX metrics to TimelineDataManager |  Major | timelineserver | Jason Lowe | Jason Lowe |
| [YARN-3350](https://issues.apache.org/jira/browse/YARN-3350) | YARN RackResolver spams logs with messages at info level |  Major | . | Wilfred Spiegelenburg | Wilfred Spiegelenburg |
| [YARN-3348](https://issues.apache.org/jira/browse/YARN-3348) | Add a 'yarn top' tool to help understand cluster usage |  Major | resourcemanager | Varun Vasudev | Varun Vasudev |
| [YARN-3294](https://issues.apache.org/jira/browse/YARN-3294) | Allow dumping of Capacity Scheduler debug logs via web UI for a fixed time period |  Major | capacityscheduler | Varun Vasudev | Varun Vasudev |
| [YARN-3293](https://issues.apache.org/jira/browse/YARN-3293) | Track and display capacity scheduler health metrics in web UI |  Major | capacityscheduler | Varun Vasudev | Varun Vasudev |
| [YARN-3271](https://issues.apache.org/jira/browse/YARN-3271) | FairScheduler: Move tests related to max-runnable-apps from TestFairScheduler to TestAppRunnability |  Major | . | Karthik Kambatla | nijel |
| [YARN-3259](https://issues.apache.org/jira/browse/YARN-3259) | FairScheduler: Trigger fairShare updates on node events |  Major | fairscheduler | Anubhav Dhoot | Anubhav Dhoot |
| [YARN-3258](https://issues.apache.org/jira/browse/YARN-3258) | FairScheduler: Need to add more logging to investigate allocations |  Minor | fairscheduler | Anubhav Dhoot | Anubhav Dhoot |
| [YARN-3174](https://issues.apache.org/jira/browse/YARN-3174) | Consolidate the NodeManager and NodeManagerRestart documentation into one |  Major | documentation | Allen Wittenauer | Masatake Iwasaki |
| [YARN-3169](https://issues.apache.org/jira/browse/YARN-3169) | Drop YARN's overview document |  Major | documentation | Allen Wittenauer | Brahma Reddy Battula |
| [YARN-3148](https://issues.apache.org/jira/browse/YARN-3148) | Allow CORS related headers to passthrough in WebAppProxyServlet |  Major | . | Prakash Ramachandran | Varun Saxena |
| [YARN-3069](https://issues.apache.org/jira/browse/YARN-3069) | Document missing properties in yarn-default.xml |  Major | documentation | Ray Chiang | Ray Chiang |
| [YARN-2980](https://issues.apache.org/jira/browse/YARN-2980) | Move health check script related functionality to hadoop-common |  Blocker | . | Ming Ma | Varun Saxena |
| [YARN-2921](https://issues.apache.org/jira/browse/YARN-2921) | Fix MockRM/MockAM#waitForState sleep too long |  Major | test | Karthik Kambatla | Tsuyoshi Ozawa |
| [YARN-2913](https://issues.apache.org/jira/browse/YARN-2913) | Fair scheduler should have ability to set MaxResourceDefault for each queue |  Major | . | Siqi Li | Siqi Li |
| [YARN-2868](https://issues.apache.org/jira/browse/YARN-2868) | FairScheduler: Metric for latency to allocate first container for an application |  Major | . | Ray Chiang | Ray Chiang |
| [YARN-2784](https://issues.apache.org/jira/browse/YARN-2784) | Make POM project names consistent |  Minor | build | Rohith Sharma K S | Rohith Sharma K S |
| [YARN-2768](https://issues.apache.org/jira/browse/YARN-2768) | Avoid cloning Resource in FSAppAttempt#updateDemand |  Minor | fairscheduler | Hong Zhiguo | Hong Zhiguo |
| [YARN-2716](https://issues.apache.org/jira/browse/YARN-2716) | Refactor ZKRMStateStore retry code with Apache Curator |  Major | . | Jian He | Karthik Kambatla |
| [YARN-2573](https://issues.apache.org/jira/browse/YARN-2573) | Integrate ReservationSystem with the RM failover mechanism |  Major | capacityscheduler, fairscheduler, resourcemanager | Subru Krishnan | Subru Krishnan |
| [YARN-2206](https://issues.apache.org/jira/browse/YARN-2206) | Update document for applications REST API response examples |  Minor | documentation | Kenji Kikushima | Brahma Reddy Battula |
| [YARN-2005](https://issues.apache.org/jira/browse/YARN-2005) | Blacklisting support for scheduling AMs |  Major | resourcemanager | Jason Lowe | Anubhav Dhoot |
| [YARN-1287](https://issues.apache.org/jira/browse/YARN-1287) | Consolidate MockClocks |  Major | . | Sandy Ryza | Sebastian Wong |
| [YARN-1050](https://issues.apache.org/jira/browse/YARN-1050) | Document the Fair Scheduler REST API |  Major | documentation, fairscheduler | Sandy Ryza | Kenji Kikushima |
| [YARN-160](https://issues.apache.org/jira/browse/YARN-160) | nodemanagers should obtain cpu/memory values from underlying OS |  Major | nodemanager | Alejandro Abdelnur | Varun Vasudev |
| [YARN-20](https://issues.apache.org/jira/browse/YARN-20) | More information for "yarn.resourcemanager.webapp.address" in yarn-default.xml |  Trivial | documentation, resourcemanager | Nemon Lou | Bartosz Ługowski |


### BUG FIXES:

| JIRA | Summary | Priority | Component | Reporter | Contributor |
|:---- |:---- | :--- |:---- |:---- |:---- |
| [HADOOP-12851](https://issues.apache.org/jira/browse/HADOOP-12851) | S3AFileSystem Uptake of ProviderUtils.excludeIncompatibleCredentialProviders |  Major | fs/s3 | Larry McCay | Larry McCay |
| [HADOOP-12849](https://issues.apache.org/jira/browse/HADOOP-12849) | TestSymlinkLocalFSFileSystem fails intermittently |  Major | test | Mingliang Liu | Mingliang Liu |
| [HADOOP-12846](https://issues.apache.org/jira/browse/HADOOP-12846) | Credential Provider Recursive Dependencies |  Major | . | Larry McCay | Larry McCay |
| [HADOOP-12843](https://issues.apache.org/jira/browse/HADOOP-12843) | Fix findbugs warnings in hadoop-common (branch-2) |  Major | . | Akira AJISAKA | Akira AJISAKA |
| [HADOOP-12831](https://issues.apache.org/jira/browse/HADOOP-12831) | LocalFS/FSOutputSummer NPEs in constructor if bytes per checksum  set to 0 |  Minor | fs | Steve Loughran | Mingliang Liu |
| [HADOOP-12795](https://issues.apache.org/jira/browse/HADOOP-12795) | KMS does not log detailed stack trace for unexpected errors. |  Major | kms | Chris Nauroth | Chris Nauroth |
| [HADOOP-12787](https://issues.apache.org/jira/browse/HADOOP-12787) | KMS SPNEGO sequence does not work with WEBHDFS |  Major | kms, security | Xiaoyu Yao | Xiaoyu Yao |
| [HADOOP-12786](https://issues.apache.org/jira/browse/HADOOP-12786) | "hadoop key" command usage is not documented |  Major | documentation | Akira AJISAKA | Xiao Chen |
| [HADOOP-12780](https://issues.apache.org/jira/browse/HADOOP-12780) | During WASB atomic rename handle crash when one directory has been renamed but not file under it. |  Critical | fs/azure | madhumita chakraborty | madhumita chakraborty |
| [HADOOP-12773](https://issues.apache.org/jira/browse/HADOOP-12773) | HBase classes fail to load with client/job classloader enabled |  Major | util | Sangjin Lee | Sangjin Lee |
| [HADOOP-12766](https://issues.apache.org/jira/browse/HADOOP-12766) | The default value of "hadoop.workaround.non.threadsafe.getpwuid" is different between core-default.xml and NativeIO.java |  Minor | . | Akira AJISAKA | Akira AJISAKA |
| [HADOOP-12761](https://issues.apache.org/jira/browse/HADOOP-12761) | incremental maven build is not really incremental |  Minor | build | Sangjin Lee | Sangjin Lee |
| [HADOOP-12755](https://issues.apache.org/jira/browse/HADOOP-12755) | Fix typo in defaultFS warning message |  Trivial | . | Andrew Wang | Andrew Wang |
| [HADOOP-12735](https://issues.apache.org/jira/browse/HADOOP-12735) | core-default.xml misspells hadoop.workaround.non.threadsafe.getpwuid |  Minor | . | Ray Chiang | Ray Chiang |
| [HADOOP-12730](https://issues.apache.org/jira/browse/HADOOP-12730) | Hadoop streaming -mapper and -reducer options are wrongly documented as required |  Major | documentation | DeepakVohra | Kengo Seki |
| [HADOOP-12718](https://issues.apache.org/jira/browse/HADOOP-12718) | Incorrect error message by fs -put local dir without permission |  Minor | . | John Zhuge | John Zhuge |
| [HADOOP-12716](https://issues.apache.org/jira/browse/HADOOP-12716) | KerberosAuthenticator#doSpnegoSequence use incorrect class to determine isKeyTab in JDK8 |  Major | security | Xiaoyu Yao | Xiaoyu Yao |
| [HADOOP-12712](https://issues.apache.org/jira/browse/HADOOP-12712) | Fix some cmake plugin and native build warnings |  Minor | native | Colin Patrick McCabe | Colin Patrick McCabe |
| [HADOOP-12700](https://issues.apache.org/jira/browse/HADOOP-12700) | Remove unused import in TestCompressorDecompressor.java |  Minor | . | John Zhuge | John Zhuge |
| [HADOOP-12699](https://issues.apache.org/jira/browse/HADOOP-12699) | TestKMS#testKMSProvider intermittently fails during 'test rollover draining' |  Major | . | Xiao Chen | Xiao Chen |
| [HADOOP-12689](https://issues.apache.org/jira/browse/HADOOP-12689) | S3 filesystem operations stopped working correctly |  Major | tools | Matthew Paduano | Matthew Paduano |
| [HADOOP-12682](https://issues.apache.org/jira/browse/HADOOP-12682) | Fix TestKMS#testKMSRestart\* failure |  Major | . | Wei-Chiu Chuang | Wei-Chiu Chuang |
| [HADOOP-12681](https://issues.apache.org/jira/browse/HADOOP-12681) | start-build-env.sh fails in branch-2 |  Blocker | build | Akira AJISAKA | Kengo Seki |
| [HADOOP-12678](https://issues.apache.org/jira/browse/HADOOP-12678) | Handle empty rename pending metadata file during atomic rename in redo path |  Critical | fs/azure | madhumita chakraborty | madhumita chakraborty |
| [HADOOP-12675](https://issues.apache.org/jira/browse/HADOOP-12675) | Fix description about retention period in usage of expunge command |  Minor | documentation | Masatake Iwasaki | Masatake Iwasaki |
| [HADOOP-12659](https://issues.apache.org/jira/browse/HADOOP-12659) | Incorrect usage of config parameters in token manager of KMS |  Major | security | Tianyin Xu | Mingliang Liu |
| [HADOOP-12658](https://issues.apache.org/jira/browse/HADOOP-12658) | Clear javadoc and check style issues around DomainSocket |  Trivial | . | Kai Zheng | Kai Zheng |
| [HADOOP-12656](https://issues.apache.org/jira/browse/HADOOP-12656) | MiniKdc throws "address in use" BindException |  Major | . | Wei-Chiu Chuang | Wei-Chiu Chuang |
| [HADOOP-12636](https://issues.apache.org/jira/browse/HADOOP-12636) | Prevent ServiceLoader failure init for unused FileSystems |  Major | fs | Inigo Goiri | Inigo Goiri |
| [HADOOP-12634](https://issues.apache.org/jira/browse/HADOOP-12634) | Change Lazy Rename Pending Operation Completion of WASB to address case of potential data loss due to partial copy |  Critical | . | Gaurav Kanade | Gaurav Kanade |
| [HADOOP-12622](https://issues.apache.org/jira/browse/HADOOP-12622) | RetryPolicies (other than FailoverOnNetworkExceptionRetry) should put on retry failed reason or the log from RMProxy's retry could be very misleading. |  Critical | auto-failover | Junping Du | Junping Du |
| [HADOOP-12618](https://issues.apache.org/jira/browse/HADOOP-12618) | NPE in TestSequenceFile |  Major | test | Brahma Reddy Battula | Brahma Reddy Battula |
| [HADOOP-12617](https://issues.apache.org/jira/browse/HADOOP-12617) | SPNEGO authentication request to non-default realm gets default realm name inserted in target server principal |  Major | security | Matt Foley | Matt Foley |
| [HADOOP-12609](https://issues.apache.org/jira/browse/HADOOP-12609) | Fix intermittent failure of TestDecayRpcScheduler |  Minor | ipc, test | Masatake Iwasaki | Masatake Iwasaki |
| [HADOOP-12608](https://issues.apache.org/jira/browse/HADOOP-12608) | Fix exception message in WASB when connecting with anonymous credential |  Major | tools | Dushyanth | Dushyanth |
| [HADOOP-12604](https://issues.apache.org/jira/browse/HADOOP-12604) | Exception may be swallowed in KMSClientProvider |  Major | kms | Yongjun Zhang | Yongjun Zhang |
| [HADOOP-12603](https://issues.apache.org/jira/browse/HADOOP-12603) | TestSymlinkLocalFSFileContext#testSetTimesSymlinkToDir occasionally fail |  Major | test | Wei-Chiu Chuang | Wei-Chiu Chuang |
| [HADOOP-12602](https://issues.apache.org/jira/browse/HADOOP-12602) | TestMetricsSystemImpl#testQSize occasionally fail |  Major | test | Wei-Chiu Chuang | Masatake Iwasaki |
| [HADOOP-12598](https://issues.apache.org/jira/browse/HADOOP-12598) | add XML namespace declarations for some hadoop/tools modules |  Minor | build, tools | Xin Wang | Xin Wang |
| [HADOOP-12590](https://issues.apache.org/jira/browse/HADOOP-12590) | TestCompressorDecompressor failing without stack traces |  Critical | test | Steve Loughran | John Zhuge |
| [HADOOP-12589](https://issues.apache.org/jira/browse/HADOOP-12589) | Fix intermittent test failure of TestCopyPreserveFlag |  Major | test | Tsuyoshi Ozawa | Masatake Iwasaki |
| [HADOOP-12587](https://issues.apache.org/jira/browse/HADOOP-12587) | Hadoop AuthToken refuses to work without a maxinactive attribute in issued token |  Blocker | security | Steve Loughran | Benoy Antony |
| [HADOOP-12584](https://issues.apache.org/jira/browse/HADOOP-12584) | Disable browsing the static directory in HttpServer2 |  Major | security | Robert Kanter | Robert Kanter |
| [HADOOP-12565](https://issues.apache.org/jira/browse/HADOOP-12565) | Replace DSA with RSA for SSH key type in SingleCluster.md |  Minor | documentation | Alexander Veit | Mingliang Liu |
| [HADOOP-12560](https://issues.apache.org/jira/browse/HADOOP-12560) | Fix sprintf warnings in {{DomainSocket.c}} introduced by HADOOP-12344 |  Major | native | Colin Patrick McCabe | Mingliang Liu |
| [HADOOP-12559](https://issues.apache.org/jira/browse/HADOOP-12559) | KMS connection failures should trigger TGT renewal |  Major | security | Zhe Zhang | Zhe Zhang |
| [HADOOP-12551](https://issues.apache.org/jira/browse/HADOOP-12551) | Introduce FileNotFoundException for WASB FileSystem API |  Major | tools | Dushyanth | Dushyanth |
| [HADOOP-12545](https://issues.apache.org/jira/browse/HADOOP-12545) | Hadoop javadoc has broken links for AccessControlList, ImpersonationProvider, DefaultImpersonationProvider, and DistCp |  Major | documentation | Arshad Mohammad | Arshad Mohammad |
| [HADOOP-12542](https://issues.apache.org/jira/browse/HADOOP-12542) | TestDNS fails on Windows after HADOOP-12437. |  Major | net | Chris Nauroth | Chris Nauroth |
| [HADOOP-12540](https://issues.apache.org/jira/browse/HADOOP-12540) | TestAzureFileSystemInstrumentation#testClientErrorMetrics fails intermittently due to assumption that a lease error will be thrown. |  Major | azure, test | Chris Nauroth | Gaurav Kanade |
| [HADOOP-12533](https://issues.apache.org/jira/browse/HADOOP-12533) | Introduce FileNotFoundException in WASB for read and seek API |  Major | tools | Dushyanth | Dushyanth |
| [HADOOP-12519](https://issues.apache.org/jira/browse/HADOOP-12519) | hadoop-azure tests should avoid creating a metrics configuration file in the module root directory. |  Minor | azure, test | Chris Nauroth | Chris Nauroth |
| [HADOOP-12513](https://issues.apache.org/jira/browse/HADOOP-12513) | Dockerfile lacks initial 'apt-get update' |  Trivial | build | Akihiro Suda | Akihiro Suda |
| [HADOOP-12508](https://issues.apache.org/jira/browse/HADOOP-12508) | delete fails with exception when lease is held on blob |  Blocker | azure | Gaurav Kanade | Gaurav Kanade |
| [HADOOP-12484](https://issues.apache.org/jira/browse/HADOOP-12484) | Single File Rename Throws Incorrectly In Potential Race Condition Scenarios |  Major | tools | Gaurav Kanade | Gaurav Kanade |
| [HADOOP-12483](https://issues.apache.org/jira/browse/HADOOP-12483) | Maintain wrapped SASL ordering for postponed IPC responses |  Critical | ipc | Daryn Sharp | Daryn Sharp |
| [HADOOP-12482](https://issues.apache.org/jira/browse/HADOOP-12482) | Race condition in JMX cache update |  Major | . | Tony Wu | Tony Wu |
| [HADOOP-12479](https://issues.apache.org/jira/browse/HADOOP-12479) | ProtocMojo does not log the reason for a protoc compilation failure. |  Minor | build | Chris Nauroth | Chris Nauroth |
| [HADOOP-12478](https://issues.apache.org/jira/browse/HADOOP-12478) | Shell.getWinUtilsPath()  has been renamed Shell.getWinutilsPath() |  Critical | util | Steve Loughran | Steve Loughran |
| [HADOOP-12474](https://issues.apache.org/jira/browse/HADOOP-12474) | MiniKMS should use random ports for Jetty server by default |  Major | . | Mingliang Liu | Mingliang Liu |
| [HADOOP-12468](https://issues.apache.org/jira/browse/HADOOP-12468) | Partial group resolution failure should not result in user lockout |  Minor | security | Wei-Chiu Chuang | Wei-Chiu Chuang |
| [HADOOP-12467](https://issues.apache.org/jira/browse/HADOOP-12467) | Respect user-defined JAVA\_LIBRARY\_PATH in Windows Hadoop scripts |  Minor | scripts | Radhey Shah | Radhey Shah |
| [HADOOP-12452](https://issues.apache.org/jira/browse/HADOOP-12452) | Fix tracing documention reflecting the update to htrace-4 |  Major | documentation | Masatake Iwasaki | Masatake Iwasaki |
| [HADOOP-12449](https://issues.apache.org/jira/browse/HADOOP-12449) | TestDNS and TestNetUtils failing if no network |  Minor | test | Steve Loughran | Steve Loughran |
| [HADOOP-12448](https://issues.apache.org/jira/browse/HADOOP-12448) | TestTextCommand: use mkdirs rather than mkdir to create test directory |  Major | test | Colin Patrick McCabe | Colin Patrick McCabe |
| [HADOOP-12447](https://issues.apache.org/jira/browse/HADOOP-12447) | Clean up some htrace integration issues |  Major | tracing | Colin Patrick McCabe | Colin Patrick McCabe |
| [HADOOP-12441](https://issues.apache.org/jira/browse/HADOOP-12441) | Fix kill command behavior under some Linux distributions. |  Critical | . | Wangda Tan | Wangda Tan |
| [HADOOP-12440](https://issues.apache.org/jira/browse/HADOOP-12440) | TestRPC#testRPCServerShutdown did not produce the desired thread states before shutting down |  Minor | . | Xiao Chen | Xiao Chen |
| [HADOOP-12438](https://issues.apache.org/jira/browse/HADOOP-12438) | Reset RawLocalFileSystem.useDeprecatedFileStatus in TestLocalFileSystem |  Trivial | test | Chris Nauroth | Chris Nauroth |
| [HADOOP-12437](https://issues.apache.org/jira/browse/HADOOP-12437) | Allow SecurityUtil to lookup alternate hostnames |  Major | net, security | Arpit Agarwal | Arpit Agarwal |
| [HADOOP-12423](https://issues.apache.org/jira/browse/HADOOP-12423) | Handle failure of registering shutdownhook by ShutdownHookManager in static block |  Minor | fs | Abhishek Agarwal | Abhishek Agarwal |
| [HADOOP-12418](https://issues.apache.org/jira/browse/HADOOP-12418) | TestRPC.testRPCInterruptedSimple fails intermittently |  Major | test | Steve Loughran | Kihwal Lee |
| [HADOOP-12417](https://issues.apache.org/jira/browse/HADOOP-12417) | TestWebDelegationToken failing with port in use |  Major | test | Steve Loughran | Mingliang Liu |
| [HADOOP-12407](https://issues.apache.org/jira/browse/HADOOP-12407) | Test failing: hadoop.ipc.TestSaslRPC |  Critical | security, test | Steve Loughran | Steve Loughran |
| [HADOOP-12388](https://issues.apache.org/jira/browse/HADOOP-12388) | Fix components' version information in the web page 'About the Cluster' |  Minor | util | Jun Gong | Jun Gong |
| [HADOOP-12386](https://issues.apache.org/jira/browse/HADOOP-12386) | RetryPolicies.RETRY\_FOREVER should be able to specify a retry interval |  Major | . | Wangda Tan | Sunil G |
| [HADOOP-12374](https://issues.apache.org/jira/browse/HADOOP-12374) | Description of hdfs expunge command is confusing |  Major | documentation, trash | Weiwei Yang | Weiwei Yang |
| [HADOOP-12362](https://issues.apache.org/jira/browse/HADOOP-12362) | Set hadoop.tmp.dir and hadoop.log.dir in pom |  Major | . | Charlie Helin | Charlie Helin |
| [HADOOP-12356](https://issues.apache.org/jira/browse/HADOOP-12356) | Fix computing CPU usage statistics on Windows |  Major | util | Yunqi Zhang | Inigo Goiri |
| [HADOOP-12352](https://issues.apache.org/jira/browse/HADOOP-12352) | Delay in checkpointing Trash can leave trash for 2 intervals before deleting |  Trivial | trash | Casey Brotherton | Casey Brotherton |
| [HADOOP-12348](https://issues.apache.org/jira/browse/HADOOP-12348) | MetricsSystemImpl creates MetricsSourceAdapter with wrong time unit parameter. |  Major | metrics | zhihai xu | zhihai xu |
| [HADOOP-12347](https://issues.apache.org/jira/browse/HADOOP-12347) | Fix mismatch parameter name in javadocs of AuthToken#setMaxInactives |  Trivial | . | Xiaoyu Yao | Xiaoyu Yao |
| [HADOOP-12346](https://issues.apache.org/jira/browse/HADOOP-12346) | Increase some default timeouts / retries for S3a connector |  Major | fs/s3 | Sean Mackrory | Sean Mackrory |
| [HADOOP-12322](https://issues.apache.org/jira/browse/HADOOP-12322) | typos in rpcmetrics.java |  Trivial | ipc | Anu Engineer | Anu Engineer |
| [HADOOP-12317](https://issues.apache.org/jira/browse/HADOOP-12317) | Applications fail on NM restart on some linux distro because NM container recovery declares AM container as LOST |  Critical | . | Anubhav Dhoot | Anubhav Dhoot |
| [HADOOP-12313](https://issues.apache.org/jira/browse/HADOOP-12313) | NPE in JvmPauseMonitor when calling stop() before start() |  Critical | . | Rohith Sharma K S | Gabor Liptak |
| [HADOOP-12302](https://issues.apache.org/jira/browse/HADOOP-12302) | Fix native compilation on Windows after HADOOP-7824 |  Blocker | . | Vinayakumar B | Vinayakumar B |
| [HADOOP-12274](https://issues.apache.org/jira/browse/HADOOP-12274) | Remove direct download link from BUILDING.txt |  Minor | documentation | Caleb Severn | Caleb Severn |
| [HADOOP-12268](https://issues.apache.org/jira/browse/HADOOP-12268) | AbstractContractAppendTest#testRenameFileBeingAppended misses rename operation. |  Major | test | zhihai xu | zhihai xu |
| [HADOOP-12258](https://issues.apache.org/jira/browse/HADOOP-12258) | Need translate java.nio.file.NoSuchFileException to FileNotFoundException to avoid regression |  Critical | fs | zhihai xu | zhihai xu |
| [HADOOP-12252](https://issues.apache.org/jira/browse/HADOOP-12252) | LocalDirAllocator should not throw NPE with empty string configuration. |  Minor | fs | zhihai xu | zhihai xu |
| [HADOOP-12245](https://issues.apache.org/jira/browse/HADOOP-12245) | References to misspelled REMAINING\_QUATA in FileSystemShell.md |  Minor | documentation | Gera Shegalov | Gabor Liptak |
| [HADOOP-12240](https://issues.apache.org/jira/browse/HADOOP-12240) | Fix tests requiring native library to be skipped in non-native profile |  Minor | test | Masatake Iwasaki | Masatake Iwasaki |
| [HADOOP-12239](https://issues.apache.org/jira/browse/HADOOP-12239) | StorageException complaining " no lease ID" when updating FolderLastModifiedTime in WASB |  Major | azure, tools | Duo Xu | Duo Xu |
| [HADOOP-12237](https://issues.apache.org/jira/browse/HADOOP-12237) | releasedocmaker.py doesn't work behind a proxy |  Major | yetus | Tsuyoshi Ozawa | Tsuyoshi Ozawa |
| [HADOOP-12235](https://issues.apache.org/jira/browse/HADOOP-12235) | hadoop-openstack junit & mockito dependencies should be "provided" |  Minor | build, fs/swift | Steve Loughran | Ted Yu |
| [HADOOP-12209](https://issues.apache.org/jira/browse/HADOOP-12209) | Comparable type should be in FileStatus |  Minor | fs | Yong Zhang | Yong Zhang |
| [HADOOP-12202](https://issues.apache.org/jira/browse/HADOOP-12202) | releasedocmaker drops missing component and assignee entries |  Blocker | yetus | Allen Wittenauer | Allen Wittenauer |
| [HADOOP-12201](https://issues.apache.org/jira/browse/HADOOP-12201) | Add tracing to FileSystem#createFileSystem and Globber#glob |  Major | . | Colin Patrick McCabe | Colin Patrick McCabe |
| [HADOOP-12200](https://issues.apache.org/jira/browse/HADOOP-12200) | TestCryptoStreamsWithOpensslAesCtrCryptoCodec should be skipped in non-native profile |  Minor | test | Masatake Iwasaki | Masatake Iwasaki |
| [HADOOP-12181](https://issues.apache.org/jira/browse/HADOOP-12181) | Fix intermittent test failure of TestZKSignerSecretProvider |  Minor | . | Masatake Iwasaki | Masatake Iwasaki |
| [HADOOP-12178](https://issues.apache.org/jira/browse/HADOOP-12178) | NPE during handling of SASL setup if problem with SASL resolver class |  Minor | ipc | Steve Loughran | Steve Loughran |
| [HADOOP-12175](https://issues.apache.org/jira/browse/HADOOP-12175) | FsShell must load SpanReceiverHost to support tracing |  Major | tracing | Masatake Iwasaki | Masatake Iwasaki |
| [HADOOP-12173](https://issues.apache.org/jira/browse/HADOOP-12173) | NetworkTopology#add calls NetworkTopology#toString always |  Major | . | Inigo Goiri | Inigo Goiri |
| [HADOOP-12171](https://issues.apache.org/jira/browse/HADOOP-12171) | Shorten overly-long htrace span names for server |  Major | tracing | Colin Patrick McCabe | Colin Patrick McCabe |
| [HADOOP-12164](https://issues.apache.org/jira/browse/HADOOP-12164) | Fix TestMove and TestFsShellReturnCode failed to get command name using reflection. |  Minor | . | Lei (Eddy) Xu | Lei (Eddy) Xu |
| [HADOOP-12159](https://issues.apache.org/jira/browse/HADOOP-12159) | Move DistCpUtils#compareFs() to org.apache.hadoop.fs.FileUtil and fix for HA namespaces |  Major | . | Ray Chiang | Ray Chiang |
| [HADOOP-12154](https://issues.apache.org/jira/browse/HADOOP-12154) | FileSystem#getUsed() returns the file length only from root '/' |  Major | . | tongshiquan | J.Andreina |
| [HADOOP-12153](https://issues.apache.org/jira/browse/HADOOP-12153) | ByteBufferReadable doesn't declare @InterfaceAudience and @InterfaceStability |  Minor | fs | Steve Loughran | Brahma Reddy Battula |
| [HADOOP-12124](https://issues.apache.org/jira/browse/HADOOP-12124) | Add HTrace support for FsShell |  Major | . | Colin Patrick McCabe | Colin Patrick McCabe |
| [HADOOP-12119](https://issues.apache.org/jira/browse/HADOOP-12119) | hadoop fs -expunge does not work for federated namespace |  Major | . | Vrushali C | J.Andreina |
| [HADOOP-12117](https://issues.apache.org/jira/browse/HADOOP-12117) | Potential NPE from Configuration#loadProperty with allowNullValueProperties set. |  Minor | conf | zhihai xu | zhihai xu |
| [HADOOP-12116](https://issues.apache.org/jira/browse/HADOOP-12116) | Fix unrecommended syntax usages in hadoop/hdfs/yarn script for cygwin in branch-2 |  Major | scripts | Li Lu | Li Lu |
| [HADOOP-12107](https://issues.apache.org/jira/browse/HADOOP-12107) | long running apps may have a huge number of StatisticsData instances under FileSystem |  Critical | fs | Sangjin Lee | Sangjin Lee |
| [HADOOP-12098](https://issues.apache.org/jira/browse/HADOOP-12098) | Remove redundant test dependencies in Hadoop Archives |  Minor | . | Varun Saxena | Varun Saxena |
| [HADOOP-12095](https://issues.apache.org/jira/browse/HADOOP-12095) | org.apache.hadoop.fs.shell.TestCount fails |  Major | test | Brahma Reddy Battula | Brahma Reddy Battula |
| [HADOOP-12089](https://issues.apache.org/jira/browse/HADOOP-12089) | StorageException complaining " no lease ID" when updating FolderLastModifiedTime in WASB |  Major | tools | Duo Xu | Duo Xu |
| [HADOOP-12088](https://issues.apache.org/jira/browse/HADOOP-12088) | KMSClientProvider uses equalsIgnoreCase("application/json") |  Major | kms | Steve Loughran | Brahma Reddy Battula |
| [HADOOP-12087](https://issues.apache.org/jira/browse/HADOOP-12087) | [JDK8] Fix javadoc errors caused by incorrect or illegal tags |  Major | documentation | Akira AJISAKA | Akira AJISAKA |
| [HADOOP-12076](https://issues.apache.org/jira/browse/HADOOP-12076) | Incomplete Cache Mechanism in CredentialProvider API |  Major | security | Larry McCay | Larry McCay |
| [HADOOP-12074](https://issues.apache.org/jira/browse/HADOOP-12074) | in Shell.java#runCommand() rethrow InterruptedException as InterruptedIOException |  Trivial | . | Lavkesh Lahngir | Lavkesh Lahngir |
| [HADOOP-12073](https://issues.apache.org/jira/browse/HADOOP-12073) | Azure FileSystem PageBlobInputStream does not return -1 on EOF |  Major | tools | Ivan Mitic | Ivan Mitic |
| [HADOOP-12058](https://issues.apache.org/jira/browse/HADOOP-12058) | Fix dead links to DistCp and Hadoop Archives pages. |  Minor | documentation, site | Kazuho Fujii | Kazuho Fujii |
| [HADOOP-12056](https://issues.apache.org/jira/browse/HADOOP-12056) | Use DirectoryStream in DiskChecker#checkDirs to detect errors when listing a directory |  Major | util | zhihai xu | zhihai xu |
| [HADOOP-12054](https://issues.apache.org/jira/browse/HADOOP-12054) | RPC client should not retry for InvalidToken exceptions |  Critical | ipc | Daryn Sharp | Varun Saxena |
| [HADOOP-12052](https://issues.apache.org/jira/browse/HADOOP-12052) | IPC client downgrades all exception types to IOE, breaks callers trying to use them |  Critical | . | Steve Loughran | Brahma Reddy Battula |
| [HADOOP-12051](https://issues.apache.org/jira/browse/HADOOP-12051) | ProtobufRpcEngine.invoke() should use Exception.toString() over getMessage in logging/span events |  Minor | ipc | Steve Loughran | Varun Saxena |
| [HADOOP-12042](https://issues.apache.org/jira/browse/HADOOP-12042) | Users may see TrashPolicy if hdfs dfs -rm is run |  Major | . | Allen Wittenauer | J.Andreina |
| [HADOOP-12037](https://issues.apache.org/jira/browse/HADOOP-12037) | Fix wrong classname in example configuration of hadoop-auth documentation |  Trivial | documentation | Masatake Iwasaki | Masatake Iwasaki |
| [HADOOP-12019](https://issues.apache.org/jira/browse/HADOOP-12019) | update BUILDING.txt to include python for 'mvn site' in windows |  Major | . | Vinayakumar B | Vinayakumar B |
| [HADOOP-12018](https://issues.apache.org/jira/browse/HADOOP-12018) | smart-apply-patch.sh fails if the patch edits CR+LF files and is created by 'git diff --no-prefix' |  Minor | build | Akira AJISAKA | Kengo Seki |
| [HADOOP-12017](https://issues.apache.org/jira/browse/HADOOP-12017) | Hadoop archives command should use configurable replication factor when closing |  Major | . | Zhe Zhang | Bibin A Chundatt |
| [HADOOP-12014](https://issues.apache.org/jira/browse/HADOOP-12014) | hadoop-config.cmd displays a wrong error message |  Minor | scripts | Kengo Seki | Kengo Seki |
| [HADOOP-12004](https://issues.apache.org/jira/browse/HADOOP-12004) | test-patch breaks with reexec in certain situations |  Critical | . | Allen Wittenauer | Sean Busbey |
| [HADOOP-12001](https://issues.apache.org/jira/browse/HADOOP-12001) | Limiting LDAP search conflicts with posixGroup addition |  Blocker | security | Patrick White | Patrick White |
| [HADOOP-11994](https://issues.apache.org/jira/browse/HADOOP-11994) | smart-apply-patch wrongly assumes that git is infallible |  Major | test | Allen Wittenauer | Kengo Seki |
| [HADOOP-11991](https://issues.apache.org/jira/browse/HADOOP-11991) | test-patch.sh isn't re-executed even if smart-apply-patch.sh is modified |  Major | test | Kengo Seki | Kengo Seki |
| [HADOOP-11988](https://issues.apache.org/jira/browse/HADOOP-11988) | Fix typo in the document for hadoop fs -find |  Trivial | documentation | Akira AJISAKA | Kengo Seki |
| [HADOOP-11969](https://issues.apache.org/jira/browse/HADOOP-11969) | ThreadLocal initialization in several classes is not thread safe |  Critical | io | Sean Busbey | Sean Busbey |
| [HADOOP-11963](https://issues.apache.org/jira/browse/HADOOP-11963) | Metrics documentation for FSNamesystem misspells PendingDataNodeMessageCount. |  Trivial | documentation | Chris Nauroth | Anu Engineer |
| [HADOOP-11962](https://issues.apache.org/jira/browse/HADOOP-11962) | Sasl message with MD5 challenge text shouldn't be LOG out even in debug level. |  Critical | ipc, security | Junping Du | Junping Du |
| [HADOOP-11959](https://issues.apache.org/jira/browse/HADOOP-11959) | WASB should configure client side socket timeout in storage client blob request options |  Major | tools | Ivan Mitic | Ivan Mitic |
| [HADOOP-11958](https://issues.apache.org/jira/browse/HADOOP-11958) | MetricsSystemImpl fails to show backtrace when an error occurs |  Major | . | Jason Lowe | Jason Lowe |
| [HADOOP-11955](https://issues.apache.org/jira/browse/HADOOP-11955) | Fix a typo in the cluster setup doc |  Trivial | . | Kihwal Lee | Yanjun Wang |
| [HADOOP-11951](https://issues.apache.org/jira/browse/HADOOP-11951) | test-patch should give better info about failures to handle dev-support updates without resetrepo option |  Minor | . | Sean Busbey | Sean Busbey |
| [HADOOP-11947](https://issues.apache.org/jira/browse/HADOOP-11947) | test-patch should return early from determine-issue  when run in jenkins mode. |  Minor | . | Sean Busbey | Sean Busbey |
| [HADOOP-11942](https://issues.apache.org/jira/browse/HADOOP-11942) | Add links to SLGUserGuide to site index |  Minor | documentation | Masatake Iwasaki | Masatake Iwasaki |
| [HADOOP-11936](https://issues.apache.org/jira/browse/HADOOP-11936) | Dockerfile references a removed image |  Major | . | Allen Wittenauer | Allen Wittenauer |
| [HADOOP-11928](https://issues.apache.org/jira/browse/HADOOP-11928) | Test-patch check for @author tags incorrectly flags removal of @author tags |  Major | . | Sean Busbey | Kengo Seki |
| [HADOOP-11927](https://issues.apache.org/jira/browse/HADOOP-11927) | Fix "undefined reference to dlopen" error when compiling libhadooppipes |  Major | build, native, tools | Xianyin Xin | Xianyin Xin |
| [HADOOP-11926](https://issues.apache.org/jira/browse/HADOOP-11926) | test-patch.sh mv does wrong math |  Major | . | Allen Wittenauer | Allen Wittenauer |
| [HADOOP-11924](https://issues.apache.org/jira/browse/HADOOP-11924) | Tolerate JDK-8047340-related exceptions in Shell#isSetSidAvailable preventing class init |  Major | . | Gera Shegalov | Tsuyoshi Ozawa |
| [HADOOP-11922](https://issues.apache.org/jira/browse/HADOOP-11922) | Misspelling of threshold in log4j.properties for tests in hadoop-tools |  Minor | . | Brahma Reddy Battula | Gabor Liptak |
| [HADOOP-11917](https://issues.apache.org/jira/browse/HADOOP-11917) | test-patch.sh should work with ${BASEDIR}/patchprocess setups |  Blocker | . | Allen Wittenauer | Allen Wittenauer |
| [HADOOP-11916](https://issues.apache.org/jira/browse/HADOOP-11916) | TestStringUtils#testLowerAndUpperStrings failed on MAC due to a JVM bug |  Minor | . | Ming Ma | Ming Ma |
| [HADOOP-11912](https://issues.apache.org/jira/browse/HADOOP-11912) | Extra configuration key used in TraceUtils should respect prefix |  Minor | . | Masatake Iwasaki | Masatake Iwasaki |
| [HADOOP-11900](https://issues.apache.org/jira/browse/HADOOP-11900) | Add failIfNoTests=false to hadoop-build-tools pom |  Major | test | Gera Shegalov | Gera Shegalov |
| [HADOOP-11898](https://issues.apache.org/jira/browse/HADOOP-11898) | add nfs3 and portmap starting command in hadoop-daemon.sh in branch-2 |  Minor | bin, nfs | Brandon Li | Brandon Li |
| [HADOOP-11889](https://issues.apache.org/jira/browse/HADOOP-11889) | Make checkstyle runnable from root project |  Major | build, test | Gera Shegalov | Gera Shegalov |
| [HADOOP-11885](https://issues.apache.org/jira/browse/HADOOP-11885) | hadoop-dist dist-layout-stitching.sh does not work with dash |  Major | build | Andrew Wang | Andrew Wang |
| [HADOOP-11878](https://issues.apache.org/jira/browse/HADOOP-11878) | FileContext.java # fixRelativePart should check for not null for a more informative exception |  Major | . | Brahma Reddy Battula | Brahma Reddy Battula |
| [HADOOP-11877](https://issues.apache.org/jira/browse/HADOOP-11877) | SnappyDecompressor's Logger class name is wrong |  Major | conf | Surendra Singh Lilhore | Surendra Singh Lilhore |
| [HADOOP-11876](https://issues.apache.org/jira/browse/HADOOP-11876) | Refactor code to make it more readable, minor maybePrintStats bug |  Trivial | tools/distcp | Zoran Dimitrijevic | Zoran Dimitrijevic |
| [HADOOP-11870](https://issues.apache.org/jira/browse/HADOOP-11870) | [JDK8] AuthenticationFilter, CertificateUtil, SignerSecretProviders, KeyAuthorizationKeyProvider Javadoc issues |  Major | build | Robert Kanter | Robert Kanter |
| [HADOOP-11866](https://issues.apache.org/jira/browse/HADOOP-11866) | increase readability and reliability of checkstyle, shellcheck, and whitespace reports |  Minor | . | Naganarasimha G R | Allen Wittenauer |
| [HADOOP-11864](https://issues.apache.org/jira/browse/HADOOP-11864) | JWTRedirectAuthenticationHandler breaks java8 javadocs |  Major | build | Steve Loughran | Larry McCay |
| [HADOOP-11861](https://issues.apache.org/jira/browse/HADOOP-11861) | test-patch.sh rewrite addendum patch |  Major | build | Anu Engineer | Allen Wittenauer |
| [HADOOP-11859](https://issues.apache.org/jira/browse/HADOOP-11859) | PseudoAuthenticationHandler fails with httpcomponents v4.4 |  Major | . | Eugene Koifman | Eugene Koifman |
| [HADOOP-11848](https://issues.apache.org/jira/browse/HADOOP-11848) | Incorrect arguments to sizeof in DomainSocket.c |  Major | native | Malcolm Kavalsky | Malcolm Kavalsky |
| [HADOOP-11846](https://issues.apache.org/jira/browse/HADOOP-11846) | TestCertificateUtil.testCorruptPEM failing on Jenkins JDK8 |  Major | build, security | Steve Loughran | Larry McCay |
| [HADOOP-11821](https://issues.apache.org/jira/browse/HADOOP-11821) | Fix findbugs warnings in hadoop-sls |  Major | tools | Akira AJISAKA | Brahma Reddy Battula |
| [HADOOP-11819](https://issues.apache.org/jira/browse/HADOOP-11819) | HttpServerFunctionalTest#prepareTestWebapp should create web app directory if it does not exist. |  Minor | . | Rohith Sharma K S | Rohith Sharma K S |
| [HADOOP-11811](https://issues.apache.org/jira/browse/HADOOP-11811) | Fix typos in hadoop-project/pom.xml and TestAccessControlList |  Minor | . | Chen He | Brahma Reddy Battula |
| [HADOOP-11800](https://issues.apache.org/jira/browse/HADOOP-11800) | Clean up some test methods in TestCodec.java |  Major | test | Akira AJISAKA | Brahma Reddy Battula |
| [HADOOP-11797](https://issues.apache.org/jira/browse/HADOOP-11797) | releasedocmaker.py needs to put ASF headers on output |  Major | build | Allen Wittenauer | Allen Wittenauer |
| [HADOOP-11760](https://issues.apache.org/jira/browse/HADOOP-11760) | Fix typo of javadoc in DistCp |  Trivial | . | Chen He | Brahma Reddy Battula |
| [HADOOP-11743](https://issues.apache.org/jira/browse/HADOOP-11743) | maven doesn't clean all the site files |  Minor | documentation | Allen Wittenauer | ramtin |
| [HADOOP-11724](https://issues.apache.org/jira/browse/HADOOP-11724) | DistCp throws NPE when the target directory is root. |  Minor | . | Lei (Eddy) Xu | Lei (Eddy) Xu |
| [HADOOP-11704](https://issues.apache.org/jira/browse/HADOOP-11704) | DelegationTokenAuthenticationFilter must pass ipaddress instead of hostname to ProxyUsers#authorize() |  Major | . | Anubhav Dhoot | Anubhav Dhoot |
| [HADOOP-11685](https://issues.apache.org/jira/browse/HADOOP-11685) | StorageException complaining " no lease ID" during HBase distributed log splitting |  Major | tools | Duo Xu | Duo Xu |
| [HADOOP-11677](https://issues.apache.org/jira/browse/HADOOP-11677) | Add cookie flags for logs and static contexts |  Major | . | nijel | nijel |
| [HADOOP-11628](https://issues.apache.org/jira/browse/HADOOP-11628) | SPNEGO auth does not work with CNAMEs in JDK8 |  Blocker | security | Daryn Sharp | Daryn Sharp |
| [HADOOP-11581](https://issues.apache.org/jira/browse/HADOOP-11581) | Fix Multithreaded correctness Warnings #org.apache.hadoop.fs.shell.Ls |  Major | . | Brahma Reddy Battula | Brahma Reddy Battula |
| [HADOOP-11568](https://issues.apache.org/jira/browse/HADOOP-11568) | Description on usage of classpath in hadoop command is incomplete. |  Trivial | tools | Archana T | Archana T |
| [HADOOP-11515](https://issues.apache.org/jira/browse/HADOOP-11515) | Upgrade jsch lib to jsch-0.1.51 to avoid problems running on java7 |  Major | build | Johannes Zillmann | Tsuyoshi Ozawa |
| [HADOOP-11328](https://issues.apache.org/jira/browse/HADOOP-11328) | ZKFailoverController does not log Exception when doRun raises errors |  Major | ha | Tianyin Xu | Tianyin Xu |
| [HADOOP-11252](https://issues.apache.org/jira/browse/HADOOP-11252) | RPC client does not time out by default |  Critical | ipc | Wilfred Spiegelenburg | Masatake Iwasaki |
| [HADOOP-11218](https://issues.apache.org/jira/browse/HADOOP-11218) | Add TLSv1.1,TLSv1.2 to KMS, HttpFS, SSLFactory |  Critical | kms | Robert Kanter | Vijay Singh |
| [HADOOP-11149](https://issues.apache.org/jira/browse/HADOOP-11149) | Increase the timeout of TestZKFailoverController |  Major | test | Rajat Jain | Steve Loughran |
| [HADOOP-11120](https://issues.apache.org/jira/browse/HADOOP-11120) | hadoop fs -rmr gives wrong advice |  Major | . | Allen Wittenauer | Juliet Hougland |
| [HADOOP-11098](https://issues.apache.org/jira/browse/HADOOP-11098) | [JDK8] Max Non Heap Memory default changed between JDK7 and 8 |  Major | . | Travis Thompson | Tsuyoshi Ozawa |
| [HADOOP-10945](https://issues.apache.org/jira/browse/HADOOP-10945) | 4-digit octal umask permissions throws a parse error |  Major | fs | Jason Lowe | Chang Li |
| [HADOOP-10941](https://issues.apache.org/jira/browse/HADOOP-10941) | Proxy user verification NPEs if remote host is unresolvable |  Critical | ipc, security | Daryn Sharp | Benoy Antony |
| [HADOOP-10798](https://issues.apache.org/jira/browse/HADOOP-10798) | globStatus() should always return a sorted list of files |  Minor | . | Felix Borchers | Colin Patrick McCabe |
| [HADOOP-10615](https://issues.apache.org/jira/browse/HADOOP-10615) | FileInputStream in JenkinsHash#main() is never closed |  Minor | . | Ted Yu | Chen He |
| [HADOOP-10582](https://issues.apache.org/jira/browse/HADOOP-10582) | Fix the test case for copying to non-existent dir in TestFsShellCopy |  Minor | fs | Kousuke Saruta | Kousuke Saruta |
| [HADOOP-10406](https://issues.apache.org/jira/browse/HADOOP-10406) | TestIPC.testIpcWithReaderQueuing may fail |  Major | ipc | Tsz Wo Nicholas Sze | Xiao Chen |
| [HADOOP-10387](https://issues.apache.org/jira/browse/HADOOP-10387) | Misspelling of threshold in log4j.properties for tests in hadoop-common-project |  Minor | conf, test | Kenji Kikushima | Brahma Reddy Battula |
| [HADOOP-10356](https://issues.apache.org/jira/browse/HADOOP-10356) | Corrections in winutils/chmod.c |  Trivial | bin | René Nyffenegger | René Nyffenegger |
| [HADOOP-10318](https://issues.apache.org/jira/browse/HADOOP-10318) | Incorrect reference to nodeFile in RumenToSLSConverter error message |  Minor | . | Ted Yu | Wei Yan |
| [HADOOP-10296](https://issues.apache.org/jira/browse/HADOOP-10296) | Incorrect null check in SwiftRestClient#buildException() |  Minor | . | Ted Yu | Kanaka Kumar Avvaru |
| [HADOOP-10027](https://issues.apache.org/jira/browse/HADOOP-10027) | \*Compressor\_deflateBytesDirect passes instance instead of jclass to GetStaticObjectField |  Minor | native | Eric Abbott | Hui Zheng |
| [HADOOP-9891](https://issues.apache.org/jira/browse/HADOOP-9891) | CLIMiniCluster instructions fail with MiniYarnCluster ClassNotFoundException |  Minor | documentation | Steve Loughran | Darrell Taylor |
| [HADOOP-9822](https://issues.apache.org/jira/browse/HADOOP-9822) | create constant MAX\_CAPACITY in RetryCache rather than hard-coding 16 in RetryCache constructor |  Minor | . | Tsuyoshi Ozawa | Tsuyoshi Ozawa |
| [HADOOP-9729](https://issues.apache.org/jira/browse/HADOOP-9729) | The example code of org.apache.hadoop.util.Tool is incorrect |  Major | util | hellojinjie | hellojinjie |
| [HADOOP-9692](https://issues.apache.org/jira/browse/HADOOP-9692) | Improving log message when SequenceFile reader throws EOFException on zero-length file |  Major | . | Chu Tong | Zhe Zhang |
| [HADOOP-9121](https://issues.apache.org/jira/browse/HADOOP-9121) | InodeTree.java has redundant check for vName while throwing exception |  Major | fs | Arup Malakar | Arup Malakar |
| [HADOOP-8818](https://issues.apache.org/jira/browse/HADOOP-8818) | Should use equals() rather than == to compare String or Text in MD5MD5CRC32FileChecksum and TFileDumper |  Minor | fs, io | Brandon Li | Brandon Li |
| [HADOOP-8751](https://issues.apache.org/jira/browse/HADOOP-8751) | NPE in Token.toString() when Token is constructed using null identifier |  Minor | security | Vlad Rozov | Kanaka Kumar Avvaru |
| [HADOOP-8437](https://issues.apache.org/jira/browse/HADOOP-8437) | getLocalPathForWrite should throw IOException for invalid paths |  Major | fs | Brahma Reddy Battula | Brahma Reddy Battula |
| [HADOOP-8436](https://issues.apache.org/jira/browse/HADOOP-8436) | NPE In getLocalPathForWrite ( path, conf ) when the required context item is not configured |  Major | fs | Brahma Reddy Battula | Brahma Reddy Battula |
| [HADOOP-8419](https://issues.apache.org/jira/browse/HADOOP-8419) | GzipCodec NPE upon reset with IBM JDK |  Major | io | Luke Lu | Yu Li |
| [HADOOP-8174](https://issues.apache.org/jira/browse/HADOOP-8174) | Remove confusing comment in Path#isAbsolute() |  Trivial | fs | Suresh Srinivas | Suresh Srinivas |
| [HADOOP-7817](https://issues.apache.org/jira/browse/HADOOP-7817) | RawLocalFileSystem.append() should give FSDataOutputStream with accurate .getPos() |  Minor | fs | Kristofer Tomasette | Kanaka Kumar Avvaru |
| [HADOOP-7165](https://issues.apache.org/jira/browse/HADOOP-7165) | listLocatedStatus(path, filter) is not redefined in FilterFs |  Major | fs | Hairong Kuang | Hairong Kuang |
| [HADOOP-7161](https://issues.apache.org/jira/browse/HADOOP-7161) | Remove unnecessary oro package from dependency management section |  Minor | build | Todd Lipcon | Sean Busbey |
| [HDFS-9864](https://issues.apache.org/jira/browse/HDFS-9864) | Correct reference for RENEWDELEGATIONTOKEN and CANCELDELEGATIONTOKEN in webhdfs doc |  Major | documentation | Brahma Reddy Battula | Brahma Reddy Battula |
| [HDFS-9855](https://issues.apache.org/jira/browse/HDFS-9855) | Modify TestAuditLoggerWithCommands to workaround the absence of HDFS-8332 |  Major | test | Kuhu Shukla | Kuhu Shukla |
| [HDFS-9844](https://issues.apache.org/jira/browse/HDFS-9844) | Correct path creation in getTrashRoot to handle root dir |  Blocker | encryption | Zhe Zhang | Zhe Zhang |
| [HDFS-9842](https://issues.apache.org/jira/browse/HDFS-9842) | dfs.datanode.balance.bandwidthPerSec should accept friendly size units |  Minor | balancer & mover | Lin Yiqun | Lin Yiqun |
| [HDFS-9839](https://issues.apache.org/jira/browse/HDFS-9839) | Reduce verbosity of processReport logging |  Major | namenode | Arpit Agarwal | Arpit Agarwal |
| [HDFS-9815](https://issues.apache.org/jira/browse/HDFS-9815) | Move o.a.h.fs.Hdfs to hadoop-hdfs-client |  Blocker | . | Haohui Mai | Vinayakumar B |
| [HDFS-9801](https://issues.apache.org/jira/browse/HDFS-9801) | ReconfigurableBase should update the cached configuration |  Major | datanode | Arpit Agarwal | Arpit Agarwal |
| [HDFS-9799](https://issues.apache.org/jira/browse/HDFS-9799) | Reimplement getCurrentTrashDir to remove incompatibility |  Blocker | . | Zhe Zhang | Zhe Zhang |
| [HDFS-9790](https://issues.apache.org/jira/browse/HDFS-9790) | HDFS Balancer should exit with a proper message if upgrade is not finalized |  Major | . | Xiaobing Zhou | Xiaobing Zhou |
| [HDFS-9788](https://issues.apache.org/jira/browse/HDFS-9788) | Incompatible tag renumbering in HeartbeatResponseProto |  Blocker | rolling upgrades | Andrew Wang | Andrew Wang |
| [HDFS-9784](https://issues.apache.org/jira/browse/HDFS-9784) | Example usage is not correct in Transparent Encryption document |  Major | documentation | Takashi Ohnishi | Takashi Ohnishi |
| [HDFS-9779](https://issues.apache.org/jira/browse/HDFS-9779) | TestReplicationPolicyWithNodeGroup NODE variable picks wrong rack value |  Minor | test | Kuhu Shukla | Kuhu Shukla |
| [HDFS-9777](https://issues.apache.org/jira/browse/HDFS-9777) | Fix typos in DFSAdmin command line and documentation |  Trivial | hdfs-client | Wei-Chiu Chuang | Wei-Chiu Chuang |
| [HDFS-9765](https://issues.apache.org/jira/browse/HDFS-9765) | TestBlockScanner#testVolumeIteratorWithCaching fails intermittently |  Major | test | Mingliang Liu | Akira AJISAKA |
| [HDFS-9764](https://issues.apache.org/jira/browse/HDFS-9764) | DistCp doesn't print value for several arguments including -numListstatusThreads |  Minor | distcp | Yongjun Zhang | Wei-Chiu Chuang |
| [HDFS-9761](https://issues.apache.org/jira/browse/HDFS-9761) | Rebalancer sleeps too long between iterations |  Blocker | balancer & mover | Adrian Bridgett | Mingliang Liu |
| [HDFS-9760](https://issues.apache.org/jira/browse/HDFS-9760) | WebHDFS AuthFilter cannot be configured with custom AltKerberos auth handler |  Major | webhdfs | Ryan Sasson | Ryan Sasson |
| [HDFS-9752](https://issues.apache.org/jira/browse/HDFS-9752) | Permanent write failures may happen to slow writers during datanode rolling upgrades |  Critical | . | Kihwal Lee | Walter Su |
| [HDFS-9748](https://issues.apache.org/jira/browse/HDFS-9748) | When addExpectedReplicasToPending is called twice, pendingReplications should avoid duplication |  Minor | . | Walter Su | Walter Su |
| [HDFS-9739](https://issues.apache.org/jira/browse/HDFS-9739) | DatanodeStorage.isValidStorageId() is broken |  Critical | hdfs-client | Kihwal Lee | Mingliang Liu |
| [HDFS-9718](https://issues.apache.org/jira/browse/HDFS-9718) | HAUtil#getConfForOtherNodes should unset independent generic keys before initialize |  Major | namenode | DENG FEI | DENG FEI |
| [HDFS-9713](https://issues.apache.org/jira/browse/HDFS-9713) | DataXceiver#copyBlock should return if block is pinned |  Major | datanode | Uma Maheswara Rao G | Uma Maheswara Rao G |
| [HDFS-9708](https://issues.apache.org/jira/browse/HDFS-9708) | FSNamesystem.initAuditLoggers() doesn't trim classnames |  Minor | fs | Steve Loughran | Mingliang Liu |
| [HDFS-9701](https://issues.apache.org/jira/browse/HDFS-9701) | DN may deadlock when hot-swapping under load |  Major | . | Xiao Chen | Xiao Chen |
| [HDFS-9682](https://issues.apache.org/jira/browse/HDFS-9682) | Fix a typo "aplication" in HttpFS document |  Trivial | documentation | Weiwei Yang | Weiwei Yang |
| [HDFS-9672](https://issues.apache.org/jira/browse/HDFS-9672) | o.a.h.hdfs.TestLeaseRecovery2 fails intermittently |  Major | test | Mingliang Liu | Mingliang Liu |
| [HDFS-9655](https://issues.apache.org/jira/browse/HDFS-9655) | NN should start JVM pause monitor before loading fsimage |  Critical | . | John Zhuge | John Zhuge |
| [HDFS-9639](https://issues.apache.org/jira/browse/HDFS-9639) | Inconsistent Logging in BootstrapStandby |  Minor | ha | BELUGA BEHR | Xiaobing Zhou |
| [HDFS-9623](https://issues.apache.org/jira/browse/HDFS-9623) | Update example configuration of block state change log in log4j.properties |  Minor | logging | Masatake Iwasaki | Masatake Iwasaki |
| [HDFS-9619](https://issues.apache.org/jira/browse/HDFS-9619) | SimulatedFSDataset sometimes can not find blockpool for the correct namenode |  Major | datanode, test | Wei-Chiu Chuang | Wei-Chiu Chuang |
| [HDFS-9612](https://issues.apache.org/jira/browse/HDFS-9612) | DistCp worker threads are not terminated after jobs are done. |  Major | distcp | Wei-Chiu Chuang | Wei-Chiu Chuang |
| [HDFS-9605](https://issues.apache.org/jira/browse/HDFS-9605) | Add links to failed volumes to explorer.html in HDFS Web UI |  Minor | . | Archana T | Archana T |
| [HDFS-9601](https://issues.apache.org/jira/browse/HDFS-9601) | NNThroughputBenchmark.BlockReportStats should handle NotReplicatedYetException on adding block |  Major | test | Masatake Iwasaki | Masatake Iwasaki |
| [HDFS-9600](https://issues.apache.org/jira/browse/HDFS-9600) | do not check replication if the block is under construction |  Critical | . | Phil Yang | Phil Yang |
| [HDFS-9597](https://issues.apache.org/jira/browse/HDFS-9597) | BaseReplicationPolicyTest should update data node stats after adding a data node |  Blocker | datanode | Wei-Chiu Chuang | Wei-Chiu Chuang |
| [HDFS-9589](https://issues.apache.org/jira/browse/HDFS-9589) | Block files which have been hardlinked should be duplicated before the DataNode appends to the them |  Major | datanode | Colin Patrick McCabe | Colin Patrick McCabe |
| [HDFS-9584](https://issues.apache.org/jira/browse/HDFS-9584) | NPE in distcp when ssl configuration file does not exist in class path. |  Major | distcp | Surendra Singh Lilhore | Surendra Singh Lilhore |
| [HDFS-9572](https://issues.apache.org/jira/browse/HDFS-9572) | Prevent DataNode log spam if a client connects on the data transfer port but sends no data. |  Major | datanode | Chris Nauroth | Chris Nauroth |
| [HDFS-9571](https://issues.apache.org/jira/browse/HDFS-9571) | Fix ASF Licence warnings in Jenkins reports |  Major | test | Brahma Reddy Battula | Brahma Reddy Battula |
| [HDFS-9565](https://issues.apache.org/jira/browse/HDFS-9565) | TestDistributedFileSystem.testLocatedFileStatusStorageIdsTypes is flaky due to race condition |  Minor | fs, test | Wei-Chiu Chuang | Wei-Chiu Chuang |
| [HDFS-9549](https://issues.apache.org/jira/browse/HDFS-9549) | TestCacheDirectives#testExceedsCapacity is flaky |  Major | . | Wei-Chiu Chuang | Xiao Chen |
| [HDFS-9535](https://issues.apache.org/jira/browse/HDFS-9535) | Newly completed blocks in IBR should not be considered under-replicated too quickly |  Major | namenode | Jing Zhao | Mingliang Liu |
| [HDFS-9519](https://issues.apache.org/jira/browse/HDFS-9519) | Some coding improvement in SecondaryNameNode#main |  Major | namenode | Yongjun Zhang | Xiao Chen |
| [HDFS-9515](https://issues.apache.org/jira/browse/HDFS-9515) | NPE when MiniDFSCluster#shutdown is invoked on uninitialized reference |  Minor | . | Wei-Chiu Chuang | Wei-Chiu Chuang |
| [HDFS-9514](https://issues.apache.org/jira/browse/HDFS-9514) | TestDistributedFileSystem.testDFSClientPeerWriteTimeout failing; exception being swallowed |  Major | hdfs-client, test | Steve Loughran | Wei-Chiu Chuang |
| [HDFS-9505](https://issues.apache.org/jira/browse/HDFS-9505) | HDFS Architecture documentation needs to be refreshed. |  Major | documentation | Chris Nauroth | Masatake Iwasaki |
| [HDFS-9503](https://issues.apache.org/jira/browse/HDFS-9503) | Replace -namenode option with -fs for NNThroughputBenchmark |  Major | test | Konstantin Shvachko | Mingliang Liu |
| [HDFS-9493](https://issues.apache.org/jira/browse/HDFS-9493) | Test o.a.h.hdfs.server.namenode.TestMetaSave fails in trunk |  Major | test | Mingliang Liu | Tony Wu |
| [HDFS-9484](https://issues.apache.org/jira/browse/HDFS-9484) | NNThroughputBenchmark$BlockReportStats should not send empty block reports |  Major | test | Mingliang Liu | Mingliang Liu |
| [HDFS-9467](https://issues.apache.org/jira/browse/HDFS-9467) | Fix data race accessing writeLockHeldTimeStamp in FSNamesystem |  Major | namenode | Mingliang Liu | Mingliang Liu |
| [HDFS-9459](https://issues.apache.org/jira/browse/HDFS-9459) | hadoop-hdfs-native-client fails test build on Windows after transition to ctest. |  Blocker | build, test | Chris Nauroth | Chris Nauroth |
| [HDFS-9458](https://issues.apache.org/jira/browse/HDFS-9458) | TestBackupNode always binds to port 50070, which can cause bind failures. |  Major | test | Chris Nauroth | Xiao Chen |
| [HDFS-9456](https://issues.apache.org/jira/browse/HDFS-9456) | BlockPlacementPolicyWithNodeGroup should override verifyBlockPlacement |  Major | . | Junping Du | Xiaobing Zhou |
| [HDFS-9443](https://issues.apache.org/jira/browse/HDFS-9443) | Disabling HDFS client socket cache causes logging message printed to console for CLI commands. |  Trivial | hdfs-client | Chris Nauroth | Chris Nauroth |
| [HDFS-9435](https://issues.apache.org/jira/browse/HDFS-9435) | TestBlockRecovery#testRBWReplicas is failing intermittently |  Major | . | Rakesh R | Rakesh R |
| [HDFS-9430](https://issues.apache.org/jira/browse/HDFS-9430) | Remove waitForLoadingFSImage since checkNNStartup has ensured image loaded and namenode started. |  Major | . | Brahma Reddy Battula | Brahma Reddy Battula |
| [HDFS-9428](https://issues.apache.org/jira/browse/HDFS-9428) | Fix intermittent failure of TestDNFencing.testQueueingWithAppend |  Minor | test | Masatake Iwasaki | Masatake Iwasaki |
| [HDFS-9421](https://issues.apache.org/jira/browse/HDFS-9421) | NNThroughputBenchmark replication test NPE with -namenode option |  Major | benchmarks | Xiaoyu Yao | Mingliang Liu |
| [HDFS-9407](https://issues.apache.org/jira/browse/HDFS-9407) | TestFileTruncate fails with BindException |  Major | test | Brahma Reddy Battula | Brahma Reddy Battula |
| [HDFS-9406](https://issues.apache.org/jira/browse/HDFS-9406) | FSImage may get corrupted after deleting snapshot |  Major | namenode | Stanislav Antic | Yongjun Zhang |
| [HDFS-9401](https://issues.apache.org/jira/browse/HDFS-9401) | Fix findbugs warnings in BlockRecoveryWorker |  Major | . | Brahma Reddy Battula | Brahma Reddy Battula |
| [HDFS-9400](https://issues.apache.org/jira/browse/HDFS-9400) | TestRollingUpgradeRollback fails on branch-2. |  Blocker | . | Chris Nauroth | Brahma Reddy Battula |
| [HDFS-9397](https://issues.apache.org/jira/browse/HDFS-9397) | Fix typo for readChecksum() LOG.warn in BlockSender.java |  Trivial | . | Enrique Flores | Enrique Flores |
| [HDFS-9396](https://issues.apache.org/jira/browse/HDFS-9396) | Total files and directories on jmx and web UI on standby is uninitialized |  Blocker | . | Kihwal Lee | Kihwal Lee |
| [HDFS-9394](https://issues.apache.org/jira/browse/HDFS-9394) | branch-2 hadoop-hdfs-client fails during FileSystem ServiceLoader initialization, because HftpFileSystem is missing. |  Critical | hdfs-client | Chris Nauroth | Mingliang Liu |
| [HDFS-9393](https://issues.apache.org/jira/browse/HDFS-9393) | After choosing favored nodes, choosing nodes for remaining replicas should go through BlockPlacementPolicy |  Major | . | J.Andreina | J.Andreina |
| [HDFS-9387](https://issues.apache.org/jira/browse/HDFS-9387) | Fix namenodeUri parameter parsing in NNThroughputBenchmark |  Major | test | Mingliang Liu | Mingliang Liu |
| [HDFS-9384](https://issues.apache.org/jira/browse/HDFS-9384) | TestWebHdfsContentLength intermittently hangs and fails due to TCP conversation mismatch between client and server. |  Minor | test | Chris Nauroth | Chris Nauroth |
| [HDFS-9378](https://issues.apache.org/jira/browse/HDFS-9378) | hadoop-hdfs-client tests do not write logs. |  Minor | test | Chris Nauroth | Chris Nauroth |
| [HDFS-9372](https://issues.apache.org/jira/browse/HDFS-9372) | Remove dead code in DataStorage.recoverTransitionRead |  Major | datanode | Duo Zhang | Duo Zhang |
| [HDFS-9364](https://issues.apache.org/jira/browse/HDFS-9364) | Unnecessary DNS resolution attempts when creating NameNodeProxies |  Major | ha, performance | Xiao Chen | Xiao Chen |
| [HDFS-9362](https://issues.apache.org/jira/browse/HDFS-9362) | TestAuditLogger#testAuditLoggerWithCallContext assumes Unix line endings, fails on Windows. |  Minor | test | Chris Nauroth | Chris Nauroth |
| [HDFS-9360](https://issues.apache.org/jira/browse/HDFS-9360) | Storage type usage isn't updated properly after file deletion |  Major | . | Ming Ma | Ming Ma |
| [HDFS-9358](https://issues.apache.org/jira/browse/HDFS-9358) | TestNodeCount#testNodeCount timed out |  Major | test | Wei-Chiu Chuang | Masatake Iwasaki |
| [HDFS-9357](https://issues.apache.org/jira/browse/HDFS-9357) | NN UI renders icons of decommissioned DN incorrectly |  Critical | . | Archana T | Surendra Singh Lilhore |
| [HDFS-9356](https://issues.apache.org/jira/browse/HDFS-9356) | Decommissioning node does not have Last Contact value in the UI |  Major | . | Archana T | Surendra Singh Lilhore |
| [HDFS-9351](https://issues.apache.org/jira/browse/HDFS-9351) | checkNNStartup() need to be called when fsck calls FSNamesystem.getSnapshottableDirs() |  Major | namenode | Yongjun Zhang | Xiao Chen |
| [HDFS-9347](https://issues.apache.org/jira/browse/HDFS-9347) | Invariant assumption in TestQuorumJournalManager.shutdown() is wrong |  Major | test | Wei-Chiu Chuang | Wei-Chiu Chuang |
| [HDFS-9336](https://issues.apache.org/jira/browse/HDFS-9336) | deleteSnapshot throws NPE when snapshotname is null |  Major | . | Brahma Reddy Battula | Brahma Reddy Battula |
| [HDFS-9332](https://issues.apache.org/jira/browse/HDFS-9332) | Fix Precondition failures from NameNodeEditLogRoller while saving namespace |  Major | . | Andrew Wang | Andrew Wang |
| [HDFS-9329](https://issues.apache.org/jira/browse/HDFS-9329) | TestBootstrapStandby#testRateThrottling is flaky because fsimage size is smaller than IO buffer size |  Minor | test | Zhe Zhang | Zhe Zhang |
| [HDFS-9318](https://issues.apache.org/jira/browse/HDFS-9318) | considerLoad factor can be improved |  Major | . | Kuhu Shukla | Kuhu Shukla |
| [HDFS-9313](https://issues.apache.org/jira/browse/HDFS-9313) | Possible NullPointerException in BlockManager if no excess replica can be chosen |  Major | . | Ming Ma | Ming Ma |
| [HDFS-9302](https://issues.apache.org/jira/browse/HDFS-9302) | WebHDFS truncate throws NullPointerException if newLength is not provided |  Minor | webhdfs | Karthik Palaniappan | Jagadesh Kiran N |
| [HDFS-9301](https://issues.apache.org/jira/browse/HDFS-9301) | HDFS clients can't construct HdfsConfiguration instances |  Major | . | Steve Loughran | Mingliang Liu |
| [HDFS-9286](https://issues.apache.org/jira/browse/HDFS-9286) | HttpFs does not parse ACL syntax correctly for operation REMOVEACLENTRIES |  Major | fs | Wei-Chiu Chuang | Wei-Chiu Chuang |
| [HDFS-9284](https://issues.apache.org/jira/browse/HDFS-9284) | fsck command should not print exception trace when file not found |  Major | . | Jagadesh Kiran N | Jagadesh Kiran N |
| [HDFS-9279](https://issues.apache.org/jira/browse/HDFS-9279) | Decomissioned capacity should not be considered for configured/used capacity |  Major | . | Kuhu Shukla | Kuhu Shukla |
| [HDFS-9274](https://issues.apache.org/jira/browse/HDFS-9274) | Default value of dfs.datanode.directoryscan.throttle.limit.ms.per.sec should be consistent |  Trivial | datanode | Yi Liu | Yi Liu |
| [HDFS-9270](https://issues.apache.org/jira/browse/HDFS-9270) | TestShortCircuitLocalRead should not leave socket after unit test |  Minor | test | Masatake Iwasaki | Masatake Iwasaki |
| [HDFS-9268](https://issues.apache.org/jira/browse/HDFS-9268) | fuse\_dfs chown crashes when uid is passed as -1 |  Minor | . | Wei-Chiu Chuang | Colin Patrick McCabe |
| [HDFS-9249](https://issues.apache.org/jira/browse/HDFS-9249) | NPE is thrown if an IOException is thrown in NameNode constructor |  Minor | namenode | Wei-Chiu Chuang | Wei-Chiu Chuang |
| [HDFS-9245](https://issues.apache.org/jira/browse/HDFS-9245) | Fix findbugs warnings in hdfs-nfs/WriteCtx |  Major | nfs | Mingliang Liu | Mingliang Liu |
| [HDFS-9237](https://issues.apache.org/jira/browse/HDFS-9237) | NPE at TestDataNodeVolumeFailureToleration#tearDown |  Major | test | Brahma Reddy Battula | Brahma Reddy Battula |
| [HDFS-9236](https://issues.apache.org/jira/browse/HDFS-9236) | Missing sanity check for block size during block recovery |  Major | datanode | Tony Wu | Tony Wu |
| [HDFS-9235](https://issues.apache.org/jira/browse/HDFS-9235) | hdfs-native-client build getting errors when built with cmake 2.6 |  Minor | hdfs-client | Eric Payne | Eric Payne |
| [HDFS-9231](https://issues.apache.org/jira/browse/HDFS-9231) | fsck doesn't list correct file path when Bad Replicas/Blocks are in a snapshot |  Major | snapshots | Xiao Chen | Xiao Chen |
| [HDFS-9225](https://issues.apache.org/jira/browse/HDFS-9225) | Fix intermittent test failure of TestBlockManager.testBlocksAreNotUnderreplicatedInSingleRack |  Minor | test | Masatake Iwasaki | Masatake Iwasaki |
| [HDFS-9224](https://issues.apache.org/jira/browse/HDFS-9224) | TestFileTruncate fails intermittently with BindException |  Major | test | Brahma Reddy Battula | Brahma Reddy Battula |
| [HDFS-9222](https://issues.apache.org/jira/browse/HDFS-9222) | Add hadoop-hdfs-client as a dependency of hadoop-hdfs-native-client |  Major | . | Haohui Mai | Mingliang Liu |
| [HDFS-9215](https://issues.apache.org/jira/browse/HDFS-9215) | Suppress the RAT warnings in hdfs-native-client module |  Minor | . | Haohui Mai | Haohui Mai |
| [HDFS-9211](https://issues.apache.org/jira/browse/HDFS-9211) | Fix incorrect version in hadoop-hdfs-native-client/pom.xml from HDFS-9170 branch-2 backport |  Major | build | Eric Payne | Eric Payne |
| [HDFS-9210](https://issues.apache.org/jira/browse/HDFS-9210) | Fix some misuse of %n in VolumeScanner#printStats |  Minor | datanode | Xiaoyu Yao | Xiaoyu Yao |
| [HDFS-9208](https://issues.apache.org/jira/browse/HDFS-9208) | Disabling atime may fail clients like distCp |  Major | . | Kihwal Lee | Kihwal Lee |
| [HDFS-9196](https://issues.apache.org/jira/browse/HDFS-9196) | Fix TestWebHdfsContentLength |  Major | . | Tsuyoshi Ozawa | Masatake Iwasaki |
| [HDFS-9193](https://issues.apache.org/jira/browse/HDFS-9193) | Fix incorrect references the usages of the DN in dfshealth.js |  Minor | . | Chang Li | Chang Li |
| [HDFS-9191](https://issues.apache.org/jira/browse/HDFS-9191) | Typo in  Hdfs.java.  NoSuchElementException is misspelled |  Trivial | documentation | Catherine Palmer | Catherine Palmer |
| [HDFS-9187](https://issues.apache.org/jira/browse/HDFS-9187) | Fix null pointer error in Globber when FS was not constructed via FileSystem#createFileSystem |  Major | tracing | stack | Colin Patrick McCabe |
| [HDFS-9176](https://issues.apache.org/jira/browse/HDFS-9176) | TestDirectoryScanner#testThrottling often fails. |  Minor | test | Yi Liu | Daniel Templeton |
| [HDFS-9174](https://issues.apache.org/jira/browse/HDFS-9174) | Fix findbugs warnings in FSOutputSummer.tracer and DirectoryScanner$ReportCompiler.currentThread |  Critical | . | Yi Liu | Yi Liu |
| [HDFS-9147](https://issues.apache.org/jira/browse/HDFS-9147) | Fix the setting of visibleLength in ExternalBlockReader |  Major | hdfs-client | Colin Patrick McCabe | Colin Patrick McCabe |
| [HDFS-9142](https://issues.apache.org/jira/browse/HDFS-9142) | Separating Configuration object for namenode(s) in MiniDFSCluster |  Major | . | Siqi Li | Siqi Li |
| [HDFS-9141](https://issues.apache.org/jira/browse/HDFS-9141) | Thread leak in Datanode#refreshVolumes |  Major | datanode | Uma Maheswara Rao G | Uma Maheswara Rao G |
| [HDFS-9137](https://issues.apache.org/jira/browse/HDFS-9137) | DeadLock between DataNode#refreshVolumes and BPOfferService#registrationSucceeded |  Major | datanode | Uma Maheswara Rao G | Uma Maheswara Rao G |
| [HDFS-9133](https://issues.apache.org/jira/browse/HDFS-9133) | ExternalBlockReader and ReplicaAccessor need to return -1 on read when at EOF |  Major | hdfs-client | Colin Patrick McCabe | Colin Patrick McCabe |
| [HDFS-9128](https://issues.apache.org/jira/browse/HDFS-9128) | TestWebHdfsFileContextMainOperations and TestSWebHdfsFileContextMainOperations fail due to invalid HDFS path on Windows. |  Trivial | test | Chris Nauroth | Chris Nauroth |
| [HDFS-9123](https://issues.apache.org/jira/browse/HDFS-9123) | Copying from the root to a subdirectory should be forbidden |  Minor | fs | Wei-Chiu Chuang | Wei-Chiu Chuang |
| [HDFS-9107](https://issues.apache.org/jira/browse/HDFS-9107) | Prevent NN's unrecoverable death spiral after full GC |  Critical | namenode | Daryn Sharp | Daryn Sharp |
| [HDFS-9100](https://issues.apache.org/jira/browse/HDFS-9100) | HDFS Balancer does not respect dfs.client.use.datanode.hostname |  Major | balancer & mover | Yongjun Zhang | Casey Brotherton |
| [HDFS-9092](https://issues.apache.org/jira/browse/HDFS-9092) | Nfs silently drops overlapping write requests and causes data copying to fail |  Major | nfs | Yongjun Zhang | Yongjun Zhang |
| [HDFS-9080](https://issues.apache.org/jira/browse/HDFS-9080) | update htrace version to 4.0.1 |  Major | tracing | Colin Patrick McCabe | Colin Patrick McCabe |
| [HDFS-9076](https://issues.apache.org/jira/browse/HDFS-9076) | Log full path instead of inodeId in DFSClient#closeAllFilesBeingWritten() |  Major | hdfs-client | Surendra Singh Lilhore | Surendra Singh Lilhore |
| [HDFS-9073](https://issues.apache.org/jira/browse/HDFS-9073) | Fix failures in TestLazyPersistLockedMemory#testReleaseOnEviction |  Critical | test | J.Andreina | J.Andreina |
| [HDFS-9072](https://issues.apache.org/jira/browse/HDFS-9072) | Fix random failures in TestJMXGet |  Critical | test | J.Andreina | J.Andreina |
| [HDFS-9069](https://issues.apache.org/jira/browse/HDFS-9069) | TestNameNodeMetricsLogger failing -port in use |  Critical | test | Steve Loughran | Steve Loughran |
| [HDFS-9067](https://issues.apache.org/jira/browse/HDFS-9067) | o.a.h.hdfs.server.datanode.fsdataset.impl.TestLazyWriter is failing in trunk |  Critical | . | Haohui Mai | Surendra Singh Lilhore |
| [HDFS-9063](https://issues.apache.org/jira/browse/HDFS-9063) | Correctly handle snapshot path for getContentSummary |  Major | namenode | Jing Zhao | Jing Zhao |
| [HDFS-9044](https://issues.apache.org/jira/browse/HDFS-9044) | Give Priority to FavouredNodes , before selecting nodes from FavouredNode's Node Group |  Major | . | J.Andreina | J.Andreina |
| [HDFS-9036](https://issues.apache.org/jira/browse/HDFS-9036) | In BlockPlacementPolicyWithNodeGroup#chooseLocalStorage , random node is selected eventhough fallbackToLocalRack is true. |  Major | . | J.Andreina | J.Andreina |
| [HDFS-9013](https://issues.apache.org/jira/browse/HDFS-9013) | Deprecate NameNodeMXBean#getNNStarted in branch2 and remove from trunk |  Major | namenode | Surendra Singh Lilhore | Surendra Singh Lilhore |
| [HDFS-9009](https://issues.apache.org/jira/browse/HDFS-9009) | Send metrics logs to NullAppender by default |  Major | logging | Arpit Agarwal | Arpit Agarwal |
| [HDFS-9003](https://issues.apache.org/jira/browse/HDFS-9003) | ForkJoin thread pool leaks |  Major | . | Kihwal Lee | Kihwal Lee |
| [HDFS-9001](https://issues.apache.org/jira/browse/HDFS-9001) | DFSUtil.getNsServiceRpcUris() can return too many entries in a non-HA, non-federated cluster |  Major | . | Daniel Templeton | Daniel Templeton |
| [HDFS-8999](https://issues.apache.org/jira/browse/HDFS-8999) | Allow a file to be closed with COMMITTED but not yet COMPLETE blocks. |  Major | namenode | Jitendra Nath Pandey | Tsz Wo Nicholas Sze |
| [HDFS-8996](https://issues.apache.org/jira/browse/HDFS-8996) | Consolidate validateLog and scanLog in FJM#EditLogFile |  Major | journal-node, namenode | Zhe Zhang | Zhe Zhang |
| [HDFS-8969](https://issues.apache.org/jira/browse/HDFS-8969) | Clean up findbugs warnings for HDFS-8823 and HDFS-8932 |  Major | namenode | Anu Engineer | Anu Engineer |
| [HDFS-8964](https://issues.apache.org/jira/browse/HDFS-8964) | When validating the edit log, do not read at or beyond the file offset that is being written |  Major | journal-node, namenode | Zhe Zhang | Zhe Zhang |
| [HDFS-8963](https://issues.apache.org/jira/browse/HDFS-8963) | Fix incorrect sign extension of xattr length in HDFS-8900 |  Critical | . | Haohui Mai | Colin Patrick McCabe |
| [HDFS-8961](https://issues.apache.org/jira/browse/HDFS-8961) | Surpress findbug warnings of o.a.h.hdfs.shortcircuit.DfsClientShmManager.EndpointShmManager in hdfs-client |  Major | . | Haohui Mai | Mingliang Liu |
| [HDFS-8942](https://issues.apache.org/jira/browse/HDFS-8942) | Update hyperlink to rack awareness page in HDFS Architecture documentation |  Trivial | documentation | Masatake Iwasaki | Masatake Iwasaki |
| [HDFS-8941](https://issues.apache.org/jira/browse/HDFS-8941) | DistributedFileSystem listCorruptFileBlocks API should resolve relative path |  Major | hdfs-client | Rakesh R | Rakesh R |
| [HDFS-8939](https://issues.apache.org/jira/browse/HDFS-8939) | Test(S)WebHdfsFileContextMainOperations failing on branch-2 |  Major | webhdfs | Jakob Homan | Chris Nauroth |
| [HDFS-8932](https://issues.apache.org/jira/browse/HDFS-8932) | NPE thrown in NameNode when try to get "TotalSyncCount" metric before editLogStream initialization |  Major | . | Surendra Singh Lilhore | Surendra Singh Lilhore |
| [HDFS-8930](https://issues.apache.org/jira/browse/HDFS-8930) | Block report lease may leak if the 2nd full block report comes when NN is still in safemode |  Minor | . | Jing Zhao | Jing Zhao |
| [HDFS-8923](https://issues.apache.org/jira/browse/HDFS-8923) | Add -source flag to balancer usage message |  Trivial | balancer & mover, documentation | Chris Trezzo | Chris Trezzo |
| [HDFS-8922](https://issues.apache.org/jira/browse/HDFS-8922) | Link the native\_mini\_dfs test library with libdl, since IBM Java requires it |  Major | build | Ayappan | Ayappan |
| [HDFS-8914](https://issues.apache.org/jira/browse/HDFS-8914) | Document HA support in the HDFS HdfsDesign.md |  Major | documentation | Ravindra Babu | Lars Francke |
| [HDFS-8908](https://issues.apache.org/jira/browse/HDFS-8908) | TestAppendSnapshotTruncate may fail with IOException: Failed to replace a bad datanode |  Minor | test | Tsz Wo Nicholas Sze | Tsz Wo Nicholas Sze |
| [HDFS-8898](https://issues.apache.org/jira/browse/HDFS-8898) | Create API and command-line argument to get quota and quota usage without detailed content summary |  Major | fs | Joep Rottinghuis | Ming Ma |
| [HDFS-8896](https://issues.apache.org/jira/browse/HDFS-8896) | DataNode object isn't GCed when shutdown, because it has GC root in ShutdownHookManager |  Minor | test | Walter Su | Walter Su |
| [HDFS-8894](https://issues.apache.org/jira/browse/HDFS-8894) | Set SO\_KEEPALIVE on DN server sockets |  Major | datanode | Nathan Roberts | Kanaka Kumar Avvaru |
| [HDFS-8885](https://issues.apache.org/jira/browse/HDFS-8885) | ByteRangeInputStream used in webhdfs does not override available() |  Minor | webhdfs | Shradha Revankar | Shradha Revankar |
| [HDFS-8866](https://issues.apache.org/jira/browse/HDFS-8866) | Typo in docs: Rumtime -\> Runtime |  Trivial | documentation, webhdfs | Jakob Homan | Gabor Liptak |
| [HDFS-8856](https://issues.apache.org/jira/browse/HDFS-8856) | Make LeaseManager#countPath O(1) |  Major | namenode | Arpit Agarwal | Arpit Agarwal |
| [HDFS-8855](https://issues.apache.org/jira/browse/HDFS-8855) | Webhdfs client leaks active NameNode connections |  Major | webhdfs | Bob Hansen | Xiaobing Zhou |
| [HDFS-8847](https://issues.apache.org/jira/browse/HDFS-8847) | change TestHDFSContractAppend to not override testRenameFileBeingAppended method. |  Major | test | zhihai xu | zhihai xu |
| [HDFS-8844](https://issues.apache.org/jira/browse/HDFS-8844) | TestHDFSCLI does not cleanup the test directory |  Minor | test | Akira AJISAKA | Masatake Iwasaki |
| [HDFS-8810](https://issues.apache.org/jira/browse/HDFS-8810) | Correct assertions in TestDFSInotifyEventInputStream class. |  Minor | test | Surendra Singh Lilhore | Surendra Singh Lilhore |
| [HDFS-8809](https://issues.apache.org/jira/browse/HDFS-8809) | HDFS fsck reports under construction blocks as "CORRUPT" |  Major | tools | Sudhir Prakash | Jing Zhao |
| [HDFS-8807](https://issues.apache.org/jira/browse/HDFS-8807) | dfs.datanode.data.dir does not handle spaces between storageType and URI correctly |  Major | datanode | Anu Engineer | Anu Engineer |
| [HDFS-8797](https://issues.apache.org/jira/browse/HDFS-8797) | WebHdfsFileSystem creates too many connections for pread |  Major | webhdfs | Jing Zhao | Jing Zhao |
| [HDFS-8785](https://issues.apache.org/jira/browse/HDFS-8785) | TestDistributedFileSystem is failing in trunk |  Major | test | Arpit Agarwal | Xiaoyu Yao |
| [HDFS-8780](https://issues.apache.org/jira/browse/HDFS-8780) | Fetching live/dead datanode list with arg true for removeDecommissionNode,returns list with decom node. |  Major | . | J.Andreina | J.Andreina |
| [HDFS-8779](https://issues.apache.org/jira/browse/HDFS-8779) | WebUI fails to display block IDs that are larger than 2^53 - 1 |  Minor | webhdfs | Walter Su | Haohui Mai |
| [HDFS-8778](https://issues.apache.org/jira/browse/HDFS-8778) | TestBlockReportRateLimiting#testLeaseExpiration can deadlock |  Major | test | Arpit Agarwal | Arpit Agarwal |
| [HDFS-8773](https://issues.apache.org/jira/browse/HDFS-8773) | Few FSNamesystem metrics are not documented in the Metrics page |  Major | documentation | Rakesh R | Rakesh R |
| [HDFS-8772](https://issues.apache.org/jira/browse/HDFS-8772) | Fix TestStandbyIsHot#testDatanodeRestarts which occasionally fails |  Major | . | Walter Su | Walter Su |
| [HDFS-8751](https://issues.apache.org/jira/browse/HDFS-8751) | Remove setBlocks API from INodeFile and misc code cleanup |  Major | namenode | Zhe Zhang | Zhe Zhang |
| [HDFS-8749](https://issues.apache.org/jira/browse/HDFS-8749) | Fix findbugs warning in BlockManager.java |  Minor | . | Akira AJISAKA | Brahma Reddy Battula |
| [HDFS-8729](https://issues.apache.org/jira/browse/HDFS-8729) | Fix testTruncateWithDataNodesRestartImmediately occasionally failed |  Minor | . | Walter Su | Walter Su |
| [HDFS-8716](https://issues.apache.org/jira/browse/HDFS-8716) | introduce a new config specifically for safe mode block count |  Major | . | Chang Li | Chang Li |
| [HDFS-8706](https://issues.apache.org/jira/browse/HDFS-8706) | Fix typo in datanode startup options in HDFSCommands.html |  Major | . | Brahma Reddy Battula | Brahma Reddy Battula |
| [HDFS-8687](https://issues.apache.org/jira/browse/HDFS-8687) | Remove the duplicate usage message from Dfsck.java |  Major | . | Brahma Reddy Battula | Brahma Reddy Battula |
| [HDFS-8686](https://issues.apache.org/jira/browse/HDFS-8686) | WebHdfsFileSystem#getXAttr(Path p, final String name) doesn't work if namespace is in capitals |  Major | webhdfs | Jagadesh Kiran N | Kanaka Kumar Avvaru |
| [HDFS-8682](https://issues.apache.org/jira/browse/HDFS-8682) | Should not remove decommissioned node,while calculating the number of live/dead decommissioned node. |  Major | . | J.Andreina | J.Andreina |
| [HDFS-8670](https://issues.apache.org/jira/browse/HDFS-8670) | Better to exclude decommissioned nodes for namenode NodeUsage JMX |  Major | . | Ming Ma | J.Andreina |
| [HDFS-8666](https://issues.apache.org/jira/browse/HDFS-8666) | speedup TestMover |  Major | test | Walter Su | Walter Su |
| [HDFS-8665](https://issues.apache.org/jira/browse/HDFS-8665) | Fix replication check in DFSTestUtils#waitForReplication |  Trivial | test | Andrew Wang | Andrew Wang |
| [HDFS-8646](https://issues.apache.org/jira/browse/HDFS-8646) | Prune cached replicas from DatanodeDescriptor state on replica invalidation |  Major | caching | Andrew Wang | Andrew Wang |
| [HDFS-8642](https://issues.apache.org/jira/browse/HDFS-8642) | Make TestFileTruncate more reliable |  Minor | . | Rakesh R | Rakesh R |
| [HDFS-8628](https://issues.apache.org/jira/browse/HDFS-8628) | Update missing command option for fetchdt |  Major | documentation | J.Andreina | J.Andreina |
| [HDFS-8607](https://issues.apache.org/jira/browse/HDFS-8607) | TestFileCorruption doesn't work as expected |  Major | test | Walter Su | Walter Su |
| [HDFS-8593](https://issues.apache.org/jira/browse/HDFS-8593) | Calculation of effective layout version mishandles comparison to current layout version in storage. |  Major | namenode | Chris Nauroth | Chris Nauroth |
| [HDFS-8592](https://issues.apache.org/jira/browse/HDFS-8592) | SafeModeException never get unwrapped |  Major | . | Haohui Mai | Haohui Mai |
| [HDFS-8586](https://issues.apache.org/jira/browse/HDFS-8586) | Dead Datanode is allocated for write when client is  from deadnode |  Critical | . | Brahma Reddy Battula | Brahma Reddy Battula |
| [HDFS-8581](https://issues.apache.org/jira/browse/HDFS-8581) | ContentSummary on / skips further counts on yielding lock |  Minor | namenode | tongshiquan | J.Andreina |
| [HDFS-8579](https://issues.apache.org/jira/browse/HDFS-8579) | Update HDFS usage with missing options |  Minor | . | J.Andreina | J.Andreina |
| [HDFS-8577](https://issues.apache.org/jira/browse/HDFS-8577) | Avoid retrying to recover lease on a file which does not exist |  Major | . | J.Andreina | J.Andreina |
| [HDFS-8568](https://issues.apache.org/jira/browse/HDFS-8568) | TestClusterId#testFormatWithEmptyClusterIdOption is failing |  Major | . | Rakesh R | Rakesh R |
| [HDFS-8565](https://issues.apache.org/jira/browse/HDFS-8565) | Typo in dfshealth.html - "Decomissioning" |  Trivial | . | nijel | nijel |
| [HDFS-8554](https://issues.apache.org/jira/browse/HDFS-8554) | TestDatanodeLayoutUpgrade fails on Windows. |  Major | test | Chris Nauroth | Chris Nauroth |
| [HDFS-8552](https://issues.apache.org/jira/browse/HDFS-8552) | Fix hdfs CLI usage message for namenode and zkfc |  Major | . | Xiaoyu Yao | Brahma Reddy Battula |
| [HDFS-8551](https://issues.apache.org/jira/browse/HDFS-8551) | Fix hdfs datanode CLI usage message |  Major | . | Xiaoyu Yao | Brahma Reddy Battula |
| [HDFS-8548](https://issues.apache.org/jira/browse/HDFS-8548) | Minicluster throws NPE on shutdown |  Major | . | Mike Drob | Surendra Singh Lilhore |
| [HDFS-8542](https://issues.apache.org/jira/browse/HDFS-8542) | WebHDFS getHomeDirectory behavior does not match specification |  Major | webhdfs | Jakob Homan | Kanaka Kumar Avvaru |
| [HDFS-8539](https://issues.apache.org/jira/browse/HDFS-8539) | Hdfs doesnt have class 'debug' in windows |  Major | scripts | Sumana Sathish | Anu Engineer |
| [HDFS-8513](https://issues.apache.org/jira/browse/HDFS-8513) | Rename BlockPlacementPolicyRackFaultTolarent to BlockPlacementPolicyRackFaultTolerant |  Minor | namenode | Andrew Wang | Andrew Wang |
| [HDFS-8470](https://issues.apache.org/jira/browse/HDFS-8470) | fsimage loading progress should update inode, delegation token and cache pool count. |  Minor | namenode | tongshiquan | Surendra Singh Lilhore |
| [HDFS-8463](https://issues.apache.org/jira/browse/HDFS-8463) | Calling DFSInputStream.seekToNewSource just after stream creation causes  NullPointerException |  Minor | . | Masatake Iwasaki | Masatake Iwasaki |
| [HDFS-8446](https://issues.apache.org/jira/browse/HDFS-8446) | Separate safemode related operations in GetBlockLocations() |  Minor | . | Haohui Mai | Haohui Mai |
| [HDFS-8429](https://issues.apache.org/jira/browse/HDFS-8429) | Avoid stuck threads if there is an error in DomainSocketWatcher that stops the thread |  Major | . | zhouyingchao | zhouyingchao |
| [HDFS-8421](https://issues.apache.org/jira/browse/HDFS-8421) | Move startFile() and related operations into FSDirWriteFileOp |  Major | . | Haohui Mai | Haohui Mai |
| [HDFS-8407](https://issues.apache.org/jira/browse/HDFS-8407) | libhdfs hdfsListDirectory must set errno to 0 on success |  Major | native | Juan Yu | Masatake Iwasaki |
| [HDFS-8388](https://issues.apache.org/jira/browse/HDFS-8388) | Time and Date format need to be in sync in NameNode UI page |  Minor | . | Archana T | Surendra Singh Lilhore |
| [HDFS-8386](https://issues.apache.org/jira/browse/HDFS-8386) | Improve synchronization of 'streamer' reference in DFSOutputStream |  Major | hdfs-client | Rakesh R | Rakesh R |
| [HDFS-8380](https://issues.apache.org/jira/browse/HDFS-8380) | Always call addStoredBlock on blocks which have been shifted from one storage to another |  Major | . | Colin Patrick McCabe | Colin Patrick McCabe |
| [HDFS-8371](https://issues.apache.org/jira/browse/HDFS-8371) | Fix test failure in TestHdfsConfigFields for spanreceiver properties |  Major | . | Ray Chiang | Ray Chiang |
| [HDFS-8362](https://issues.apache.org/jira/browse/HDFS-8362) | Java Compilation Error in TestHdfsConfigFields.java |  Major | . | Arshad Mohammad | Arshad Mohammad |
| [HDFS-8358](https://issues.apache.org/jira/browse/HDFS-8358) | TestTraceAdmin fails |  Major | . | Kihwal Lee | Masatake Iwasaki |
| [HDFS-8351](https://issues.apache.org/jira/browse/HDFS-8351) | Remove namenode -finalize option from document |  Major | documentation | Akira AJISAKA | Akira AJISAKA |
| [HDFS-8346](https://issues.apache.org/jira/browse/HDFS-8346) | libwebhdfs build fails during link due to unresolved external symbols. |  Major | native | Chris Nauroth | Chris Nauroth |
| [HDFS-8345](https://issues.apache.org/jira/browse/HDFS-8345) | Storage policy APIs must be exposed via the FileSystem interface |  Major | hdfs-client | Arpit Agarwal | Arpit Agarwal |
| [HDFS-8340](https://issues.apache.org/jira/browse/HDFS-8340) | Fix NFS documentation of nfs.wtmax |  Minor | documentation, nfs | Ajith S | Ajith S |
| [HDFS-8337](https://issues.apache.org/jira/browse/HDFS-8337) | Accessing httpfs via webhdfs doesn't work from a jar with kerberos |  Major | security, webhdfs | Yongjun Zhang | Yongjun Zhang |
| [HDFS-8335](https://issues.apache.org/jira/browse/HDFS-8335) | FSNamesystem should construct FSPermissionChecker only if permission is enabled |  Major | . | David Bryson | Gabor Liptak |
| [HDFS-8326](https://issues.apache.org/jira/browse/HDFS-8326) | Documentation about when checkpoints are run is out of date |  Major | documentation | Misty Stanley-Jones | Misty Stanley-Jones |
| [HDFS-8325](https://issues.apache.org/jira/browse/HDFS-8325) | Misspelling of threshold in log4j.properties for tests |  Minor | test | Brahma Reddy Battula | Brahma Reddy Battula |
| [HDFS-8321](https://issues.apache.org/jira/browse/HDFS-8321) | CacheDirectives and CachePool operations should throw RetriableException in safemode |  Major | . | Haohui Mai | Haohui Mai |
| [HDFS-8311](https://issues.apache.org/jira/browse/HDFS-8311) | DataStreamer.transfer() should timeout the socket InputStream. |  Major | hdfs-client | Esteban Gutierrez | Esteban Gutierrez |
| [HDFS-8300](https://issues.apache.org/jira/browse/HDFS-8300) | Fix unit test failures and findbugs warning caused by HDFS-8283 |  Major | . | Jing Zhao | Jing Zhao |
| [HDFS-8292](https://issues.apache.org/jira/browse/HDFS-8292) | Move conditional in fmt\_time from dfs-dust.js to status.html |  Minor | namenode | Charles Lamb | Charles Lamb |
| [HDFS-8290](https://issues.apache.org/jira/browse/HDFS-8290) | WebHDFS calls before namesystem initialization can cause NullPointerException. |  Minor | webhdfs | Chris Nauroth | Chris Nauroth |
| [HDFS-8276](https://issues.apache.org/jira/browse/HDFS-8276) | LazyPersistFileScrubber should be disabled if scrubber interval configured zero |  Major | namenode | Surendra Singh Lilhore | Surendra Singh Lilhore |
| [HDFS-8274](https://issues.apache.org/jira/browse/HDFS-8274) | NFS configuration nfs.dump.dir not working |  Major | nfs | Ajith S | Ajith S |
| [HDFS-8268](https://issues.apache.org/jira/browse/HDFS-8268) | Port conflict log for data node server is not sufficient |  Minor | datanode | Mohammad Shahid Khan | Mohammad Shahid Khan |
| [HDFS-8257](https://issues.apache.org/jira/browse/HDFS-8257) | Namenode rollingUpgrade option is incorrect in document |  Major | documentation | J.Andreina | J.Andreina |
| [HDFS-8256](https://issues.apache.org/jira/browse/HDFS-8256) | fsck "-storagepolicies , -blockId ,-replicaDetails " options are missed out in usage and from documentation |  Major | documentation | J.Andreina | J.Andreina |
| [HDFS-8232](https://issues.apache.org/jira/browse/HDFS-8232) | Missing datanode counters when using Metrics2 sink interface |  Major | datanode | Anu Engineer | Anu Engineer |
| [HDFS-8231](https://issues.apache.org/jira/browse/HDFS-8231) | StackTrace displayed at client while QuotaByStorageType exceeds |  Major | hdfs-client | J.Andreina | J.Andreina |
| [HDFS-8229](https://issues.apache.org/jira/browse/HDFS-8229) | LAZY\_PERSIST file gets deleted after NameNode restart. |  Major | namenode | Surendra Singh Lilhore | Surendra Singh Lilhore |
| [HDFS-8222](https://issues.apache.org/jira/browse/HDFS-8222) | Remove usage of "dfsadmin -upgradeProgress " from document which  is no longer supported |  Major | documentation | J.Andreina | J.Andreina |
| [HDFS-8217](https://issues.apache.org/jira/browse/HDFS-8217) | During block recovery for truncate Log new Block Id in case of copy-on-truncate is true. |  Major | datanode | Vinayakumar B | Vinayakumar B |
| [HDFS-8214](https://issues.apache.org/jira/browse/HDFS-8214) | Secondary NN Web UI shows wrong date for Last Checkpoint |  Major | namenode | Charles Lamb | Charles Lamb |
| [HDFS-8211](https://issues.apache.org/jira/browse/HDFS-8211) | DataNode UUID is always null in the JMX counter |  Minor | datanode | Anu Engineer | Anu Engineer |
| [HDFS-8206](https://issues.apache.org/jira/browse/HDFS-8206) | Fix the typos in hadoop-hdfs-httpfs |  Major | . | Brahma Reddy Battula | Brahma Reddy Battula |
| [HDFS-8205](https://issues.apache.org/jira/browse/HDFS-8205) | CommandFormat#parse() should not parse option as value of option |  Blocker | . | Peter Shi | Peter Shi |
| [HDFS-8191](https://issues.apache.org/jira/browse/HDFS-8191) | Fix byte to integer casting in SimulatedFSDataset#simulatedByte |  Minor | . | Zhe Zhang | Zhe Zhang |
| [HDFS-8187](https://issues.apache.org/jira/browse/HDFS-8187) | Remove usage of "-setStoragePolicy" and "-getStoragePolicy" using dfsadmin cmd (as it is not been supported) |  Major | documentation | J.Andreina | J.Andreina |
| [HDFS-8175](https://issues.apache.org/jira/browse/HDFS-8175) | Provide information on snapshotDiff for supporting the comparison between snapshot and current status |  Major | documentation | J.Andreina | J.Andreina |
| [HDFS-8174](https://issues.apache.org/jira/browse/HDFS-8174) | Update replication count to live rep count in fsck report |  Minor | . | J.Andreina | J.Andreina |
| [HDFS-8173](https://issues.apache.org/jira/browse/HDFS-8173) | NPE thrown at DataNode shutdown when HTTP server was not able to create |  Minor | datanode | Archana T | Surendra Singh Lilhore |
| [HDFS-8164](https://issues.apache.org/jira/browse/HDFS-8164) | cTime is 0 in VERSION file for newly formatted NameNode. |  Minor | namenode | Chris Nauroth | Xiao Chen |
| [HDFS-8150](https://issues.apache.org/jira/browse/HDFS-8150) | Make getFileChecksum fail for blocks under construction |  Critical | . | Kihwal Lee | J.Andreina |
| [HDFS-8149](https://issues.apache.org/jira/browse/HDFS-8149) | The footer of the Web UI "Hadoop, 2014" is old |  Major | . | Akira AJISAKA | Brahma Reddy Battula |
| [HDFS-8148](https://issues.apache.org/jira/browse/HDFS-8148) |  NPE thrown at Namenode startup,. |  Minor | namenode | Archana T | Surendra Singh Lilhore |
| [HDFS-8142](https://issues.apache.org/jira/browse/HDFS-8142) | DistributedFileSystem encryption zone commands should resolve relative paths |  Major | . | Rakesh R | Rakesh R |
| [HDFS-8113](https://issues.apache.org/jira/browse/HDFS-8113) | Add check for null BlockCollection pointers in BlockInfoContiguous structures |  Major | namenode | Chengbing Liu | Chengbing Liu |
| [HDFS-8111](https://issues.apache.org/jira/browse/HDFS-8111) | NPE thrown when invalid FSImage filename given for "hdfs oiv\_legacy" cmd |  Minor | tools | Archana T | Surendra Singh Lilhore |
| [HDFS-8097](https://issues.apache.org/jira/browse/HDFS-8097) | TestFileTruncate is failing intermittently |  Major | test | Rakesh R | Rakesh R |
| [HDFS-8096](https://issues.apache.org/jira/browse/HDFS-8096) | DatanodeMetrics#blocksReplicated will get incremented early and even for failed transfers |  Major | datanode | Vinayakumar B | Vinayakumar B |
| [HDFS-8067](https://issues.apache.org/jira/browse/HDFS-8067) | haadmin prints out stale help messages |  Minor | hdfs-client | Ajith S | Ajith S |
| [HDFS-8055](https://issues.apache.org/jira/browse/HDFS-8055) | NullPointerException when topology script is missing. |  Major | namenode | Anu Engineer | Anu Engineer |
| [HDFS-8043](https://issues.apache.org/jira/browse/HDFS-8043) | NPE in MiniDFSCluster teardown |  Major | test | Steve Loughran | Brahma Reddy Battula |
| [HDFS-8037](https://issues.apache.org/jira/browse/HDFS-8037) | CheckAccess in WebHDFS silently accepts malformed FsActions parameters |  Minor | webhdfs | Jake Low | Walter Su |
| [HDFS-8026](https://issues.apache.org/jira/browse/HDFS-8026) | Trace FSOutputSummer#writeChecksumChunks rather than DFSOutputStream#writeChunk |  Minor | . | Colin Patrick McCabe | Colin Patrick McCabe |
| [HDFS-8002](https://issues.apache.org/jira/browse/HDFS-8002) | Website refers to /trash directory |  Major | documentation | Mike Drob | Brahma Reddy Battula |
| [HDFS-7998](https://issues.apache.org/jira/browse/HDFS-7998) | HDFS Federation : Command mentioned to add a NN to existing federated cluster is wrong |  Minor | documentation | Ajith S | Ajith S |
| [HDFS-7997](https://issues.apache.org/jira/browse/HDFS-7997) | The first non-existing xattr should also throw IOException |  Minor | . | zhouyingchao | zhouyingchao |
| [HDFS-7993](https://issues.apache.org/jira/browse/HDFS-7993) | Provide each Replica details in fsck |  Major | . | Ming Ma | J.Andreina |
| [HDFS-7990](https://issues.apache.org/jira/browse/HDFS-7990) | IBR delete ack should not be delayed |  Major | namenode | Daryn Sharp | Daryn Sharp |
| [HDFS-7939](https://issues.apache.org/jira/browse/HDFS-7939) | Two fsimage\_rollback\_\* files are created which are not deleted after rollback. |  Critical | . | J.Andreina | J.Andreina |
| [HDFS-7922](https://issues.apache.org/jira/browse/HDFS-7922) | ShortCircuitCache#close is not releasing ScheduledThreadPoolExecutors |  Major | . | Rakesh R | Rakesh R |
| [HDFS-7899](https://issues.apache.org/jira/browse/HDFS-7899) | Improve EOF error message |  Minor | hdfs-client | Harsh J | Jagadesh Kiran N |
| [HDFS-7897](https://issues.apache.org/jira/browse/HDFS-7897) | Shutdown metrics when stopping JournalNode |  Major | . | zhouyingchao | zhouyingchao |
| [HDFS-7867](https://issues.apache.org/jira/browse/HDFS-7867) | Update action param from "start" to "prepare" in rolling upgrade javadoc |  Trivial | . | J.Andreina | J.Andreina |
| [HDFS-7847](https://issues.apache.org/jira/browse/HDFS-7847) | Modify NNThroughputBenchmark to be able to operate on a remote NameNode |  Major | . | Colin Patrick McCabe | Charles Lamb |
| [HDFS-7833](https://issues.apache.org/jira/browse/HDFS-7833) | DataNode reconfiguration does not recalculate valid volumes required, based on configured failed volumes tolerated. |  Major | datanode | Chris Nauroth | Lei (Eddy) Xu |
| [HDFS-7728](https://issues.apache.org/jira/browse/HDFS-7728) | Avoid updating quota usage while loading edits |  Major | . | Jing Zhao | Jing Zhao |
| [HDFS-7608](https://issues.apache.org/jira/browse/HDFS-7608) | hdfs dfsclient  newConnectedPeer has no write timeout |  Major | fuse-dfs, hdfs-client | zhangshilong | Xiaoyu Yao |
| [HDFS-7582](https://issues.apache.org/jira/browse/HDFS-7582) | Enforce maximum number of ACL entries separately per access and default. |  Major | namenode | Vinayakumar B | Vinayakumar B |
| [HDFS-7501](https://issues.apache.org/jira/browse/HDFS-7501) | TransactionsSinceLastCheckpoint can be negative on SBNs |  Major | namenode | Harsh J | Gautam Gopalakrishnan |
| [HDFS-7452](https://issues.apache.org/jira/browse/HDFS-7452) | skip StandbyException log for getCorruptFiles() |  Minor | . | Brahma Reddy Battula | Brahma Reddy Battula |
| [HDFS-7401](https://issues.apache.org/jira/browse/HDFS-7401) | Add block info to DFSInputStream' WARN message when it adds node to deadNodes |  Minor | . | Ming Ma | Arshad Mohammad |
| [HDFS-7261](https://issues.apache.org/jira/browse/HDFS-7261) | storageMap is accessed without synchronization in DatanodeDescriptor#updateHeartbeatState() |  Major | . | Ted Yu | Brahma Reddy Battula |
| [HDFS-6955](https://issues.apache.org/jira/browse/HDFS-6955) | DN should reserve disk space for a full block when creating tmp files |  Major | datanode | Arpit Agarwal | Kanaka Kumar Avvaru |
| [HDFS-6885](https://issues.apache.org/jira/browse/HDFS-6885) | Fix wrong use of BytesWritable in FSEditLogOp#RenameOp |  Minor | namenode | Yi Liu | Yi Liu |
| [HDFS-6860](https://issues.apache.org/jira/browse/HDFS-6860) | BlockStateChange logs are too noisy |  Major | namenode | Arpit Agarwal | Chang Li |
| [HDFS-6832](https://issues.apache.org/jira/browse/HDFS-6832) | Fix the usage of 'hdfs namenode' command |  Minor | . | Akira AJISAKA | Manjunath Ballur |
| [HDFS-6763](https://issues.apache.org/jira/browse/HDFS-6763) | Initialize file system-wide quota once on transitioning to active |  Major | ha, namenode | Daryn Sharp | Kihwal Lee |
| [HDFS-6666](https://issues.apache.org/jira/browse/HDFS-6666) | Abort NameNode and DataNode startup if security is enabled but block access token is not enabled. |  Minor | datanode, namenode, security | Chris Nauroth | Vijay Bhat |
| [HDFS-6576](https://issues.apache.org/jira/browse/HDFS-6576) | Datanode log is generating at root directory in security mode |  Minor | datanode, scripts | Surendra Singh Lilhore | Surendra Singh Lilhore |
| [HDFS-6533](https://issues.apache.org/jira/browse/HDFS-6533) | TestBPOfferService#testBasicFunctionalitytest fails intermittently |  Major | datanode, hdfs-client | Yongjun Zhang | Wei-Chiu Chuang |
| [HDFS-6348](https://issues.apache.org/jira/browse/HDFS-6348) | SecondaryNameNode not terminating properly on runtime exceptions |  Major | namenode | Rakesh R | Rakesh R |
| [HDFS-6291](https://issues.apache.org/jira/browse/HDFS-6291) | FSImage may be left unclosed in BootstrapStandby#doRun() |  Minor | ha | Ted Yu | Sanghyun Yun |
| [HDFS-6101](https://issues.apache.org/jira/browse/HDFS-6101) | TestReplaceDatanodeOnFailure fails occasionally |  Major | test | Arpit Agarwal | Wei-Chiu Chuang |
| [HDFS-5802](https://issues.apache.org/jira/browse/HDFS-5802) | NameNode does not check for inode type before traversing down a path |  Trivial | namenode | Harsh J | Xiao Chen |
| [HDFS-5356](https://issues.apache.org/jira/browse/HDFS-5356) | MiniDFSCluster shoud close all open FileSystems when shutdown() |  Critical | test | haosdent | Rakesh R |
| [HDFS-4448](https://issues.apache.org/jira/browse/HDFS-4448) | Allow HA NN to start in secure mode with wildcard address configured |  Major | ha, namenode, security | Aaron T. Myers | Aaron T. Myers |
| [HDFS-4366](https://issues.apache.org/jira/browse/HDFS-4366) | Block Replication Policy Implementation May Skip Higher-Priority Blocks for Lower-Priority Blocks |  Major | . | Derek Dagit | Derek Dagit |
| [HDFS-3716](https://issues.apache.org/jira/browse/HDFS-3716) | Purger should remove stale fsimage ckpt files |  Minor | namenode | suja s | J.Andreina |
| [HDFS-3384](https://issues.apache.org/jira/browse/HDFS-3384) | DataStreamer thread should be closed immediatly when failed to setup a PipelineForAppendOrRecovery |  Major | hdfs-client | Brahma Reddy Battula | Uma Maheswara Rao G |
| [HDFS-3325](https://issues.apache.org/jira/browse/HDFS-3325) | When configuring "dfs.namenode.safemode.threshold-pct" to a value greater or equal to 1 there is mismatch in the UI report |  Minor | . | J.Andreina | J.Andreina |
| [HDFS-3059](https://issues.apache.org/jira/browse/HDFS-3059) | ssl-server.xml causes NullPointer |  Minor | datanode, security | Evert Lammerts | Xiao Chen |
| [HDFS-2956](https://issues.apache.org/jira/browse/HDFS-2956) | calling fetchdt without a --renewer argument throws NPE |  Major | security | Todd Lipcon | Vinayakumar B |
| [HDFS-2484](https://issues.apache.org/jira/browse/HDFS-2484) | checkLease should throw FileNotFoundException when file does not exist |  Major | namenode | Konstantin Shvachko | Rakesh R |
| [HDFS-2261](https://issues.apache.org/jira/browse/HDFS-2261) | AOP unit tests are not getting compiled or run |  Minor | test | Giridharan Kesavan | Haohui Mai |
| [HDFS-1172](https://issues.apache.org/jira/browse/HDFS-1172) | Blocks in newly completed files are considered under-replicated too quickly |  Major | namenode | Todd Lipcon | Masatake Iwasaki |
| [MAPREDUCE-6635](https://issues.apache.org/jira/browse/MAPREDUCE-6635) | Unsafe long to int conversion in UncompressedSplitLineReader and IndexOutOfBoundsException |  Critical | . | Sergey Shelukhin | Junping Du |
| [MAPREDUCE-6619](https://issues.apache.org/jira/browse/MAPREDUCE-6619) | HADOOP\_CLASSPATH is overwritten in MR container |  Major | mrv2 | shanyu zhao | Junping Du |
| [MAPREDUCE-6616](https://issues.apache.org/jira/browse/MAPREDUCE-6616) | Fail to create jobhistory file if there are some multibyte characters in the job name |  Major | jobhistoryserver | Akira AJISAKA | Kousuke Saruta |
| [MAPREDUCE-6610](https://issues.apache.org/jira/browse/MAPREDUCE-6610) | JobHistoryEventHandler should not swallow timeline response |  Trivial | . | Li Lu | Li Lu |
| [MAPREDUCE-6605](https://issues.apache.org/jira/browse/MAPREDUCE-6605) | Fix typos mapreduce.map.skip.proc.count.autoincr and mapreduce.reduce.skip.proc.count.autoincr in mapred-default.xml |  Major | documentation | Dong Zhen | Kai Sasaki |
| [MAPREDUCE-6601](https://issues.apache.org/jira/browse/MAPREDUCE-6601) | Fix typo in Job#setUseNewAPI |  Trivial | . | Kai Sasaki | Kai Sasaki |
| [MAPREDUCE-6595](https://issues.apache.org/jira/browse/MAPREDUCE-6595) | Fix findbugs warnings in OutputCommitter and FileOutputCommitter |  Major | . | Akira AJISAKA | Akira AJISAKA |
| [MAPREDUCE-6593](https://issues.apache.org/jira/browse/MAPREDUCE-6593) | TestJobHistoryEventHandler.testTimelineEventHandling fails on trunk because of NPE |  Major | . | Tsuyoshi Ozawa | Naganarasimha G R |
| [MAPREDUCE-6589](https://issues.apache.org/jira/browse/MAPREDUCE-6589) | TestTaskLog outputs a log under directory other than target/test-dir |  Major | test | Akira AJISAKA | Akira AJISAKA |
| [MAPREDUCE-6583](https://issues.apache.org/jira/browse/MAPREDUCE-6583) | Clarify confusing sentence in MapReduce tutorial document |  Minor | documentation | chris snow | Kai Sasaki |
| [MAPREDUCE-6577](https://issues.apache.org/jira/browse/MAPREDUCE-6577) | MR AM unable to load native library without MR\_AM\_ADMIN\_USER\_ENV set |  Critical | mr-am | Sangjin Lee | Sangjin Lee |
| [MAPREDUCE-6574](https://issues.apache.org/jira/browse/MAPREDUCE-6574) | MR AM should print host of failed tasks. |  Major | . | Wangda Tan | Mohammad Shahid Khan |
| [MAPREDUCE-6563](https://issues.apache.org/jira/browse/MAPREDUCE-6563) | Streaming documentation contains a stray '%' character. |  Trivial | documentation | Chris Nauroth | Chris Nauroth |
| [MAPREDUCE-6557](https://issues.apache.org/jira/browse/MAPREDUCE-6557) | Some tests in mapreduce-client-app are writing outside of target |  Blocker | build | Allen Wittenauer | Akira AJISAKA |
| [MAPREDUCE-6553](https://issues.apache.org/jira/browse/MAPREDUCE-6553) | Replace '\u2b05' with '\<-' in rendering job configuration |  Minor | jobhistoryserver | Akira AJISAKA | Gabor Liptak |
| [MAPREDUCE-6550](https://issues.apache.org/jira/browse/MAPREDUCE-6550) | archive-logs tool changes log ownership to the Yarn user when using DefaultContainerExecutor |  Major | . | Robert Kanter | Robert Kanter |
| [MAPREDUCE-6533](https://issues.apache.org/jira/browse/MAPREDUCE-6533) | testDetermineCacheVisibilities of TestClientDistributedCacheManager is broken |  Major | . | Chang Li | Chang Li |
| [MAPREDUCE-6515](https://issues.apache.org/jira/browse/MAPREDUCE-6515) | Update Application priority in AM side from AM-RM heartbeat |  Major | applicationmaster | Sunil G | Sunil G |
| [MAPREDUCE-6508](https://issues.apache.org/jira/browse/MAPREDUCE-6508) | TestNetworkedJob fails consistently due to delegation token changes on RM. |  Major | test | Rohith Sharma K S | Akira AJISAKA |
| [MAPREDUCE-6503](https://issues.apache.org/jira/browse/MAPREDUCE-6503) | archive-logs tool should use HADOOP\_PREFIX instead of HADOOP\_HOME |  Major | . | Robert Kanter | Robert Kanter |
| [MAPREDUCE-6495](https://issues.apache.org/jira/browse/MAPREDUCE-6495) | Docs for archive-logs tool |  Major | documentation | Robert Kanter | Robert Kanter |
| [MAPREDUCE-6494](https://issues.apache.org/jira/browse/MAPREDUCE-6494) | Permission issue when running archive-logs tool as different users |  Major | . | Robert Kanter | Robert Kanter |
| [MAPREDUCE-6485](https://issues.apache.org/jira/browse/MAPREDUCE-6485) | MR job hanged forever because all resources are taken up by reducers and the last map attempt never get resource to run |  Critical | applicationmaster | Bob | Xianyin Xin |
| [MAPREDUCE-6484](https://issues.apache.org/jira/browse/MAPREDUCE-6484) | Yarn Client uses local address instead of RM address as token renewer in a secure cluster when RM HA is enabled. |  Major | client, security | zhihai xu | zhihai xu |
| [MAPREDUCE-6480](https://issues.apache.org/jira/browse/MAPREDUCE-6480) | archive-logs tool may miss applications |  Major | . | Robert Kanter | Robert Kanter |
| [MAPREDUCE-6460](https://issues.apache.org/jira/browse/MAPREDUCE-6460) | TestRMContainerAllocator.testAttemptNotFoundCausesRMCommunicatorException fails |  Major | test | zhihai xu | zhihai xu |
| [MAPREDUCE-6452](https://issues.apache.org/jira/browse/MAPREDUCE-6452) | NPE when intermediate encrypt enabled for LocalRunner |  Major | . | Bibin A Chundatt | zhihai xu |
| [MAPREDUCE-6433](https://issues.apache.org/jira/browse/MAPREDUCE-6433) | launchTime may be negative |  Major | jobhistoryserver, mrv2 | Allen Wittenauer | zhihai xu |
| [MAPREDUCE-6421](https://issues.apache.org/jira/browse/MAPREDUCE-6421) | Fix findbugs warning in RMContainerAllocator.reduceNodeLabelExpression |  Major | . | Ray Chiang | Brahma Reddy Battula |
| [MAPREDUCE-6420](https://issues.apache.org/jira/browse/MAPREDUCE-6420) | Interrupted Exception in LocalContainerLauncher should be logged in warn/info level |  Major | . | Chang Li | Chang Li |
| [MAPREDUCE-6419](https://issues.apache.org/jira/browse/MAPREDUCE-6419) | JobHistoryServer doesn't sort properly based on Job ID when Job id's exceed 9999 |  Major | webapps | Devaraj K | Mohammad Shahid Khan |
| [MAPREDUCE-6418](https://issues.apache.org/jira/browse/MAPREDUCE-6418) | MRApp should not shutdown LogManager during shutdown |  Major | test | Chang Li | Chang Li |
| [MAPREDUCE-6413](https://issues.apache.org/jira/browse/MAPREDUCE-6413) | TestLocalJobSubmission is failing with unknown host |  Major | test | Jason Lowe | zhihai xu |
| [MAPREDUCE-6405](https://issues.apache.org/jira/browse/MAPREDUCE-6405) | NullPointerException in App Attempts page |  Major | . | Siqi Li | Siqi Li |
| [MAPREDUCE-6403](https://issues.apache.org/jira/browse/MAPREDUCE-6403) | Fix typo in the usage of NNBench |  Trivial | documentation | Akira AJISAKA | Jagadesh Kiran N |
| [MAPREDUCE-6400](https://issues.apache.org/jira/browse/MAPREDUCE-6400) | Multiple shuffle transfer fails because input is closed too early |  Blocker | task | Akira AJISAKA | Brahma Reddy Battula |
| [MAPREDUCE-6389](https://issues.apache.org/jira/browse/MAPREDUCE-6389) | Fix BaileyBorweinPlouffe CLI usage message |  Trivial | . | Brahma Reddy Battula | Brahma Reddy Battula |
| [MAPREDUCE-6382](https://issues.apache.org/jira/browse/MAPREDUCE-6382) | Don't escape HTML links in Diagnostics in JHS job overview |  Major | . | Siqi Li | Siqi Li |
| [MAPREDUCE-6374](https://issues.apache.org/jira/browse/MAPREDUCE-6374) | Distributed Cache File visibility should check permission of full path |  Major | . | Chang Li | Chang Li |
| [MAPREDUCE-6373](https://issues.apache.org/jira/browse/MAPREDUCE-6373) | The logger reports total input paths but it is referring to input files |  Trivial | . | Andi Chirita Amdocs | Bibin A Chundatt |
| [MAPREDUCE-6366](https://issues.apache.org/jira/browse/MAPREDUCE-6366) | mapreduce.terasort.final.sync configuration in TeraSort  doesn't work |  Trivial | examples | Takuya Fukudome | Takuya Fukudome |
| [MAPREDUCE-6363](https://issues.apache.org/jira/browse/MAPREDUCE-6363) | [NNBench] Lease mismatch error when running with multiple mappers |  Critical | benchmarks | Brahma Reddy Battula | Bibin A Chundatt |
| [MAPREDUCE-6360](https://issues.apache.org/jira/browse/MAPREDUCE-6360) | TestMapreduceConfigFields is placed in wrong dir, introducing compile error |  Major | . | Vinayakumar B | Arshad Mohammad |
| [MAPREDUCE-6359](https://issues.apache.org/jira/browse/MAPREDUCE-6359) | RM HA setup, "Cluster" tab links populated with AM hostname instead of RM |  Minor | . | Aroop Maliakkal | zhaoyunjiong |
| [MAPREDUCE-6357](https://issues.apache.org/jira/browse/MAPREDUCE-6357) | MultipleOutputs.write() API should document that output committing is not utilized when input path is absolute |  Major | documentation | Ivan Mitic | Dustin Cote |
| [MAPREDUCE-6356](https://issues.apache.org/jira/browse/MAPREDUCE-6356) | Misspelling of threshold in log4j.properties for tests |  Minor | test | Brahma Reddy Battula | Brahma Reddy Battula |
| [MAPREDUCE-6353](https://issues.apache.org/jira/browse/MAPREDUCE-6353) | Divide by zero error in MR AM when calculating available containers |  Major | mr-am | Anubhav Dhoot | Anubhav Dhoot |
| [MAPREDUCE-6350](https://issues.apache.org/jira/browse/MAPREDUCE-6350) | JobHistory doesn't support fully-functional search |  Critical | jobhistoryserver | Siqi Li | Siqi Li |
| [MAPREDUCE-6349](https://issues.apache.org/jira/browse/MAPREDUCE-6349) | Fix typo in property org.apache.hadoop.mapreduce.lib.chain.Chain.REDUCER\_INPUT\_VALUE\_CLASS |  Minor | . | Ray Chiang | Ray Chiang |
| [MAPREDUCE-6345](https://issues.apache.org/jira/browse/MAPREDUCE-6345) | Documentation fix for when CRLA is enabled for MRAppMaster logs |  Trivial | documentation | Rohit Agarwal | Rohit Agarwal |
| [MAPREDUCE-6342](https://issues.apache.org/jira/browse/MAPREDUCE-6342) | Make POM project names consistent |  Minor | build | Rohith Sharma K S | Rohith Sharma K S |
| [MAPREDUCE-6341](https://issues.apache.org/jira/browse/MAPREDUCE-6341) | Fix typo in mapreduce tutorial |  Trivial | . | John Michael Luy | John Michael Luy |
| [MAPREDUCE-6333](https://issues.apache.org/jira/browse/MAPREDUCE-6333) | TestEvents,TestAMWebServicesTasks,TestAppController are broken due to MAPREDUCE-6297 |  Major | . | Siqi Li | Siqi Li |
| [MAPREDUCE-6330](https://issues.apache.org/jira/browse/MAPREDUCE-6330) | Fix typo in Task Attempt API's URL in documentations |  Minor | documentation | Ryu Kobayashi | Ryu Kobayashi |
| [MAPREDUCE-6314](https://issues.apache.org/jira/browse/MAPREDUCE-6314) | TestPipeApplication fails on trunk |  Major | test | Varun Vasudev | Varun Vasudev |
| [MAPREDUCE-6302](https://issues.apache.org/jira/browse/MAPREDUCE-6302) | Preempt reducers after a configurable timeout irrespective of headroom |  Critical | . | mai shurong | Karthik Kambatla |
| [MAPREDUCE-6300](https://issues.apache.org/jira/browse/MAPREDUCE-6300) | Task list sort by task id broken |  Minor | . | Siqi Li | Siqi Li |
| [MAPREDUCE-6294](https://issues.apache.org/jira/browse/MAPREDUCE-6294) | Remove an extra parameter described in Javadoc of TockenCache |  Trivial | . | Chen He | Brahma Reddy Battula |
| [MAPREDUCE-6293](https://issues.apache.org/jira/browse/MAPREDUCE-6293) | Set job classloader on uber-job's LocalContainerLauncher event thread |  Major | mr-am | Sangjin Lee | Sangjin Lee |
| [MAPREDUCE-6286](https://issues.apache.org/jira/browse/MAPREDUCE-6286) | A typo in HistoryViewer makes some code useless, which causes counter limits are not reset correctly. |  Major | client | zhihai xu | zhihai xu |
| [MAPREDUCE-6281](https://issues.apache.org/jira/browse/MAPREDUCE-6281) | Fix javadoc in Terasort |  Trivial | . | Albert Chu | Albert Chu |
| [MAPREDUCE-6266](https://issues.apache.org/jira/browse/MAPREDUCE-6266) | Job#getTrackingURL should consistently return a proper URL |  Minor | . | Ray Chiang | Ray Chiang |
| [MAPREDUCE-6252](https://issues.apache.org/jira/browse/MAPREDUCE-6252) | JobHistoryServer should not fail when encountering a missing directory |  Major | jobhistoryserver | Craig Welch | Craig Welch |
| [MAPREDUCE-6242](https://issues.apache.org/jira/browse/MAPREDUCE-6242) | Progress report log is incredibly excessive in application master |  Major | applicationmaster | Jian Fang | Varun Saxena |
| [MAPREDUCE-6213](https://issues.apache.org/jira/browse/MAPREDUCE-6213) | NullPointerException caused by job history server addr not resolvable |  Minor | applicationmaster | Peng Zhang | Peng Zhang |
| [MAPREDUCE-6199](https://issues.apache.org/jira/browse/MAPREDUCE-6199) | AbstractCounters are not reset completely on deserialization |  Major | . | Anubhav Dhoot | Anubhav Dhoot |
| [MAPREDUCE-6165](https://issues.apache.org/jira/browse/MAPREDUCE-6165) | [JDK8] TestCombineFileInputFormat failed on JDK8 |  Minor | . | Wei Yan | Akira AJISAKA |
| [MAPREDUCE-6121](https://issues.apache.org/jira/browse/MAPREDUCE-6121) | JobResourceUpdater#compareFs() doesn't handle HA namespaces |  Major | mrv2 | Thomas Graves | Ray Chiang |
| [MAPREDUCE-6068](https://issues.apache.org/jira/browse/MAPREDUCE-6068) | Illegal progress value warnings in map tasks |  Major | mrv2, task | Todd Lipcon | Binglin Chang |
| [MAPREDUCE-6038](https://issues.apache.org/jira/browse/MAPREDUCE-6038) | A boolean may be set error in the Word Count v2.0 in MapReduce Tutorial |  Minor | . | Pei Ma | Tsuyoshi Ozawa |
| [MAPREDUCE-5965](https://issues.apache.org/jira/browse/MAPREDUCE-5965) | Hadoop streaming throws error if list of input files is high. Error is: "error=7, Argument list too long at if number of input file is high" |  Major | . | Arup Malakar | Wilfred Spiegelenburg |
| [MAPREDUCE-5905](https://issues.apache.org/jira/browse/MAPREDUCE-5905) | CountersStrings.toEscapedCompactStrings outputs unnecessary "null" strings |  Minor | . | Akira AJISAKA | Akira AJISAKA |
| [MAPREDUCE-5875](https://issues.apache.org/jira/browse/MAPREDUCE-5875) | Make Counter limits consistent across JobClient, MRAppMaster, and YarnChild |  Major | applicationmaster, client, task | Gera Shegalov | Gera Shegalov |
| [MAPREDUCE-5817](https://issues.apache.org/jira/browse/MAPREDUCE-5817) | Mappers get rescheduled on node transition even after all reducers are completed |  Major | applicationmaster | Sangjin Lee | Sangjin Lee |
| [MAPREDUCE-5807](https://issues.apache.org/jira/browse/MAPREDUCE-5807) | Print usage for TeraSort job. |  Trivial | examples | Rohith Sharma K S | Rohith Sharma K S |
| [MAPREDUCE-5763](https://issues.apache.org/jira/browse/MAPREDUCE-5763) | Warn message about httpshuffle in NM logs |  Major | . | Sandy Ryza | Akira AJISAKA |
| [MAPREDUCE-5708](https://issues.apache.org/jira/browse/MAPREDUCE-5708) | Duplicate String.format in YarnOutputFiles.getSpillFileForWrite |  Minor | . | Konstantin Weitz | Konstantin Weitz |
| [MAPREDUCE-5448](https://issues.apache.org/jira/browse/MAPREDUCE-5448) | MapFileOutputFormat#getReaders bug with invisible files/folders |  Minor | mrv2 | Maysam Yabandeh | Maysam Yabandeh |
| [MAPREDUCE-5002](https://issues.apache.org/jira/browse/MAPREDUCE-5002) | AM could potentially allocate a reduce container to a map attempt |  Major | mr-am | Jason Lowe | Chang Li |
| [MAPREDUCE-4844](https://issues.apache.org/jira/browse/MAPREDUCE-4844) | Counters / AbstractCounters have constant references not declared final |  Major | . | Gera Shegalov | Brahma Reddy Battula |
| [MAPREDUCE-3383](https://issues.apache.org/jira/browse/MAPREDUCE-3383) | Duplicate job.getOutputValueGroupingComparator() in ReduceTask |  Major | . | Binglin Chang | Binglin Chang |
| [MAPREDUCE-2094](https://issues.apache.org/jira/browse/MAPREDUCE-2094) | LineRecordReader should not seek into non-splittable, compressed streams. |  Major | task | Niels Basjes | Niels Basjes |
| [YARN-4748](https://issues.apache.org/jira/browse/YARN-4748) | ApplicationHistoryManagerOnTimelineStore should not swallow exceptions on generateApplicationReport |  Major | timelineserver | Li Lu | Li Lu |
| [YARN-4722](https://issues.apache.org/jira/browse/YARN-4722) | AsyncDispatcher logs redundant event queue sizes |  Major | . | Jason Lowe | Jason Lowe |
| [YARN-4709](https://issues.apache.org/jira/browse/YARN-4709) | NMWebServices produces incorrect JSON for containers |  Critical | . | Varun Saxena | Varun Saxena |
| [YARN-4707](https://issues.apache.org/jira/browse/YARN-4707) | Remove the extra char (\>) from SecureContainer.md |  Major | documentation | Brahma Reddy Battula | Brahma Reddy Battula |
| [YARN-4667](https://issues.apache.org/jira/browse/YARN-4667) | RM Admin CLI for refreshNodesResources throws NPE when nothing is configured |  Major | client | Naganarasimha G R | Naganarasimha G R |
| [YARN-4654](https://issues.apache.org/jira/browse/YARN-4654) | Yarn node label CLI should parse "=" correctly when trying to remove all labels on a node |  Major | . | Wangda Tan | Naganarasimha G R |
| [YARN-4617](https://issues.apache.org/jira/browse/YARN-4617) | LeafQueue#pendingOrderingPolicy should always use fixed ordering policy instead of using same as active applications ordering policy |  Major | capacity scheduler | Rohith Sharma K S | Rohith Sharma K S |
| [YARN-4608](https://issues.apache.org/jira/browse/YARN-4608) | Redundant code statement in WritingYarnApplications |  Minor | documentation | Kai Sasaki | Kai Sasaki |
| [YARN-4605](https://issues.apache.org/jira/browse/YARN-4605) | Spelling mistake in the help message of "yarn applicationattempt" command |  Trivial | client, yarn | Manjunath Ballur | Weiwei Yang |
| [YARN-4596](https://issues.apache.org/jira/browse/YARN-4596) | SystemMetricPublisher should not swallow error messages from TimelineClient#putEntities |  Major | timelineserver | Li Lu | Li Lu |
| [YARN-4592](https://issues.apache.org/jira/browse/YARN-4592) | Remove unused GetContainerStatus proto |  Minor | . | Chang Li | Chang Li |
| [YARN-4581](https://issues.apache.org/jira/browse/YARN-4581) | AHS writer thread leak makes RM crash while RM is recovering |  Major | resourcemanager | sandflee | sandflee |
| [YARN-4565](https://issues.apache.org/jira/browse/YARN-4565) | When sizeBasedWeight enabled for FairOrderingPolicy in CapacityScheduler, Sometimes lead to situation where all queue resources consumed by AMs only |  Major | capacity scheduler, capacityscheduler | Karam Singh | Wangda Tan |
| [YARN-4546](https://issues.apache.org/jira/browse/YARN-4546) | ResourceManager crash due to scheduling opportunity overflow |  Critical | resourcemanager | Jason Lowe | Jason Lowe |
| [YARN-4538](https://issues.apache.org/jira/browse/YARN-4538) | QueueMetrics pending  cores and memory metrics wrong |  Major | . | Bibin A Chundatt | Bibin A Chundatt |
| [YARN-4534](https://issues.apache.org/jira/browse/YARN-4534) | Remove the redundant symbol in yarn rmadmin help msg |  Trivial | . | Lin Yiqun | Lin Yiqun |
| [YARN-4524](https://issues.apache.org/jira/browse/YARN-4524) | Cleanup AppSchedulingInfo |  Major | scheduler | Karthik Kambatla | Karthik Kambatla |
| [YARN-4520](https://issues.apache.org/jira/browse/YARN-4520) | FinishAppEvent is leaked in leveldb if no app's container running on this node |  Major | nodemanager | sandflee | sandflee |
| [YARN-4519](https://issues.apache.org/jira/browse/YARN-4519) | potential deadlock of CapacityScheduler between decrease container and assign containers |  Major | capacityscheduler | sandflee | MENG DING |
| [YARN-4510](https://issues.apache.org/jira/browse/YARN-4510) | Fix SLS startup failure caused by NPE |  Critical | . | Bibin A Chundatt | Bibin A Chundatt |
| [YARN-4502](https://issues.apache.org/jira/browse/YARN-4502) | Fix two AM containers get allocated when AM restart |  Critical | . | Yesha Vora | Vinod Kumar Vavilapalli |
| [YARN-4477](https://issues.apache.org/jira/browse/YARN-4477) | FairScheduler: Handle condition which can result in an infinite loop in attemptScheduling. |  Major | fairscheduler | Tao Jie | Tao Jie |
| [YARN-4461](https://issues.apache.org/jira/browse/YARN-4461) | Redundant nodeLocalityDelay log in LeafQueue |  Trivial | capacityscheduler | Jason Lowe | Eric Payne |
| [YARN-4454](https://issues.apache.org/jira/browse/YARN-4454) | NM to nodelabel mapping going wrong after RM restart |  Critical | . | Bibin A Chundatt | Bibin A Chundatt |
| [YARN-4452](https://issues.apache.org/jira/browse/YARN-4452) | NPE when submit Unmanaged application |  Critical | . | Naganarasimha G R | Naganarasimha G R |
| [YARN-4440](https://issues.apache.org/jira/browse/YARN-4440) | FSAppAttempt#getAllowedLocalityLevelByTime should init the lastScheduler time |  Major | fairscheduler | Lin Yiqun | Lin Yiqun |
| [YARN-4431](https://issues.apache.org/jira/browse/YARN-4431) | Not necessary to do unRegisterNM() if NM get stop due to failed to connect to RM |  Major | nodemanager | Junping Du | Junping Du |
| [YARN-4422](https://issues.apache.org/jira/browse/YARN-4422) | Generic AHS sometimes doesn't show started, node, or logs on App page |  Major | . | Eric Payne | Eric Payne |
| [YARN-4421](https://issues.apache.org/jira/browse/YARN-4421) | Remove dead code in RmAppImpl.RMAppRecoveredTransition |  Trivial | resourcemanager | Daniel Templeton | Daniel Templeton |
| [YARN-4418](https://issues.apache.org/jira/browse/YARN-4418) | AM Resource Limit per partition can be updated to ResourceUsage as well |  Major | resourcemanager | Sunil G | Sunil G |
| [YARN-4411](https://issues.apache.org/jira/browse/YARN-4411) | RMAppAttemptImpl#createApplicationAttemptReport throws IllegalArgumentException |  Major | resourcemanager | yarntime | Bibin A Chundatt |
| [YARN-4408](https://issues.apache.org/jira/browse/YARN-4408) | NodeManager still reports negative running containers |  Major | nodemanager | Robert Kanter | Robert Kanter |
| [YARN-4403](https://issues.apache.org/jira/browse/YARN-4403) | (AM/NM/Container)LivelinessMonitor should use monotonic time when calculating period |  Critical | . | Junping Du | Junping Du |
| [YARN-4402](https://issues.apache.org/jira/browse/YARN-4402) | TestNodeManagerShutdown And TestNodeManagerResync fails with bind exception |  Major | test | Brahma Reddy Battula | Brahma Reddy Battula |
| [YARN-4392](https://issues.apache.org/jira/browse/YARN-4392) | ApplicationCreatedEvent event time resets after RM restart/failover |  Critical | . | Xuan Gong | Naganarasimha G R |
| [YARN-4389](https://issues.apache.org/jira/browse/YARN-4389) | "yarn.am.blacklisting.enabled" and "yarn.am.blacklisting.disable-failure-threshold" should be app specific rather than a setting for whole YARN cluster |  Critical | applications | Junping Du | Sunil G |
| [YARN-4387](https://issues.apache.org/jira/browse/YARN-4387) | Fix typo in FairScheduler log message |  Minor | fairscheduler | Xin Wang | Xin Wang |
| [YARN-4386](https://issues.apache.org/jira/browse/YARN-4386) | refreshNodesGracefully() should send recommission event to active RMNodes only |  Minor | graceful | Kuhu Shukla | Kuhu Shukla |
| [YARN-4367](https://issues.apache.org/jira/browse/YARN-4367) | SLS webapp doesn't load |  Major | scheduler-load-simulator | Karthik Kambatla | Karthik Kambatla |
| [YARN-4315](https://issues.apache.org/jira/browse/YARN-4315) | NaN in Queue percentage for cluster apps page |  Minor | . | Bibin A Chundatt | Bibin A Chundatt |
| [YARN-4302](https://issues.apache.org/jira/browse/YARN-4302) | SLS not able start due to NPE in SchedulerApplicationAttempt#getResourceUsageReport |  Major | . | Bibin A Chundatt | Bibin A Chundatt |
| [YARN-4300](https://issues.apache.org/jira/browse/YARN-4300) | [JDK8] Fix javadoc errors caused by wrong tags |  Blocker | build, documentation | Akira AJISAKA | Akira AJISAKA |
| [YARN-4298](https://issues.apache.org/jira/browse/YARN-4298) | Fix findbugs warnings in hadoop-yarn-common |  Minor | . | Varun Saxena | Sunil G |
| [YARN-4296](https://issues.apache.org/jira/browse/YARN-4296) | DistributedShell Log.info is not friendly |  Major | applications/distributed-shell | Xiaowei Wang | Xiaowei Wang |
| [YARN-4294](https://issues.apache.org/jira/browse/YARN-4294) | [JDK8] Fix javadoc errors caused by wrong reference and illegal tag |  Blocker | build, documentation | Akira AJISAKA | Akira AJISAKA |
| [YARN-4289](https://issues.apache.org/jira/browse/YARN-4289) | TestDistributedShell failing with bind exception |  Major | test | Brahma Reddy Battula | Brahma Reddy Battula |
| [YARN-4288](https://issues.apache.org/jira/browse/YARN-4288) | NodeManager restart should keep retrying to register to RM while connection exception happens during RM failed over. |  Critical | nodemanager | Junping Du | Junping Du |
| [YARN-4284](https://issues.apache.org/jira/browse/YARN-4284) | condition for AM blacklisting is too narrow |  Major | resourcemanager | Sangjin Lee | Sangjin Lee |
| [YARN-4270](https://issues.apache.org/jira/browse/YARN-4270) | Limit application resource reservation on nodes for non-node/rack specific requests |  Major | fairscheduler | Arun Suresh | Arun Suresh |
| [YARN-4256](https://issues.apache.org/jira/browse/YARN-4256) | YARN fair scheduler vcores with decimal values |  Minor | fairscheduler | Prabhu Joseph | Jun Gong |
| [YARN-4251](https://issues.apache.org/jira/browse/YARN-4251) | TestAMRMClientOnRMRestart#testAMRMClientOnAMRMTokenRollOverOnRMRestart is failing |  Major | test | Brahma Reddy Battula | Brahma Reddy Battula |
| [YARN-4250](https://issues.apache.org/jira/browse/YARN-4250) | NPE in AppSchedulingInfo#isRequestLabelChanged |  Major | resourcemanager, scheduler | Brahma Reddy Battula | Brahma Reddy Battula |
| [YARN-4246](https://issues.apache.org/jira/browse/YARN-4246) | NPE while listing app attempt |  Major | . | Varun Saxena | nijel |
| [YARN-4235](https://issues.apache.org/jira/browse/YARN-4235) | FairScheduler PrimaryGroup does not handle empty groups returned for a user |  Major | fairscheduler | Anubhav Dhoot | Anubhav Dhoot |
| [YARN-4225](https://issues.apache.org/jira/browse/YARN-4225) | Add preemption status to yarn queue -status for capacity scheduler |  Minor | capacity scheduler, yarn | Eric Payne | Eric Payne |
| [YARN-4223](https://issues.apache.org/jira/browse/YARN-4223) | Findbugs warnings in hadoop-yarn-server-nodemanager project |  Minor | nodemanager | Varun Saxena | Varun Saxena |
| [YARN-4204](https://issues.apache.org/jira/browse/YARN-4204) | ConcurrentModificationException in FairSchedulerQueueInfo |  Major | . | Anubhav Dhoot | Anubhav Dhoot |
| [YARN-4201](https://issues.apache.org/jira/browse/YARN-4201) | AMBlacklist does not work for minicluster |  Major | resourcemanager | Jun Gong | Jun Gong |
| [YARN-4188](https://issues.apache.org/jira/browse/YARN-4188) | MoveApplicationAcrossQueuesResponse should be an abstract class |  Minor | resourcemanager | Giovanni Matteo Fumarola | Giovanni Matteo Fumarola |
| [YARN-4176](https://issues.apache.org/jira/browse/YARN-4176) | Resync NM nodelabels with RM periodically for distributed nodelabels |  Major | . | Bibin A Chundatt | Bibin A Chundatt |
| [YARN-4169](https://issues.apache.org/jira/browse/YARN-4169) | Fix racing condition of TestNodeStatusUpdaterForLabels |  Critical | test | Steve Loughran | Naganarasimha G R |
| [YARN-4167](https://issues.apache.org/jira/browse/YARN-4167) | NPE on RMActiveServices#serviceStop when store is null |  Minor | . | Bibin A Chundatt | Bibin A Chundatt |
| [YARN-4155](https://issues.apache.org/jira/browse/YARN-4155) | TestLogAggregationService.testLogAggregationServiceWithInterval failing |  Critical | test | Steve Loughran | Bibin A Chundatt |
| [YARN-4152](https://issues.apache.org/jira/browse/YARN-4152) | NM crash with NPE when LogAggregationService#stopContainer called for absent container |  Critical | log-aggregation, nodemanager | Bibin A Chundatt | Bibin A Chundatt |
| [YARN-4151](https://issues.apache.org/jira/browse/YARN-4151) | Fix findbugs errors in hadoop-yarn-server-common module |  Major | . | MENG DING | MENG DING |
| [YARN-4130](https://issues.apache.org/jira/browse/YARN-4130) | Duplicate declaration of ApplicationId in RMAppManager#submitApplication method |  Trivial | resourcemanager | Kai Sasaki | Kai Sasaki |
| [YARN-4126](https://issues.apache.org/jira/browse/YARN-4126) | RM should not issue delegation tokens in unsecure mode |  Major | . | Jian He | Bibin A Chundatt |
| [YARN-4121](https://issues.apache.org/jira/browse/YARN-4121) | Typos in capacity scheduler documentation. |  Trivial | documentation | Kai Sasaki | Kai Sasaki |
| [YARN-4115](https://issues.apache.org/jira/browse/YARN-4115) | Reduce loglevel of ContainerManagementProtocolProxy to Debug |  Minor | . | Anubhav Dhoot | Anubhav Dhoot |
| [YARN-4106](https://issues.apache.org/jira/browse/YARN-4106) | NodeLabels for NM in distributed mode is not updated even after clusterNodelabel addition in RM |  Major | . | Bibin A Chundatt | Bibin A Chundatt |
| [YARN-4078](https://issues.apache.org/jira/browse/YARN-4078) | getPendingResourceRequestForAttempt is present in AbstractYarnScheduler should be present in YarnScheduler interface instead |  Minor | resourcemanager | Naganarasimha G R | Naganarasimha G R |
| [YARN-4073](https://issues.apache.org/jira/browse/YARN-4073) | Unused ApplicationACLsManager in ContainerManagerImpl |  Trivial | . | Naganarasimha G R | Naganarasimha G R |
| [YARN-4066](https://issues.apache.org/jira/browse/YARN-4066) | Large number of queues choke fair scheduler |  Major | fairscheduler | Johan Gustavsson | Johan Gustavsson |
| [YARN-4044](https://issues.apache.org/jira/browse/YARN-4044) | Running applications information changes such as movequeue is not published to TimeLine server |  Critical | resourcemanager, timelineserver | Sunil G | Sunil G |
| [YARN-4028](https://issues.apache.org/jira/browse/YARN-4028) | AppBlock page key update and diagnostics value null on recovery |  Minor | . | Bibin A Chundatt | Bibin A Chundatt |
| [YARN-4026](https://issues.apache.org/jira/browse/YARN-4026) | FiCaSchedulerApp: ContainerAllocator should be able to choose how to order pending resource requests |  Major | . | Wangda Tan | Wangda Tan |
| [YARN-4017](https://issues.apache.org/jira/browse/YARN-4017) | container-executor overuses PATH\_MAX |  Major | nodemanager | Allen Wittenauer | Sidharta Seethana |
| [YARN-3987](https://issues.apache.org/jira/browse/YARN-3987) | am container complete msg ack to NM once RM receive it |  Major | resourcemanager | sandflee | sandflee |
| [YARN-3986](https://issues.apache.org/jira/browse/YARN-3986) | getTransferredContainers in AbstractYarnScheduler should be present in YarnScheduler interface instead |  Major | scheduler | Varun Saxena | Varun Saxena |
| [YARN-3983](https://issues.apache.org/jira/browse/YARN-3983) | Make CapacityScheduler to easier extend application allocation logic |  Major | . | Wangda Tan | Wangda Tan |
| [YARN-3982](https://issues.apache.org/jira/browse/YARN-3982) | container-executor parsing of container-executor.cfg broken in trunk and branch-2 |  Blocker | nodemanager | Varun Vasudev | Varun Vasudev |
| [YARN-3973](https://issues.apache.org/jira/browse/YARN-3973) | Recent changes to application priority management break reservation system from YARN-1051 |  Major | resourcemanager | Carlo Curino | Carlo Curino |
| [YARN-3971](https://issues.apache.org/jira/browse/YARN-3971) | Skip RMNodeLabelsManager#checkRemoveFromClusterNodeLabelsOfQueue on nodelabel recovery |  Critical | resourcemanager | Bibin A Chundatt | Bibin A Chundatt |
| [YARN-3966](https://issues.apache.org/jira/browse/YARN-3966) | Fix excessive loggings in CapacityScheduler |  Major | . | Jian He | Jian He |
| [YARN-3963](https://issues.apache.org/jira/browse/YARN-3963) | AddNodeLabel on duplicate label addition shows success |  Minor | . | Bibin A Chundatt | Bibin A Chundatt |
| [YARN-3958](https://issues.apache.org/jira/browse/YARN-3958) | TestYarnConfigurationFields should be moved to hadoop-yarn-api module |  Major | . | Varun Saxena | Varun Saxena |
| [YARN-3957](https://issues.apache.org/jira/browse/YARN-3957) | FairScheduler NPE In FairSchedulerQueueInfo causing scheduler page to return 500 |  Major | fairscheduler | Anubhav Dhoot | Anubhav Dhoot |
| [YARN-3954](https://issues.apache.org/jira/browse/YARN-3954) | TestYarnConfigurationFields#testCompareConfigurationClassAgainstXml fails in trunk |  Major | . | Varun Saxena | Varun Saxena |
| [YARN-3941](https://issues.apache.org/jira/browse/YARN-3941) | Proportional Preemption policy should try to avoid sending duplicate PREEMPT\_CONTAINER event to scheduler |  Major | capacityscheduler | Sunil G | Sunil G |
| [YARN-3932](https://issues.apache.org/jira/browse/YARN-3932) | SchedulerApplicationAttempt#getResourceUsageReport and UserInfo should based on total-used-resources |  Major | resourcemanager | Bibin A Chundatt | Bibin A Chundatt |
| [YARN-3919](https://issues.apache.org/jira/browse/YARN-3919) | NPEs' while stopping service after exception during CommonNodeLabelsManager#start |  Trivial | resourcemanager | Varun Saxena | Varun Saxena |
| [YARN-3917](https://issues.apache.org/jira/browse/YARN-3917) | getResourceCalculatorPlugin for the default should intercept all exceptions |  Major | . | Gera Shegalov | Gera Shegalov |
| [YARN-3900](https://issues.apache.org/jira/browse/YARN-3900) | Protobuf layout  of yarn\_security\_token causes errors in other protos that include it |  Major | . | Anubhav Dhoot | Anubhav Dhoot |
| [YARN-3894](https://issues.apache.org/jira/browse/YARN-3894) | RM startup should fail for wrong CS xml NodeLabel capacity configuration |  Critical | capacityscheduler | Bibin A Chundatt | Bibin A Chundatt |
| [YARN-3892](https://issues.apache.org/jira/browse/YARN-3892) | NPE on RMStateStore#serviceStop when CapacityScheduler#serviceInit fails |  Minor | . | Bibin A Chundatt | Bibin A Chundatt |
| [YARN-3888](https://issues.apache.org/jira/browse/YARN-3888) | ApplicationMaster link is broken in RM WebUI when appstate is NEW |  Minor | resourcemanager | Bibin A Chundatt | Bibin A Chundatt |
| [YARN-3885](https://issues.apache.org/jira/browse/YARN-3885) | ProportionalCapacityPreemptionPolicy doesn't preempt if queue is more than 2 level |  Blocker | yarn | Ajith S | Ajith S |
| [YARN-3882](https://issues.apache.org/jira/browse/YARN-3882) | AggregatedLogFormat should close aclScanner and ownerScanner after create them. |  Minor | nodemanager | zhihai xu | zhihai xu |
| [YARN-3875](https://issues.apache.org/jira/browse/YARN-3875) | FSSchedulerNode#reserveResource() doesn't print Application Id properly in log |  Minor | . | Bibin A Chundatt | Bibin A Chundatt |
| [YARN-3860](https://issues.apache.org/jira/browse/YARN-3860) | rmadmin -transitionToActive should check the state of non-target node |  Major | resourcemanager | Masatake Iwasaki | Masatake Iwasaki |
| [YARN-3859](https://issues.apache.org/jira/browse/YARN-3859) | LeafQueue doesn't print user properly for application add |  Minor | capacityscheduler | Devaraj K | Varun Saxena |
| [YARN-3849](https://issues.apache.org/jira/browse/YARN-3849) | Too much of preemption activity causing continuos killing of containers across queues |  Critical | capacityscheduler | Sunil G | Sunil G |
| [YARN-3846](https://issues.apache.org/jira/browse/YARN-3846) | RM Web UI queue filter is not working |  Major | yarn | Mohammad Shahid Khan | Mohammad Shahid Khan |
| [YARN-3845](https://issues.apache.org/jira/browse/YARN-3845) | Scheduler page does not render RGBA color combinations in IE11 |  Minor | . | Jagadesh Kiran N | Mohammad Shahid Khan |
| [YARN-3840](https://issues.apache.org/jira/browse/YARN-3840) | Resource Manager web ui issue when sorting application by id (with application having id \> 9999) |  Major | resourcemanager | LINTE | Varun Saxena |
| [YARN-3837](https://issues.apache.org/jira/browse/YARN-3837) | javadocs of TimelineAuthenticationFilterInitializer give wrong prefix for auth options |  Minor | timelineserver | Steve Loughran | Bibin A Chundatt |
| [YARN-3835](https://issues.apache.org/jira/browse/YARN-3835) | hadoop-yarn-server-resourcemanager test package bundles core-site.xml, yarn-site.xml |  Minor | resourcemanager | Vamsee Yarlagadda | Vamsee Yarlagadda |
| [YARN-3830](https://issues.apache.org/jira/browse/YARN-3830) | AbstractYarnScheduler.createReleaseCache may try to clean a null attempt |  Major | scheduler | nijel | nijel |
| [YARN-3826](https://issues.apache.org/jira/browse/YARN-3826) | Race condition in ResourceTrackerService leads to wrong diagnostics messages |  Major | resourcemanager | Chengbing Liu | Chengbing Liu |
| [YARN-3824](https://issues.apache.org/jira/browse/YARN-3824) | Fix two minor nits in member variable properties of YarnConfiguration |  Trivial | yarn | Ray Chiang | Ray Chiang |
| [YARN-3823](https://issues.apache.org/jira/browse/YARN-3823) | Fix mismatch in default values for yarn.scheduler.maximum-allocation-vcores property |  Minor | . | Ray Chiang | Ray Chiang |
| [YARN-3805](https://issues.apache.org/jira/browse/YARN-3805) | Update the documentation of Disk Checker based on YARN-90 |  Minor | documentation | Masatake Iwasaki | Masatake Iwasaki |
| [YARN-3794](https://issues.apache.org/jira/browse/YARN-3794) | TestRMEmbeddedElector fails because of ambiguous LOG reference |  Major | test | Chengbing Liu | Chengbing Liu |
| [YARN-3790](https://issues.apache.org/jira/browse/YARN-3790) | usedResource from rootQueue metrics may get stale data for FS scheduler after recovering the container |  Major | fairscheduler, test | Rohith Sharma K S | zhihai xu |
| [YARN-3785](https://issues.apache.org/jira/browse/YARN-3785) | Support for Resource as an argument during submitApp call in MockRM test class |  Minor | resourcemanager | Sunil G | Sunil G |
| [YARN-3778](https://issues.apache.org/jira/browse/YARN-3778) | Fix Yarn resourcemanger CLI usage |  Major | . | Brahma Reddy Battula | Brahma Reddy Battula |
| [YARN-3770](https://issues.apache.org/jira/browse/YARN-3770) | SerializedException should also handle java.lang.Error |  Major | . | Lavkesh Lahngir | Lavkesh Lahngir |
| [YARN-3768](https://issues.apache.org/jira/browse/YARN-3768) | ArrayIndexOutOfBoundsException with empty environment variables |  Major | yarn | Joe Ferner | zhihai xu |
| [YARN-3762](https://issues.apache.org/jira/browse/YARN-3762) | FairScheduler: CME on FSParentQueue#getQueueUserAclInfo |  Critical | fairscheduler | Karthik Kambatla | Karthik Kambatla |
| [YARN-3751](https://issues.apache.org/jira/browse/YARN-3751) | TestAHSWebServices fails after YARN-3467 |  Major | . | Zhijie Shen | Sunil G |
| [YARN-3749](https://issues.apache.org/jira/browse/YARN-3749) | We should make a copy of configuration when init MiniYARNCluster with multiple RMs |  Major | . | Chun Chen | Chun Chen |
| [YARN-3747](https://issues.apache.org/jira/browse/YARN-3747) | TestLocalDirsHandlerService should delete the created test directory logDir2 |  Minor | test | David Moore | David Moore |
| [YARN-3745](https://issues.apache.org/jira/browse/YARN-3745) | SerializedException should also try to instantiate internal exception with the default constructor |  Major | . | Lavkesh Lahngir | Lavkesh Lahngir |
| [YARN-3714](https://issues.apache.org/jira/browse/YARN-3714) | AM proxy filter can not get RM webapp address from yarn.resourcemanager.hostname.rm-id |  Minor | . | Masatake Iwasaki | Masatake Iwasaki |
| [YARN-3707](https://issues.apache.org/jira/browse/YARN-3707) | RM Web UI queue filter doesn't work |  Blocker | . | Wangda Tan | Wangda Tan |
| [YARN-3695](https://issues.apache.org/jira/browse/YARN-3695) | ServerProxy (NMProxy, etc.) shouldn't retry forever for non network exception. |  Major | . | Junping Du | Raju Bairishetti |
| [YARN-3655](https://issues.apache.org/jira/browse/YARN-3655) | FairScheduler: potential livelock due to maxAMShare limitation and container reservation |  Critical | fairscheduler | zhihai xu | zhihai xu |
| [YARN-3654](https://issues.apache.org/jira/browse/YARN-3654) | ContainerLogsPage web UI should not have meta-refresh |  Major | yarn | Xuan Gong | Xuan Gong |
| [YARN-3629](https://issues.apache.org/jira/browse/YARN-3629) | NodeID is always printed as "null" in node manager initialization log. |  Major | . | nijel | nijel |
| [YARN-3617](https://issues.apache.org/jira/browse/YARN-3617) | Fix WindowsResourceCalculatorPlugin.getCpuFrequency() returning always -1 |  Minor | . | Georg Berendt | J.Andreina |
| [YARN-3604](https://issues.apache.org/jira/browse/YARN-3604) | removeApplication in ZKRMStateStore should also disable watch. |  Minor | resourcemanager | zhihai xu | zhihai xu |
| [YARN-3602](https://issues.apache.org/jira/browse/YARN-3602) | TestResourceLocalizationService.testPublicResourceInitializesLocalDir fails Intermittently due to IOException from cleanup |  Minor | test | zhihai xu | zhihai xu |
| [YARN-3600](https://issues.apache.org/jira/browse/YARN-3600) | AM container link is broken (on a killed application, at least) |  Major | . | Sergey Shelukhin | Naganarasimha G R |
| [YARN-3594](https://issues.apache.org/jira/browse/YARN-3594) | WintuilsProcessStubExecutor.startStreamReader leaks streams |  Trivial | nodemanager | Steve Loughran | Lars Francke |
| [YARN-3592](https://issues.apache.org/jira/browse/YARN-3592) | Fix typos in RMNodeLabelsManager |  Trivial | resourcemanager | Junping Du | Sunil G |
| [YARN-3591](https://issues.apache.org/jira/browse/YARN-3591) | Resource localization on a bad disk causes subsequent containers failure |  Major | . | Lavkesh Lahngir | Lavkesh Lahngir |
| [YARN-3589](https://issues.apache.org/jira/browse/YARN-3589) | RM and AH web UI display DOCTYPE wrongly |  Major | webapp | Rohith Sharma K S | Rohith Sharma K S |
| [YARN-3587](https://issues.apache.org/jira/browse/YARN-3587) | Fix the javadoc of DelegationTokenSecretManager in projects of yarn, etc. |  Minor | documentation | Akira AJISAKA | Gabor Liptak |
| [YARN-3584](https://issues.apache.org/jira/browse/YARN-3584) | [Log mesage correction] : MIssing space in Diagnostics message |  Trivial | . | nijel | nijel |
| [YARN-3582](https://issues.apache.org/jira/browse/YARN-3582) | NPE in WebAppProxyServlet |  Major | . | Jian He | Jian He |
| [YARN-3577](https://issues.apache.org/jira/browse/YARN-3577) | Misspelling of threshold in log4j.properties for tests |  Minor | test | Brahma Reddy Battula | Brahma Reddy Battula |
| [YARN-3572](https://issues.apache.org/jira/browse/YARN-3572) | Correct typos in WritingYarnApplications.md |  Minor | documentation | Sandeep Khurana | Gabor Liptak |
| [YARN-3564](https://issues.apache.org/jira/browse/YARN-3564) | Fix TestContainerAllocation.testAMContainerAllocationWhenDNSUnavailable fails randomly |  Major | . | Jian He | Jian He |
| [YARN-3552](https://issues.apache.org/jira/browse/YARN-3552) | RM Web UI shows -1 running containers for completed apps |  Trivial | webapp | Rohith Sharma K S | Rohith Sharma K S |
| [YARN-3533](https://issues.apache.org/jira/browse/YARN-3533) | Test: Fix launchAM in MockRM to wait for attempt to be scheduled |  Major | yarn | Anubhav Dhoot | Anubhav Dhoot |
| [YARN-3530](https://issues.apache.org/jira/browse/YARN-3530) | ATS throws exception on trying to filter results without otherinfo. |  Critical | timelineserver | Sreenath Somarajapuram | Zhijie Shen |
| [YARN-3523](https://issues.apache.org/jira/browse/YARN-3523) | Cleanup ResourceManagerAdministrationProtocol interface audience |  Major | client, resourcemanager | Wangda Tan | Naganarasimha G R |
| [YARN-3517](https://issues.apache.org/jira/browse/YARN-3517) | RM web ui for dumping scheduler logs should be for admins only |  Blocker | resourcemanager, security | Varun Vasudev | Varun Vasudev |
| [YARN-3495](https://issues.apache.org/jira/browse/YARN-3495) | Confusing log generated by FairScheduler |  Major | . | Brahma Reddy Battula | Brahma Reddy Battula |
| [YARN-3493](https://issues.apache.org/jira/browse/YARN-3493) | RM fails to come up with error "Failed to load/recover state" when  mem settings are changed |  Critical | yarn | Sumana Sathish | Jian He |
| [YARN-3473](https://issues.apache.org/jira/browse/YARN-3473) | Fix RM Web UI configuration for some properties |  Minor | resourcemanager | Ray Chiang | Ray Chiang |
| [YARN-3459](https://issues.apache.org/jira/browse/YARN-3459) | Fix failiure of TestLog4jWarningErrorMetricsAppender |  Blocker | . | Li Lu | Varun Vasudev |
| [YARN-3453](https://issues.apache.org/jira/browse/YARN-3453) | Fair Scheduler: Parts of preemption logic uses DefaultResourceCalculator even in DRF mode causing thrashing |  Major | fairscheduler | Ashwin Shankar | Arun Suresh |
| [YARN-3444](https://issues.apache.org/jira/browse/YARN-3444) | Fix typo capabililty |  Trivial | applications/distributed-shell | Gabor Liptak | Gabor Liptak |
| [YARN-3436](https://issues.apache.org/jira/browse/YARN-3436) | Fix URIs in documention of YARN web service REST APIs |  Minor | documentation, resourcemanager | Bibin A Chundatt | Bibin A Chundatt |
| [YARN-3435](https://issues.apache.org/jira/browse/YARN-3435) | AM container to be allocated Appattempt AM container shown as null |  Trivial | resourcemanager | Bibin A Chundatt | Bibin A Chundatt |
| [YARN-3434](https://issues.apache.org/jira/browse/YARN-3434) | Interaction between reservations and userlimit can result in significant ULF violation |  Major | capacityscheduler | Thomas Graves | Thomas Graves |
| [YARN-3433](https://issues.apache.org/jira/browse/YARN-3433) | Jersey tests failing with Port in Use -again |  Critical | build, test | Steve Loughran | Brahma Reddy Battula |
| [YARN-3429](https://issues.apache.org/jira/browse/YARN-3429) | TestAMRMTokens.testTokenExpiry fails Intermittently with error message:Invalid AMRMToken |  Major | test | zhihai xu | zhihai xu |
| [YARN-3425](https://issues.apache.org/jira/browse/YARN-3425) | NPE from RMNodeLabelsManager.serviceStop when NodeLabelsManager.serviceInit failed |  Minor | resourcemanager | Bibin A Chundatt | Bibin A Chundatt |
| [YARN-3415](https://issues.apache.org/jira/browse/YARN-3415) | Non-AM containers can be counted towards amResourceUsage of a Fair Scheduler queue |  Critical | fairscheduler | Rohit Agarwal | zhihai xu |
| [YARN-3400](https://issues.apache.org/jira/browse/YARN-3400) | [JDK 8] Build Failure due to unreported exceptions in RPCUtil |  Major | . | Robert Kanter | Robert Kanter |
| [YARN-3397](https://issues.apache.org/jira/browse/YARN-3397) | yarn rmadmin should skip -failover |  Minor | resourcemanager | J.Andreina | J.Andreina |
| [YARN-3396](https://issues.apache.org/jira/browse/YARN-3396) | Handle URISyntaxException in ResourceLocalizationService |  Major | nodemanager | Chengbing Liu | Brahma Reddy Battula |
| [YARN-3395](https://issues.apache.org/jira/browse/YARN-3395) | FairScheduler: Trim whitespaces when using username for queuename |  Major | fairscheduler | zhihai xu | zhihai xu |
| [YARN-3394](https://issues.apache.org/jira/browse/YARN-3394) | WebApplication  proxy documentation is incomplete |  Minor | resourcemanager | Bibin A Chundatt | Naganarasimha G R |
| [YARN-3387](https://issues.apache.org/jira/browse/YARN-3387) | Previous AM's container complete message couldn't pass to current am if am restarted and rm changed |  Critical | resourcemanager | sandflee | sandflee |
| [YARN-3383](https://issues.apache.org/jira/browse/YARN-3383) | AdminService should use "warn" instead of "info" to log exception when operation fails |  Major | resourcemanager | Wangda Tan | Li Lu |
| [YARN-3375](https://issues.apache.org/jira/browse/YARN-3375) | NodeHealthScriptRunner.shouldRun() check is performing 3 times for starting NodeHealthScriptRunner |  Minor | nodemanager | Devaraj K | Devaraj K |
| [YARN-3305](https://issues.apache.org/jira/browse/YARN-3305) | AM-Used Resource for leafqueue is wrongly populated if AM ResourceRequest is less than minimumAllocation |  Major | scheduler | Rohith Sharma K S | Rohith Sharma K S |
| [YARN-3269](https://issues.apache.org/jira/browse/YARN-3269) | Yarn.nodemanager.remote-app-log-dir could not be configured to fully qualified path |  Major | . | Xuan Gong | Xuan Gong |
| [YARN-3266](https://issues.apache.org/jira/browse/YARN-3266) | RMContext inactiveNodes should have NodeId as map key |  Major | resourcemanager | Chengbing Liu | Chengbing Liu |
| [YARN-3243](https://issues.apache.org/jira/browse/YARN-3243) | CapacityScheduler should pass headroom from parent to children to make sure ParentQueue obey its capacity limits. |  Major | capacityscheduler, resourcemanager | Wangda Tan | Wangda Tan |
| [YARN-3205](https://issues.apache.org/jira/browse/YARN-3205) | FileSystemRMStateStore should disable FileSystem Cache to avoid get a Filesystem with an old configuration. |  Major | resourcemanager | zhihai xu | zhihai xu |
| [YARN-3197](https://issues.apache.org/jira/browse/YARN-3197) | Confusing log generated by CapacityScheduler |  Minor | capacityscheduler | Hitesh Shah | Varun Saxena |
| [YARN-3097](https://issues.apache.org/jira/browse/YARN-3097) | Logging of resource recovery on NM restart has redundancies |  Minor | nodemanager | Jason Lowe | Eric Payne |
| [YARN-3021](https://issues.apache.org/jira/browse/YARN-3021) | YARN's delegation-token handling disallows certain trust setups to operate properly over DistCp |  Major | security | Harsh J | Yongjun Zhang |
| [YARN-3018](https://issues.apache.org/jira/browse/YARN-3018) | Unify the default value for yarn.scheduler.capacity.node-locality-delay in code and default xml file |  Trivial | capacityscheduler | nijel | nijel |
| [YARN-2893](https://issues.apache.org/jira/browse/YARN-2893) | AMLaucher: sporadic job failures due to EOFException in readTokenStorageStream |  Major | resourcemanager | Gera Shegalov | zhihai xu |
| [YARN-2821](https://issues.apache.org/jira/browse/YARN-2821) | Distributed shell app master becomes unresponsive sometimes |  Major | applications/distributed-shell | Varun Vasudev | Varun Vasudev |
| [YARN-2725](https://issues.apache.org/jira/browse/YARN-2725) | Adding test cases of retrying requests about ZKRMStateStore |  Major | . | Tsuyoshi Ozawa | Tsuyoshi Ozawa |
| [YARN-2597](https://issues.apache.org/jira/browse/YARN-2597) | MiniYARNCluster should propagate reason for AHS not starting |  Major | test | Steve Loughran | Steve Loughran |
| [YARN-2454](https://issues.apache.org/jira/browse/YARN-2454) | Fix compareTo of variable UNBOUNDED in o.a.h.y.util.resource.Resources. |  Major | . | Xu Yang | Xu Yang |
| [YARN-2421](https://issues.apache.org/jira/browse/YARN-2421) | RM still allocates containers to an app in the FINISHING state |  Major | scheduler | Thomas Graves | Chang Li |
| [YARN-2194](https://issues.apache.org/jira/browse/YARN-2194) | Cgroups cease to work in RHEL7 |  Critical | nodemanager | Wei Yan | Wei Yan |
| [YARN-2123](https://issues.apache.org/jira/browse/YARN-2123) | Progress bars in Web UI always at 100% due to non-US locale |  Major | webapp | Johannes Simon | Akira AJISAKA |
| [YARN-1993](https://issues.apache.org/jira/browse/YARN-1993) | Cross-site scripting vulnerability in TextView.java |  Major | webapp | Ted Yu | Kenji Kikushima |
| [YARN-1912](https://issues.apache.org/jira/browse/YARN-1912) | ResourceLocalizer started without any jvm memory control |  Major | nodemanager | stanley shi | Masatake Iwasaki |
| [YARN-1832](https://issues.apache.org/jira/browse/YARN-1832) | Fix wrong MockLocalizerStatus#equals implementation |  Minor | nodemanager | Hong Zhiguo | Hong Zhiguo |
| [YARN-1556](https://issues.apache.org/jira/browse/YARN-1556) | NPE getting application report with a null appId |  Minor | client | Steve Loughran | Weiwei Yang |
| [YARN-1519](https://issues.apache.org/jira/browse/YARN-1519) | check if sysconf is implemented before using it |  Major | nodemanager | Radim Kolar | Radim Kolar |
| [YARN-1382](https://issues.apache.org/jira/browse/YARN-1382) | Remove unusableRMNodesConcurrentSet (never used) in NodeListManager to get rid of memory leak |  Major | resourcemanager | Alejandro Abdelnur | Rohith Sharma K S |


### TESTS:

| JIRA | Summary | Priority | Component | Reporter | Contributor |
|:---- |:---- | :--- |:---- |:---- |:---- |
| [HADOOP-12736](https://issues.apache.org/jira/browse/HADOOP-12736) | TestTimedOutTestsListener#testThreadDumpAndDeadlocks sometimes times out |  Major | . | Xiao Chen | Xiao Chen |
| [HADOOP-12715](https://issues.apache.org/jira/browse/HADOOP-12715) | TestValueQueue#testgetAtMostPolicyALL fails intermittently |  Major | . | Xiao Chen | Xiao Chen |
| [HADOOP-12696](https://issues.apache.org/jira/browse/HADOOP-12696) | Add Tests for S3FileSystem Contract |  Major | tools | Matthew Paduano | Matthew Paduano |
| [HADOOP-12564](https://issues.apache.org/jira/browse/HADOOP-12564) |  Upgrade JUnit3 TestCase to JUnit 4 in org.apache.hadoop.io package |  Trivial | test | Dustin Cote | Dustin Cote |
| [HADOOP-12035](https://issues.apache.org/jira/browse/HADOOP-12035) | shellcheck plugin displays a wrong version potentially |  Trivial | build | Kengo Seki | Kengo Seki |
| [HADOOP-12030](https://issues.apache.org/jira/browse/HADOOP-12030) | test-patch should only report on newly introduced findbugs warnings. |  Major | . | Sean Busbey | Sean Busbey |
| [HADOOP-12000](https://issues.apache.org/jira/browse/HADOOP-12000) | cannot use --java-home in test-patch |  Major | scripts | Allen Wittenauer | Allen Wittenauer |
| [HADOOP-11965](https://issues.apache.org/jira/browse/HADOOP-11965) | determine-flaky-tests needs a summary mode |  Minor | . | Allen Wittenauer | Yufei Gu |
| [HADOOP-11949](https://issues.apache.org/jira/browse/HADOOP-11949) | Add user-provided plugins to test-patch |  Major | . | Sean Busbey | Sean Busbey |
| [HADOOP-11944](https://issues.apache.org/jira/browse/HADOOP-11944) | add option to test-patch to avoid relocating patch process directory |  Minor | . | Sean Busbey | Sean Busbey |
| [HADOOP-11930](https://issues.apache.org/jira/browse/HADOOP-11930) | test-patch in offline mode should tell maven to be in offline mode |  Major | . | Sean Busbey | Sean Busbey |
| [HADOOP-11906](https://issues.apache.org/jira/browse/HADOOP-11906) | test-patch.sh should use 'file' command for patch determinism |  Major | . | Allen Wittenauer | Sean Busbey |
| [HADOOP-11904](https://issues.apache.org/jira/browse/HADOOP-11904) | test-patch.sh goes into an infinite loop on non-maven builds |  Critical | test | Allen Wittenauer | Allen Wittenauer |
| [HADOOP-11884](https://issues.apache.org/jira/browse/HADOOP-11884) | test-patch.sh should pull the real findbugs version |  Minor | test | Allen Wittenauer | Kengo Seki |
| [HADOOP-11881](https://issues.apache.org/jira/browse/HADOOP-11881) | test-patch.sh javac result is wildly wrong |  Major | build, test | Allen Wittenauer | Kengo Seki |
| [HADOOP-10729](https://issues.apache.org/jira/browse/HADOOP-10729) | Add tests for PB RPC in case version mismatch of client and server |  Major | ipc | Junping Du | Junping Du |
| [HDFS-9773](https://issues.apache.org/jira/browse/HDFS-9773) | Remove dead code related to SimulatedFSDataset in tests |  Minor | test | Akira AJISAKA | Brahma Reddy Battula |
| [HDFS-9626](https://issues.apache.org/jira/browse/HDFS-9626) | TestBlockReplacement#testBlockReplacement fails occasionally |  Minor | test | Xiao Chen | Xiao Chen |
| [HDFS-9429](https://issues.apache.org/jira/browse/HDFS-9429) | Tests in TestDFSAdminWithHA intermittently fail with EOFException |  Major | test | Xiao Chen | Xiao Chen |
| [HDFS-9410](https://issues.apache.org/jira/browse/HDFS-9410) | Some tests should always reset sysout and syserr |  Minor | test | Xiao Chen | Xiao Chen |
| [HDFS-9354](https://issues.apache.org/jira/browse/HDFS-9354) | Fix TestBalancer#testBalancerWithZeroThreadsForMove on Windows |  Major | test | Xiaoyu Yao | Xiaoyu Yao |
| [HDFS-9339](https://issues.apache.org/jira/browse/HDFS-9339) | Extend full test of KMS ACLs |  Major | test | Daniel Templeton | Daniel Templeton |
| [HDFS-9295](https://issues.apache.org/jira/browse/HDFS-9295) | Add a thorough test of the full KMS code path |  Critical | security, test | Daniel Templeton | Daniel Templeton |
| [HDFS-9153](https://issues.apache.org/jira/browse/HDFS-9153) | Pretty-format the output for DFSIO |  Major | . | Kai Zheng | Kai Zheng |
| [HDFS-8834](https://issues.apache.org/jira/browse/HDFS-8834) | TestReplication#testReplicationWhenBlockCorruption is not valid after HDFS-6482 |  Minor | datanode | Lei (Eddy) Xu | Lei (Eddy) Xu |
| [HDFS-8645](https://issues.apache.org/jira/browse/HDFS-8645) | Resolve inconsistent code in TestReplicationPolicy between trunk and branch-2 |  Major | namenode | Zhe Zhang | Zhe Zhang |
| [HDFS-8247](https://issues.apache.org/jira/browse/HDFS-8247) | TestDiskspaceQuotaUpdate#testAppendOverTypeQuota is failing |  Major | test | Anu Engineer | Xiaoyu Yao |
| [HDFS-8243](https://issues.apache.org/jira/browse/HDFS-8243) | Files written by TestHostsFiles and TestNameNodeMXBean are causing Release Audit Warnings. |  Minor | test | Ruth Wisniewski | Ruth Wisniewski |
| [HDFS-7559](https://issues.apache.org/jira/browse/HDFS-7559) | Create unit test to automatically compare HDFS related classes and hdfs-default.xml |  Minor | . | Ray Chiang | Ray Chiang |
| [HDFS-7553](https://issues.apache.org/jira/browse/HDFS-7553) | fix the TestDFSUpgradeWithHA due to BindException |  Major | test | Liang Xie | Xiao Chen |
| [HDFS-6408](https://issues.apache.org/jira/browse/HDFS-6408) | Remove redundant definitions in log4j.properties |  Minor | test | Abhiraj Butala | Abhiraj Butala |
| [HDFS-6263](https://issues.apache.org/jira/browse/HDFS-6263) | Remove DRFA.MaxBackupIndex config from log4j.properties |  Minor | . | Akira AJISAKA | Abhiraj Butala |
| [HDFS-2070](https://issues.apache.org/jira/browse/HDFS-2070) | Add more unit tests for FsShell getmerge |  Major | test | XieXianshan | Daniel Templeton |
| [MAPREDUCE-6614](https://issues.apache.org/jira/browse/MAPREDUCE-6614) | Remove unnecessary code in TestMapreduceConfigFields |  Minor | test | Akira AJISAKA | Kai Sasaki |
| [MAPREDUCE-6204](https://issues.apache.org/jira/browse/MAPREDUCE-6204) | TestJobCounters should use new properties instead of JobConf.MAPRED\_TASK\_JAVA\_OPTS |  Minor | test | sam liu | sam liu |
| [MAPREDUCE-5045](https://issues.apache.org/jira/browse/MAPREDUCE-5045) | UtilTest#isCygwin method appears to be unused |  Trivial | contrib/streaming, test | Chris Nauroth | Neelesh Srinivas Salian |
| [YARN-3992](https://issues.apache.org/jira/browse/YARN-3992) | TestApplicationPriority.testApplicationPriorityAllocation fails intermittently |  Major | . | Zhijie Shen | Sunil G |
| [YARN-3956](https://issues.apache.org/jira/browse/YARN-3956) | Fix TestNodeManagerHardwareUtils fails on Mac |  Minor | nodemanager | Varun Vasudev | Varun Vasudev |
| [YARN-3573](https://issues.apache.org/jira/browse/YARN-3573) | MiniMRYarnCluster constructor that starts the timeline server using a boolean should be marked deprecated |  Major | timelineserver | Mit Desai | Brahma Reddy Battula |
| [YARN-3343](https://issues.apache.org/jira/browse/YARN-3343) | TestCapacitySchedulerNodeLabelUpdate.testNodeUpdate sometime fails in trunk |  Minor | . | Xuan Gong | Rohith Sharma K S |
| [YARN-3339](https://issues.apache.org/jira/browse/YARN-3339) | TestDockerContainerExecutor should pull a single image and not the entire centos repository |  Minor | test | Ravindra Kumar Naik | Ravindra Kumar Naik |
| [YARN-2871](https://issues.apache.org/jira/browse/YARN-2871) | TestRMRestart#testRMRestartGetApplicationList sometime fails in trunk |  Minor | . | Ted Yu | zhihai xu |
| [YARN-2666](https://issues.apache.org/jira/browse/YARN-2666) | TestFairScheduler.testContinuousScheduling fails Intermittently |  Major | scheduler | Tsuyoshi Ozawa | zhihai xu |
| [YARN-1880](https://issues.apache.org/jira/browse/YARN-1880) | Cleanup TestApplicationClientProtocolOnHA |  Trivial | test | Tsuyoshi Ozawa | Tsuyoshi Ozawa |


### SUB-TASKS:

| JIRA | Summary | Priority | Component | Reporter | Contributor |
|:---- |:---- | :--- |:---- |:---- |:---- |
| [HADOOP-12813](https://issues.apache.org/jira/browse/HADOOP-12813) | Migrate TestRPC and related codes to rebase on ProtobufRpcEngine |  Major | . | Kai Zheng | Kai Zheng |
| [HADOOP-12752](https://issues.apache.org/jira/browse/HADOOP-12752) | Improve diagnostics/use of envvar/sysprop credential propagation |  Minor | security | Steve Loughran | Steve Loughran |
| [HADOOP-12711](https://issues.apache.org/jira/browse/HADOOP-12711) | Remove dependency on commons-httpclient for ServletUtil |  Major | . | Wei-Chiu Chuang | Wei-Chiu Chuang |
| [HADOOP-12582](https://issues.apache.org/jira/browse/HADOOP-12582) | Using BytesWritable's getLength() and getBytes() instead of get() and getSize() |  Major | . | Tsuyoshi Ozawa | Akira AJISAKA |
| [HADOOP-12475](https://issues.apache.org/jira/browse/HADOOP-12475) | Replace guava Cache with ConcurrentHashMap for caching Connection in ipc Client |  Major | conf, io, ipc | Walter Su | Walter Su |
| [HADOOP-12457](https://issues.apache.org/jira/browse/HADOOP-12457) | [JDK8] Fix a failure of compiling common by javadoc |  Major | . | Tsuyoshi Ozawa | Akira AJISAKA |
| [HADOOP-12292](https://issues.apache.org/jira/browse/HADOOP-12292) | Make use of DeleteObjects optional |  Major | fs/s3 | Thomas Demoor | Thomas Demoor |
| [HADOOP-12269](https://issues.apache.org/jira/browse/HADOOP-12269) | Update aws-sdk dependency to 1.10.6 |  Major | fs/s3 | Thomas Demoor | Thomas Demoor |
| [HADOOP-12184](https://issues.apache.org/jira/browse/HADOOP-12184) | Remove unused Linux-specific constants in NativeIO |  Major | native | Martin Walsh | Martin Walsh |
| [HADOOP-12170](https://issues.apache.org/jira/browse/HADOOP-12170) | hadoop-common's JNIFlags.cmake is redundant and can be removed |  Minor | native | Alan Burlison | Alan Burlison |
| [HADOOP-12112](https://issues.apache.org/jira/browse/HADOOP-12112) | Make hadoop-common-project Native code -Wall-clean |  Major | native | Alan Burlison | Alan Burlison |
| [HADOOP-12104](https://issues.apache.org/jira/browse/HADOOP-12104) | Migrate Hadoop Pipes native build to new CMake framework |  Major | build | Alan Burlison | Alan Burlison |
| [HADOOP-12040](https://issues.apache.org/jira/browse/HADOOP-12040) | Adjust inputs order for the decode API in raw erasure coder |  Major | . | Kai Zheng | Kai Zheng |
| [HADOOP-12036](https://issues.apache.org/jira/browse/HADOOP-12036) | Consolidate all of the cmake extensions in one directory |  Major | . | Allen Wittenauer | Alan Burlison |
| [HADOOP-11974](https://issues.apache.org/jira/browse/HADOOP-11974) | Fix FIONREAD #include on Solaris |  Minor | net | Alan Burlison | Alan Burlison |
| [HADOOP-11954](https://issues.apache.org/jira/browse/HADOOP-11954) | Solaris does not support RLIMIT\_MEMLOCK as in Linux |  Major | . | Malcolm Kavalsky | Alan Burlison |
| [HADOOP-11918](https://issues.apache.org/jira/browse/HADOOP-11918) | Listing an empty s3a root directory throws FileNotFound. |  Minor | . | Lei (Eddy) Xu | Lei (Eddy) Xu |
| [HADOOP-11613](https://issues.apache.org/jira/browse/HADOOP-11613) | Remove commons-httpclient dependency from hadoop-azure |  Major | . | Akira AJISAKA | Masatake Iwasaki |
| [HADOOP-11262](https://issues.apache.org/jira/browse/HADOOP-11262) | Enable YARN to use S3A |  Major | fs/s3 | Thomas Demoor | Pieter Reuse |
| [HADOOP-10597](https://issues.apache.org/jira/browse/HADOOP-10597) | RPC Server signals backoff to clients when all request queues are full |  Major | . | Ming Ma | Ming Ma |
| [HADOOP-10300](https://issues.apache.org/jira/browse/HADOOP-10300) | Allowed deferred sending of call responses |  Major | ipc | Daryn Sharp | Daryn Sharp |
| [HADOOP-7824](https://issues.apache.org/jira/browse/HADOOP-7824) | NativeIO.java flags and identifiers must be set correctly for each platform, not hardcoded to their Linux values |  Major | native | Dmytro Shteflyuk | Martin Walsh |
| [HDFS-9438](https://issues.apache.org/jira/browse/HDFS-9438) | TestPipelinesFailover assumes Linux ifconfig |  Minor | test | Alan Burlison | John Zhuge |
| [HDFS-9433](https://issues.apache.org/jira/browse/HDFS-9433) | DFS getEZForPath API on a non-existent file should throw FileNotFoundException |  Major | encryption | Rakesh R | Rakesh R |
| [HDFS-9304](https://issues.apache.org/jira/browse/HDFS-9304) | Add HdfsClientConfigKeys class to TestHdfsConfigFields#configurationClasses |  Major | build | Mingliang Liu | Mingliang Liu |
| [HDFS-9223](https://issues.apache.org/jira/browse/HDFS-9223) | Code cleanup for DatanodeDescriptor and HeartbeatManager |  Minor | namenode | Jing Zhao | Jing Zhao |
| [HDFS-9214](https://issues.apache.org/jira/browse/HDFS-9214) | Support reconfiguring dfs.datanode.balance.max.concurrent.moves without DN restart |  Major | datanode | Xiaobing Zhou | Xiaobing Zhou |
| [HDFS-9170](https://issues.apache.org/jira/browse/HDFS-9170) | Move libhdfs / fuse-dfs / libwebhdfs to hdfs-client |  Major | . | Haohui Mai | Haohui Mai |
| [HDFS-9168](https://issues.apache.org/jira/browse/HDFS-9168) | Move client side unit test to hadoop-hdfs-client |  Major | build | Haohui Mai | Haohui Mai |
| [HDFS-9167](https://issues.apache.org/jira/browse/HDFS-9167) | Update pom.xml in other modules to depend on hdfs-client instead of hdfs |  Major | build | Haohui Mai | Mingliang Liu |
| [HDFS-9166](https://issues.apache.org/jira/browse/HDFS-9166) | Move hftp / hsftp filesystem to hfds-client |  Major | build | Haohui Mai | Mingliang Liu |
| [HDFS-9165](https://issues.apache.org/jira/browse/HDFS-9165) | Move entries in META-INF/services/o.a.h.fs.FileSystem to hdfs-client |  Major | build | Haohui Mai | Mingliang Liu |
| [HDFS-9160](https://issues.apache.org/jira/browse/HDFS-9160) | [OIV-Doc] : Missing details of "delimited" for processor options |  Major | . | nijel | nijel |
| [HDFS-9159](https://issues.apache.org/jira/browse/HDFS-9159) | [OIV] : return value of the command is not correct if invalid value specified in "-p (processor)" option |  Major | . | nijel | nijel |
| [HDFS-9158](https://issues.apache.org/jira/browse/HDFS-9158) | [OEV-Doc] : Document does not mention about "-f" and "-r" options |  Major | . | nijel | nijel |
| [HDFS-9157](https://issues.apache.org/jira/browse/HDFS-9157) | [OEV and OIV] : Unnecessary parsing for mandatory arguements if "-h" option is specified as the only option |  Major | . | nijel | nijel |
| [HDFS-9155](https://issues.apache.org/jira/browse/HDFS-9155) | OEV should treat .XML files as XML even when the file name extension is uppercase |  Major | . | nijel | nijel |
| [HDFS-9134](https://issues.apache.org/jira/browse/HDFS-9134) | Move LEASE\_{SOFTLIMIT,HARDLIMIT}\_PERIOD constants from HdfsServerConstants to HdfsConstants |  Major | . | Mingliang Liu | Mingliang Liu |
| [HDFS-9131](https://issues.apache.org/jira/browse/HDFS-9131) | Move config keys used by hdfs-client to HdfsClientConfigKeys |  Major | . | Mingliang Liu | Mingliang Liu |
| [HDFS-9111](https://issues.apache.org/jira/browse/HDFS-9111) | Move hdfs-client protobuf convert methods from PBHelper to PBHelperClient |  Major | . | Mingliang Liu | Mingliang Liu |
| [HDFS-9101](https://issues.apache.org/jira/browse/HDFS-9101) | Remove deprecated NameNode.getUri() static helper method |  Major | . | Mingliang Liu | Mingliang Liu |
| [HDFS-9084](https://issues.apache.org/jira/browse/HDFS-9084) | Pagination, sorting and filtering of files/directories in the HDFS Web UI |  Major | . | Ravi Prakash | Ravi Prakash |
| [HDFS-9041](https://issues.apache.org/jira/browse/HDFS-9041) | Move entries in META-INF/services/o.a.h.fs.FileSystem to hdfs-client |  Major | build | Haohui Mai | Mingliang Liu |
| [HDFS-9039](https://issues.apache.org/jira/browse/HDFS-9039) | Separate client and server side methods of o.a.h.hdfs.NameNodeProxies |  Major | . | Mingliang Liu | Mingliang Liu |
| [HDFS-9022](https://issues.apache.org/jira/browse/HDFS-9022) | Move NameNode.getAddress() and NameNode.getUri() to hadoop-hdfs-client |  Major | hdfs-client | Mingliang Liu | Mingliang Liu |
| [HDFS-9015](https://issues.apache.org/jira/browse/HDFS-9015) | Refactor TestReplicationPolicy to test different block placement policies |  Major | . | Ming Ma | Ming Ma |
| [HDFS-9012](https://issues.apache.org/jira/browse/HDFS-9012) | Move o.a.h.hdfs.protocol.datatransfer.PipelineAck class to hadoop-hdfs-client module |  Major | build | Mingliang Liu | Mingliang Liu |
| [HDFS-9010](https://issues.apache.org/jira/browse/HDFS-9010) | Replace NameNode.DEFAULT\_PORT with HdfsClientConfigKeys.DFS\_NAMENODE\_RPC\_PORT\_DEFAULT config key |  Major | build | Mingliang Liu | Mingliang Liu |
| [HDFS-9008](https://issues.apache.org/jira/browse/HDFS-9008) | Balancer#Parameters class could use a builder pattern |  Minor | balancer & mover | Chris Trezzo | Chris Trezzo |
| [HDFS-9007](https://issues.apache.org/jira/browse/HDFS-9007) | Fix HDFS Balancer to honor upgrade domain policy |  Major | . | Ming Ma | Ming Ma |
| [HDFS-9006](https://issues.apache.org/jira/browse/HDFS-9006) | Provide BlockPlacementPolicy that supports upgrade domain |  Major | . | Ming Ma | Ming Ma |
| [HDFS-9004](https://issues.apache.org/jira/browse/HDFS-9004) | Add upgrade domain to DatanodeInfo |  Major | . | Ming Ma | Ming Ma |
| [HDFS-9002](https://issues.apache.org/jira/browse/HDFS-9002) | Move o.a.h.hdfs.net/\*Peer classes to hdfs-client |  Major | build | Mingliang Liu | Mingliang Liu |
| [HDFS-8990](https://issues.apache.org/jira/browse/HDFS-8990) | Move RemoteBlockReader to hdfs-client module |  Major | build | Mingliang Liu | Mingliang Liu |
| [HDFS-8984](https://issues.apache.org/jira/browse/HDFS-8984) | Move replication queues related methods in FSNamesystem to BlockManager |  Major | . | Haohui Mai | Haohui Mai |
| [HDFS-8980](https://issues.apache.org/jira/browse/HDFS-8980) | Remove unnecessary block replacement in INodeFile |  Major | namenode | Jing Zhao | Jing Zhao |
| [HDFS-8971](https://issues.apache.org/jira/browse/HDFS-8971) | Remove guards when calling LOG.debug() and LOG.trace() in client package |  Major | build | Mingliang Liu | Mingliang Liu |
| [HDFS-8962](https://issues.apache.org/jira/browse/HDFS-8962) | Clean up checkstyle warnings in o.a.h.hdfs.DfsClientConf |  Major | build | Mingliang Liu | Mingliang Liu |
| [HDFS-8951](https://issues.apache.org/jira/browse/HDFS-8951) | Move the shortcircuit package to hdfs-client |  Major | build | Mingliang Liu | Mingliang Liu |
| [HDFS-8948](https://issues.apache.org/jira/browse/HDFS-8948) | Use GenericTestUtils to set log levels in TestPread and TestReplaceDatanodeOnFailure |  Major | build | Mingliang Liu | Mingliang Liu |
| [HDFS-8934](https://issues.apache.org/jira/browse/HDFS-8934) | Move ShortCircuitShm to hdfs-client |  Major | build | Mingliang Liu | Mingliang Liu |
| [HDFS-8925](https://issues.apache.org/jira/browse/HDFS-8925) | Move BlockReaderLocal to hdfs-client |  Major | build | Mingliang Liu | Mingliang Liu |
| [HDFS-8890](https://issues.apache.org/jira/browse/HDFS-8890) | Allow admin to specify which blockpools the balancer should run on |  Major | balancer & mover | Chris Trezzo | Chris Trezzo |
| [HDFS-8862](https://issues.apache.org/jira/browse/HDFS-8862) | BlockManager#excessReplicateMap should use a HashMap |  Major | namenode | Yi Liu | Yi Liu |
| [HDFS-8826](https://issues.apache.org/jira/browse/HDFS-8826) | Balancer may not move blocks efficiently in some cases |  Major | balancer & mover | Tsz Wo Nicholas Sze | Tsz Wo Nicholas Sze |
| [HDFS-8824](https://issues.apache.org/jira/browse/HDFS-8824) | Do not use small blocks for balancing the cluster |  Major | balancer & mover | Tsz Wo Nicholas Sze | Tsz Wo Nicholas Sze |
| [HDFS-8823](https://issues.apache.org/jira/browse/HDFS-8823) | Move replication factor into individual blocks |  Major | . | Haohui Mai | Haohui Mai |
| [HDFS-8818](https://issues.apache.org/jira/browse/HDFS-8818) | Allow Balancer to run faster |  Major | balancer & mover | Tsz Wo Nicholas Sze | Tsz Wo Nicholas Sze |
| [HDFS-8805](https://issues.apache.org/jira/browse/HDFS-8805) | Archival Storage: getStoragePolicy should not need superuser privilege |  Major | balancer & mover, namenode | Hui Zheng | Brahma Reddy Battula |
| [HDFS-8803](https://issues.apache.org/jira/browse/HDFS-8803) | Move DfsClientConf to hdfs-client |  Major | build | Haohui Mai | Mingliang Liu |
| [HDFS-8801](https://issues.apache.org/jira/browse/HDFS-8801) | Convert BlockInfoUnderConstruction as a feature |  Major | namenode | Zhe Zhang | Jing Zhao |
| [HDFS-8795](https://issues.apache.org/jira/browse/HDFS-8795) | Improve InvalidateBlocks#node2blocks |  Major | . | Yi Liu | Yi Liu |
| [HDFS-8794](https://issues.apache.org/jira/browse/HDFS-8794) | Improve CorruptReplicasMap#corruptReplicasMap |  Major | . | Yi Liu | Yi Liu |
| [HDFS-8792](https://issues.apache.org/jira/browse/HDFS-8792) | BlockManager#postponedMisreplicatedBlocks should use a LightWeightHashSet to save memory |  Major | . | Yi Liu | Yi Liu |
| [HDFS-8742](https://issues.apache.org/jira/browse/HDFS-8742) | Inotify: Support event for OP\_TRUNCATE |  Major | namenode | Surendra Singh Lilhore | Surendra Singh Lilhore |
| [HDFS-8740](https://issues.apache.org/jira/browse/HDFS-8740) | Move DistributedFileSystem to hadoop-hdfs-client |  Major | build | Yi Liu | Mingliang Liu |
| [HDFS-8733](https://issues.apache.org/jira/browse/HDFS-8733) | Keep server related definition in hdfs.proto on server side |  Major | . | Yi Liu | Mingliang Liu |
| [HDFS-8730](https://issues.apache.org/jira/browse/HDFS-8730) | Clean up the import statements in ClientProtocol |  Minor | . | Takanobu Asanuma | Takanobu Asanuma |
| [HDFS-8726](https://issues.apache.org/jira/browse/HDFS-8726) | Move protobuf files that define the client-sever protocols to hdfs-client |  Major | build | Haohui Mai | Haohui Mai |
| [HDFS-8721](https://issues.apache.org/jira/browse/HDFS-8721) | Add a metric for number of encryption zones |  Major | encryption | Rakesh R | Rakesh R |
| [HDFS-8651](https://issues.apache.org/jira/browse/HDFS-8651) | Make hadoop-hdfs-project Native code -Wall-clean |  Major | native | Alan Burlison | Alan Burlison |
| [HDFS-8635](https://issues.apache.org/jira/browse/HDFS-8635) | Migrate HDFS native build to new CMake framework |  Major | build | Alan Burlison | Alan Burlison |
| [HDFS-8620](https://issues.apache.org/jira/browse/HDFS-8620) | Clean up the checkstyle warinings about ClientProtocol |  Major | . | Takanobu Asanuma | Takanobu Asanuma |
| [HDFS-8541](https://issues.apache.org/jira/browse/HDFS-8541) | Mover should exit with NO\_MOVE\_PROGRESS if there is no move progress |  Minor | balancer & mover | Tsz Wo Nicholas Sze | Surendra Singh Lilhore |
| [HDFS-8540](https://issues.apache.org/jira/browse/HDFS-8540) | Mover should exit with NO\_MOVE\_BLOCK if no block can be moved |  Major | balancer & mover | Tsz Wo Nicholas Sze | Surendra Singh Lilhore |
| [HDFS-8495](https://issues.apache.org/jira/browse/HDFS-8495) | Consolidate append() related implementation into a single class |  Major | namenode | Rakesh R | Rakesh R |
| [HDFS-8493](https://issues.apache.org/jira/browse/HDFS-8493) | Consolidate truncate() related implementation in a single class |  Major | . | Haohui Mai | Rakesh R |
| [HDFS-8489](https://issues.apache.org/jira/browse/HDFS-8489) | Subclass BlockInfo to represent contiguous blocks |  Major | namenode | Zhe Zhang | Zhe Zhang |
| [HDFS-8482](https://issues.apache.org/jira/browse/HDFS-8482) | Rename BlockInfoContiguous to BlockInfo |  Major | . | Zhe Zhang | Zhe Zhang |
| [HDFS-8454](https://issues.apache.org/jira/browse/HDFS-8454) | Remove unnecessary throttling in TestDatanodeDeath |  Major | test | Arpit Agarwal | Arpit Agarwal |
| [HDFS-8403](https://issues.apache.org/jira/browse/HDFS-8403) | Eliminate retries in TestFileCreation#testOverwriteOpenForWrite |  Major | test | Arpit Agarwal | Arpit Agarwal |
| [HDFS-8377](https://issues.apache.org/jira/browse/HDFS-8377) | Support HTTP/2 in datanode |  Major | . | Duo Zhang | Duo Zhang |
| [HDFS-8314](https://issues.apache.org/jira/browse/HDFS-8314) | Move HdfsServerConstants#IO\_FILE\_BUFFER\_SIZE and SMALL\_BUFFER\_SIZE to the users |  Major | . | Haohui Mai | Li Lu |
| [HDFS-8310](https://issues.apache.org/jira/browse/HDFS-8310) | Fix TestCLI.testAll 'help: help for find' on Windows |  Minor | test | Xiaoyu Yao | Kiran Kumar M R |
| [HDFS-8309](https://issues.apache.org/jira/browse/HDFS-8309) | Skip unit test using DataNodeTestUtils#injectDataDirFailure() on Windows |  Minor | test | Xiaoyu Yao | Xiaoyu Yao |
| [HDFS-8278](https://issues.apache.org/jira/browse/HDFS-8278) | HDFS Balancer should consider remaining storage % when checking for under-utilized machines |  Major | balancer & mover | Gopal V | Tsz Wo Nicholas Sze |
| [HDFS-8249](https://issues.apache.org/jira/browse/HDFS-8249) | Separate HdfsConstants into the client and the server side class |  Major | hdfs-client | Haohui Mai | Haohui Mai |
| [HDFS-8248](https://issues.apache.org/jira/browse/HDFS-8248) | Store INodeId instead of the INodeFile object in BlockInfoContiguous |  Major | . | Haohui Mai | Haohui Mai |
| [HDFS-8238](https://issues.apache.org/jira/browse/HDFS-8238) | Move ClientProtocol to the hdfs-client |  Major | build | Haohui Mai | Takanobu Asanuma |
| [HDFS-8237](https://issues.apache.org/jira/browse/HDFS-8237) | Move all protocol classes used by ClientProtocol to hdfs-client |  Major | build | Haohui Mai | Haohui Mai |
| [HDFS-8218](https://issues.apache.org/jira/browse/HDFS-8218) | Move classes that used by ClientProtocol into hdfs-client |  Major | build | Haohui Mai | Haohui Mai |
| [HDFS-8192](https://issues.apache.org/jira/browse/HDFS-8192) | Eviction should key off used locked memory instead of ram disk free space |  Major | datanode | Arpit Agarwal | Arpit Agarwal |
| [HDFS-8185](https://issues.apache.org/jira/browse/HDFS-8185) | Separate client related routines in HAUtil into a new class |  Major | build, hdfs-client | Haohui Mai | Haohui Mai |
| [HDFS-8169](https://issues.apache.org/jira/browse/HDFS-8169) | Move LocatedBlocks and related classes to hdfs-client |  Major | build, hdfs-client | Haohui Mai | Haohui Mai |
| [HDFS-8165](https://issues.apache.org/jira/browse/HDFS-8165) | Move GRANDFATHER\_GENERATION\_STAMP and GRANDFATER\_INODE\_ID to hdfs-client |  Major | build | Haohui Mai | Haohui Mai |
| [HDFS-8157](https://issues.apache.org/jira/browse/HDFS-8157) | Writes to RAM DISK reserve locked memory for block files |  Major | datanode | Arpit Agarwal | Arpit Agarwal |
| [HDFS-8103](https://issues.apache.org/jira/browse/HDFS-8103) | Move BlockTokenSecretManager.AccessMode into BlockTokenIdentifier |  Minor | security | Haohui Mai | Haohui Mai |
| [HDFS-8102](https://issues.apache.org/jira/browse/HDFS-8102) | Separate webhdfs retry configuration keys from DFSConfigKeys |  Minor | hdfs-client | Haohui Mai | Haohui Mai |
| [HDFS-8100](https://issues.apache.org/jira/browse/HDFS-8100) | Refactor DFSClient.Conf to a standalone class |  Minor | hdfs-client | Tsz Wo Nicholas Sze | Tsz Wo Nicholas Sze |
| [HDFS-8089](https://issues.apache.org/jira/browse/HDFS-8089) | Move o.a.h.hdfs.web.resources.\* to the client jars |  Minor | build | Haohui Mai | Haohui Mai |
| [HDFS-8086](https://issues.apache.org/jira/browse/HDFS-8086) | Move LeaseRenewer to the hdfs.client.impl package |  Minor | hdfs-client | Tsz Wo Nicholas Sze | Takanobu Asanuma |
| [HDFS-8085](https://issues.apache.org/jira/browse/HDFS-8085) | Move CorruptFileBlockIterator to the hdfs.client.impl package |  Minor | hdfs-client | Tsz Wo Nicholas Sze | Tsz Wo Nicholas Sze |
| [HDFS-8084](https://issues.apache.org/jira/browse/HDFS-8084) | Separate the client failover conf from DFSConfigKeys |  Major | hdfs-client | Tsz Wo Nicholas Sze | Tsz Wo Nicholas Sze |
| [HDFS-8083](https://issues.apache.org/jira/browse/HDFS-8083) | Separate the client write conf from DFSConfigKeys |  Major | hdfs-client | Tsz Wo Nicholas Sze | Tsz Wo Nicholas Sze |
| [HDFS-8082](https://issues.apache.org/jira/browse/HDFS-8082) | Separate the client read conf from DFSConfigKeys |  Major | hdfs-client | Tsz Wo Nicholas Sze | Tsz Wo Nicholas Sze |
| [HDFS-8080](https://issues.apache.org/jira/browse/HDFS-8080) | Separate JSON related routines used by WebHdfsFileSystem to a package local class |  Minor | hdfs-client | Haohui Mai | Haohui Mai |
| [HDFS-8079](https://issues.apache.org/jira/browse/HDFS-8079) | Separate the client retry conf from DFSConfigKeys |  Major | hdfs-client | Tsz Wo Nicholas Sze | Tsz Wo Nicholas Sze |
| [HDFS-8053](https://issues.apache.org/jira/browse/HDFS-8053) | Move DFSIn/OutputStream and related classes to hadoop-hdfs-client |  Major | build | Haohui Mai | Mingliang Liu |
| [HDFS-8052](https://issues.apache.org/jira/browse/HDFS-8052) | Move WebHdfsFileSystem into hadoop-hdfs-client |  Major | build | Haohui Mai | Haohui Mai |
| [HDFS-8049](https://issues.apache.org/jira/browse/HDFS-8049) | Annotation client implementation as private |  Major | hdfs-client | Tsz Wo Nicholas Sze | Takuya Fukudome |
| [HDFS-8034](https://issues.apache.org/jira/browse/HDFS-8034) | Fix TestDFSClientRetries#testDFSClientConfigurationLocateFollowingBlockInitialDelay for Windows |  Minor | test | Xiaoyu Yao | Xiaoyu Yao |
| [HDFS-7995](https://issues.apache.org/jira/browse/HDFS-7995) | Implement chmod in the HDFS Web UI |  Major | . | Ravi Prakash | Ravi Prakash |
| [HDFS-7986](https://issues.apache.org/jira/browse/HDFS-7986) | Allow files / directories to be deleted from the NameNode UI |  Major | . | Ravi Prakash | Ravi Prakash |
| [HDFS-7923](https://issues.apache.org/jira/browse/HDFS-7923) | The DataNodes should rate-limit their full block reports by asking the NN on heartbeat messages |  Major | . | Colin Patrick McCabe | Colin Patrick McCabe |
| [HDFS-7893](https://issues.apache.org/jira/browse/HDFS-7893) | Update the POM to create a separate hdfs-client jar |  Major | build | Haohui Mai | Haohui Mai |
| [HDFS-7854](https://issues.apache.org/jira/browse/HDFS-7854) | Separate class DataStreamer out of DFSOutputStream |  Major | hdfs-client | Li Bo | Li Bo |
| [HDFS-7796](https://issues.apache.org/jira/browse/HDFS-7796) | Include X-editable for slick contenteditable fields in the web UI |  Major | . | Ravi Prakash | Ravi Prakash |
| [HDFS-7779](https://issues.apache.org/jira/browse/HDFS-7779) | Support changing ownership, group and replication in HDFS Web UI |  Major | . | Ravi Prakash | Ravi Prakash |
| [HDFS-7713](https://issues.apache.org/jira/browse/HDFS-7713) | Implement mkdirs in the HDFS Web UI |  Major | . | Ravi Prakash | Ravi Prakash |
| [HDFS-7701](https://issues.apache.org/jira/browse/HDFS-7701) | Support reporting per storage type quota and usage with hadoop/hdfs shell |  Major | datanode, namenode | Xiaoyu Yao | Peter Shi |
| [HDFS-7529](https://issues.apache.org/jira/browse/HDFS-7529) | Consolidate encryption zone related implementation into a single class |  Major | . | Haohui Mai | Rakesh R |
| [HDFS-7483](https://issues.apache.org/jira/browse/HDFS-7483) | Display information per tier on the Namenode UI |  Major | . | Benoy Antony | Benoy Antony |
| [HDFS-7390](https://issues.apache.org/jira/browse/HDFS-7390) | Provide JMX metrics per storage type |  Major | . | Benoy Antony | Benoy Antony |
| [HDFS-7192](https://issues.apache.org/jira/browse/HDFS-7192) | DN should ignore lazyPersist hint if the writer is not local |  Major | datanode | Arpit Agarwal | Arpit Agarwal |
| [HDFS-6249](https://issues.apache.org/jira/browse/HDFS-6249) | Output AclEntry in PBImageXmlWriter |  Minor | tools | Akira AJISAKA | Surendra Singh Lilhore |
| [MAPREDUCE-6394](https://issues.apache.org/jira/browse/MAPREDUCE-6394) | Speed up Task processing loop in HsTasksBlock#render() |  Major | jobhistoryserver | Ray Chiang | Ray Chiang |
| [MAPREDUCE-6376](https://issues.apache.org/jira/browse/MAPREDUCE-6376) | Add avro binary support for jhist files |  Major | jobhistoryserver | Ray Chiang | Ray Chiang |
| [YARN-4680](https://issues.apache.org/jira/browse/YARN-4680) | TimerTasks leak in ATS V1.5 Writer |  Major | timelineserver | Xuan Gong | Xuan Gong |
| [YARN-4643](https://issues.apache.org/jira/browse/YARN-4643) | Container recovery is broken with delegating container runtime |  Critical | yarn | Sidharta Seethana | Sidharta Seethana |
| [YARN-4614](https://issues.apache.org/jira/browse/YARN-4614) | TestApplicationPriority#testApplicationPriorityAllocationWithChangeInPriority fails occasionally |  Major | test | Jason Lowe | Sunil G |
| [YARN-4557](https://issues.apache.org/jira/browse/YARN-4557) | Fix improper Queues sorting in PartitionedQueueComparator when accessible-node-labels=\* |  Major | resourcemanager | Naganarasimha G R | Naganarasimha G R |
| [YARN-4537](https://issues.apache.org/jira/browse/YARN-4537) | Pull out priority comparison from fifocomparator and use compound comparator for FifoOrdering policy |  Major | capacity scheduler | Rohith Sharma K S | Rohith Sharma K S |
| [YARN-4479](https://issues.apache.org/jira/browse/YARN-4479) | Retrospect app-priority in pendingOrderingPolicy during recovering applications |  Major | api, resourcemanager | Rohith Sharma K S | Rohith Sharma K S |
| [YARN-4416](https://issues.apache.org/jira/browse/YARN-4416) | Deadlock due to synchronised get Methods in AbstractCSQueue |  Minor | capacity scheduler, resourcemanager | Naganarasimha G R | Naganarasimha G R |
| [YARN-4405](https://issues.apache.org/jira/browse/YARN-4405) | Support node label store in non-appendable file system |  Major | api, client, resourcemanager | Wangda Tan | Wangda Tan |
| [YARN-4384](https://issues.apache.org/jira/browse/YARN-4384) | updateNodeResource CLI should not accept negative values for resource |  Major | graceful, resourcemanager | Sushmitha Sreenivasan | Junping Du |
| [YARN-4358](https://issues.apache.org/jira/browse/YARN-4358) | Improve relationship between SharingPolicy and ReservationAgent |  Major | capacityscheduler, fairscheduler, resourcemanager | Carlo Curino | Carlo Curino |
| [YARN-4345](https://issues.apache.org/jira/browse/YARN-4345) | yarn rmadmin -updateNodeResource doesn't work |  Critical | graceful, resourcemanager | Sushmitha Sreenivasan | Junping Du |
| [YARN-4340](https://issues.apache.org/jira/browse/YARN-4340) | Add "list" API to reservation system |  Major | capacityscheduler, fairscheduler, resourcemanager | Carlo Curino | Sean Po |
| [YARN-4309](https://issues.apache.org/jira/browse/YARN-4309) | Add container launch related debug information to container logs when a container fails |  Major | nodemanager | Varun Vasudev | Varun Vasudev |
| [YARN-4304](https://issues.apache.org/jira/browse/YARN-4304) | AM max resource configuration per partition to be displayed/updated correctly in UI and in various partition related metrics |  Major | webapp | Sunil G | Sunil G |
| [YARN-4293](https://issues.apache.org/jira/browse/YARN-4293) | ResourceUtilization should be a part of yarn node CLI |  Major | . | Wangda Tan | Sunil G |
| [YARN-4292](https://issues.apache.org/jira/browse/YARN-4292) | ResourceUtilization should be a part of NodeInfo REST API |  Major | . | Wangda Tan | Sunil G |
| [YARN-4267](https://issues.apache.org/jira/browse/YARN-4267) | Add additional logging to container launch implementations in container-executor |  Major | yarn | Sidharta Seethana | Sidharta Seethana |
| [YARN-4265](https://issues.apache.org/jira/browse/YARN-4265) | Provide new timeline plugin storage to support fine-grained entity caching |  Major | timelineserver | Li Lu | Li Lu |
| [YARN-4262](https://issues.apache.org/jira/browse/YARN-4262) | Allow whitelisted users to run privileged docker containers. |  Major | yarn | Sidharta Seethana | Sidharta Seethana |
| [YARN-4258](https://issues.apache.org/jira/browse/YARN-4258) | Add support for controlling capabilities for docker containers |  Major | yarn | Sidharta Seethana | Sidharta Seethana |
| [YARN-4255](https://issues.apache.org/jira/browse/YARN-4255) | container-executor does not clean up docker operation command files. |  Minor | . | Sidharta Seethana | Sidharta Seethana |
| [YARN-4248](https://issues.apache.org/jira/browse/YARN-4248) | REST API for submit/update/delete Reservations |  Major | resourcemanager | Carlo Curino | Carlo Curino |
| [YARN-4243](https://issues.apache.org/jira/browse/YARN-4243) | Add retry on establishing Zookeeper conenction in EmbeddedElectorService#serviceInit |  Major | resourcemanager | Xuan Gong | Xuan Gong |
| [YARN-4234](https://issues.apache.org/jira/browse/YARN-4234) | New put APIs in TimelineClient for ats v1.5 |  Major | timelineserver | Xuan Gong | Xuan Gong |
| [YARN-4230](https://issues.apache.org/jira/browse/YARN-4230) | Increasing container resource while there is no headroom left will cause ResourceManager to crash |  Critical | resourcemanager | MENG DING | MENG DING |
| [YARN-4219](https://issues.apache.org/jira/browse/YARN-4219) | New levelDB cache storage for timeline v1.5 |  Major | . | Li Lu | Li Lu |
| [YARN-4215](https://issues.apache.org/jira/browse/YARN-4215) | RMNodeLabels Manager Need to verify and replace node labels for the only modified Node Label Mappings in the request |  Major | resourcemanager | Naganarasimha G R | Naganarasimha G R |
| [YARN-4184](https://issues.apache.org/jira/browse/YARN-4184) | Remove update reservation state api from state store as its not used by ReservationSystem |  Major | capacityscheduler, fairscheduler, resourcemanager | Anubhav Dhoot | Sean Po |
| [YARN-4171](https://issues.apache.org/jira/browse/YARN-4171) | Resolve findbugs/javac warnings in YARN-1197 branch |  Major | api, nodemanager, resourcemanager | Wangda Tan | Wangda Tan |
| [YARN-4170](https://issues.apache.org/jira/browse/YARN-4170) | AM need to be notified with priority in AllocateResponse |  Major | resourcemanager | Sunil G | Sunil G |
| [YARN-4164](https://issues.apache.org/jira/browse/YARN-4164) | Retrospect update ApplicationPriority API return type |  Major | resourcemanager | Rohith Sharma K S | Rohith Sharma K S |
| [YARN-4162](https://issues.apache.org/jira/browse/YARN-4162) | CapacityScheduler: Add resource usage by partition and queue capacity by partition to REST API |  Major | api, client, resourcemanager | Naganarasimha G R | Naganarasimha G R |
| [YARN-4141](https://issues.apache.org/jira/browse/YARN-4141) | Runtime Application Priority change should not throw exception for applications at finishing states |  Major | resourcemanager | Sunil G | Sunil G |
| [YARN-4140](https://issues.apache.org/jira/browse/YARN-4140) | RM container allocation delayed incase of app submitted to Nodelabel partition |  Major | scheduler | Bibin A Chundatt | Bibin A Chundatt |
| [YARN-4138](https://issues.apache.org/jira/browse/YARN-4138) | Roll back container resource allocation after resource increase token expires |  Major | api, nodemanager, resourcemanager | MENG DING | MENG DING |
| [YARN-4136](https://issues.apache.org/jira/browse/YARN-4136) | LinuxContainerExecutor loses info when forwarding ResourceHandlerException |  Trivial | nodemanager | Steve Loughran | Bibin A Chundatt |
| [YARN-4100](https://issues.apache.org/jira/browse/YARN-4100) | Add Documentation for Distributed and Delegated-Centralized Node Labels feature |  Major | api, client, resourcemanager | Naganarasimha G R | Naganarasimha G R |
| [YARN-4098](https://issues.apache.org/jira/browse/YARN-4098) | Document ApplicationPriority feature |  Major | resourcemanager | Rohith Sharma K S | Rohith Sharma K S |
| [YARN-4082](https://issues.apache.org/jira/browse/YARN-4082) | Container shouldn't be killed when node's label updated. |  Major | capacity scheduler | Wangda Tan | Wangda Tan |
| [YARN-4034](https://issues.apache.org/jira/browse/YARN-4034) | Render cluster Max Priority in scheduler metrics in RM web UI |  Minor | resourcemanager, webapp | Rohith Sharma K S | Rohith Sharma K S |
| [YARN-4023](https://issues.apache.org/jira/browse/YARN-4023) | Publish Application Priority to TimelineServer |  Major | timelineserver | Sunil G | Sunil G |
| [YARN-4014](https://issues.apache.org/jira/browse/YARN-4014) | Support user cli interface in for Application Priority |  Major | client, resourcemanager | Rohith Sharma K S | Rohith Sharma K S |
| [YARN-4004](https://issues.apache.org/jira/browse/YARN-4004) | container-executor should print output of docker logs if the docker container exits with non-0 exit status |  Major | nodemanager | Varun Vasudev | Varun Vasudev |
| [YARN-3985](https://issues.apache.org/jira/browse/YARN-3985) | Make ReservationSystem persist state using RMStateStore reservation APIs |  Major | resourcemanager | Anubhav Dhoot | Anubhav Dhoot |
| [YARN-3980](https://issues.apache.org/jira/browse/YARN-3980) | Plumb resource-utilization info in node heartbeat through to the scheduler |  Major | resourcemanager, scheduler | Karthik Kambatla | Inigo Goiri |
| [YARN-3974](https://issues.apache.org/jira/browse/YARN-3974) | Refactor the reservation system test cases to use parameterized base test |  Major | capacityscheduler, fairscheduler | Subru Krishnan | Subru Krishnan |
| [YARN-3970](https://issues.apache.org/jira/browse/YARN-3970) | REST api support for Application Priority |  Major | webapp | Sunil G | Naganarasimha G R |
| [YARN-3964](https://issues.apache.org/jira/browse/YARN-3964) | Support NodeLabelsProvider at Resource Manager side |  Major | . | Dian Fu | Dian Fu |
| [YARN-3948](https://issues.apache.org/jira/browse/YARN-3948) | Display Application Priority in RM Web UI |  Major | webapp | Sunil G | Sunil G |
| [YARN-3946](https://issues.apache.org/jira/browse/YARN-3946) | Update exact reason as to why a submitted app is in ACCEPTED state to app's diagnostic message |  Major | capacity scheduler, resourcemanager | Sumit Nigam | Naganarasimha G R |
| [YARN-3930](https://issues.apache.org/jira/browse/YARN-3930) | FileSystemNodeLabelsStore should make sure edit log file closed when exception is thrown |  Major | api, client, resourcemanager | Dian Fu | Dian Fu |
| [YARN-3887](https://issues.apache.org/jira/browse/YARN-3887) | Support for changing Application priority during runtime |  Major | capacityscheduler, resourcemanager | Sunil G | Sunil G |
| [YARN-3873](https://issues.apache.org/jira/browse/YARN-3873) | pendingApplications in LeafQueue should also use OrderingPolicy |  Major | capacityscheduler | Sunil G | Sunil G |
| [YARN-3868](https://issues.apache.org/jira/browse/YARN-3868) | ContainerManager recovery for container resizing |  Major | nodemanager | MENG DING | MENG DING |
| [YARN-3867](https://issues.apache.org/jira/browse/YARN-3867) | ContainerImpl changes to support container resizing |  Major | nodemanager | MENG DING | MENG DING |
| [YARN-3866](https://issues.apache.org/jira/browse/YARN-3866) | AM-RM protocol changes to support container resizing |  Major | api | MENG DING | MENG DING |
| [YARN-3853](https://issues.apache.org/jira/browse/YARN-3853) | Add docker container runtime support to LinuxContainterExecutor |  Major | yarn | Sidharta Seethana | Sidharta Seethana |
| [YARN-3852](https://issues.apache.org/jira/browse/YARN-3852) | Add docker container support to container-executor |  Major | yarn | Sidharta Seethana | Abin Shahab |
| [YARN-3844](https://issues.apache.org/jira/browse/YARN-3844) | Make hadoop-yarn-project Native code -Wall-clean |  Major | build | Alan Burlison | Alan Burlison |
| [YARN-3827](https://issues.apache.org/jira/browse/YARN-3827) | Migrate YARN native build to new CMake framework |  Major | build | Alan Burlison | Alan Burlison |
| [YARN-3800](https://issues.apache.org/jira/browse/YARN-3800) | Reduce storage footprint for ReservationAllocation |  Major | capacityscheduler, fairscheduler, resourcemanager | Anubhav Dhoot | Anubhav Dhoot |
| [YARN-3787](https://issues.apache.org/jira/browse/YARN-3787) | loading applications by filtering appstartedTime period for ATS Web UI |  Major | resourcemanager, webapp, yarn | Xuan Gong | Xuan Gong |
| [YARN-3766](https://issues.apache.org/jira/browse/YARN-3766) | ATS Web UI breaks because of YARN-3467 |  Blocker | resourcemanager, webapp, yarn | Xuan Gong | Xuan Gong |
| [YARN-3739](https://issues.apache.org/jira/browse/YARN-3739) | Add reservation system recovery to RM recovery process |  Major | capacityscheduler, fairscheduler, resourcemanager | Subru Krishnan | Subru Krishnan |
| [YARN-3738](https://issues.apache.org/jira/browse/YARN-3738) | Add support for recovery of reserved apps running under dynamic queues |  Major | capacityscheduler, resourcemanager | Subru Krishnan | Subru Krishnan |
| [YARN-3736](https://issues.apache.org/jira/browse/YARN-3736) | Add RMStateStore apis to store and load accepted reservations for failover |  Major | capacityscheduler, fairscheduler, resourcemanager | Subru Krishnan | Anubhav Dhoot |
| [YARN-3724](https://issues.apache.org/jira/browse/YARN-3724) | Use POSIX nftw(3) instead of fts(3) |  Major | . | Malcolm Kavalsky | Alan Burlison |
| [YARN-3717](https://issues.apache.org/jira/browse/YARN-3717) | Expose app/am/queue's node-label-expression to RM web UI / CLI / REST-API |  Major | . | Naganarasimha G R | Naganarasimha G R |
| [YARN-3716](https://issues.apache.org/jira/browse/YARN-3716) | Node-label-expression should be included by ResourceRequestPBImpl.toString |  Minor | api | Xianyin Xin | Xianyin Xin |
| [YARN-3684](https://issues.apache.org/jira/browse/YARN-3684) | Change ContainerExecutor's primary lifecycle methods to use a more extensible mechanism for passing information. |  Major | yarn | Sidharta Seethana | Sidharta Seethana |
| [YARN-3656](https://issues.apache.org/jira/browse/YARN-3656) | LowCost: A Cost-Based Placement Agent for YARN Reservations |  Major | capacityscheduler, resourcemanager | Ishai Menache | Jonathan Yaniv |
| [YARN-3647](https://issues.apache.org/jira/browse/YARN-3647) | RMWebServices api's should use updated api from CommonNodeLabelsManager to get NodeLabel object |  Major | resourcemanager | Sunil G | Sunil G |
| [YARN-3635](https://issues.apache.org/jira/browse/YARN-3635) | Get-queue-mapping should be a common interface of YarnScheduler |  Major | scheduler | Wangda Tan | Tan, Wangda |
| [YARN-3632](https://issues.apache.org/jira/browse/YARN-3632) | Ordering policy should be allowed to reorder an application when demand changes |  Major | capacityscheduler | Craig Welch | Craig Welch |
| [YARN-3593](https://issues.apache.org/jira/browse/YARN-3593) | Add label-type and Improve "DEFAULT\_PARTITION" in Node Labels Page |  Major | webapp | Naganarasimha G R | Naganarasimha G R |
| [YARN-3583](https://issues.apache.org/jira/browse/YARN-3583) | Support of NodeLabel object instead of plain String in YarnClient side. |  Major | client | Sunil G | Sunil G |
| [YARN-3581](https://issues.apache.org/jira/browse/YARN-3581) | Deprecate -directlyAccessNodeLabelStore in RMAdminCLI |  Major | api, client, resourcemanager | Wangda Tan | Naganarasimha G R |
| [YARN-3579](https://issues.apache.org/jira/browse/YARN-3579) | CommonNodeLabelsManager should support NodeLabel instead of string label name when getting node-to-label/label-to-label mappings |  Minor | resourcemanager | Sunil G | Sunil G |
| [YARN-3565](https://issues.apache.org/jira/browse/YARN-3565) | NodeHeartbeatRequest/RegisterNodeManagerRequest should use NodeLabel object instead of String |  Blocker | api, client, resourcemanager | Wangda Tan | Naganarasimha G R |
| [YARN-3543](https://issues.apache.org/jira/browse/YARN-3543) | ApplicationReport should be able to tell whether the Application is AM managed or not. |  Major | api | Spandan Dutta | Rohith Sharma K S |
| [YARN-3541](https://issues.apache.org/jira/browse/YARN-3541) | Add version info on timeline service / generic history web UI and REST API |  Major | timelineserver | Zhijie Shen | Zhijie Shen |
| [YARN-3534](https://issues.apache.org/jira/browse/YARN-3534) | Collect memory/cpu usage on the node |  Major | nodemanager, resourcemanager | Inigo Goiri | Inigo Goiri |
| [YARN-3521](https://issues.apache.org/jira/browse/YARN-3521) | Support return structured NodeLabel objects in REST API |  Major | api, client, resourcemanager | Wangda Tan | Sunil G |
| [YARN-3505](https://issues.apache.org/jira/browse/YARN-3505) | Node's Log Aggregation Report with SUCCEED should not cached in RMApps |  Critical | log-aggregation | Junping Du | Xuan Gong |
| [YARN-3463](https://issues.apache.org/jira/browse/YARN-3463) | Integrate OrderingPolicy Framework with CapacityScheduler |  Major | capacityscheduler | Craig Welch | Craig Welch |
| [YARN-3454](https://issues.apache.org/jira/browse/YARN-3454) | Add efficient merge operation to RLESparseResourceAllocation |  Major | resourcemanager | Carlo Curino | Carlo Curino |
| [YARN-3448](https://issues.apache.org/jira/browse/YARN-3448) | Add Rolling Time To Lives Level DB Plugin Capabilities |  Major | timelineserver | Jonathan Eagles | Jonathan Eagles |
| [YARN-3445](https://issues.apache.org/jira/browse/YARN-3445) | Cache runningApps in RMNode for getting running apps on given NodeId |  Major | nodemanager, resourcemanager | Junping Du | Junping Du |
| [YARN-3443](https://issues.apache.org/jira/browse/YARN-3443) | Create a 'ResourceHandler' subsystem to ease addition of support for new resource types on the NM |  Major | nodemanager | Sidharta Seethana | Sidharta Seethana |
| [YARN-3413](https://issues.apache.org/jira/browse/YARN-3413) | Node label attributes (like exclusivity) should settable via addToClusterNodeLabels but shouldn't be changeable at runtime |  Major | api, client, resourcemanager | Wangda Tan | Wangda Tan |
| [YARN-3366](https://issues.apache.org/jira/browse/YARN-3366) | Outbound network bandwidth : classify/shape traffic originating from YARN containers |  Major | . | Sidharta Seethana | Sidharta Seethana |
| [YARN-3365](https://issues.apache.org/jira/browse/YARN-3365) | Add support for using the 'tc' tool via container-executor |  Major | nodemanager | Sidharta Seethana | Sidharta Seethana |
| [YARN-3362](https://issues.apache.org/jira/browse/YARN-3362) | Add node label usage in RM CapacityScheduler web UI |  Major | capacityscheduler, resourcemanager, webapp | Wangda Tan | Naganarasimha G R |
| [YARN-3361](https://issues.apache.org/jira/browse/YARN-3361) | CapacityScheduler side changes to support non-exclusive node labels |  Major | capacityscheduler | Wangda Tan | Wangda Tan |
| [YARN-3356](https://issues.apache.org/jira/browse/YARN-3356) | Capacity Scheduler FiCaSchedulerApp should use ResourceUsage to track used-resources-by-label. |  Major | capacityscheduler, resourcemanager | Wangda Tan | Wangda Tan |
| [YARN-3354](https://issues.apache.org/jira/browse/YARN-3354) | Container should contains node-labels asked by original ResourceRequests |  Major | api, capacityscheduler, nodemanager, resourcemanager | Wangda Tan | Wangda Tan |
| [YARN-3347](https://issues.apache.org/jira/browse/YARN-3347) | Improve YARN log command to get AMContainer logs as well as running containers logs |  Major | log-aggregation | Xuan Gong | Xuan Gong |
| [YARN-3345](https://issues.apache.org/jira/browse/YARN-3345) | Add non-exclusive node label API to RMAdmin protocol and NodeLabelsManager |  Major | api, client, resourcemanager | Wangda Tan | Wangda Tan |
| [YARN-3326](https://issues.apache.org/jira/browse/YARN-3326) | Support RESTful API for getLabelsToNodes |  Minor | resourcemanager | Naganarasimha G R | Naganarasimha G R |
| [YARN-3319](https://issues.apache.org/jira/browse/YARN-3319) | Implement a FairOrderingPolicy |  Major | scheduler | Craig Welch | Craig Welch |
| [YARN-3318](https://issues.apache.org/jira/browse/YARN-3318) | Create Initial OrderingPolicy Framework and FifoOrderingPolicy |  Major | scheduler | Craig Welch | Craig Welch |
| [YARN-3250](https://issues.apache.org/jira/browse/YARN-3250) | Support admin cli interface in for Application Priority |  Major | resourcemanager | Sunil G | Rohith Sharma K S |
| [YARN-3226](https://issues.apache.org/jira/browse/YARN-3226) | UI changes for decommissioning node |  Major | graceful | Junping Du | Sunil G |
| [YARN-3225](https://issues.apache.org/jira/browse/YARN-3225) | New parameter or CLI for decommissioning node gracefully in RMAdmin CLI |  Major | graceful | Junping Du | Devaraj K |
| [YARN-3223](https://issues.apache.org/jira/browse/YARN-3223) | Resource update during NM graceful decommission |  Major | graceful, nodemanager, resourcemanager | Junping Du | Brook Zhou |
| [YARN-3216](https://issues.apache.org/jira/browse/YARN-3216) | Max-AM-Resource-Percentage should respect node labels |  Critical | resourcemanager | Wangda Tan | Sunil G |
| [YARN-3212](https://issues.apache.org/jira/browse/YARN-3212) | RMNode State Transition Update with DECOMMISSIONING state |  Major | graceful, resourcemanager | Junping Du | Junping Du |
| [YARN-3116](https://issues.apache.org/jira/browse/YARN-3116) | [Collector wireup] We need an assured way to determine if a container is an AM container on NM |  Major | nodemanager, timelineserver | Zhijie Shen | Giovanni Matteo Fumarola |
| [YARN-3110](https://issues.apache.org/jira/browse/YARN-3110) | Few issues in ApplicationHistory web ui |  Minor | applications, timelineserver | Bibin A Chundatt | Naganarasimha G R |
| [YARN-3006](https://issues.apache.org/jira/browse/YARN-3006) | Improve the error message when attempting manual failover with auto-failover enabled |  Minor | . | Akira AJISAKA | Akira AJISAKA |
| [YARN-2923](https://issues.apache.org/jira/browse/YARN-2923) | Support configuration based NodeLabelsProvider Service in Distributed Node Label Configuration Setup |  Major | nodemanager | Naganarasimha G R | Naganarasimha G R |
| [YARN-2918](https://issues.apache.org/jira/browse/YARN-2918) | Don't fail RM if queue's configured labels are not existed in cluster-node-labels |  Major | resourcemanager | Rohith Sharma K S | Wangda Tan |
| [YARN-2884](https://issues.apache.org/jira/browse/YARN-2884) | Proxying all AM-RM communications |  Major | nodemanager, resourcemanager | Carlo Curino | Kishore Chaliparambil |
| [YARN-2740](https://issues.apache.org/jira/browse/YARN-2740) | Fix NodeLabelsManager to properly handle node label modifications when distributed node label configuration enabled |  Major | resourcemanager | Wangda Tan | Naganarasimha G R |
| [YARN-2729](https://issues.apache.org/jira/browse/YARN-2729) | Support script based NodeLabelsProvider Interface in Distributed Node Label Configuration Setup |  Major | nodemanager | Naganarasimha G R | Naganarasimha G R |
| [YARN-2696](https://issues.apache.org/jira/browse/YARN-2696) | Queue sorting in CapacityScheduler should consider node label |  Major | capacityscheduler, resourcemanager | Wangda Tan | Wangda Tan |
| [YARN-2619](https://issues.apache.org/jira/browse/YARN-2619) | NodeManager: Add cgroups support for disk I/O isolation |  Major | . | Wei Yan | Varun Vasudev |
| [YARN-2575](https://issues.apache.org/jira/browse/YARN-2575) | Create separate ACLs for Reservation create/update/delete/list ops |  Major | capacityscheduler, fairscheduler, resourcemanager | Subru Krishnan | Sean Po |
| [YARN-2556](https://issues.apache.org/jira/browse/YARN-2556) | Tool to measure the performance of the timeline server |  Major | timelineserver | Jonathan Eagles | Chang Li |
| [YARN-2498](https://issues.apache.org/jira/browse/YARN-2498) | Respect labels in preemption policy of capacity scheduler for inter-queue preemption |  Major | resourcemanager | Wangda Tan | Wangda Tan |
| [YARN-2495](https://issues.apache.org/jira/browse/YARN-2495) | Allow admin specify labels from each NM (Distributed configuration) |  Major | resourcemanager | Wangda Tan | Naganarasimha G R |
| [YARN-2392](https://issues.apache.org/jira/browse/YARN-2392) | add more diags about app retry limits on AM failures |  Minor | resourcemanager | Steve Loughran | Steve Loughran |
| [YARN-2331](https://issues.apache.org/jira/browse/YARN-2331) | Distinguish shutdown during supervision vs. shutdown for rolling upgrade |  Major | nodemanager | Jason Lowe | Jason Lowe |
| [YARN-2003](https://issues.apache.org/jira/browse/YARN-2003) | Support for Application priority : Changes in RM and Capacity Scheduler |  Major | resourcemanager | Sunil G | Sunil G |
| [YARN-1897](https://issues.apache.org/jira/browse/YARN-1897) | CLI and core support for signal container functionality |  Major | api | Ming Ma | Ming Ma |
| [YARN-1651](https://issues.apache.org/jira/browse/YARN-1651) | CapacityScheduler side changes to support increase/decrease container resource. |  Major | resourcemanager, scheduler | Wangda Tan | Wangda Tan |
| [YARN-1645](https://issues.apache.org/jira/browse/YARN-1645) | ContainerManager implementation to support container resizing |  Major | nodemanager | Wangda Tan | MENG DING |
| [YARN-1644](https://issues.apache.org/jira/browse/YARN-1644) | RM-NM protocol changes and NodeStatusUpdater implementation to support container resizing |  Major | nodemanager | Wangda Tan | MENG DING |
| [YARN-1643](https://issues.apache.org/jira/browse/YARN-1643) | Make ContainersMonitor can support change monitoring size of an allocated container in NM side |  Major | nodemanager | Wangda Tan | MENG DING |
| [YARN-1510](https://issues.apache.org/jira/browse/YARN-1510) | Make NMClient support change container resources |  Major | nodemanager | Wangda Tan (No longer used) | MENG DING |
| [YARN-1509](https://issues.apache.org/jira/browse/YARN-1509) | Make AMRMClient support send increase container request and get increased/decreased containers |  Major | resourcemanager | Wangda Tan (No longer used) | MENG DING |
| [YARN-1462](https://issues.apache.org/jira/browse/YARN-1462) | AHS API and other AHS changes to handle tags for completed MR jobs |  Major | . | Karthik Kambatla | Xuan Gong |
| [YARN-1449](https://issues.apache.org/jira/browse/YARN-1449) | AM-NM protocol changes to support container resizing |  Major | api | Wangda Tan (No longer used) | MENG DING |
| [YARN-1402](https://issues.apache.org/jira/browse/YARN-1402) | Related Web UI, CLI changes on exposing client API to check log aggregation status |  Major | . | Xuan Gong | Xuan Gong |
| [YARN-1376](https://issues.apache.org/jira/browse/YARN-1376) | NM need to notify the log aggregation status to RM through Node heartbeat |  Major | . | Xuan Gong | Xuan Gong |
| [YARN-1279](https://issues.apache.org/jira/browse/YARN-1279) | Expose a client API to allow clients to figure if log aggregation is complete |  Major | . | Arun C Murthy | Xuan Gong |
| [YARN-1012](https://issues.apache.org/jira/browse/YARN-1012) | Report NM aggregated container resource utilization in heartbeat |  Major | nodemanager | Arun C Murthy | Inigo Goiri |
| [YARN-644](https://issues.apache.org/jira/browse/YARN-644) | Basic null check is not performed on passed in arguments before using them in ContainerManagerImpl.startContainer |  Minor | nodemanager | Omkar Vinit Joshi | Varun Saxena |
| [YARN-433](https://issues.apache.org/jira/browse/YARN-433) | When RM is catching up with node updates then it should not expire acquired containers |  Major | resourcemanager | Bikas Saha | Xuan Gong |
| [YARN-313](https://issues.apache.org/jira/browse/YARN-313) | Add Admin API for supporting node resource configuration in command line |  Critical | client, graceful | Junping Du | Inigo Goiri |
| [YARN-221](https://issues.apache.org/jira/browse/YARN-221) | NM should provide a way for AM to tell it not to aggregate logs. |  Major | log-aggregation, nodemanager | Robert Joseph Evans | Ming Ma |


### OTHER:

| JIRA | Summary | Priority | Component | Reporter | Contributor |
|:---- |:---- | :--- |:---- |:---- |:---- |
| [HADOOP-12567](https://issues.apache.org/jira/browse/HADOOP-12567) | NPE in SaslRpcServer |  Major | . | Sergey Shelukhin | Sergey Shelukhin |
| [HADOOP-12514](https://issues.apache.org/jira/browse/HADOOP-12514) | Make static fields in GenericTestUtils for assertExceptionContains() package-private and final |  Minor | test | Mingliang Liu | Mingliang Liu |
| [HADOOP-12446](https://issues.apache.org/jira/browse/HADOOP-12446) | Undeprecate createNonRecursive() |  Major | . | Ted Yu | Ted Yu |
| [HADOOP-11814](https://issues.apache.org/jira/browse/HADOOP-11814) | Reformat hadoop-annotations, o.a.h.classification.tools |  Minor | . | Li Lu | Li Lu |
| [HDFS-9377](https://issues.apache.org/jira/browse/HDFS-9377) | Fix findbugs warnings in FSDirSnapshotOp |  Major | namenode | Mingliang Liu | Mingliang Liu |
| [HDFS-9343](https://issues.apache.org/jira/browse/HDFS-9343) | Empty caller context considered invalid |  Major | . | Mingliang Liu | Mingliang Liu |
| [HDFS-9184](https://issues.apache.org/jira/browse/HDFS-9184) | Logging HDFS operation's caller context into audit logs |  Major | . | Mingliang Liu | Mingliang Liu |
| [HDFS-9130](https://issues.apache.org/jira/browse/HDFS-9130) | Use GenericTestUtils#setLogLevel to the logging level |  Major | . | Mingliang Liu | Mingliang Liu |
| [HDFS-9027](https://issues.apache.org/jira/browse/HDFS-9027) | Refactor o.a.h.hdfs.DataStreamer#isLazyPersist() method |  Major | . | Mingliang Liu | Mingliang Liu |
| [HDFS-8979](https://issues.apache.org/jira/browse/HDFS-8979) | Clean up checkstyle warnings in hadoop-hdfs-client module |  Major | . | Mingliang Liu | Mingliang Liu |
| [HDFS-8938](https://issues.apache.org/jira/browse/HDFS-8938) | Extract BlockToMarkCorrupt and ReplicationWork as standalone classes from BlockManager |  Major | . | Mingliang Liu | Mingliang Liu |
| [MAPREDUCE-6483](https://issues.apache.org/jira/browse/MAPREDUCE-6483) | Replace deprecated method NameNode.getUri() with DFSUtilClient.getNNUri() in TestMRCredentials |  Major | test | Mingliang Liu | Mingliang Liu |
| [MAPREDUCE-6477](https://issues.apache.org/jira/browse/MAPREDUCE-6477) | Replace usage of deprecated NameNode.DEFAULT\_PORT in TestFileSystem |  Major | . | Mingliang Liu | Mingliang Liu |
| [MAPREDUCE-6388](https://issues.apache.org/jira/browse/MAPREDUCE-6388) | Remove deprecation warnings from JobHistoryServer classes |  Minor | jobhistoryserver | Ray Chiang | Ray Chiang |
| [YARN-3357](https://issues.apache.org/jira/browse/YARN-3357) | Move TestFifoScheduler to FIFO package |  Major | scheduler, test | Rohith Sharma K S | Rohith Sharma K S |
| [YARN-3026](https://issues.apache.org/jira/browse/YARN-3026) | Move application-specific container allocation logic from LeafQueue to FiCaSchedulerApp |  Major | capacityscheduler | Wangda Tan | Wangda Tan |


