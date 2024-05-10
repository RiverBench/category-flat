A benchmark task measuring the throughput (in statements per second) of deserializing a byte stream into a flat sequence of RDF triples or RDF quads.

## Methodology

### Data

Flat distributions of any dataset in the [`flat` category](../../categories/flat/index.md) of RiverBench may be used for this task.

### Workload

The task consists of deserializing serialized RDF data stored in memory to a flat sequence of RDF statements. To isolate the performance of the deserializer itself, the following steps are taken:

- The data (serialized RDF statements in the tested serialization format) is preloaded into memory before the benchmark starts.
- The deserialization process is repeated multiple times to amortize the cost of the initial setup, just-in-time code recompilation, and other external factors.
- The deserialized statements are not inserted into any data structure or database, but just temporarily stored in memory and immediately discarded. This is to avoid the overhead of maintaining additional data structures.
    - See the [`flat-rdf-store-loading`](../flat-rdf-store-loading/index.md) task for a benchmark that measures the time taken to load the deserialized data into a database.

### Metrics

The primary metric is the throughput of the deserialization process, measured in RDF statements (triples or quads) per second. This is calculated as the total number of RDF statements deserialized divided by the total time taken to deserialize them.


## Results

There are no results with RiverBench available for this task yet.

## Examples and references

- In the paper about the ERI format, a similar benchmark can be found in Section 4.3. The corresponding task in the paper is named "Decompression time" and measures the time taken to deserialize the entire sequence of triples.
    - Fernández, J. D., Llaves, A., & Corcho, O. (2014). Efficient RDF interchange (ERI) format for RDF data streams. In The Semantic Web–ISWC 2014: 13th International Semantic Web Conference, Riva del Garda, Italy, October 19-23, 2014. Proceedings, Part II 13 (pp. 244-259). Springer International Publishing.
    - https://doi.org/10.1007/978-3-319-11915-1_16

## See also

- Version of this task for grouped RDF streams: [`stream-deserialization-throughput`](../stream-deserialization-throughput/index.md)
- The inverse task: [`flat-serialization-throughput`](../flat-serialization-throughput/index.md)
