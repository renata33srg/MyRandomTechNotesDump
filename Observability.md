# Observability Tools

- [Prometheus](#prometheus)
- [Grafana](#grafana)
- [Kiali](#kiali)

## Prometheus <a name="prometheus"></a>

Prometheus is an open-source systems monitoring and alerting toolkit that collects and stores its metrics as time series data, i.e. metrics information is stored with the timestamp at which it was recorded, alongside optional key-value pairs called _labels_.  

### Main features

    - a multi-dimensional data model with time series data identified by metric name and key/value pairs
	- PromQL, a flexible query language to leverage this dimensionality
	- no reliance on distributed storage; single server nodes are autonomous 
	- time series collection happens via a pull model over HTTP
	- pushing time series is supported via an intermediary gateway
	- targets are discovered via service discovery or static configuration
	- multiple modes of graphing and dashboarding support


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

