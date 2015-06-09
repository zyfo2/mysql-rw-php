# include file: #

```
require_once('mysql_rw_php.class.php');
```

# set mysql link info rw/ro: #

```
//rw info
$db_rw = array(
	'dbhost'=>'www.aslibra.com',
	'dbuser'=>'aslibra',
	'dbpw'=>'www.aslibra.com',
	'dbname'=>'test'
);

$db_ro = array(
	array(
		'dbhost'=>'www.aslibra.com:4306',
		'dbuser'=>'aslibra',
		'dbpw'=>'www.aslibra.com'
	)
);
```

# link to master first: #

```
$DB = new mysql_rw_php;

//connect Master
$DB->connect($db_rw[dbhost], $db_rw[dbuser], $db_rw[dbpw], $db_rw[dbname]);
```

# you have two method to link slave #

```
//Method 1: connect one server
$DB->connect_ro($db_ro[0][dbhost], $db_ro[0][dbuser], $db_ro[0][dbpw]);

//Method 2: connect one server from a list by rand
$DB->set_ro_list($db_ro);
```

# then you can use $DB as usual #