##查询:

SELECT * FROM table //查询整个表并返回表数据

SELECT * FROM table WHERE id = '1' //带条件查询

SELECT id,name FROM table //返回指定字段

SELECT * FROM table WHERE name `LIKE` '%value%'   //模糊查询

SELECT * FROM table ASC   //升序 (DESC为降序)

INSERT INTO table(id,name)VALUES(value1,value2)   //插入数据

DELETE FROM table WHERE id = '1'    //删除数据

UPDATE table SET name="value" WHERE id = '1'    //更新数据

SELECT SUM(id) FROM table    //id字段求和

SELECT AVG(id) FROM table    //id字段求平均数

SELECT COUNT(*) FROM table   //查询表的总行数

SELECT MAX(id) FROM table   //查询id字段的最大值

SELECT MIN(id) FROM table   //查询id字段的最小值

SELECT DISTINCT name FROM table   //过滤重复数据

