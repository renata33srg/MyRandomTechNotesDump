# Observability Tools

- [Prometheus](#prometheus)
- [Grafana](#grafana)
- [Kiali](#kiali)

## Prometheus <a name="prometheus"></a>

Prometheus is an open-source systems monitoring and alerting toolkit that collects and stores its metrics as time series data, i.e. metrics information is stored with the timestamp at which it was recorded, alongside optional key-value pairs called _labels_.  

### Main features

- a multi-dimensional [data model](#datamodel) with time series data identified by metric name and key/value pairs
- **PromQL**, a flexible [query language](#querylanguage) to leverage this dimensionality
- no reliance on distributed storage; single server nodes are autonomous 
- time series collection happens via a pull model over HTTP
- [pushing time series](#pushingtimeseries) is supported via an intermediary gateway
- targets are discovered via service discovery or static configuration
- multiple modes of graphing and dashboarding support  

---

Notes of main features

<details>
<summary>Data Model <a name="datamodel"></a></summary> 

>
> Prometheus fundamentally stores all data as time series: streams of timestamped values belonging to the same metric and the same set of labeled dimensions. Besides stored time series, Prometheus may generate temporary derived time series as the result of queries.
> 
> **Metric names and labels**  
> Every time series is uniquely identified by its metric name and optional key-value pairs called _labels_.
> The metric name specifies the general feature of a system that is measured (e.g. http_requests_total - the total number of HTTP requests received). It may contain ASCII letters and digits, as well as underscores and colons. It must match the regex `[a-zA-Z_:][a-zA-Z0-9_:]*`.
> 
>> Note: The colons are reserved for user defined recording rules. They should not be used by exporters or direct instrumentation.
>
> *Labels* enable Prometheus's dimensional data model: any given combination of labels for the same metric name identifies a particular dimensional instantiation of that metric (for example: all HTTP requests that used the method POST to the /api/tracks handler). The query language allows filtering and aggregation based on these dimensions. Changing any label value, including adding or removing a label, will create a new time series.
> Label names may contain ASCII letters, numbers, as well as underscores. They must match the regex `[a-zA-Z_][a-zA-Z0-9_]*`. Label names beginning with __ are reserved for internal use.
> Label values may contain any Unicode characters. A label with an empty label value is considered equivalent to a label that does not exist.
> 
> **Samples**  
> Samples form the actual time series data. Each sample consists of:
> - a float64 value
> - a millisecond-precision timestamp
> 
> **Notation**  
> Given a metric name and a set of labels, time series are frequently identified using this notation:
> ```
> <metric name>{<label name>=<label value>, ...}
> ```
> 
> For example, a time series with the metric name **api_http_requests_total** and the *labels* method="POST" and handler="/messages" could be written like this:
> ```
> api_http_requests_total{method="POST", handler="/messages"}
> ```
>
</details>

<details>
<summary>Querying <a name="querylanguage"></a></summary>	

> 

</details>

	
<details>
<summary>Pushing Time Series <a name="pushingtimeseries"></a></summary>	

>
> The Prometheus Pushgateway allows you to push time series from **short-lived service-level batch jobs** to an intermediary job which Prometheus can scrape. Combined with Prometheus's simple text-based exposition format, this makes it easy to instrument even shell scripts without a client library.  
> There are several pitfalls when blindly using the Pushgateway instead of Prometheus's usual pull model for general metrics collection:  
> - When monitoring multiple instances through a single Pushgateway, the Pushgateway becomes both a single point of failure and a potential bottleneck.
> - You lose Prometheus's automatic instance health monitoring via the up metric (generated on every scrape).  
> - The Pushgateway never forgets series pushed to it and will expose them to Prometheus forever unless those series are manually deleted via the Pushgateway's API.
> - The latter point is especially relevant when multiple instances of a job differentiate their metrics in the Pushgateway via an instance label or similar.
> - Metrics for an instance will then remain in the Pushgateway even if the originating instance is renamed or removed.
>	
> ```
> This is because the lifecycle of the Pushgateway as a metrics cache is fundamentally separate from the lifecycle of the processes that push metrics to it.
> ```
> - Contrast this to Prometheus's usual pull-style monitoring: when an instance disappears (intentional or not), its metrics will automatically disappear along with it. When using the Pushgateway, this is not the case, and you would now have to delete any stale metrics manually or automate this lifecycle synchronization yourself.
>
> Usually, the **only valid use case for the Pushgateway is for capturing the outcome of a service-level batch job**. A "service-level" batch job is one which is not semantically related to a specific machine or job instance (for example, a batch job that deletes a number of users for an entire service). Such a job's metrics should not include a machine or instance label to decouple the lifecycle of specific machines or instances from the pushed metrics. This decreases the burden for managing stale metrics in the Pushgateway.   
>
> **Alternative strategies**  
> If an inbound firewall or NAT is preventing you from pulling metrics from targets, consider moving the Prometheus server behind the network barrier as well. We generally recommend running Prometheus servers on the same network as the monitored instances. Otherwise, consider PushProx, which allows Prometheus to traverse a firewall or NAT.  
> For batch jobs that are related to a machine (such as automatic security update cronjobs or configuration management client runs), **expose the resulting metrics using the Node Exporter's textfile collector** instead of the Pushgateway.   
> For more information on using the Pushgateway and use from a Unix shell, see the project's [README.md](https://github.com/prometheus/pushgateway/blob/master/README.md).  
> For use from Java see the [PushGateway](https://prometheus.github.io/client_java/io/prometheus/client/exporter/PushGateway.html) class.
> For use from Go see the Push and Add methods.
>
> For use from Python see Exporting to a [Pushgateway](https://github.com/prometheus/client_python#exporting-to-a-pushgateway).
>
	
</details>
	
---

## Grafana <a name="grafana"></a>

## Kiali <a name="kiali"></a>

Kiali is a management console for Istio service mesh. With Kiali is possible to manage, visualize, validate and troubleshoot services by seeing the topology of communication between services, identifying possible health issues, examining logs, metrics and tracing (with Jaeger), detecting misconfigurations  etc.  

### Deployment configuration

The recommended way to deploy Kiali is via the Kiali Operator, either using Helm Charts or OperatorHub. The Kiali Operator is a Kubernetes Operator and manages your Kiali installation. It watches the **Kiali Custom Resource** (**Kiali CR**), a *YAML file that holds the deployment configuration*.    

It is only necessary to install the Kiali Operator once. After the operator is installed you only need to create or edit the Kiali CR. Never manually edit resources created by the Kiali Operator.  

Creating, updating, or removing a Kiali CR will trigger the Kiali Operator to install, update, or remove Kiali. The Operator provides comprehensive defaults for all properties of the Kiali CR. Hence, the minimal Kiali CR does not have a `spec`:

```yaml
apiVersion: kiali.io/v1alpha1
kind: Kiali
metadata:
  name: kiali
```

By default, the Kiali operator installs Kiali in the same namespace where the Kiali CR is created. However, it is possible to specify a different namespace for installation:

```yaml
spec:
  deployment:
    namespace: "custom-kiali-nameespace"
```

It is assumed that Kiali is installed to the same namespace as Istio. Kiali reads some Istio resources and may not work properly if those resources are not found. Thus, if you are installing Kiali and Istio on different namespaces, you must specify what is the Istio namespace:

```yaml
spec:
  istio_namespace: "istio-system"
```


By default, Kiali will print up to INFO-level messages in simple text format. You can change the log level, output format, and time format as in the following example:

```yaml
spec:
  deployment:
    logger:
      # Supported values are "trace", "debug", "info", "warn", "error" and "fatal"
      log_level: error  
      # Supported values are "text" and "json".
      log_format: json  
      time_field_format: "2006-01-02T15:04:05Z07:00"
```

In Kiali, there are some special logs called audit logs that are emitted each time a user creates, updates or deletes a resource through Kiali. Audit logs are INFO-level messages and are enabled by default.

