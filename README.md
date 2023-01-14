# Get week day with MySQL
## Find out the day of the week using mysql

How to use?

```C++
    
static const days_name[7][22] = {"monday", "tuesday", "wednesday", "thursday", "friday", "saturday", "sunday"};

printf("current week day: %s", days_name[ get_week_day() ]);

```