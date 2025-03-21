# Logs and Observability

EMQX provides a series of observability-related features to help with system monitoring, management, and diagnosing. All these features can be accessed and configured on the Dashboard under the following menu items:

**Monitoring**:

- [Metrics](./metrics-and-stats.md)

  EMQX provides metrics monitoring functions, based on which the operation and maintenance personnel can monitor the current service status and troubleshoot possible system malfunctions. Users can use the EMQX Dashboard, HTTP API, and system topics to trace the metrics data. 

- [Alarm](./alarms.md)

  EMQX has offered a built-in monitoring and alarm functionality for monitoring the CPU occupancy, system and process memory occupancy, number of processes, rule engine resource status, cluster partition and healing, and will raise an alarm in case of system malfunctions.

**Management**:

- [Logs](./log.md)

  Logs provide a reliable source of information for troubleshooting and system performance optimization. You can find the record about the access, operating, or network issues from EMQX logs.

- [Integrate with Prometheus](./prometheus.md)

  [Prometheus](https://prometheus.io/) is the monitoring solution open-sourced by SoundCloud, featuring its support for multidimensional data models, flexible query language, and powerful alarm management. EMQX supports integrating with Prometheus to collect system metrics and pushing metrics to `pushgateway`.

- [Integrate with Datadog](./datadog)

  [Datadog](https://www.datadoghq.com/) is an observability platform that provides unified, real-time observability and security solutions for applications. EMQX supports the integration of Datadog to help you understand the EMQX operating status, monitor and troubleshoot system performance issues, and view EMQX metrics on the Datadog console.

**Diagnose**:

- [Topic Metrics](./topic-metrics.md)

  EMQX provides a topic monitoring feature(called Topic Metrics) that allows you to count the number of messages sent and received, the rate, and other metrics for a given topic. You can view and use this feature through the **Diagnose** -> **Topic Metrics** page on Dashboard, or you can configure it through the HTTP API.

- [Slow Subscriptions](./slow-subscribers-statistics.md)

  Typically, EMQX will finish the message transmission within milliseconds, affected mainly by the network. However, there are cases where the latency of subscription messages is very high on the client side. To solve this problem, EMQX provides a Slow subscriptions feature.

- [Log Trace](./tracer.md)

  EMQX 5.x has added the Log Trace feature, allowing users only to enable debug level logs output for specific client IDs, topics or IPs in real-time.



