## DataFrame

Spark SQL 的 DataFrame API 允许我们使用 DataFrame 而不用必须去注册临时表或者 生成 SQL 表达式。DataFrame API 既有 transformation 操作也有 action 操作。

### 创建 DataFrame

从 Spark 数据源进行创建

```bash
在 Spark SQL 中 SparkSession 是创建 DataFrame 和执行 SQL 的入口，创建 DataFrame 有三种方式：通过 Spark 的数据源进行创建；从一个存在的 RDD 进行转换；还可以从 Hive Table 进行查询返回。 1) 从 Spark 数据源进行创建 ➢ 查看 Spark 支持创建文件的数据源格式

scala> spark.read.
csv format jdbc json load option options orc parquet schema 
table text textFile
#在 spark 的 bin/data 目录中创建 user.json 文件
{"username":"zhangsan","age":20}
#读取 json 文件创建 DataFrame
scala> val df = spark.read.json("data/user.json")
df: org.apache.spark.sql.DataFrame = [age: bigint， username: string]
#注意：如果从内存中获取数据，spark 可以知道数据类型具体是什么。如果是数字，默认作 为 Int 处理；但是从文件中读取的数字，不能确定是什么类型，所以用 bigint 接收，可以和 Long 类型转换，但是和 Int 不能进行转换

#展示结果
+---+--------+
|age|username|
+---+--------+
| 20|zhangsan|
+---+--------+
```

从 RDD 进行转换

从 Hive Table 进行查询返回

RDD只关心数据

DataFrame还关心结构

# SparkSQL 核心编程

样例类可以直接生成伴生对象和apply方法，例如case class User。。。直接User就可以创建对象

## 数据的加载和保存

### 通用的加载和保存方式

SparkSQL 提供了通用的保存数据和数据加载的方式。这里的通用指的是使用相同的API，根据不同的参数读取和保存不同格式的数据，SparkSQL 默认读取和保存的文件格式为 parquet

* 加载数据

方法1:

```scala
scala>spark.sql("select * from json.`/opt/module/data/user.json`").show
```

方法2:

```scala
scala> spark.read.format("…")[.option("…")].load("…")

scala> spark.read.format(json).load("/opt/module/data/user.json")
简写
scala> spark.read.json.("/opt/module/data/user.json")
```

* 保存数据

df.write.save 是保存数据的通用方法

```scala
scala>df.write.
csv jdbc json orc parquet textFile… …

scala>df.write.format("…")[.option("…")].save("…")
scala>df.write.format(json).save("/opt/module/data/output/")
```

保存操作可以使用 SaveMode, 用来指明如何处理数据，使用 mode()方法来设置。 有一点很重要: 这些 SaveMode 都是没有加锁的, 也不是原子操作。

SaveMode 是一个枚举类，其中的常量包括：

| Scala/Java                      | Any Language     | Meaning                              |
| ------------------------------- | ---------------- | ------------------------------------ |
| SaveMode.ErrorIfExists(default) | "error"(default) | 如果文件已经存在则抛出异常           |
| SaveMode.Append                 | "append"         | 如果文件已经存在则追加               |
| SaveMode.Overwrite              | "overwrite"      | 如果文件已经存在则覆盖，旧的都删除！ |
| SaveMode.Ignore                 | "ignore"         | 如果文件已经存在则忽略               |

```scala
df.write.mode("append").json("/opt/module/data/output")
```



