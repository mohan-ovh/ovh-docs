---
title: How to use object storage with Apache Spark on the Data Processing platform
slug: object-storage
excerpt: Object storage based on Swift and its S3 API is the common way to store data. Let’s find out how to do it !
section: How to
order: 5
---

**Last updated 07<sup>th</sup> May, 2020**

## Objective
This guide gives you some basic examples about using OpenStack Swift and its S3 API with OVHcloud Data Processing.

We will use both the OpenStack Swift native API and its S3 API in read/write mode.

Samples are based on the well-known WordCount. We will first read data from a text file, then count the frequence of each word in this particular file.

## Requirements
- Access to the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager).
- An OVHcloud account
- A cloud project in your OVHcloud account (see [How to create a cloud project](../../public-cloud/getting_started_with_public_cloud_logging_in_and_creating_a_project){.external} for details).
- Data Processing activated (see [How to activate the Data Processing](../activation){.external} for details).
- First use of OVHcloud Data Processing already done. For example, the first tutorial [Calculating π number with Apache Spark](../pi-spark){.external}.
- An environment file is required.
The following is an example with only dependencies required for this How to: [environment.yml](https://github.com/ovh/data-processing-samples/tree/master/python_objectStorage/environment.yml).
Otherwise, this [How to](../generate-environment) explains how to generate an environment file.
- The input file 'wordcount.txt' used by the following samples is available [Here](https://github.com/ovh/data-processing-samples/tree/master/python_objectStorage/wordcount.txt).
You have to upload it in the same Swift container as the one used for Python samples. Please refer to this documentation that explains how to create a Swift container [Getting started with the Swift API](../../public-cloud/getting_started_with_the_swift_api/).

## Read data in the current container with Apache Spark using OpenStack Swift API

Find below the code in Python that reads one object wordcount.txt in the current container and prints the number of occurrences per word.

Save it in a file called 'wordcount.py' or download it from this repository: [Data Processing Samples - Object Storage](https://github.com/ovh/data-processing-samples/tree/master/python_objectStorage/wordcount.py).

Here we use Apache Spark and the OpenStack Swift API.

```python
from __future__ import print_function
from operator import add
from pyspark.sql import SparkSession

if __name__ == "__main__":

    # create a SparkSession
    spark = SparkSession\
        .builder\
        .appName("PythonWordCount")\
        .getOrCreate()

    # read the input file directly in the same Swift container that hosts the current script
    # create a rdd that contains lines of the input file
    lines = spark.read.text("wordcount.txt").rdd.map(lambda r: r[0])

    # split lines, extract words and count the number of occurrences for each of them
    counts = lines.flatMap(lambda x: x.split(' ')) \
                  .map(lambda x: (x, 1)) \
                  .reduceByKey(add)

    # print the result
    output = counts.collect()
    for (word, count) in output:
        print("%s: %i" % (word, count))

    # very important: stop the current session
    spark.stop()
```

## Read data with Apache Spark using OpenStack Swift S3 API

Find below the code in Python that:

- reads one object 'wordcount.txt' in Swift through its S3 API
- stores the number of occurrences per word in S3 object
- prints the result

Save it in a file called 'wordcount_s3only.py' or download it from this repository: [Data Processing Samples - Object Storage](https://github.com/ovh/data-processing-samples/tree/master/python_objectStorage/wordcount_s3only.py).

Credentials provided for S3 can concern any Swift container.

```python
from __future__ import print_function
from operator import add
from pyspark.sql import SparkSession

if __name__ == "__main__":

    # create a SparkSession
    # We want to use the Swift S3 API. So we have to provide some attributes
    spark = SparkSession\
        .builder\
        .appName("PythonWordCount") \
        .config("spark.hadoop.fs.s3a.access.key", "7decf61921524a6b828c9305a77bb201") \
        .config("spark.hadoop.fs.s3a.secret.key", "9e9c50f2ff514fc3bdc5f98e61bec81f") \
        .config("spark.hadoop.fs.s3a.impl", "org.apache.hadoop.fs.s3a.S3AFileSystem")\
        .config("spark.hadoop.fs.s3a.path.style.access", "true")\
        .config("spark.hadoop.fs.s3a.endpoint", "s3.gra.cloud.ovh.net")\
        .getOrCreate()

    # read the input file in Swift through the S3 API
    # create a rdd that contains lines of the input file
    lines = spark.read.text("s3a://odp-s3/wordcount.txt").rdd.map(lambda r: r[0])

    # split lines, extract words and count the number of occurrences for each of them
    counts = lines.flatMap(lambda x: x.split(' ')) \
                  .map(lambda x: (x, 1)) \
                  .reduceByKey(add)

    # store the result in the same (or another) bucket but in the same project
    # according to the attributes provided in SparkSession
    counts.saveAsTextFile("s3a://odp-s3/wordcount_result.txt")

    # print the result
    output = counts.collect()
    for (word, count) in output:
        print("%s: %i" % (word, count))

    # very important: stop the current session
    spark.stop()
```

## Read data with Apache Spark using the both OpenStack Swift API and its S3 implementation

Find below the code in Python that:

- reads one object 'wordcount.txt' through the native Swift API
- stores the number of occurrences per word in Swift through its S3 API
- prints the result

Save it in a file called 'wordcount_both.py' or download it from this repository: [Data Processing Samples - Object Storage](https://github.com/ovh/data-processing-samples/tree/master/python_objectStorage/wordcount_both.py).

Credentials provided for S3 can concern any Swift container.
Thus, we can read data from one Swift container and write the result in another container.

```python
from __future__ import print_function
from operator import add
from pyspark.sql import SparkSession

if __name__ == "__main__":

    # create a SparkSession
    # we want to use the Swift S3 API. So we have to provide some attributes
    spark = SparkSession \
        .builder \
        .appName("PythonWordCount") \
        .config("spark.hadoop.fs.s3a.access.key", "7decf61921524a6b828c9305a77bb201") \
        .config("spark.hadoop.fs.s3a.secret.key", "9e9c50f2ff514fc3bdc5f98e61bec81f") \
        .config("spark.hadoop.fs.s3a.impl", "org.apache.hadoop.fs.s3a.S3AFileSystem") \
        .config("spark.hadoop.fs.s3a.path.style.access", "true") \
        .config("spark.hadoop.fs.s3a.endpoint", "s3.gra.cloud.ovh.net") \
        .getOrCreate()

    # read the input file directly in the same Swift container that hosts the current script
    # create a rdd that contains lines of the input file
    lines = spark.read.text("wordcount.txt").rdd.map(lambda r: r[0])

    # split lines, extract words and count the number of occurrences for each of them
    counts = lines.flatMap(lambda x: x.split(' ')) \
                  .map(lambda x: (x, 1)) \
                  .reduceByKey(add)

    # store the result in the same (or another) container according to the attributes provided in SparkSession
    # here we use the S3 API
    counts.saveAsTextFile("s3a://odp-s3/wordcount_result.txt")

    # print the result
    output = counts.collect()
    for (word, count) in output:
        print("%s: %i" % (word, count))

    # very important: stop the current session
    spark.stop()
```

## Read data with boto3 API

Boto3 is the Amazon Web Services (AWS) Software Development Kit (SDK) for Python, which allows Python developers to write software that makes use of services like Amazon S3 and Amazon EC2.
[Boto3 - the AWS SDK for Python](https://pypi.org/project/boto3/) 

Find below the code in Python that stores one basic string in S3 object.

Save it in a file called 'boto3_sample.py' or download it from this repository: [Data Processing Samples - Object Storage](https://github.com/ovh/data-processing-samples/tree/master/python_objectStorage/boto3_sample.py).

Credentials provided for S3 can concern any Swift container.

Here we don't use Spark but sometimes depending on your use cases you may have to interact with S3 outside the Apache Spark framework.

```python
import boto3
import io

if __name__ == "__main__":

    # here we use boto3 to access the container through the Swift S3 API
    # so we have to define some attributes to provide an access to the swift container
    s3 = boto3.client('s3',
                      aws_access_key_id="7decf61921524a6b828c9305a77bb201",
                      aws_secret_access_key="9e9c50f2ff514fc3bdc5f98e61bec81f",
                      endpoint_url="https://s3.gra.cloud.ovh.net/",
                      region_name="gra")

    bytes_to_write = b"This a string to be written in a file."

    file = io.BytesIO(bytes_to_write)

    # write string through the S3 API with boto3
    s3.upload_fileobj(file, "odp-s3", "test_write_string.txt")
```

## Go further

These samples are quite basic. They provide the first step to interact with object storage from within your code and, then, go further.

Concerning the 'WordCount' use case, here is a link to the tutorial with a more advanced [Wordcount](../wordcount-spark){.external}.

If you are not familiar with Apache Spark, we recommend you to visit [Apache Spark's official website](https://spark.apache.org/) and [pyspark's documentation](https://spark.apache.org/docs/latest/api/python/index.html).

You can send your questions, suggestions or feedbacks in our community of users in our public [Gitter](https://gitter.im/ovh/data-processing){.external}

