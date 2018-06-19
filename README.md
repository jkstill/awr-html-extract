
# Extract CSV Data from AWR HTML Reports


HTML AWR reports have been converted to asciidoc via pandoc

[pandoc](https://pandoc.org/)

pandoc --columns=65000 --eol=lf --ascii -f html -t asciidoc INFILE -o OUTfILE

## Why do this?

Becuase sometimes the only available AWR data is from HTML reports that have been saved.

Otherwise and AWR diff report would have be quite useful.

So, get data from the following report sections


Begin Time
Elapsed Time 
DB Time

Both Elapsed and DB Time are reported in minutes, and converted to seconds.

Time, Executions and Average times from 

- Load Profile
- Top 5 Timed Foreground events
- CPU stats
- Memory stats
- Time Model Statistics
- Operating System Statistics
- Operating System Statistics (detail)
- Foreground Wait Class
- SQL ordered by Elapsed Time
- SQL ordered by CPU Time
- SQL ordered by User I/O Wait Time

Some of the SQL stats
Top 10 from each of :

- Top Foreground Wait Events
- Top Background Wait Events


Example:


./parse-awr.pl awrrpt*.txt

Begin Time: 25-Sep-17 08:00:01
Elapsed Seconds: 39600.6
DB Seconds: 629137.2
 
Begin Time: 06-Nov-17 08:00:01
Elapsed Seconds: 32400.6
DB Seconds: 523926

Begin Time: 07-Nov-17 02:00:02
Elapsed Seconds: 3599.4
DB Seconds: 91552.8

Begin Time: 12-Dec-17 09:00:01
Elapsed Seconds: 10800
DB Seconds: 162718.8

Begin Time: 12-Dec-17 12:00:01
Elapsed Seconds: 21600.6
DB Seconds: 282987


>  ls -l *.csv
-rwxr-xr-x 1 oracle dba  4363 Jun 19 15:28 background-wait-events.csv
-rwxr-xr-x 1 oracle dba  3136 Jun 19 15:28 foreground-wait-class.csv
-rwxr-xr-x 1 oracle dba  4387 Jun 19 15:28 foreground-wait-events.csv
-rwxr-xr-x 1 oracle dba   414 Jun 19 15:28 host-cpu.csv
-rwxr-xr-x 1 oracle dba   343 Jun 19 15:28 instance-cpu.csv
-rwxr-xr-x 1 oracle dba  5035 Jun 19 15:28 load-profile.csv
-rwxr-xr-x 1 oracle dba  1474 Jun 19 15:28 memory-stats.csv
-rwxr-xr-x 1 oracle dba 11000 Jun 19 15:28 os-stats-detail.csv
-rwxr-xr-x 1 oracle dba  6377 Jun 19 15:28 os-stats.csv
-rwxr-xr-x 1 oracle dba  9361 Jun 19 15:28 sql-by-cpu.csv
-rwxr-xr-x 1 oracle dba  9124 Jun 19 15:28 sql-by-elapsed.csv
-rwxr-xr-x 1 oracle dba  9229 Jun 19 15:28 sql-by-io.csv
-rwxr-xr-x 1 oracle dba  5729 Jun 19 15:28 time-model-stats.csv
-rwxr-xr-x 1 oracle dba  2180 Jun 19 15:28 top-foreground-events.csv


