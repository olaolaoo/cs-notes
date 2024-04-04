Spark 3.0.0m scala 2.12

wordcount

spark是运行应用程序的环境，连接spark，将写的程序运行在上面。

* 1.TODO 建立和Spark框架的连接

  基于 Spark3.0 版 本，使用时请注意对应版本

在pom.xml上添加依赖:
  <dependencies>
        <dependency>
            <groupId>org.apache.spark</groupId>
            <artifactId>spark-core_2.12</artifactId>
            <version>3.0.0</version>
        </dependency>
    </dependencies>

```scala
//new SparkConf()配置对象
//setMaster()标识环境的方法
//setAppName()设置程序名称方法
val sparkConf = new SparkConf().setMaster("local").setAppName("WordCount")
val sc=new SparkContext(sparkConf)
```

* 2.TODO 执行业务操作

```scala
// 1. 读取文件，获取一行一行的数据
//    hello world
val lines: RDD[String] = sc.textFile("datas")

// 2. 将一行数据进行拆分，形成一个一个的单词（分词）
//    扁平化：将整体拆分成个体的操作
//   "hello world" => hello, world, hello, world
val words: RDD[String] = lines.flatMap(_.split(" "))

// 3. 将数据根据单词进行分组，便于统计
//    (hello, hello, hello), (world, world)
val wordGroup: RDD[(String, Iterable[String])] = words.groupBy(word=>word)

// 4. 对分组后的数据进行转换
//    (hello, 3), (world, 2)
val wordToCount = wordGroup.map {
    case ( word, list ) => {
        (word, list.size)
    }
}

// 5. 将转换结果采集到控制台打印出来
val array: Array[(String, Int)] = wordToCount.collect()
array.foreach(println)
```



* 3.TODO 关闭连接

```scala
sc.stop()
```



