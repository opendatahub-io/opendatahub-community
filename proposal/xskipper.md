---
title: Xskipper data skipping for spark
---

Xskipper is An Extensible [Data Skipping](https://xskipper.io/master/concepts/data-skipping) Framework, it provides a library for creating, managing and deploying data skipping indexes with Apache Spark.

- Boosts performance and reduce cost by skipping over irrelevant data
- Supports Parquet, CSV, JSON, ORC and Avro
- Hive tables supported
- Supports MinMax, ValueList and BloomFilter indexes out of the box
- Supports data skipping for User Defined Functions
- Easy to add additional index types

Xskipper is a Spark extension, [open source project](https://github.com/xskipper-io/xskipper), with scala and python api. To get started boosting sql queries with spark, get xskipper jar that fits your spark version and add it to spark packages jars.

## Architecture
[Xskipper Data Skipping Architecture](https://xskipper.io/master/concepts/extensible/)

## User Use Cases
Spark big data users who want to boost performance and reduce cost by indexing their data and skipping over irrelevant data

## Implementation
Xskipper is a Spark extension with [scala and python api](https://xskipper.io/master/api/indexing/). 
Xskipper jar for the relevant spark version should be added to pyspark packages jars, once the jar is included data can be indexed and dataskipping can be enabled. See [example notebook](https://github.com/xskipper-io/xskipper/blob/master/notebooks/python/Xskipper%20-%20Python%20Sample.ipynb).

## Testing
In JupiterHub select spark2.4 based image (Minimal python with apache spark)
Import xskipper pyspark notebook example (see link in Implementation section above)
Update "Setup" and "Indexing a dataset" sections cells to use local filesystem for data and metadata as shown in [ODH notebook setup](img/XskipperNotebookUseOfLocalFS.png), and test on spark standalone mode.
If Xskipper module cannot be found, restart kernel/shut down and start server until found.
Run the notebook to verify xskipper functionality and api running as expected.

## More info

- [IEEE Big Data 2020 paper - Extensible Data Skipping](https://arxiv.org/abs/2009.08150)
- [Adding xskipper support to JupiterHub Spark notebooks](https://github.com/opendatahub-io/odh-manifests/pull/451)
- [Issue](https://issues.redhat.com/projects/ODH/issues/ODH-447)
- [Getting started Guide](https://xskipper.io/master/getting-started/quick-start-guide/)
