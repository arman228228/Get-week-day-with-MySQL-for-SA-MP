# Get week day with MySQL
### Find out the day of the week using MySQL

Function (MySQL R41 Version):

```Pawn

get_week_day()
{
	new day_id,
    	       Cache: mysql_result,
	       year, month, day,
	       fmt_date[35];
		
	getdate(year, month, day);
	
 	/*
  	mysql_connect_id - instead, use your database connection variable
 	*/
  
	format(fmt_date, sizeof(fmt_date), "SELECT WEEKDAY(\"%02d-%02d-%d\")", year, month, day);
	
	mysql_result = mysql_query(mysql_connect_id, fmt_date);
	
	if(cache_num_rows())
		cache_get_value_index_int(0, 0, day_id);

	cache_delete(mysql_result);
    
  	return day_id;
}

```

Function (MySQL R39 Version):

```Pawn

get_week_day()
{
	new day_id,
    	Cache: mysql_result,
		year, month, day,
		fmt_date[35];
		
	getdate(year, month, day);
	
 	/*
  	mysql_connect_id - instead, use your database connection variable
 	*/
  
	format(fmt_date, sizeof(fmt_date), "SELECT WEEKDAY(\"%02d-%02d-%d\")", year, month, day);
	
	mysql_result = mysql_query(mysql_connect_id, fmt_date);
	
	if(cache_num_rows())
    	       day_id = cache_get_row_int(0, 0, mysql_connect_id);

	cache_delete(mysql_result);
    
  	return day_id;
}

```

How to use:

```Pawn
    
static const days_name[7][12] = {
	"monday", "tuesday", "wednesday", "thursday", "friday", "saturday", "sunday"
};

printf("current week day: %s", days_name[ get_week_day() ]);

```
