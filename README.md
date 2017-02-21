# 3.4


Q1. Explain the importance of Namenode in Hadoop cluster

Q2. Practice the beginners commands for HDFS from the below link



Q1.the importance of Namenode in Hadoop cluster :

NameNode:

NameNode does NOT store the files but only the file's metadata. 
NameNode oversees the health of DataNode and coordinates access to the data stored in DataNode. 
Name node keeps track of all the file system related information such as to
1.Which section of file is saved in which part of the cluster
2.Last access time for the files
3.User permissions like which user have access to the file

The NameNode is the centerpiece of an HDFS file system. It keeps the directory tree of all files in the file system, and tracks where across the cluster the file data is kept. It does not store the data of these files itself.

Client applications talk to the NameNode whenever they wish to locate a file, or when they want to add/copy/move/delete a file. The NameNode responds the successful requests by returning a list of relevant DataNode servers where the data lives.

The NameNode is a Single Point of Failure for the HDFS Cluster. HDFS is not currently a High Availability system. When the NameNode goes down, the file system goes offline. There is an optional SecondaryNameNode that can be hosted on a separate machine. It only creates checkpoints of the namespace by merging the edits file into the fsimage file and does not provide any real redundancy. Hadoop 0.21+ has a BackupNameNode that is part of a plan to have an HA name service, but it needs active contributions from the people who want it (i.e. you) to make it Highly Available.

It is essential to look after the NameNode. Here are some recommendations from production use

Use a good server with lots of RAM. The more RAM you have, the bigger the file system, or the smaller the block size.
Use ECC RAM.
On Java6u15 or later, run the server VM with compressed pointers -XX:+UseCompressedOops to cut the JVM heap size down.
List more than one name node directory in the configuration, so that multiple copies of the file system meta-data will be stored. As long as the directories are on separate disks, a single disk failure will not corrupt the meta-data.
Configure the NameNode to store one set of transaction logs on a separate disk from the image.
Configure the NameNode to store another set of transaction logs to a network mounted disk.
Monitor the disk space available to the NameNode. If free space is getting low, add more storage.
Do not host DataNode, JobTracker or TaskTracker services on the same system.




Q2.beginners commands for HDFS : 

1.Put Command

The ‘put’command feeds the data in to the HDFS.

Syntax: hadoop dfs –put </source path> </destination path>

2.List Command

The ‘list’command displays all the available files inside a particular path.

Syntax: hadoop dfs –ls </source path>

3.Get Command

The ‘get’ command copies the entire contents of the mentioned file to the local drive.

Syntax: hadoop dfs –get </source path> </destination path>

4.Make Directory Command

The ‘mkdir’ command creates a new directory in the specified location.

Syntax: hadoop dfs –mkdir </source path>

5.View contents of particular file

The ‘cat’ command is used to display all the contents of a file.

Syntax: hadoop dfs –cat </path[filename]>

6.Duplicating a Complete File inside the HDFS.

The ‘copyfromlocal’ command will copy file from the local file system to the HDFS.

Syntax: hadoop dfs –copyFromLocal </source path> </destination path>

7.Duplicating a File from HDFS to the Local File System.

The ‘copytolocal’ command will copy files from the HDFS to the local file system.

Syntax: hadoop dfs –copyToLocal </source path> </destination path>

8.Removing the File

The command ‘rm’ will delete the file stored inside the HDFS.

Syntax: hadoop dfs –rm </path[filename]>

9.Run a DFS Filesystem to Check Utility

The command ‘fsck’ is used for checking the consistency of a file system

Syntax: hadoop fsck </file path>

10.Run a Cluster Balancing Utility

The command ‘balancer’ will check for work load on nodes in cluster and balance it.

Syntax: hadoop balancer

11.Check Directory Space in HDFS

The command will show the file size occupied by file inside cluster.

Syntax: hadoop dfs -du -s -h </file path>

12.List all the Hadoop File System Shell Commands

The ‘fs’ command lists down all the shell commands of the Hadoop File System.

Syntax: hadoop fs [options]

13.Asking for Help

The ‘help’ command is for asking for help or querying a particular question.

Command: hadoop fs -help
