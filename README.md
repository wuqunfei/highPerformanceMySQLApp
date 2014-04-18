highPerformanceMySQLApp
=======================

How to design high performance mysql application? <br>
There are so many documents on online.But I will give my best and easy solution in 23 million clients in Shanghai production enviroment.<br>

1. From monitor and parameter View<br>
If you have experiences in Mysql maintaining, there are hundreds of parameters in my.cnf. Almost of us will forget and be confused to understand very deeply.So I give you a very good tools named monyog, https://www.webyog.com/product/monyog. Getting up and running quickly is easy, and having a centralized location for monitoring is very useful. The graphs are beautiful and the statistics that are graphed are useful time-savers. And give you good advise to adjust parameter.<br>
 ![image](https://raw.githubusercontent.com/wuqunfei/highPerformanceMySQLApp/master/real-time-database.png)

2. From Developing View<br>
I think you are so understand SQL developing, but I still want to enhance INDEX power in many conditions. Re-design index to improve usage of INDEX hit-radio is easy and fast way to fix your problem at once. I suggest you can use TOAD (http://www.quest.com/toad/) which is good tool to analyze and explain SQL performance and INDEX usage instead of write explain SQL by ourselves one by one. Another SQL skill is stored procedure, if you don’t mind it will take your core Java logic into database, stored procedure is also good way for complex logic and reducing initial SQL statement parsing and optimization.<br>

3. From Maintaining View <br>
One big-data table is very slow for any database. So oracle introduced partitioned tables long times ago. MySQL copy this idea since version 5.x. If you don’t use it now, I strong recommend you could use this rocket skill. It could improve query and insert function remarkably. Simply explanation, this technology will save your one table data into several piece files on disk and have a special index to fast your query speed and reduce your IO & CPU usage. We do this strategy in every database.<br>
![image](https://raw.githubusercontent.com/wuqunfei/highPerformanceMySQLApp/master/partitioned.png)
 Beside Partition, replication is the foundation for building large, high-performance applications on top of MySQL, using the so-called “scale-out” architecture. There are so many documents on Google easily.<br>
![image](https://raw.githubusercontent.com/wuqunfei/highPerformanceMySQLApp/master/Sync.png)<br>
My team uses it in production environment. It’s easy to configure and build this architecture. But for my experience,  MySQL 5.X still need to improve their production, specially in Sync data from master to replica when exception of network or system restart. Owning to this disadvantage, we write automotive-sync-tools instead of MySQL sync when it was broken.<br>




