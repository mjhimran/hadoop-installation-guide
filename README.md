# Hadoop-installation-guide
At First we have to Download "Necessary Files for Hadoop" from this repository.
*Oracle [Java](https://www.oracle.com/apac/java/technologies/javase/javase8-archive-downloads.html#license-lightbox)* and 
need to create an account to download the software. or download from this repository.
Then install it on location "C:\Java\jdk" or after default installation move the "jdk-1.8" folder to "C:\Java" and reaname the it "jdk-1.8" to "jdk".
After changing these stuff go to *Environmental Variable* and add "JAVA_HOME" with variable value: "C:\Java\jdk\bin" at "User Variables" and 
Edit "System Variable" also add the location "C:\Java\jdk\bin" then press OK.
# Open CMD on your search bar. Then hit Enter. Check the java version by "java -version" command.

After succesfully installing the Java, 
Download [*Hadoop*](https://dlcdn.apache.org/hadoop/common/hadoop-3.4.0/hadoop-3.4.0.tar.gz) and extract it, and 
Rename the folder "hadoop-3.4.0" as "hadoop". Then delete the "bin" folder from the "hadoop" folder. 
Download the "bin" and "data" folder from this github repository, extract it and paste in the "hadoop" folder.
After that copy files from the "necessary Files for Hadoop" folder and paste it on "C:\hadoop\etc\hadoop" folder.

Then set environmental variables
in User Variables
add a new variable with name: HADOOP_HOME
with value: C:\hadoop

and in the System Variables,
Edit and add two new values: 1. C:\hadoop\bin
                             2. C:\hadoop\sbin

Then go to your windows search bar and type CMD and press enter then type *cd C:\hadoop\etc\hadoop*
Format the Namenode
Formatting the NameNode is done once when hadoop is installed and not for running hadoop filesystem, else it will delete all the data inside HDFS.

now let us start with start the dfs and yarn command 
  *start-dfs.cmd*
  *start-yarn.cmd*

Now you can access the UI by typing *localhost:9870* on your internet browser.



