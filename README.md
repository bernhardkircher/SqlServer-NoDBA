# SqlServer-NoDBA

This repository contains scripts,links,.. on how to handle/monitor/maintain/troubleshoot an MS SQLServer as a software developer and you don't have a fulltime DBA.

# Where to begin
http://www.brentozar.com/sql/developers-guide-faking-database-administration/

# Start-Troubleshooting
Sites/Queries that help to get an overview of the current system

## who-is-active
http://sqlblog.com/blogs/adam_machanic/archive/2012/03/22/released-who-is-active-v11-11.aspx

 It can be used in several ways, to see what is running at the moment you launch the script or you can run it in loops to monitor some specific action, as slow queries for example.
 sell also: http://www.brentozar.com/archive/2010/09/sql-server-dba-scripts-how-to-find-slow-sql-server-queries/
 

https://sqlserverperformance.wordpress.com/2010/12/29/updated-sql-2005-and-2008-diagnostic-queries/

### What to do in case of a problem:
exec sp_whoisactive @get_locks = 1, @get_additional_info = 1

which returns inforamtion about the current executing queries (duration, who executed it, executed sql, locks, current state of the query, IO inforamtion etc). Additional pass the @get_plans = 1 parameter to retrive each queries execution plan (may be slow).
see 

https://www.brentozar.com/archive/2010/09/sql-server-dba-scripts-how-to-find-slow-sql-server-queries/
http://sqlblog.com/blogs/adam_machanic/default.aspx
http://sqlmag.com/sql-server/spwhoisactive

#### Asp.Net/IIS related analysis:

What to do in case of a lock and you are running asp.net on IIS and have no existing logging/tools within your application:
execute in powershell as admin (or via IIS Manager GUI - see links below):
c:\windows\system32\inetsrv\appcmd list requests /elapsed:1000
which gives you current running IIS Requests.
see for more info:
https://technet.microsoft.com/en-us/library/cc732518(v=ws.10).aspx 
http://www.iis.net/learn/get-started/getting-started-with-iis/getting-started-with-appcmdexe

If this is not possible, additional options would be:
- use IIS Logparser to analyze the logfiles (long running requeusts) etc.
http://www.iis.net/downloads/community/2010/04/log-parser-22 
or use IIS Logparser Lizard ($)
- Use tools like Glimpse or Miniprofiler and add it to your application to gain isnight into your application.
http://getglimpse.com/
http://miniprofiler.com/
- 

# Temp DB:
http://www.brentozar.com/blitz/tempdb-data-files/
