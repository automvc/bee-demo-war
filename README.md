
Bee
=========
**Bee** is an ORM framework.  
**Honey** is the implementation of the Bee.  
**Bee** is **I Sea** (Intuitive,Simple, Easy, Automatic) style ORM framework.  
**Bee** see:  
https://github.com/automvc/bee  
**Honey** see:  
https://github.com/automvc/honey  

## [中文介绍](https://github.com/automvc/bee/blob/master/README_CN.md)  
[点击链接可查看中文介绍](https://github.com/automvc/bee/blob/master/README_CN.md)  

## Requirement  
jdk1.7+

## Feature & Function: 

**V1.0**  
Single entity(table) Suid (select,update,insert,delete) object-oriented operation.  
Automatically generate the Javabean via DB table or view(MySQL,MariaDB).  
Javabean no annotation,no xml.  
Automatically mapping the table column and the Javabean field.  
Javabean support the raw type:int,double,and so on.  
PreparedStatement support.  
Procedure support.  
Native SQL support.  
Batch operate support.  
Transaction support.  
Automatic filter the null and empty field for default.  
MAX,MIN,SUM,AVG,COUNT support.  
Order by,Paging.  
Select some field.  
Dynamic & random combination of query conditions,no need to prepare the interface in advance; new query requirements, no need to change the query interface.  
All Suid(select,update,insert,delete) operation use the same Bee interface,no longer need any new dao interface.  
Users/Developer only need to pay attention to the Bee interface.  

**V1.1**  
Json format Result support.  
Procedure(Query type) support.  

**V1.2**  
Customer sql support #{para} placeholder,eg:name=#{name}; like keyword support:#{%para%},#{%para},#{para%}  

Quick Start:
=========	
## 1. Create the database and the table  

Create one database,default name is bee.  
Create the table and init the data by run the bee.sql file(it is mysql sql script).  

## 2. Update the database configuration in bee.properties if need  

bee.db.driverName = com.mysql.jdbc.Driver  
bee.db.url =jdbc:mysql://localhost:3306/bee?characterEncoding=UTF-8  
bee.db.username = root  
bee.db.password =  

## 3. Run the following java code  

```java
		
import java.math.BigDecimal;
import java.util.List;

import org.bee.osql.Suid;
import org.honey.osql.core.BeeFactory;
import org.honey.osql.example.entity.Orders;

/**
 * @author KingStar
 * @since  1.0
 */
public class OsqlExamEN {
	
	public static void main(String[] args) {
		Suid suid=BeeFactory.getHoneyFactory().getSuid();
		
		Orders orders1=new Orders();
		orders1.setId(100001L);
		orders1.setName("Bee--ORM Framework");
		
		List<Orders> list1 =suid.select(orders1);  //select
		for (int i = 0; i < list1.size(); i++) {
			System.out.println(list1.get(i).toString());
		}
		
		orders1.setName("Bee--ORM Framework");
		int updateNum=suid.update(orders1);   //update
		System.out.println("update record:"+updateNum);
		
		Orders orders2=new Orders();
		orders2.setUserid("client01");
		orders2.setName("ORM book");
		orders2.setTotal(new BigDecimal(91));
		orders2.setRemark("");  //empty String test
		
		int insertNum=suid.insert(orders2); //insert
		System.out.println("insert record:"+insertNum);
		
		int deleteNum=suid.delete(orders2);   //delete
		System.out.println("delete record:"+deleteNum);
		
		List<Orders> list2 =suid.select(orders1); //select  confirm the data
		for (int i = 0; i < list2.size(); i++) {
			System.out.println(list2.get(i).toString());
		}
	}

}
```


#### Author's email:    honeysoft@126.com  
##### If you have any problem on bee, please let me know kindly! Thank you, so much! 
