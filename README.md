# Hadoop-installation-guide


## 1. Prerequisites

* **Operating System**: Windows 10 or later
* **Disk Space**: ≥ 5 GB free

---

## 2. Java Installation

1. **Download JDK 8**

   * Visit Oracle’s Java SE 8 Archive Downloads:
     [https://www.oracle.com/apac/java/technologies/javase/javase8-archive-downloads.html#license-lightbox](https://www.oracle.com/apac/java/technologies/javase/javase8-archive-downloads.html#license-lightbox)
   * Create (or log in to) your Oracle account, accept the license agreement, and download the Windows x64 installer.

2. **Install to `C:\Java`**

   * Run the installer.
   * When prompted for the destination folder, change it to:

     ```
     C:\Java
     ```
   * Complete the installation.

3. **Relocate JDK Folder**

   * If the installer created `C:\Program Files\Java\jdk-1.8`, move this entire `jdk-1.8` folder to `C:\Java\jdk-1.8`.
   * Delete the `Java` folder from `C:\Program Files` folder.

4. **Configure Environment Variables**

   * Open **System Properties** → **Advanced** → **Environment Variables**.
   * Under **User variables**, click **New**:

     * **Variable name**: `JAVA_HOME`
     * **Variable value**: `C:\Java\jdk-1.8\bin`
   * Under **System variables**, select **Path** → **Edit** → **New**, then add:

     ```
     C:\Java\jdk-1.8\bin
     ```
   * Click **OK** to apply.

5. **Verify Installation**

   * Open **Command Prompt** and run:

     ```
     java -version
     ```
   * You should see output indicating Java 1.8.x is installed.

---

## 3. Hadoop Installation

### 3.1 Download and Extract

1. **Download Hadoop**

   * Official mirror: [https://dlcdn.apache.org/hadoop/common/hadoop-3.4.0/hadoop-3.4.0.tar.gz](https://dlcdn.apache.org/hadoop/common/hadoop-3.4.0/hadoop-3.4.0.tar.gz)

2. **Extract to `C:\hadoop`**

   * Run WinRAR (as Administrator) or another archive tool.
   * Extract `hadoop-3.4.0.tar.gz` to `C:\`
   * Rename the extracted folder from `hadoop-3.4.0` to:

     ```
     C:\hadoop
     ```

3. **Populate Binaries and Configuration**

   * Delete the existing `C:\hadoop\bin` directory.
   * From your downloaded repository, copy the provided `bin\` and `data\` folders into `C:\hadoop`.
   * Copy all configuration files from “Necessary Files for Hadoop” into:

     ```
     C:\hadoop\etc\hadoop
     ```

### 3.2 Configure Environment Variables

1. **User Variables**

   * **New variable**:

     * **Name**: `HADOOP_HOME`
     * **Value**: `C:\hadoop\bin`

2. **System Variables**

   * Edit **Path**, then **New** → add:

     ```
     C:\hadoop\bin
     C:\hadoop\sbin
     ```
   * Apply changes.

### 3.3 Initializing HDFS

1. **Verify Hadoop**

   * Open a new Command Prompt (Admin) and execute:

     ```
     hadoop version
     ```
2. **Format NameNode**

   * In Administrator Command Prompt, run:

     ```
     hdfs namenode -format
     ```

   > **Note:** Only format once during initial setup. Formatting again will erase all HDFS data.

---

## 4. Starting Hadoop Services

1. **Run CMD as administrator and locate sbin folder**
    ```
    C:\Windows\System32> cd C:\hadoop\sbin 
    ```

2. **Start HDFS**

   ```
   C:\hadoop\sbin> start-dfs.cmd
   ```
2. **Start YARN**

   ```
   C:\hadoop\sbin> start-yarn.cmd
   ```
3. **Verify with JPS**

   ```
   C:\hadoop\sbin> jps
   ```

   You should see processes such as `NameNode`, `DataNode`, `ResourceManager`, etc.

---

## 5. Web Interfaces

* **HDFS NameNode UI**: [http://localhost:9870](http://localhost:9870)
* **YARN ResourceManager UI**: [http://localhost:8088](http://localhost:8088)

---

## 6. Troubleshooting & Tips

* Always run Command Prompt **as Administrator** when interacting with Hadoop scripts.
* If you modify configuration files (`core-site.xml`, `hdfs-site.xml`, etc.), restart services:

  ```
  stop-dfs.cmd
  stop-yarn.cmd
  start-dfs.cmd
  start-yarn.cmd
  ```
* Check log files in `C:\hadoop\logs` for error details.
* Ensure no other services occupy ports 9870 or 8088.