Event router
------------

A pod forwarding kubernetes events to EFK aggregated logging stack.

- **eventrouter** is deployed to logging project, has a service account and its own role to read events
- **eventrouter** watches kubernetes events, marshalls them to JSON and outputs to its sink, currently only various formatting to STDOUT
- **fluentd** picks them up and inserts to elasticsearch *.operations* index

- `openshift_logging_install_eventrouter`: When 'True', eventrouter will be installed. When 'False', eventrouter will be uninstalled.

Configuration variables:

- `openshift_logging_eventrouter_image_prefix`: The prefix for the eventrouter logging image. Defaults to `openshift_logging_image_prefix`.
- `openshift_logging_eventrouter_image_version`: The image version for the logging eventrouter. Defaults to 'latest'.
- `openshift_logging_eventrouter_sink`: Select a sink for eventrouter, supported 'stdout' and 'glog'. Defaults to 'stdout'.
- `openshift_logging_eventrouter_nodeselector`: A map of labels (e.g. {"node":"infra","region":"west"} to select the nodes where the pod will land.
- `openshift_logging_eventrouter_cpu_limit`: The amount of CPU to allocate to eventrouter. Defaults to '100m'.
- `openshift_logging_eventrouter_memory_limit`: The memory limit for eventrouter pods. Defaults to '128Mi'.
- `openshift_logging_eventrouter_namespace`: The namespace where eventrouter is deployed. Defaults to 'default'.
