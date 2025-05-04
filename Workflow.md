## Workflow: HDFS Data Ingestion & MapReduce WordCount

### 2. Interact with HDFS

1. **List root directory**

   ```bash
   hdfs dfs -ls /
   ```
2. **Create a new HDFS directory**

   ```bash
   hdfs dfs -mkdir /imran
   ```
3. **Verify via UI**

   * Browse → Utilities → Browse the File System → `/`

---

### 3. Upload Files to HDFS

1. **Upload a video file**

   ```bash
   hdfs dfs -put "C:\local\path\video.mp4" /imran/video.mp4
   ```
2. **Upload a large text file**

   ```bash
   hdfs dfs -put "C:\local\path\large.txt" /imran/large.txt
   ```
3. **View tail of text file**

   ```bash
   hdfs dfs -tail /imran/large.txt
   ```
4. **Upload a folder of part files**

   ```bash
   hdfs dfs -put "C:\local\path\part-files-folder" /imran/parts
   ```

---

### 4. Run Built‑in WordCount MapReduce

1. **Locate the example JAR**

   ```
   %HADOOP_HOME%\share\hadoop\mapreduce\hadoop-mapreduce-examples-*.jar
   ```
2. **Execute WordCount**

   ```bash
   hadoop jar "%HADOOP_HOME%\share\hadoop\mapreduce\hadoop-mapreduce-examples-*.jar" \
     wordcount \
     /imran/large.txt \
     /imran/wordcount-output
   ```
3. **Monitor job status**

   * In ResourceManager UI → “Applications” → filter by “wordcount”

---

### 5. Adjust JVM Memory (if Heap Space Errors)

1. **Edit `mapred-site.xml`**
   Path: `%HADOOP_HOME%\etc\hadoop\mapred-site.xml`
2. **Add or update these properties**:

   ```xml
   <property>
     <name>mapreduce.map.java.opts</name>
     <value>-Xmx4096m</value>
   </property>
   <property>
     <name>mapreduce.reduce.java.opts</name>
     <value>-Xmx6144m</value>
   </property>
   ```
3. **Remove previous output**

   ```bash
   hdfs dfs -rm -r /imran/wordcount-output
   ```
4. **Rerun the WordCount job** (see Step 4.2)

---

### 6. Retrieve Results

1. **List output directory**

   ```bash
   hdfs dfs -ls /imran/wordcount-output
   ```
2. **Fetch results to local**

   ```bash
   hdfs dfs -get /imran/wordcount-output/part-r-00000 C:\local\path\result.txt
   ```
3. **Open `result.txt`** in any text editor to review word counts.
        