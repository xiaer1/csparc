#### CSParC（Chinese cross-domain Semantic Parsing in Context）


目前国内外并未涉及多轮跨语言上下文相关语义解析领域，我们基于英文数据集[SParC](https://yale-lily.github.io/sparc)，发布了多轮跨语言（中英文）上下文相关NL2SQL数据集。如下是CSParC数据集统计特性 和 数据示例

​																表1 CSParC数据统计

|       | 交互次数 | 问句-SQL对 | 数据库数量 | 表格数量/数据库数量 |
| :---: | :------: | :--------: | :--------: | :-----------------: |
| Total |   3456   |   10228    |    160     |        5.11         |
| Train |   2410   |    7216    |    112     |        5.16         |
|  Dev  |   374    |    1044    |     16     |        4.37         |
| Test  |   672    |    1968    |     32     |        5.31         |



​																表2 CSParC数据示例

| 需求目标：                       | 给出在最大容量的教室里授课的课程标题和学分。                 |
| -------------------------------- | ------------------------------------------------------------ |
| Q1： 教室的最大容量是多少？      | SELECT max(capacity) FROM classroom                          |
| Q2：在那里授课的课程标题是什么？ | SELECT T3.title FROM classroom AS T1 JOIN section AS T2 ON T1.building = T2.building AND T1.room_number = T2.room_number JOIN course AS T3 ON T2.course_id = T3.course_id WHERE T1.capacity = (SELECT max(capacity) FROM classroom) |
| Q3：此外，该课程有哪些学分       | SELECT T3.title, T3.credits FROM classroom AS T1 JOIN section AS T2 ON T1.building = T2.building AND T1.room_number = T2.room_number JOIN course AS T3 ON T2.course_id = T3.course_id WHERE T1.capacity = (SELECT max(capacity) FROM classroom) |



