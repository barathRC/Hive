# Hive
problems&amp;Solutions


1) You can create table using CREATE TABLE (Managed) & CREATE EXTERNAL TABLE (External) 
2) LOCATION specified should be an HDFS path "" to override the default LOCATION which is usr/hive/warehouse/tblname
3) HDFS DFS -push (or) copy fromfile file.txt "/path/" to copy file to the HIVE table directory path (HDFS path)
4) LOAD DATA LOCAL INPATH INTO tablename to copy file from local
5) LOAD DATA INPATH "/path1/" INTO "/path2/" moves the file from one HDFS location to another
6) HIVE has METASTORE also known as HCATALOG . Dfeault embedded METASTORE DERBY. But each cluster node has local reference hostname. So, always configure it to MySQL which is the remote METASTORE. Its centralized. It has all the table info in TBL after getting into DATABASES. Change this setting in hive-site.xml
7) HIVE supports most of the SQL data-types. It also has ARRAY<>, MAP<int,string>, STRUCT<name: string, age: int>
8) HIVE supports only equijoins (ON Operator always should have EQUALITY). INNER, LEFT OUTER etc.
9) Normal Copy or moving data or WHERE condition required only MAPPER phase.
10) HIVE supprts natively TXTFILE, AVRO, ORC, PARQUET and SEQUENCEFILE.
11) Each of the format is can be checked using DESCRIBE EXTENDED tblname or DECRIBE FORMATTED tblname. The serde option has INPUT and OUTPUT FORMAT  which is according to the format.
12) MapReduce happens in JOINS, aggregations and GROUP BY ORDER BY. You can override the settings by SET HIVE.MAPRED.REDUCES = 2 (Any value). The Mapper phase will ouput 2 partitions to the REDUCE JOB now.
13) INSERT OVERWRITE DIRECTORY /path/"
    SELECT * FROM will send your queried data to this path as file.
14) SELECT * FROM DISTRIBUTE BY col1 ORDER BY col2, col3 will PARTITION your data on the file and writes the data as per the number of partitions.
15) TBLPROPERTIES = SkipHeadlinecount and ESCAPEQUOTES.
