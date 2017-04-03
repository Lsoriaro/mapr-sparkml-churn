
This is an example using Spark Machine Learning decision trees , written in Scala, 
to demonstrate How to get started with Spark ML on a MapR sandbox 

Install and fire up the Sandbox using the instructions here: http://maprdocs.mapr.com/home/SandboxHadoop/c_sandbox_overview.html. 

Use an SSH client such as Putty (Windows) or Terminal (Mac) to login. See below for an example:
use userid: user01 and password: mapr.

For VMWare use:  $ ssh user01@ipaddress 

For Virtualbox use:  $ ssh user01@127.0.0.1 -p 2222 

You can build this project with Maven using IDEs like Eclipse or NetBeans, and then copy the JAR file to your MapR Sandbox, or you can install Maven on your sandbox and build from the Linux command line, 
for more information on maven, eclipse or netbeans use google search. 

After building the project on your laptop, you can use scp to copy your JAR file from the project target folder to the MapR Sandbox:

use userid: user01 and password: mapr.
For VMWare use:  $ scp  nameoffile.jar  user01@ipaddress:/user/user01/. 

For Virtualbox use:  $ scp -P 2222 nameoffile.jar  user01@127.0.0.1:/user/user01/.  

Copy the data files from the project data folder to the sandbox using scp to this directory /user/user01/data/uber.csv on the sandbox:
churn-bigml-20.csv 
churn-bigml-80.csv 

from the project data folder: 
For VMWare use:  $ scp  *.csv user01@ipaddress:/user/user01/.
For Virtualbox use:  $ scp -P 2222 *.csv  user01@127.0.0.1:/user/user01/data/. 

This example runs on MapR 5.2 with Spark 2.0.1 . If running on the sandbox you need to upgrade to MEP 2.0,  Spark  2.0.1 
http://maprdocs.mapr.com/home/UpgradeGuide/UpgradingEcoPacks.html
http://maprdocs.mapr.com/home/Spark/Spark_IntegrateMapRStreams.html



You can run these examples in the spark shell by copy pasthing  the code from the scala file in the spark shell after launching:
 
$spark-shell --master local[2]


Or you can run the applications with these steps:

Step 1: First compile the project: Select project  -> Run As -> Maven Install

Step 2: Copy the spark-ml-churn-1.0.jar and data to the sandbox 

To run the  standalone :

spark-submit --class example.Churn --master local[2] spark-ml-churn-1.0.jar



