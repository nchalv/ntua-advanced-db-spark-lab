# Apache Spark Lab — Advanced Database Topics

**National Technical University of Athens (NTUA)**  
**School of Electrical and Computer Engineering**  
**Advanced Database Topics · Academic Year 2026–2027**

A hands-on introduction to distributed data processing with **Apache Spark**, developed to support the semester assignment of the *Advanced Database Topics* course.

The lab combines executable **PySpark** examples with explanations of Spark's distributed execution model, SQL query optimization, physical execution plans, and performance considerations.

> **Environment note:** The live lab demonstrations use an existing **Spark 3.4** cluster with **Hadoop YARN, HDFS, Livy, and Apache Zeppelin**. The semester assignment targets **Spark 4.2.x**. Core concepts and most examples are transferable, but some newer Spark 4.x features are not available on the demonstration cluster.

## Lab materials

- **[Spark lab notebook](SparkLab.ipynb)** — Read the examples and saved outputs directly on GitHub.
- **[Sample employee data](employees.csv)** — Small dataset used for introductory DataFrame and SQL examples.
- **`images/`** — Illustrations referenced by the notebook.

If the notebook has a different filename, update the link above accordingly.

## Topics covered

| Topic | What you'll learn |
|---|---|
| RDD fundamentals | Partitions, transformations, actions, lineage, lazy evaluation, and shuffles |
| DataFrame API | Explicit schemas, filtering, projection, derived columns, grouping, and aggregation |
| Spark SQL | Temporary views, Common Table Expressions, and SQL/DataFrame equivalence |
| Distributed joins | Outer joins, anti-joins, sort-merge joins, broadcast hash joins, and hints |
| Window functions | `row_number()`, deterministic tie-breaking, and top-*k* per group |
| Data cleaning | Dates, conditional expressions, arrays, `split()`, and `explode()` |
| Physical execution plans | `explain(mode="formatted")`, `Exchange`, partial aggregation, and sorting |
| Storage optimization | Parquet, column pruning, partition pruning, and predicate pushdown |
| Reuse and measurement | Caching, recomputation, Spark UI, and benchmarking caveats |
| Adaptive execution | AQE, runtime statistics, shuffle partition coalescing, and execution stages |
| Analytical correctness | Weighted averages and multi-stage aggregation pitfalls |
| Geospatial queries | Haversine distance, Cartesian joins, and nearest-neighbor ranking |

## Viewing the notebook

GitHub can display `.ipynb` files directly in the browser, including Markdown explanations and saved results. **You do not need to install Spark or Jupyter just to read it.**

Some examples are tied to the lab cluster (for example, HDFS input/output paths). These are demonstration configurations, **not** universal paths that will work on a personal computer.

## Running the examples

To execute the examples yourself, you need a working PySpark environment and access to the required input files. Most foundational examples work in Spark 3.4; the semester assignment's newer features require its specified Spark 4.2.x environment.

For local experimentation, create a Spark session and adjust any dataset paths to your filesystem:

```python
from pyspark.sql import SparkSession, functions as F, types as T, Window

spark = SparkSession.builder.appName("AdvancedDB-SparkLab").getOrCreate()
EMPLOYEES_PATH = "employees.csv"  # adjust as needed
```

The notebook originated in Apache Zeppelin, so some exported cells or interpreter-specific settings may require adjustments in a different execution environment. **The published notebook is intended primarily as a read-only lab companion, not a turnkey standalone application.**

## Connection to the semester assignment

The examples introduce the building blocks needed for the semester project: reading and transforming datasets, constructing SQL/DataFrame queries, interpreting physical plans, reasoning about joins and shuffles, preparing partitioned Parquet data, and measuring distributed workloads.

The small teaching datasets are intentionally separate from the project datasets (**Yelp Open Dataset, GloVe, and ACS Census**). The notebook illustrates methods and common pitfalls; it does not replace the official assignment specification or provide complete solutions.

## Notes on performance

Examples using very small datasets are designed to explain *mechanisms*, not to establish performance claims. Measured runtimes may be dominated by scheduling overhead, JVM warm-up, filesystem caching, and cluster configuration. For meaningful experiments, use repeatable workloads, inspect the Spark UI, and report results across multiple runs.

## Repository structure

```text
.
├── README.md
├── SparkLab.ipynb
├── employees.csv
└── images/
    └── ...
```

The structure is illustrative and can be extended with a published HTML site or additional lab material.

## References

- [Apache Spark documentation](https://spark.apache.org/docs/latest/)
- [PySpark API reference](https://spark.apache.org/docs/latest/api/python/)
- [Spark SQL performance tuning](https://spark.apache.org/docs/latest/sql-performance-tuning.html)
- [Apache Zeppelin](https://zeppelin.apache.org/)

---

*Teaching material for the Advanced Database Topics course, NTUA, academic year 2026–2027.*
