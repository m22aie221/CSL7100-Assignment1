1. Steps to run
   a. Hadoop
     start-all.sh
   b.Jupyter noteboot for Pyspark
     cd /home/rajesh/CSL7100/PySpark/pyspark-tutorial
     python -m venv .pyspark-env
     source .pyspark-env/bin/activate
     cd /home/rajesh/CSL7100
     jupyter-lab

3. Question wise steps for hadoop
   a. Question 1
      hdfs dfs -mkdir -p Assignment1/Question1/input
      hadoop fs -ls Assignment1/Question1/input
      hdfs dfs -put file01.txt  Assignment1/Question1/input
      hdfs dfs -put file02.txt  Assignment1/Question1/input
      hadoop fs -ls Assignment1/Question1/input
      hadoop fs -cat Assignment1/Question1/input/file01.txt
      hadoop fs -cat Assignment1/Question1/input/file02.txt

      hadoop jar wc.jar WordCount Assignment1/Question1/input/ Assignment1/Question1/output/      
      hadoop fs -cat Assignment1/Question1/output/part-r-00000
      
   b. Question 4
      cd /home/rajesh/CSL7100/Assignment1/Question4
      hadoop com.sun.tools.javac.Main WordCount.java
      jar cf wc.jar WordCount*.class
      hdfs dfs -rm -r Assignment1/Question4/output
      hadoop jar wc.jar WordCount Assignment1/Question1/input/ Assignment1/Question4/output/
      hadoop fs -cat Assignment1/Question4/output/part-r-00000

   c. Question 5 & 6
      cd /home/rajesh/CSL7100/Assignment1/Question5_6
      hadoop com.sun.tools.javac.Main WordCount.java
      jar cf wc.jar WordCount*.class
      hadoop jar wc.jar WordCount Assignment1/Question1/input/ Assignment1/Question5_6/output/
      hadoop fs -cat Assignment1/Question5_6/output/part-r-00000

   d. Question 7
      hdfs dfs -mkdir -p Assignment1/data
      hdfs dfs -rm Assignment1/data/200.txt
      hdfs dfs -rm -r Assignment1/Question7/output
      
      hadoop fs -copyFromLocal /home/rajesh/CSL7100/Assignment1/data/D184MB/200.txt Assignment1/data/200.txt
      hdfs dfs -ls Assignment1/data/200.txt
      
      hadoop jar wc.jar WordCount Assignment1/data Assignment1/Question7/output
      hdfs dfs -ls -R Assignment1/Question7/output/
      
      hadoop fs -cat Assignment1/Question7/output/part-r-00000
      hdfs dfs -cat Assignment1/Question7/output/part-r-00000 | head -n 5
      
      hadoop fs -getmerge Assignment1/Question7/output/ ../Question7/output_200.txt
      head -n 5 ../Question7/output_200.txt

   e. Question 8.
      hdfs dfs -stat %r Assignment1/data/200.txt
      hdfs getconf -confKey dfs.replication
      $HADOOP_HOME/etc/hadoop/hdfs-site.xml

   f. Question 9
      cd /home/rajesh/CSL7100/Assignment1/Question9
      hadoop com.sun.tools.javac.Main WordCount.java
      jar cf wc.jar WordCount*.class

      #Assignment1/data/D184MB/200.txt
      hadoop jar wc.jar WordCount Assignment1/data Assignment1/Question9/output_128MB/
      hadoop fs -cat Assignment1/Question9/output/part-r-00000

      hdfs dfs -rm -r Assignment1/Question9/output_4MB/
      hadoop jar wc.jar WordCount Assignment1/data Assignment1/Question9/output_4MB/

      jar cf wc.jar WordCount*.class
      hadoop jar wc.jar WordCount Assignment1/data Assignment1/Question9/output_1KB/

      jar cf wc.jar WordCount*.class
      hadoop jar wc.jar WordCount Assignment1/data Assignment1/Question9/output_256B/

      # delete hdfs directories
      hdfs dfs -rm -r Assignment1/Question1/CSL7100/Assignment1/wordcount/input
      
