使用的Python版本为3.10

需要安装Python的库有如下，默认版本即可
selenium（实现爬虫），jieba（实现分词），cnsenti（实现情感分析），paramiko（控制远程服务器）



下载我们需要的第三方库时

```powershell
pip install 要安装的包名 -i http://mirrors.aliyun.com/pypi/simple/ --trusted-host mirrors.aliyun.com

pip3 install confluent-kafka -i http://mirrors.aliyun.com/pypi/simple/ --trusted-host mirrors.aliyun.com
```

国内其他源

- 清华：https://pypi.tuna.tsinghua.edu.cn/simple
- 阿里云：https://mirrors.aliyun.com/pypi/simple/
- 中国科技大学 https://pypi.mirrors.ustc.edu.cn/simple/
- 华中理工大学：https://pypi.hustunique.com/
- 山东理工大学：https://pypi.sdutlinux.org/
- 豆瓣：https://pypi.douban.com/simple/



控制浏览器时需要**驱动**，下载驱动链接，下载时注意：下载和物理机中的浏览器版本匹配的驱动
ChromeDriverUrl = https://chromedriver.chromium.org/getting-started
EdgeDriverUrl = https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver

在分词时使用的 停用词表，下载链接
https://github.com/goto456/stopwords

页面的背景壁纸
https://i.pinimg.com/736x/e4/5c/e6/e45ce6f1e01ba3a30140e05867b28de0.jpg

------

第一步：部署Hadoop集群（单机/集群均可，我的是Hadoop2.9.2集群部署）

运行命令：

```shell
start-dfs.sh
start-yarn.sh
mr-jobhistory-daemon.sh start historyserver
```

第二步：将`wordcount_one.jar`文件移动到Hadoop主节点的桌面（我的是在：/home/setting-sail/Desktop/wordcount_one.jar）

第三步：将`had.sh`文件也移动到Hadoop主节点的桌面（我的是在：/home/setting-sail/Desktop/had.sh）

运行命令：

```shell
# 注：执行前将脚本中所包含的主机名修改为自己的
bash had.sh
```

第四步：开始Python爬虫部分

第五步：调试成功后，双击`index.html`便可以打开看板



在运行Python脚本时，只需要运行`spider_douyin.py`与`CYT.py`文件即可，无先后顺序。

> 注：将代码中的服务器IP需改为自己的，以及登录的账户&密码



建议先在集群中运行`had.sh`文件，再在本地进行弹幕爬取



网页端的展示为`index.html`文件，爬到数据后直接点击打开即可，（在Edge与Chrome中均无问题）

------

## 特殊情况

一、如果Hadoop意外进入安全模式，使用以下命令即可

```shell
# 退出安全模式
hdfs dfsadmin -safemode leave

# 检查是否已成功退出安全模式
hdfs dfsadmin -safemode get
# 如果输出结果为"safe mode is OFF", 则表示安全模式已成功关闭
```

二、GitHub拉取如果困难，可以使用以下网站

https://doget.nocsdn.com/#/

------

*如果有其他问题，联系方式*
*tadpole_2021#163.com(#换成@)*