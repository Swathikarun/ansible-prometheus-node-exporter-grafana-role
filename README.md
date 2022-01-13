# ansible-prometheus-node-exporter-grafana-role

Prometheus is a standalone open-source systems monitoring and alerting toolkit. It can monitor large number of instances simultaneously and bring the output into a single dashboard. Prometheus collects and stores its metrics as time series data, i.e. metrics information is stored with the timestamp at which it was recorded, alongside optional key-value pairs called labels.

## Synopsis

An Ansible playbook is created to automate the installation of Prometheus, node_exporter and grafana using roles to deploy each components into ec2 instances.

## Architecture

![image](https://user-images.githubusercontent.com/94472101/149287112-2e2a1466-b413-441d-a97f-f3fd4eef2bda.png)


This project is done for monitoring purpose which comprises of prometheus, grafana and node_exporter.

- Prometheus: Prometheus monitors the servers (targets) and collects metrics from targets by scraping metrics HTTP endpoints.
- Node exporter: Node Exporter exposes a wide variety of hardware and kernel-related metrics like cpu,network,memory, etc..
- Grafana: Its a visualization tool which connects with every possible data source like Prometheus, graphite etc

We are using 3 instances in this project, in which prometheus (port - 9090) and grafana (port - 3000) will be installed in one instance and will consider the other 2 instances as targets where we will install node_exporter (port - 9100).

## Requirements

- Ansible installed in the master machine
- Ansible-galaxy
- 3 instances

## Provisioning

