# Get week day with MySQL
### Find out the day of the week using mysql

Function:

```Pawn

get_week_day()
{
	new dayid,
    	Cache: result,
		year, month, day,
		fmt_date[64];
		
	getdate(year, month, day);
	
 	/*
  	mysql_connect_id - instead, use your database connection variable
 	*/
  
	mysql_format(mysql_connect_id, fmt_date, 64, "SELECT WEEKDAY(\"%02d-%02d-%d\")", year, month, day);
	
	result = mysql_query(mysql_connect_id, fmt_date);
	new rows = cache_num_rows();

	if(rows)
		cache_get_value_index_int(0, 0, dayid);

	if(cache_is_valid(result)) 
    	cache_delete(result);
    
  	return dayid;
}

```

How to use:

```Pawn
    
static const days_name[7][22] = {"monday", "tuesday", "wednesday", "thursday", "friday", "saturday", "sunday"};

printf("current week day: %s", days_name[ get_week_day() ]);

```
