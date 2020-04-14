## How to Generate Date's between start date & today. 

```
from datetime import datetime, timedelta 

def get_range_date(inputdate):
    out = []
    today = datetime.today() #dtobject
    #today_ddmmyy = datetime.now().strftime('%d%m%y')  #string 
    next = datetime.strptime(inputdate,'%d%m%y')
    #Return null if the given date > today.
    if today < next:
        print (f'Error: Given date \'{next}\' is beyond today. returned null !.')
        return (out)
    #Do Loop untill  the date is today
    while today > next: 
        out.append(next)
        next = next + timedelta(days=1)
    return(out)
 ````

## Running the Function 
```
input = '290320' #ddmmyy format 
get_range_date(input)

> #Result 
[datetime.datetime(2020, 3, 29, 0, 0),
 datetime.datetime(2020, 3, 30, 0, 0),
 datetime.datetime(2020, 3, 31, 0, 0),
 datetime.datetime(2020, 4, 1, 0, 0),
 datetime.datetime(2020, 4, 2, 0, 0),
 datetime.datetime(2020, 4, 3, 0, 0),
 datetime.datetime(2020, 4, 4, 0, 0),
 datetime.datetime(2020, 4, 5, 0, 0),
 datetime.datetime(2020, 4, 6, 0, 0),
 datetime.datetime(2020, 4, 7, 0, 0),
 datetime.datetime(2020, 4, 8, 0, 0),
 datetime.datetime(2020, 4, 9, 0, 0),
 datetime.datetime(2020, 4, 10, 0, 0),
 datetime.datetime(2020, 4, 11, 0, 0),
 datetime.datetime(2020, 4, 12, 0, 0),
 datetime.datetime(2020, 4, 13, 0, 0)]
 
 ```
 
## Re-using this dateRange generator function for practical use's. 
> Generate FileNames(.json) who has mmddyy format for each day  . 

```
 def get_array_files(fprefix,inputdate):
    for i in get_range_date(inputdate):
        day_str = i.strftime('%d%m%y')
        print(f'{fprefix}_{day_str}.json')


get_array_files('FilePrefix','290320')
#Result
FilePrefix_290320.json
FilePrefix_300320.json
FilePrefix_310320.json
FilePrefix_010420.json
FilePrefix_020420.json
FilePrefix_030420.json
FilePrefix_040420.json
FilePrefix_050420.json
FilePrefix_060420.json
FilePrefix_070420.json
FilePrefix_080420.json
FilePrefix_090420.json
FilePrefix_100420.json
FilePrefix_110420.json
FilePrefix_120420.json
FilePrefix_130420.json
FilePrefix_140420.json

```
