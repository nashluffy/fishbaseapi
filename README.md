FishBase API
============

***Update*** The Ruby-based fishbase API with custom endpoints has been deprecated.

Fishbase and Sealifebase data can now be accessed programmatically using a standard S3 API at the following endpoints:

https://fishbase.ropensci.org/fishbase
https://fishbase.ropensci.org/sealifebase

For example, in python:

```python
import duckdb
duckdb.read_parquet("https://fishbase.ropensci.org/fishbase/species.parquet") 
```

These endpoints are provided by the open source [MINIO Server](https://min.io/) which conforms to the current (v4) [AWS S3 REST API](https://docs.aws.amazon.com/AmazonS3/latest/API/Welcome.html).  This supports direct REST queries or any of the many great and well-maintained client packages and tools, including [minio client](https://min.io/docs/minio/linux/reference/minio-mc.html),  [python `boto`](https://aws.amazon.com/sdk-for-python/), [Apache Arrow](https://arrow.apache.org/), etc.   

For example, with the minio client, one can explore the bucket like
```bash
$ mc alias set fishbase https://fishbase.ropensci.org
$ mc ls fishbase/sealifebase
[2024-08-01 19:31:44 BST]  23KiB STANDARD abnorm.parquet
[2024-08-01 19:31:44 BST] 311KiB STANDARD abundance.parquet
[2024-08-01 19:31:44 BST]  13KiB STANDARD abundance_delta.parquet
```
