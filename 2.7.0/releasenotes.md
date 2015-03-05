# Hadoop  2.7.0 Release Notes

These release notes cover  new developer and user-facing incompatibilities, features, and major improvements.

## Changes since Hadoop 2.6.1

---

* [YARN-2230](https://issues.apache.org/jira/browse/YARN-2230) | Minor | Fix description of yarn.scheduler.maximum-allocation-vcores in yarn-default.xml (or code)

I have modified the description of the yarn.scheduler.maximum-allocation-vcores setting in yarn-default.xml to be reflective of the actual behavior (throw InvalidRequestException when the limit is crossed).

Since this is a documentation change, I have not added any test cases.

Please review the patch, thanks!

---

* [YARN-1904](https://issues.apache.org/jira/browse/YARN-1904) | Major | Uniform the XXXXNotFound messages from ClientRMService and ApplicationHistoryClientService

I just committed this. Thanks Zhijie!

---

* [HDFS-7806](https://issues.apache.org/jira/browse/HDFS-7806) | Minor | Refactor: move StorageType from hadoop-hdfs to hadoop-common

This fix moves the public class StorageType from the package org.apache.hadoop.hdfs to org.apache.hadoop.fs.

---

* [HDFS-7774](https://issues.apache.org/jira/browse/HDFS-7774) | Critical | Unresolved symbols error while compiling HDFS on Windows 7/32 bit

LibHDFS now supports 32-bit build targets on Windows.

---

* [HDFS-7584](https://issues.apache.org/jira/browse/HDFS-7584) | Major | Enable Quota Support for Storage Types

1. Introduced quota by storage type as a hard limit on the amount of space usage allowed for different storage types (SSD, DISK, ARCHIVE) under the target directory.
2. Added {{SetQuotaByStorageType}} API and {{-storagetype}} option for  {{hdfs dfsadmin -setSpaceQuota/-clrSpaceQuota}} commands to allow set/clear quota by storage type under the target directory.


---

* [HDFS-7457](https://issues.apache.org/jira/browse/HDFS-7457) | Major | DatanodeID generates excessive garbage

Thanks for the reviews, gentlemen. I've committed this to trunk and branch-2. Thanks for identifying and working on the issue, Daryn.

---

* [HDFS-7326](https://issues.apache.org/jira/browse/HDFS-7326) | Minor | Add documentation for hdfs debug commands

Added documentation for the hdfs debug commands to the following URL in the documentation website.

hadoop-project-dist/hadoop-hdfs/HDFSCommands.html

In order to view the new documentation, build the website in a staging area:
$ mvn clean site; mvn site:stage -DstagingDirectory=/tmp/hadoop-site

Point your browser to 
file:///tmp/hadoop-site/hadoop-project/hadoop-project-dist/hadoop-hdfs/HDFSCommands.html


---

* [HDFS-6651](https://issues.apache.org/jira/browse/HDFS-6651) | Critical | Deletion failure can leak inodes permanently

No release note provided for this incompatible change.

---

* [HDFS-6252](https://issues.apache.org/jira/browse/HDFS-6252) | Minor | Phase out the old web UI in HDFS

No release note provided for this incompatible change.

---

* [HDFS-6133](https://issues.apache.org/jira/browse/HDFS-6133) | Major | Make Balancer support exclude specified path

Add a feature for replica pinning so that when a replica is pinned in a datanode, it will not be moved by Balancer/Mover.  The replica pinning feature can be enabled/disabled by "dfs.datanode.block-pinning.enabled", where the default is false.

---

* [HDFS-3689](https://issues.apache.org/jira/browse/HDFS-3689) | Major | Add support for variable length block

1. HDFS now can choose to append data to a new block instead of end of the last partial block. Users can pass {{CreateFlag.APPEND}} and  {{CreateFlag.NEW\_BLOCK}} to the {{append}} API to indicate this requirement.
2. HDFS now allows users to pass {{SyncFlag.END\_BLOCK}} to the {{hsync}} API to finish the current block and write remaining data to a new block.

---

* [HDFS-1522](https://issues.apache.org/jira/browse/HDFS-1522) | Major | Merge Block.BLOCK\_FILE\_PREFIX and DataStorage.BLOCK\_FILE\_PREFIX into one constant

This merges Block.BLOCK\_FILE\_PREFIX and DataStorage.BLOCK\_FILE\_PREFIX into one constant. Hard-coded
literals of "blk\_" in various files are also updated to use the same constant. 

---

* [HDFS-1362](https://issues.apache.org/jira/browse/HDFS-1362) | Major | Provide volume management functionality for DataNode

Based on the reconfiguration framework provided by HADOOP-7001, enable reconfigure the dfs.datanode.data.dir and add new volumes into service.

---

* [HADOOP-11498](https://issues.apache.org/jira/browse/HADOOP-11498) | Major | Bump the version of HTrace to 3.1.0-incubating

No release note provided for this incompatible change.

---

* [HADOOP-11497](https://issues.apache.org/jira/browse/HADOOP-11497) | Major | Fix typo in ClusterSetup.html#Hadoop\_Startup

Correct startup command for cluster data nodes

---

* [HADOOP-11464](https://issues.apache.org/jira/browse/HADOOP-11464) | Major | Reinstate support for launching Hadoop processes on Windows using Cygwin.

We have reinstated support for launching Hadoop processes on Windows by using Cygwin to run the shell scripts.  All processes still must have access to the native components: hadoop.dll and winutils.exe.

---

* [HADOOP-11446](https://issues.apache.org/jira/browse/HADOOP-11446) | Major | S3AOutputStream should use shared thread pool to avoid OutOfMemoryError

The following parameters are introduced in this JIRA:
fs.s3a.threads.max:    the maximum number of threads to allow in the pool used by TransferManager
fs.s3a.threads.core:    the number of threads to keep in the pool used by TransferManager
fs.s3a.threads.keepalivetime:  when the number of threads is greater than the core, this is the maximum time that excess idle threads will wait for new tasks before terminating
fs.s3a.max.total.tasks:    the maximum number of tasks that the LinkedBlockingQueue can hold

---

* [HADOOP-11385](https://issues.apache.org/jira/browse/HADOOP-11385) | Critical | Prevent cross site scripting attack on JMXJSONServlet

No release note provided for this incompatible change.

---

* [HADOOP-11348](https://issues.apache.org/jira/browse/HADOOP-11348) | Minor | Remove unused variable from CMake error message for finding openssl

Test failure is unrelated.  Committed to 2.7.  Thanks, Dian.

---

* [HADOOP-11311](https://issues.apache.org/jira/browse/HADOOP-11311) | Major | Restrict uppercase key names from being created with JCEKS

Keys with uppercase names can no longer be created when using the JavaKeyStoreProvider to resolve ambiguity about case-sensitivity in the KeyStore spec.

---

* [HADOOP-10530](https://issues.apache.org/jira/browse/HADOOP-10530) | Blocker | Make hadoop trunk build on Java7+ only

No release note provided for this incompatible change.

---

* [HADOOP-10181](https://issues.apache.org/jira/browse/HADOOP-10181) | Minor | GangliaContext does not work with multicast ganglia setup

Hadoop metrics sent to Ganglia over multicast now support optional configuration of socket TTL.  The default TTL is 1, which preserves the behavior of prior Hadoop versions.  Clusters that span multiple subnets/VLANs will likely want to increase this.

---

* [HADOOP-9922](https://issues.apache.org/jira/browse/HADOOP-9922) | Major | hadoop windows native build will fail in 32 bit machine

The Hadoop Common native components now support 32-bit build targets on Windows.

---

* [HADOOP-9629](https://issues.apache.org/jira/browse/HADOOP-9629) | Major | Support Windows Azure Storage - Blob as a file system in Hadoop

Hadoop now supports integration with Azure Storage as an alternative Hadoop Compatible File System.

---

* [HADOOP-8989](https://issues.apache.org/jira/browse/HADOOP-8989) | Major | hadoop fs -find feature

New fs -find command


