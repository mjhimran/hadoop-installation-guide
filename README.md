# hadoop-installation-guide
At First we have to Download 
*Oracle [Java](https://www.oracle.com/apac/java/technologies/javase/javase8-archive-downloads.html#license-lightbox)* and need to create an account to download the software.
Then install it on location "C:\Java\jdk" or after default installation move the "jdk-1.8" folder to "C:\Java" and reaname the it "jdk-1.8" to "jdk".
After changing these stuff go to *Environmental Variable* and add "JAVA_HOME" with variable value: "C:\Java\jdk\bin" at "User Variables" and 
Edit "System Variable" also add the location "C:\Java\jdk\bin" then press OK.
# Open CMD on your search bar. Then hit Enter. Check the java version by "java -version" command.

After succesfully installing the Java, 
Download [*Hadoop*](https://dlcdn.apache.org/hadoop/common/hadoop-3.4.0/hadoop-3.4.0.tar.gz) and extract it, and 
Rename the folder "hadoop-3.4.0" as "hadoop". Then delete the "bin" folder from the "hadoop" folder. 
Download the "bin" folder from this github repository, extract it and paste in the "hadoop" folder.





