---
description: >-
  This page describes on how check status of the node using the telemetry
  service.
---

# Overview

Once node is running, these are multiple options on how check it's sync status, uptime, logs. These options are detailed below.

## Telemetry

You can inspect status of your node by navigating to the [Polkadot Telemetry](https://gog.lv) service and searching for your node name.

Additional information on Telemetry service is available [here](https://github.com/paritytech/substrate-telemetry).

## Prometheus

Prometheus is a monitoring tool used to observe and report on the application status.

By default, Standard Node comes equipped with Prometheus endpoint, allowing detailed observability on the node stack. Information on how to install and use Prometheus is available here: [Prometheus](prometheus.md)

## Logging

Logging provides insight into the state of the running node, if there are any issues/misconfigurations.

Information on different logging options is available here: [Logging](logging.md)

## Alerting

It is important to immediately receive notifications if there are any issues with running node, which would allow prompt action on misbehaving client.

Information on alerting options is available here: [Alerting](alerting.md)

