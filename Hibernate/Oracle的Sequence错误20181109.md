bug描述：严重: ORA-00001: 违反唯一约束条件 (BSPARCH.SYS_C00389189) 500，Oracle数据插入唯一索引条件不满足，报错位置为持久化层增加函数。

解决过程：找到报错位置，进行debug调试发现ID为空，使用输出函数查看输出内容，自认为是ID为空造成的，但经过在实体类的toString()和equals()方法，发现ID存在。并在控制台输出
Menu [id=414, menuName=1212, pageUrl=1212, parentMenu=Menu [id=2, menuName=系统管理, pageUrl=null, parentMenu=Menu [id=1, menuName=菜单, pageUrl=null, parentMenu=null, desc=null, users=[]], desc=null, users=[]], desc=null, users=null]，问题就出现在ID上，每次的ID变化均会与数据库表中的ID重复。

解决方法：造成bug的原因是项目采用了Hibernate操作Oracle数据库 主键自增方法，只需将序列初始值改变即可具体方法如下。

	Oracle 序列（Sequence）主要用于生成流水号，在应用中经常会用到，特别是作为ID值，拿来做表主键使用较多。

	方法一：
		先删除序列，然后重新创建。
		DROP SEQUENCE seq_newsId； //seq_newsId为序列名
		CREATE SEQUENCE [user.]sequence_name
	    [increment by n]
	    [start with n]
	    [maxvalue n | nomaxvalue]
	    [minvalue n | nominvalue];
	    INCREMENT BY： 指定序列号之间的间隔，该值可为正的或负的整数，但不可为0。序列为升序。忽略该子句时，缺省值为1。
	    START WITH：指定生成的第一个序列号。在升序时，序列可从比最小值大的值开始，缺省值为序列的最小值。对于降序，序列可由比最大值小的值开始，缺省值为序列的最大值。
	    MAXVALUE：指定序列可生成的最大值。
	    NOMAXVALUE：为升序指定最大值为1027，为降序指定最大值为-1。
	    MINVALUE：指定序列的最小值。
	    NOMINVALUE：为升序指定最小值为1。为降序指定最小值为-1026。

	方法二：
		写个循环来增加。如果需要增加500，写个循环运行500次
		SELECT SEQUENCE_NAME.NEXTVAL FROM DUAL;

	方法三：
		通过Increment By来实现修改初始值
			若序列名称是SEQ_TEST，初始值是13，而现在要设置初始值为1013，Increment By值为:1000(1013-13)
			ALTER SEQUENCE SEQ_TEST INCREMENT BY 1000;
			SELECT SEQ_TEST.NEXTVAL FROM DUAL; //查询SEQ_TEST.NEXTVAL的值
			ALTER SEQUENCE SEQ_TEST INCREMENT BY 1;