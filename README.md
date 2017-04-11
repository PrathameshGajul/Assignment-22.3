Q.Explain in brief
● Sequence File Format
● NLine Input Format
● DB Input Format
● DB Output Format

Ans:
1)Sequence File Format
-Sequence file is a flat file consisting of binary key/value pairs.
-It is extensively used in MapReduce as input/output formats.
-It is also worth noting that, internally, the temporary outputs of maps are stored using SequenceFile.
-The SequenceFile provides a Writer, Reader and Sorter classes for writing, reading and sorting respectively.

There are 3 different SequenceFile formats:

a)Uncompressed key/value records.
b)Record compressed key/value records - only 'values' are compressed here.
c)Block compressed key/value records - both keys and values are collected in 'blocks' separately and compressed.The size of the 'block' is configurable.
The recommended way is to use the SequenceFile.createWriter methods to construct the 'preferred' writer implementation.
The SequenceFile.Reader acts as a bridge and can read any of the above SequenceFile formats.


2)NLine Input Format
-With NLineInputFormat each mapper receives fixed number of lines of input, unlike TextInputFormat and KeyValueTextInputFormat.
-The number of lines of input to each mapper can be controlled by setting the property, mapreduce.input.lineinputformat.linespermap in new API and mapred.line.input.format.linespermap in old API. The default value is 1.
-NLineInputFormat is used in applications that take a small amount of input data and run an extensive (that is, CPU-intensive) computation for it, then emit their output. 


3)DBInputFormat
-The DBInputFormat component provided in Hadoop 0.19 finally allows easy import and export of data between Hadoop and many relational databases, allowing relational data to be more easily incorporated into your data processing pipeline.
-DBInputFormat uses JDBC to connect to data sources. Because JDBC is widely implemented, DBInputFormat can work with MySQL, PostgreSQL, and several other database systems.
-Individual database vendors provide JDBC drivers to allow third-party applications (like Hadoop) to connect to their databases.
-The DBInputFormat is an InputFormat class that allows you to read data from a database.
-An InputFormat is Hadoop’s formalization of a data source; it can mean files formatted in a particular way, data read from a database, etc.
-DBInputFormat provides a simple method of scanning entire tables from a database, as well as the means to read from arbitrary SQL queries performed against the database.


4)DBOutputFormat
-The DBOutputFormat writes to the database by generating a set of INSERT statements in each reducer.
-The reducer’s close() method then executes them in a bulk transaction. Performing a large number of these from several reduce tasks concurrently can swamp a database.
-If you want to export a very large volume of data, you may be better off generating the INSERT statements into a text file, and then using a bulk data import tool provided by your database to do the database import.
-DBOutputFormat accepts <key,value> pairs, where key has a type extending DBWritable. Returned RecordWriter writes only the key to the database with a batch SQL query.

