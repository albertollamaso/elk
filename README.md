
# Elasticsearch stack scripts and snippets


- ## Slack integration
In order to be able to send alerts to slack from the watcher you need to configure a Slack webhook in the elasticsearch.yml file of your ES cluster:


 xpack.notification.slack:
   account:
     monitoring:
       url: https://hooks.slack.com/services/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K



- ## Watcher

*Source:* https://www.elastic.co/guide/en/kibana/current/watcher-ui.html

A watcher enables you to monitor, manage, create and simulate watches for your Elasticsearch indices and send alerts to your team using Slack, Email or others communication channels.

**Attention**: All the metrics used by the watcher are collected by Metricbeats by default. There are not customization or transformation in between. meaning if you deploy Metricbeats agent on your servers, you expect these watchers works properly with your data.



#### CPU Alerts
- **Check Interval:** 5 minutes
- **Indice:** metricbeat-*
- **Trigger:** *system.cpu.idle.pct* less than 1.0

#### Disk  Usage Alerts
- **Check Interval:** 5 minutes
- **Indice:** metricbeat-*
- **Trigger:** *system.filesystem.used.pct* less than 1 and Greater than or equal to 0.98

#### Memory Alerts
- **Check Interval:** 5 minutes
- **Indice:** metricbeat-*
- **Trigger:** *system.memory.used.pct* Greater than or equal to 0.90

#### SSL certificate expire Alerts
- **Check Interval:** 7 days
- **Indice:** heartbeat-*
- **Trigger:** *tls.certificate_not_valid_after* Less than or equal to 30 days

#### Website Uptime Alerts
- **Check Interval:** 3 minutes
- **Indice:** heartbeat-*
- **Trigger:**  *monitor.status* is **down**

- ## Curator
*Source:* https://github.com/elastic/curator

Have indices in Elasticsearch? This is the tool for you!

Like a museum curator manages the exhibits and collections on display, Elasticsearch Curator helps you curate, or manage your indices.

*Example Usage:* curator --config ~/.curator/curator.yml delete_indices.yml


- ## Kubernetes Logs and Monitoring

#### Colecting metrics from Kubernetes cluster using [Metricbeats](https://www.elastic.co/es/products/beats/metricbeat "Metricbeats")

https://www.elastic.co/guide/en/beats/metricbeat/current/running-on-kubernetes.html
#### Visualization

![K8s Nodes CPU](https://github.com/albertollamaso/elk/blob/master/images/nodescpu.png)
![K8s Nodes Memory](https://github.com/albertollamaso/elk/blob/master/images/nodesmemory.png)
![K8s Pods CPU](https://github.com/albertollamaso/elk/blob/master/images/podscpu.png)
![K8s Pods Memory](https://github.com/albertollamaso/elk/blob/master/images/podsmemory.png)
![K8s Resource Usage Table](https://github.com/albertollamaso/elk/blob/master/images/resourceusage.png)