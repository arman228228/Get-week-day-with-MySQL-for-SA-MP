# Get week day with MySQL
### Find out the day of the week using MySQL

Function:

```Pawn

get_week_day()
{
	new day_id,
    	Cache: mysql_result,
		year, month, day,
		fmt_date[36];
		
	getdate(year, month, day);
	
 	/*
  	mysql_connect_id - instead, use your database connection variable
 	*/
  
	mysql_format(mysql_connect_id, fmt_date, 64, "SELECT WEEKDAY(\"%02d-%02d-%d\")", year, month, day);
	
	mysql_result = mysql_query(mysql_connect_id, fmt_date);
	
	if(cache_num_rows())
		cache_get_value_index_int(0, 0, day_id);

	if(cache_is_valid(mysql_result)) 
    	cache_delete(mysql_result);
    
  	return day_id;
}

```

How to use:

```Pawn
    
static const days_name[7][22] = {
	"monday", "tuesday", "wednesday", "thursday", "friday", "saturday", "sunday"
};

printf("current week day: %s", days_name[ get_week_day() ]);

```
