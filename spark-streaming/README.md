# Spark Streaming

Spark streaming是Spark核心API的一个扩展，它对实时流式数据的处理具有可扩展性、高吞吐量、可容错性等特点。我们可以从kafka、flume、Twitter、 ZeroMQ、Kinesis等源获取数据，也可以通过由
高阶函数map、reduce、join、window等组成的复杂算法计算出数据。最后，处理后的数据可以推送到文件系统、数据库、实时仪表盘中。事实上，你可以将处理后的数据应用到Spark的[机器学习算法](https://spark.apache.org/docs/latest/mllib-guide.html)、
[图处理算法](https://spark.apache.org/docs/latest/graphx-programming-guide.html)中去。

![Spark Streaming处理流程](../img/streaming-arch.png)

在内部，它的工作原理如下图所示。Spark Streaming接收实时的输入数据流，然后将这些数据切分为批数据供Spark引擎处理，Spark引擎将数据生成最终的结果数据。

![Spark Streaming处理原理](../img/streaming-flow.png)

Spark Streaming支持一个高层的抽象，叫做离散流(`discretized stream`)或者`DStream`，它代表连续的数据流。DStream既可以利用从Kafka, Flume和Kinesis等源获取的输入数据流创建，也可以
在其他DStream的基础上通过高阶函数获得。在内部，DStream是由一系列RDDs组成。

本指南指导用户开始利用DStream编写Spark Streaming程序。用户能够利用scala、java或者Python来编写Spark Streaming程序。

注意：Spark 1.2已经为Spark Streaming引入了Python API。它的所有DStream transformations和几乎所有的输出操作可以在scala和java接口中使用。然而，它只支持基本的源如文本文件或者套接字上
的文本数据。诸如flume、kafka等外部的源的API会在将来引入。

* [一个快速的例子](a-quick-example.md)
* [基本概念](basic-concepts/README.md)
  * [关联](basic-concepts/linking.md)
  * [初始化StreamingContext](basic-concepts/initializing-StreamingContext.md)
  * [离散流](basic-concepts/discretized-streams.md)
  * [输入DStreams](basic-concepts/input-DStreams.md)
  * [DStream中的转换](basic-concepts/transformations-on-DStreams.md)
  * [DStream的输出操作](basic-concepts/output-operations-on-DStreams.md)
  * [缓存或持久化](basic-concepts/caching-persistence.md)
  * [Checkpointing](basic-concepts/checkpointing.md)
  * [部署应用程序](basic-concepts/deploying-applications.md)
  * [监控应用程序](basic-concepts/monitoring-applications.md)
* [性能调优](performance-tuning/README.md)
  * [减少批数据的执行时间](performance-tuning/reducing-processing-time.md)
  * [设置正确的批容量](performance-tuning/setting-right-batch-size.md)
  * [内存调优](performance-tuning/memory-tuning.md)
* [容错语义](fault-tolerance-semantics/README.md)