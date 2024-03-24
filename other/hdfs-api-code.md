```java
public class HdfsClient {
//    客户端对象
    private static FileSystem fs;

    @Before
    public void init() throws IOException, InterruptedException, URISyntaxException {
        //Configuration实例，这是HadoopAPI中用于存储Hadoop集群配置的标准方式，如HDFS地址等
        Configuration configuration = new Configuration();
        //设置副本个数
        configuration.set("dfs.replication", "3");
        //URI指定了Hadoop集群的地址和端口
        URI uri = new URI("hdfs://hadoop102:8020");
        //用户身份："ola"是操作文件系统时使用的用户身份。这是因为HDFS支持多用户，且根据用户身份来控制文件系统的访问权限
        String user = "ola";
        fs = FileSystem.get(uri, configuration, user);
    }

    @After
    public void close() throws IOException {
        fs.close();
    }

    // 常用操作1:创建目录
    @Test
    public void testMkdirs() throws IOException {
        fs.mkdirs(new Path("/qingshenshen/yumengmeng"));
    }

    //常用操作2:上传文件
    @Test
    public void testPut() throws IOException {
        //两个参数，上传路径，目的地路径
//        fs.copyFromLocalFile(new Path("/Users/ola/jdbc_data.sql"),new Path("/qingshenshen/yumengmeng"));
        //四个参数，上传后是否删除本地文件，上传后是否覆盖集群文件，上传路径，目的地路径
        fs.mkdirs(new Path("/qingshe nshen/rp"));
        fs.copyFromLocalFile(false, false, new Path("/Users/ola/xsync"), new Path("/qingshenshen/rp/"));
    }

    //常用操作3:API参数优先级。
    /*从高到低：
     * （1）客户端代码中设置的值 >（2）项目resource目录下的用户自定义配置文件 >（3）然后是服务器的自定义配置（xxx-site.xml） >（4）服务器的默认配置（xxx-default.xml）*/
    @Test
    public void testApi() throws IOException {
        fs.copyFromLocalFile(false, false, new Path("/Users/ola/xsync_副本2"), new Path("/qingshenshen/rp/"));
    }

    //常用操作4:下载文件
    @Test
    public void testGet() throws IOException {
        //参数的解读：
        // boolean delSrc 指是否将原文件删除
        // Path src 指要下载的文件路径
        // Path dst 指将文件下载到的路径
        // boolean useRawLocalFileSystem 是否开启文件校验，校验的话会在本地生成crc文件
        fs.copyToLocalFile(false, new Path("/jdk-8u212-linux-x64.tar.gz"), new Path("/Users/ola"), true);
    }

    //删除文件
    @Test
    public void testRm() throws IOException {
        //参数的解读: 参数1，要删除的文件路径，参数2，是否递归删除（针对有内容的文件夹）
        //常用操作5:删除文件，不需要递归
//        fs.delete(new Path("/qingshenshen/yp"),false);
        //常用操作6:删除非空目录，第二个参数true，会递归删除下面所有文件
//        fs.delete(new Path("/xiyou"),true);///xiyou/huaguoshan
        //常用操作6:删除空目录，不需要递归
        fs.delete(new Path("/xiyou1/huaguoshan"), false);
    }

    @Test
    //文件更改名称和移动
    public void testMv() throws IOException {
        //参数解读：参数1，原文件路经；参数2，目标文件路经
        //常用操作7：文件更改名称
//        fs.rename(new Path("/qingshenshen/rp"), new Path("/qingshenshen/newrp"));
        //常用操作8：文件移动并更改名称
        fs.rename(new Path("/qingshenshen/yumengmeng"), new Path("/yu"));
        //常用操作9：文件移动不改名称
//        fs.rename(new Path("/qingshenshen/newrp"), new Path("/"));
    }
    //常用操作10：文件详情查看
    @Test
    public void testListFiles() throws IOException {
        RemoteIterator<LocatedFileStatus> listFiles = fs.listFiles(new Path("/"), true);
        while(listFiles.hasNext()){
            LocatedFileStatus fileStatus = listFiles.next();
            System.out.println("========" + fileStatus.getPath() + "=========");
            System.out.println(fileStatus.getPermission());
            System.out.println(fileStatus.getOwner());
            System.out.println(fileStatus.getGroup());
            System.out.println(fileStatus.getLen());
            System.out.println(fileStatus.getModificationTime());
            System.out.println(fileStatus.getReplication());
            System.out.println(fileStatus.getBlockSize());
            System.out.println(fileStatus.getPath().getName());

            // 获取块信息
            BlockLocation[] blockLocations = fileStatus.getBlockLocations();
            System.out.println(Arrays.toString(blockLocations));
        }
    }
    //常用操作11：文件和文件夹判断
    @Test
    public void testlistStatus() throws IOException {
        FileStatus[] listStatus = fs.listStatus(new Path("/"));
        for (FileStatus status : listStatus) {
            if (status.isFile()) {
                System.out.println("文件: "+status.getPath().getName());
            }else {
                System.out.println("文件夹 :"+status.getPath().getName());
            }
        }
    }

}
```

