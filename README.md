Logstats
========

A small shell script to read in futuretense.txt / sites.log and output some useful info such as line count, longest line, start/end date, distribution of log levels, and highlight frequency/top20 of some common errors such as ORA-x codes, invalid param, exception including resource, element not found, pubsessions and publish speed

Not massively robust, if the logger format has been tweaked then it will have trouble parsing it.

Usage:

logstats.sh < sites.log
or
logstats sites.log
or
cat sites.log | logstats

Example output:

```
$ logstats < sites.log
First timestamp: 2013-11-18 08:15:07,368
Last timestamp: 2013-11-25 07:50:05,920
Time difference (seconds): 603298
Time difference (H:M:S): 23:34:58
lines: 54661
lines per second: .09
longest line: 543

FATAL: 0 (0% of total)
ERROR: 1127 (2.00% of total)
WARN: 264 (0% of total)
INFO: 20825 (38.00% of total)
DEBUG: 0 (0% of total)
TRACE: 0 (0% of total)

Exception including resource: 25 (0% of total)
Top 20 Exception including resource:
     23  /jsp/cs_deployed/Customer/Common/GetAssetData.jsp
      1  /jsp/cs_deployed/Customer/Page/AnotherPageTemplate.jsp
      1  /jsp/cs_deployed/Sitemap.jsp

ORA codes: 2 (0% of total)
Top 20 ORA codes:
      2 ORA-00907: missing right parenthesis

Exceptions: 645 (1.00% of total)
Top 20 Exceptions:
    286 javax.naming.AuthenticationException
     88 COM.FutureTense.Common.ContentServerException
     51 com.fatwire.cs.core.http.HttpAccessException
     47 javax.servlet.ServletException
     25 weblogic.servlet.internal.ServletStubImpl.onAddToMapException
     23 weblogic.servlet.jsp.PageContextImpl.handlePageException
     23 com.fatwire.assetapi.common.AssetNotExistException
     19 org.jasig.cas.client.validation.TicketValidationException
     19 com.fatwire.wem.sso.SSOException
     17 org.apache.http.conn.HttpHostConnectException
     17 java.net.ConnectException
     15 java.lang.NumberFormatException
      5 java.lang.RuntimeException
      3 java.lang.IllegalStateException
      2 java.sql.SQLSyntaxErrorException
      2 java.lang.NullPointerException
      1 java.net.URISyntaxException
      1 java.net.SocketException
      1 com.openmarket.basic.interfaces.AssetException
```
