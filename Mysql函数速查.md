#### 表格中的数据修改

##### 插入数据

<font color=green>insert</font>：`insert into table_name values(),(),...`  

​		一次性插入多行数据

​		`insert ignore into table_name values()`  

​		插入如下数据,如果数据已经存在，请忽略

​		`insert into table_name select * from table_name2`

​		将从其他表中查询到的结果插入表中

##### 表数据删除

<font color=darkgreen>delete</font>：`delect from table_name where field ...`

​		对表中的数据进行删除

##### 表数据修改

<font color=darkgreen>update</font>：`update table_name set field_name = value where`

​		对表中的数据进行修改和更新

##### 索引

<font color=darkgreen>create index</font>：`create index index_name on table_name(field_name)`

​			  为表中的某一字段创建**普通**索引

​			  `create unique index index_name on table_name(field_name)`

​			  为表中的某一字段创建**唯一**索引

<font color=darkgreen>drop index</font>：`drop index index_name on table_name`

​			删除表中的某一索引

<font color=darkgreen>force index</font>：`select * from table_name force index (index_name) where ...`

​			 使用强制索引进行查询

##### 视图

<font color=darkgreen>creat view</font>：`create view view_name as select field_name1,field_name2 from table_name`

​			为表中的字段创建视图

<font color=darkgreen>drop view</font>：`drop view view_name`

​		   删除创建的视图

##### 表字段修改

<font color=darkgreen>alter table...drop</font>：`alter table table_name drop field_name`

​					删除表中的某一字段

<font color=darkgreen>alter table...add</font>：`alter table table_name add field_name varchar(255) not null`

​				   为表格添加某一字段，并设置字段类型

​				   `alter table table_name add field_name int not null first`

​				   将新添加的字段置于表格首行

​				   `alter table table_name add field_name1 int not null after field_name2`

​				   将新添加的字段置于表格的另一字段之后

<font color=darkgreen>alter table...modify</font>：`alter table table_name modify field_name char(255)`

​					  修改表格中某一字段的数据类型

​			 		`alter table table_name modify field_name char(255) default 100`

​					 修改表中某一字段的数据类型以及默认值

<font color=darkgreen>alter table...change</font>：`alter table table_name change field_name1 field_name2 char(255)`

​					  修改表格中某一字段的字段名称及数据类型，要修改的字段名+指定新字段名及类型

<font color=darkgreen>alter table..alter</font>：`alter table table_name alter field_name set default 100`

​				    修改表中某一字段的默认值

<font color=darkgreen>alter table...rename to</font>：`alter table table_name rename to new_table_name`

​						 修改表名

#### 字符串处理函数

##### 字符串拼接

<font color=darkgreen>concat</font>：`concat(str1,separator,str2,separator,str3,...)`

​		对字段进行拼接，每个拼接字段后都要加分割符号，若分割符号为null，字段直接进行拼接

<font color=darkgreen>concat_ws</font>：`concat_ws(separator,str1,str2,str3,...)`

​		   对字段进行拼接，在最开始的时候指定分隔符号，后续字段不用添加分隔符号

<font color=darkgreen>group_concat</font>：`group_concat(distinct field_name order by field_name asc/desc separator ',')`

​			  对相同行的字段进行拼接

##### 取整函数

<font color=darkgreen>round()</font>：`round(fiele_name,decimals)`

​		 把数值字段舍入为指定的小数位数

<font color=darkgreen>floor</font>：`floor(field_name)`

​	   向下取整，主要用于获得小于或等于数值表达式的最大整数

<font color=darkgreen>ceiling</font>：`ceiling(field_name)`

​		 向上取整，主要用于获得大于或等于数值表达式的最小整数

#### 子句查询函数

<font color=darkgreen>if</font>：`if(expr1,expr2,expr3)`

​	如果expr1为True，返回expr2，如果expr1为False，返回expr3

<font color=darkgreen>case when</font>：`case when expr1 then expr2 else expr3 end`

​		   如果expr1为True，返回expr2，如果expr1为False，返回expr3

#### 窗口函数

##### 排名

<font color=darkgreen>rank_number()</font>：`rank_number() over(partition by field_name order by field_name desc/asc)`

​			   按照值排序时产生一个自增编号，不会重复（如：1、2、3、4、5、6）

<font color=darkgreen>rank()</font>：`rank() over(partition by field_name order by field_name desc/asc)`

​		按照值排序时产生一个自增编号，值相等时会重复，会产生空位（如：1、2、3、3、3、6）

<font color=darkgreen>dense_rank()</font>：`dense_rank() over(partition by field_name order by field_name desc/asc)`

​			  按照值排序时产生一个自增编号，值相等时会重复，不会产生空位（如：1、2、3、3、3、4）

#### 时间函数

<font color=darkgreen>timestampdiff()</font>：`timestampdiff(interval,before_datetime,after_datetime)`

​				 返回日期之间的整数差，interval(year,month,week,day,hour,minute,second)

<font color=darkgreen>year()</font>：`year(datetime)`

​		返回某一时间对象的年份

<font color=darkgreen>month()</font>：`year(datetime)`

​		返回某一时间对象的月份

<font color=darkgreen>week()</font>：`week(datetime)`

​		返回某一时间对象在当前年份的周数

