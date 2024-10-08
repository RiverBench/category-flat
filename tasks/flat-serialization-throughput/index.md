A benchmark task measuring the throughput (in statements per second) of serializing a flat sequence of RDF triples or RDF quads.

## Methodology

### Data

Flat distributions of any dataset in the [`flat` category](../../categories/flat/index.md) of RiverBench may be used for this task.

### Workload

The task consists of serializing RDF data stored in memory (as an array of RDF statements or similar) to a byte stream. To isolate the performance of the serializer itself, the following steps are taken:

- The data (RDF statements) is preloaded into memory before the benchmark starts.
- The RDF statements are stored in a data structure that is trivially iterable (e.g., an array).
- The serialization process is repeated multiple times to amortize the cost of the initial setup, just-in-time code recompilation, and other external factors.
- The serialized data is typically not written to disk, but just temporarily stored in memory and immediately discarded. This is to avoid the overhead of disk I/O.
    - Alternatively, in benchmarks that wish to evaluate the performance of writing to disk, especially considering the impact of different disk usage patterns (e.g., sequential vs. random access), the data may be written to disk.

### Metrics

- **Serialization throughput** – the primary metric, measured in RDF statements (triples or quads) per second. This is calculated as the total number of RDF statements serialized divided by the total time taken to serialize them.

## Results

**See the results for this task reported by the community: [RESULTS](results.md).**

## This task in benchmarks outside of RiverBench

- In the paper about the ERI format, a similar benchmark can be found in Section 4.3. The corresponding task in the paper is named "Compression time" and measures the time taken to serialize the entire sequence of triples.
    - Fernández, J. D., Llaves, A., & Corcho, O. (2014). Efficient RDF interchange (ERI) format for RDF data streams. In The Semantic Web–ISWC 2014: 13th International Semantic Web Conference, Riva del Garda, Italy, October 19-23, 2014. Proceedings, Part II 13 (pp. 244-259). Springer International Publishing. [https://doi.org/10.1007/978-3-319-11915-1_16](https://doi.org/10.1007/978-3-319-11915-1_16)

## See also

- Version of this task for grouped RDF streams: [`stream-serialization-throughput`](../stream-serialization-throughput/index.md)
- The inverse task: [`flat-deserialization-throughput`](../flat-deserialization-throughput/index.md)
