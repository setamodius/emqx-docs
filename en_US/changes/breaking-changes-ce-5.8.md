# Incompatible Changes in EMQX 5.8

## v5.8.0

- [#13080](https://github.com/emqx/emqx/pull/13080) Updated the default value of the `mqtt.retry_interval` configuration from 30 seconds to `infinity`.

  Previously, EMQX would automatically retry message deliveries every 30 seconds by default. With the new default set to `infinity`, EMQX will no longer retry message deliveries automatically. This change aligns with MQTT specification standards, which generally do not recommend in-session message delivery retries.

  We understand that some users rely on the retry feature, so the ability to configure a specific retry interval is still available for backward compatibility.

- [#13190](https://github.com/emqx/emqx/pull/13190) Discontinued support for releases on CentOS 7 and Ubuntu 18. EMQX will no longer provide builds for these operating systems due to their end-of-life status.

- [#13248](https://github.com/emqx/emqx/pull/13248) Replaced the `builtin` durable storage backend with two new backends to provide better flexibility and scalability:

  - **`builtin_local`**: A durable storage backend that does not support replication, making it suitable for single-node deployments. This backend is available in both the open-source and enterprise editions of EMQX but is not compatible with multi-node clusters.
  - **`builtin_raft`**: A durable storage backend utilizing the Raft consensus algorithm for data replication across multiple nodes. This backend is exclusively available in the enterprise edition of EMQX, providing enhanced data durability and fault tolerance.

  Additionally, several Prometheus metrics have been renamed to better reflect their functions:

  - `emqx_ds_egress_batches` has been renamed to `emqx_ds_buffer_batches`
  - `emqx_ds_egress_batches_retry` has been renamed to `emqx_ds_buffer_batches_retry`
  - `emqx_ds_egress_batches_failed` has been renamed to `emqx_ds_buffer_batches_failed`
  - `emqx_ds_egress_messages` has been renamed to `emqx_ds_buffer_messages`
  - `emqx_ds_egress_bytes` has been renamed to `emqx_ds_buffer_bytes`
  - `emqx_ds_egress_flush_time` has been renamed to `emqx_ds_buffer_flush_time`

- [#13526](https://github.com/emqx/emqx/pull/13526) Removed the Core-replicant feature from the Open-Source Edition. Starting from release 5.8, all nodes running the Open-Source Edition will operate in the Core role. This change does not impact Enterprise Edition users, who will continue to have access to the Core-replicant functionality. Additionally, the obsolete `cluster.core_nodes` configuration parameter has been removed as it is no longer needed.

- **Dashboard Updates**: The following features have been removed or restricted in the Open-Source Edition Dashboard:

  - Monitoring:
    - Delayed Publish
    - Alarms
  - Access Control:
    - Authentication (LDAP)
    - Authorization (LDAP)
    - Flapping Detect
  - Integration:
    - Flow Designer
  - Management:
    - Monitoring
    - Advanced MQTT
      - Topic Rewrite
      - Auto Subscribe
      - Delayed Publish
  - Diagnose:
    - Topic Metrics
    - Slow Subscriptions
