## Manage container logs using ELK Stack

The implementation architecture will be as follows-

![](https://github.com/dipakongit/devops_doc/blob/main/docker/images/elk1.png)

### What is ELK?

The ELK Stack consists of three open-source products - Elasticsearch, Logstash, and Kibana from Elastic. 
    • Elasticsearch is a NoSQL database that is based on the Lucene search engine. 
    • Logstash is a log pipeline tool that accepts inputs from various sources, executes different transformations, and exports the data to various targets. It is a dynamic data collection pipeline with an extensible plugin ecosystem and strong Elasticsearch synergy 
    • Kibana is a visualization UI layer that works on top of Elasticsearch. 
These three projects are used together for log analysis in various environments. So Logstash collects and parses logs, Elastic search indexes and store this information while Kibana provides a UI layer that provide actionable insights.

### Why it use?

  * Consider you have a single application running and it produces logs. Now suppose you want analyze the logs generated. One option is to manually analyze them. But suppose these logs are large, then manually analyzing them is not feasible. 
  * Suppose we have multiple Application running and all these applications produce logs. If we have to analyze the logs manually we will need to go through all the log files. These may run into hundreds. 
  We can use ELK here to analyze the logs more efficiently and also using more complex search criterias. It provides log aggregation and efficient searching. 
  
### Config and Run ELK Stack at Docker Container

Create [docker-compose.yml](https://github.com/dipakongit/devops_doc/blob/main/docker/manage%20container%20logs%20using%20elk/docker-compose.yml) , 
[logstash.conf](https://github.com/dipakongit/devops_doc/blob/main/docker/manage%20container%20logs%20using%20elk/logstash.conf), 
[Dockerfile](https://github.com/dipakongit/devops_doc/blob/main/docker/manage%20container%20logs%20using%20elk/Dockerfile) at same directory 

* Elasticsearch default port ```9200```. URL ```http://localhost:9200```
* Kibana default port ```5601```. URL ```http://localhost:5601```

### We use Syslog driver to get logs of each container

The syslog logging driver routes logs to a syslog server. The syslog protocol uses a raw string as the log message and supports a limited set of metadata. The syslog message must be formatted in a specific way to be valid. From a valid message, the receiver can extract the following information:
    * **priority**: the logging level, such as debug, warning, error, info. 
    * **timestamp**: when the event occurred. 
    * **hostname**: where the event happened. 
    * **facility**: which subsystem logged the message, such as mail or kernel. 
    * **process name and process ID (PID)**: The name and ID of the process that generated the log. 

```
             TIMESTAMP  HOSTNAME  APP-NAME  PROCID  MSGID
                    +          +             +           |        +
                    |          |             |           |        |
                    |          |             |           |        |
       +------------+          +----+        |           +----+   +---------+
       v                            v        v                v             v
2017-04-01T17:41:05.616647+08:00 a.vm {taskid:aa,version:} 1787791 {taskid:aa,version:}
```
syslog driver as the default logging driver which already have in docker. 


