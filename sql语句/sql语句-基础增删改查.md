SELECT 语句用于从表中选取数据

    SELECT 列名称 FROM 表名称
    SELECT   *    FROM 表名称

SELECT DISTINCT 语句(选取不重复的数据)

    SELECT DISTINCT 列名称 FROM 表名称

WHERE 子句

    SELECT 列名称 FROM 表名称 WHERE 列 运算符 值
 例 SELECT * FROM Persons WHERE City='Beijing'

	=	等于
	<>	不等于
	>	大于
	<	小于
	>=	大于等于
	<=	小于等于
	BETWEEN	在某个范围内
	LIKE	搜索某种模式

AND 和 OR 运算符

    SELECT * FROM Persons WHERE FirstName='Thomas' AND LastName='Carter'
    SELECT * FROM Persons WHERE firstname='Thomas' OR lastname='Carter'
    结合使用：
    SELECT * FROM Persons WHERE (FirstName='Thomas' OR FirstName='William') AND LastName='Carter'
    
ORDER BY 语句（指定的列对结果集进行排序）    注：DESC（文字反序）、ASC

    SELECT 列名称 FROM 表名称 ORDER BY 列名称

INSERT INTO 语句（向表格中插入新的行）

    INSERT INTO 表名称 VALUES (值1, 值2,....)
    INSERT INTO 表名称 (列1, 列2,...) VALUES (值1, 值2,....)

UPDATE 语句

    UPDATE 表名称 SET 列名称 = 新值 WHERE 列名称 = 某值

DELETE 语句

    DELETE FROM 表名称 WHERE 列名称 = 值
    
    DELETE FROM 表名称
    DELETE * FROM 表名称








