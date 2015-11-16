Sparklda教程

1. 下载源码：
```
git clone http://gitlab.baidu.com/liuweiwei02/SparkLda.git
```

2. 准备语料，语料格式：
```
0:1 3:4 12:3 ...
```
一行是一个文档，『0:1』表示id为0的词在该文档出现一次，词之间空格区分。

3.修改setting.py中的配置，主要是NUM_TERM和K的赋值
```
NUM_TERM=term的总数
K=topic总数
```

4. 压缩setting.py 和utils.py:
```
tar czvf pac.tar.gz setting.py utils.py
```

5. 运行：
```
spark-submit --py-files pac.tar.gz SparkLda.py data
```
其中data是语料文件，一般为hdfs绝对路径。

6.结果说明：
beta.final（python二维数组直接打印）beta[i][j]表示第i个topic中term j的权重。

目前版本不对alpha进行更新，所以结果只有beta，想过跟alpha更新差不多