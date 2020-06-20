# Running Training Log - Projected Miles Run, Average Pace, Total Miles for the Week 
Running Weekly Training Log 

I used a couple of functions in this project. I was inspired by my class, Stat 20, to use the 
tools I learned for my own life. 


The first function I use is a function that calculates the average running pace that I ran for the day. 
It also prints the miles I ran for that day, because it needs to follow suit with the other entries. 

```{r}
library(hms)
miles_run1= 8.57
print(miles_run1)
time_running1=hms(0,60)
converted_time_running=as.numeric(time_running1)
dec_runningtime=converted_time_running/miles_run1
time_in_minutes=(dec_runningtime)/60
floored_minutes=floor(time_in_minutes)
dec=time_in_minutes-trunc(time_in_minutes)
time_in_seconds=dec*60
time_stored=(hms(time_in_seconds,floored_minutes))
print(time_stored)
```


The second function I used was to calculate the total miles for the week. 

```{r}
miles_total=data.frame(miles_run1, miles_run2,miles_run3,miles_run4, miles_run5,miles_run6,miles_run7)
new_variable=sum((miles_total))
print(new_variable)
```

This function sums the values stored in the miles variables into a data frame, takes the sum, and stores that in a variable. 

The third function calculates the total time run for the week. 

```{r}
hours_run=as.numeric(time_running1+time_running2+time_running3+time_running4+time_running5+time_running6+time_running7)
converted_hours=hours_run/3600
floored_hours=floor(converted_hours)
converted_minutes=converted_hours-trunc(converted_hours)
dec_minutes=converted_minutes*60
print(hms(0,dec_minutes,floored_hours))
```

This function takes the numeric of the running time in hours, seconds, and minutes. 
For example, hms(1,10) is 10 minutes and 1 second, so the as.numeric() version is 601 seconds. Then, 
the function converts the seconds into hours. The hours are floored, to be saved for the final step. 
The next function isolated the decimal of the hour. Say you had 8.36 hours as the converted_hours decimal. 
The converted_minutes would isolate the 0.36. 
Then the decimal is converted into minutes by multiplying the decimal by 60. Finally, using the hms function, 
we can put it all together. We print 0 as the seconds variable, because we would like to round in this scenario, 
leaving out the seconds. For minutes, we have those stored in the dec_minutes variable. Lastly, floored hours
holds the hours run for the week. 

The final function is the average pace for the week. I split this function into multiple parts to 
make it easier for myself to read. 

# Average Pace for the Week 

```{r}
#need to get the total miles run for the week 
miles_total=data.frame(miles_run1, miles_run2,miles_run3,miles_run4, miles_run5,miles_run6,miles_run7)
total_miles=sum((miles_total))

#need to get the total minutes for the week 
hours_run=as.numeric(time_running1+time_running2+time_running3+time_running4+time_running5+time_running6+time_running7)
into_minutes=hours_run/60

#need to divide the total minutes for the week by the total miles for the week 

minutes_per_mile=into_minutes/total_miles

#need to floor the minutes and seconds 

floored_minutes_total=floor(minutes_per_mile)
dec=minutes_per_mile-trunc(minutes_per_mile)
time_in_seconds=dec*60
time_stored=(hms(time_in_seconds,floored_minutes_total))

print(time_stored)
```

The first part of the function totals the miles for the week from a data fram miles_total, and sets the sum to a variable, 
total_miles. 

We acquire the total minutes for the week by converting the total seconds of 
the week from the numeric total of the sum of the running times for the week 
and dividing that by 60 in a stored variable, into_minutes. 

Now we have the total miles run, and the total minutes run for the week. 

The minutes per mile can be found by dividing the total minutes by total miles variables. However, 
we need to do one final step. The last section of code floors the minutes, truncates the decimal and converts that into seconds, 
and stores that in a variable, time_stored. 

Once we print that function, we have printed the average running pace for the week. 
