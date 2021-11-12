# logstash-grafana

<img src="https://guize.com.br/logstash-grafana/logstash-grafana.png" alt="Dashboard to view Logstashs internal statistics (based on X-Pack)">

<img src="https://guize.com.br/logstash-grafana/logstash-grafana2.png" alt="Dashboard to view Logstashs internal statistics (based on X-Pack)">

<img src="https://guize.com.br/logstash-grafana/logstash-grafana3.png" alt="Dashboard to view Logstashs internal statistics (based on X-Pack)">

<br>
<h2>Dashboard to view Logstashs internal statistics (based on X-Pack)</h2>

* Queue events: Number of event queue (events in, filtered, out, event duration), etc
* JVM statistics: Memory heap used, garbage collection, JVM uptime, JVM thread count, etc
* CPU: Percent Usage, Load Average, Process File Descriptors, etc


## 💻 Prerequisites

Make sure you have met the following minimum requirements:

* Grafana 8.0.3
* Telegraf (optional)
* Telegraf - Logstash Input Plugin (optional)

## 🚀 Grafana

<b>1. Install and configure Grafana</b>

* Download and Installation: https://grafana.com/grafana/download
* Configuration: https://grafana.com/docs/grafana/v7.5/administration/configuration/

<b>2. Choose your datasource</b>
* Datasources: https://grafana.com/docs/grafana/v7.5/datasources/

<b>3. Create Variable</b>
* Instructions: https://grafana.com/docs/grafana/latest/variables/

Variable: HOST
Definition: tag_values(cpu_usage_system,host)

<b>4. Import your Dashboard using logstash-grafana code</b>
* Instructions: https://grafana.com/docs/grafana/latest/dashboards/export-import/

## 🚀 Telegraf

<b>1. Install and configure Telegraf</b>

* Download/Install e configuration: https://github.com/influxdata/telegraf

<b>2. Create configuration plugin file with "Logstash Input Plugin" content</b>

* https://github.com/influxdata/telegraf/blob/master/plugins/inputs/logstash/README.md

<b>Linux based Red-hat / Centos</b>
```
vi /etc/telegraf/telegraf.d/logstash.conf
```

<b>Configuration:</b>

```
[[inputs.logstash]]
  ## The URL of the exposed Logstash API endpoint.
  url = "http://127.0.0.1:9600"

  ## Use Logstash 5 single pipeline API, set to true when monitoring
  ## Logstash 5.
  # single_pipeline = false

  ## Enable optional collection components.  Can contain
  ## "pipelines", "process", and "jvm".
  # collect = ["pipelines", "process", "jvm"]

  ## Timeout for HTTP requests.
  # timeout = "5s"

  ## Optional HTTP Basic Auth credentials.
  # username = "username"
  # password = "pa$$word"

  ## Optional TLS Config.
  # tls_ca = "/etc/telegraf/ca.pem"
  # tls_cert = "/etc/telegraf/cert.pem"
  # tls_key = "/etc/telegraf/key.pem"

  ## Use TLS but skip chain & host verification.
  # insecure_skip_verify = false

  ## Optional HTTP headers.
  # [inputs.logstash.headers]
  #   "X-Special-Header" = "Special-Value"
```

<b>3. Restart telegraf</b>

```
service telegraf restart
```

[⬆ Voltar ao topo](#logstash-grafana)<br>

