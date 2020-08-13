#### es本地安装
* 官网下载安装包 解压直接安装，访问9200端口正常运行
* `bin/elasticsearch-plugin list` 可以查看安装了哪些插件
* `bin/elasticsearch-plugin install analysis-icu` 安装一个国际化分词插件
* 访问9200端口的/_cat/plugins 可以查看插件
* 启动多集群的方式，即每个节点指定节点名称，指定相同的集群名称，指定不同的数据存放地址
```
bin/elasticsearch -E node.name=node1 -E cluster.name=es_cluster -E path.data=node1_data -d
bin/elasticsearch -E node.name=node2 -E cluster.name=es_cluster -E path.data=node2_data -d
bin/elasticsearch -E node.name=node3 -E cluster.name=es_cluster -E path.data=node3_data -d
* 访问9200/_cat/nodes可以查看目前有哪些节点

#### kibana本地安装
* 官网下载安装kibana 解压，本机启动了es之后，可以直接运行bin/kibana，默认5601
* cmd + / 查看API帮助文档
* kibana插件安装 列表 删除：
![image](http://note.youdao.com/yws/res/14663/47C1A7EF116D4DB8BDC10AC507F05F04)

#### docker compose启动es、kibana、cerebro
* docker compose 启动相关集群: 
 ![image](http://note.youdao.com/yws/res/14667/153596F6421E4746B070E4978FDF22B5)
* 本项目中有有docker compose的yml示例文件，
* cerebro在9000端口，界面输入es的地址可以连接，可以看到集群名，消耗了多少内存等数据

#### logstash安装
* 下载logstash解压
* 到movielens里下载数据集，在github上可以看到下载教程
* logstash配置文件中指定路径是下载好的数据集地址：
![image](http://note.youdao.com/yws/res/14678/E35FB9D2FA99498AB1EB63898D4A6052)
* `sudo ./logstash -f logstash.conf` 启动logstash
