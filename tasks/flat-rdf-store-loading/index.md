A benchmark task measuring the time taken and resources used by RDF stores when loading flat RDF data (triples or quads).

## Methodology

### Data

Flat distributions of any dataset in the `flat` category of RiverBench may be used for this task.

### Workload

In this task, an RDF store is set up (for example, [Apache Jena TDB2](https://jena.apache.org/documentation/tdb2/index.html) or Virtuoso) and then loaded with a flat dump of RDF statements (triples or quads).

- When comparing multiple RDF stores, identical input data (serialized in the same format) should be used for all stores.
- The benchmark includes the time taken to deserialize the input data and insert the resulting RDF statements into the store, considering the entire process and the impact of the underlying I/O.
- Input data may be either batched or streamed, depending on the capabilities of the RDF store being tested and the specific research questions being addressed.
    - When using batched input, the input dataset is split into chunks, and each chunk is processed by the system separately. The metrics are typically calculated per chunk.
    - When using streamed input, the input dataset is processed as a continuous stream of statements. The metrics are typically calculated in regular time intervals or after processing a certain number of statements.

### Metrics

- Time taken to deserialize the input data and insert the resulting RDF statements into the store. From this measurement, the insertion throughput (in statements per second) can be calculated.
- Memory usage during and after the loading process.
- Storage space used by the RDF store during and after the loading process.
- Total CPU time used during the loading process.

## Results

There are no results with RiverBench available for this task yet.

## Examples and references

- Such a benchmark was performed in a paper comparing several RDF stores on IoT devices (Section 8). There, the authors measured the time taken to load the data and the memory usage.
    - Le-Tuan, A., Hayes, C., Hauswirth, M., & Le-Phuoc, D. (2020). Pushing the Scalability of RDF Engines on IoT Edge Devices. Sensors, 20(10), 2788.
    - https://doi.org/10.3390/s20102788
