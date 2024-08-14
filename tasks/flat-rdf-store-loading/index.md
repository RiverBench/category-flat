A benchmark task measuring the time taken and resources used by RDF stores when loading flat RDF data (triples or quads).

## Methodology

### Data

Flat distributions of any dataset in the [`flat` category](../../categories/flat/index.md) of RiverBench may be used for this task.

### Workload

In this task, an RDF store is set up (for example, [Apache Jena TDB2](https://jena.apache.org/documentation/tdb2/index.html), [OpenLink Virtuoso Open Source v7.x](https://github.com/openlink/virtuoso-opensource/), or [RDF4J's NativeStore](https://rdf4j.org/documentation/programming/repository/)) and then loaded with a flat dump of RDF statements (triples or quads).

- When comparing multiple RDF stores, identical input data (serialized in the same format) should be used for all stores.
- The benchmark includes the time taken to deserialize the input data and insert the resulting RDF statements into the store, considering the entire process and the impact of the underlying I/O.
- Input data may be either batched or streamed statement by statement, depending on the capabilities of the RDF store being tested and the specific research questions being addressed.
    - When using batched input, the input dataset is split into chunks consisting of N statements, and each chunk is processed by the system separately. The metrics (see below) are typically calculated per chunk.
    - When using streamed input, the input dataset is processed as a continuous stream of individual statements (in RDF-STaX terminology: [flat RDF stream](https://w3id.org/stax/dev/taxonomy#flat-rdf-stream)). The metrics are typically calculated in regular time intervals or after processing a certain number of statements.

### Metrics

Benchmarks may choose to measure only some of the following metrics:

- **Load time** – time taken to deserialize the input data and insert the resulting RDF statements into the RDF store, including any indexing and I/O operations. From this measurement, the loading throughput can be calculated (see below).
- **Loading throughput** – the rate at which the RDF store can load data, measured in RDF statements (triples or quads) per second. This can be either calculated per chunk (in the case of batched input) or as an average over the entire loading process.
- **Memory usage** – main system memory usage in bytes, during and after the loading process.
- **Storage size** – size of the RDF store on disk, in bytes. May be measured during and after the loading process.
- **Total CPU time** – the total CPU time (across all processors) allocated to the RDF store. Measured during the loading process.

## Results

There are no results with RiverBench available for this task yet.

## This task in benchmarks outside of RiverBench

- The Berlin SPARQL Benchmark (BSBM) includes a data loading phase where the data is loaded into the RDF store. The time taken to load the data (*LT* metric) is one of the metrics used to evaluate the performance of the RDF store. The dataset used in BSBM is synthetic.
    - Bizer, C., & Schultz, A. (2009). The Berlin SPARQK Benchmark. International Journal on Semantic Web and Information Systems (IJSWIS), 5(2), 1-24. [https://doi.org/10.4018/jswis.2009040101](https://doi.org/10.4018/jswis.2009040101)
- Similarly, the Lehigh University Benchmark (LUBM) includes a data loading phase where the data is loaded into the RDF store. The time taken to load the data (*load time* metric) is one of the metrics used to evaluate the performance of the RDF store. The dataset used in LUBM is synthetic.
    - Guo, Y., Pan, Z., & Heflin, J. (2005). LUBM: A benchmark for OWL knowledge base systems. Journal of Web Semantics, 3(2-3), 158-182. [https://doi.org/10.1016/j.websem.2005.06.005](https://doi.org/10.1016/j.websem.2005.06.005)
- A load time benchmark was performed in a paper comparing several RDF stores on a few different IoT devices (Section 8). There, the authors measured the time taken to load the data and the memory usage. A single real dataset was used.
    - Le-Tuan, A., Hayes, C., Hauswirth, M., & Le-Phuoc, D. (2020). Pushing the Scalability of RDF Engines on IoT Edge Devices. Sensors, 20(10), 2788. [https://doi.org/10.3390/s20102788](https://doi.org/10.3390/s20102788)
- The RDF-3X paper also included a load time benchmark, with 3 different datasets (non-synthetic). They report the total load time in minutes and the size on disk of the resulting store.
    - Neumann, T., & Weikum, G. (2010). The RDF-3X engine for scalable management of RDF data. The VLDB Journal, 19, 91-113. [https://doi.org/10.1007/s00778-009-0165-y](https://doi.org/10.1007/s00778-009-0165-y)
