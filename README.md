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

Initially, enable the roles path in ansible configuration file (ansible.cfg) where we keep the roles

```
# vi /etc/ansible/ansibl.cfg

roles_path   = /etc/ansible/roles
```

Now create 3 roles say "prometheus, node-exporter and grafana" using the command "ansible-galaxy".

```
ansible-galaxy init prometheus
ansible-galaxy init node-exporter
ansible-galaxy init grafana
```
Bring the contents of the roles "prometheus, node-exporter and grafana" in the above mentioned roles path and run the playbook using the below command:

```
ansible-playbook -i hosts prometheus.yml
```

## Result

## Prometheus

![image](https://user-images.githubusercontent.com/94472101/149366924-da79e36e-2e8f-4f4d-925b-cfcfcec30b5a.png)


## Grafana

![image](https://user-images.githubusercontent.com/94472101/149355217-e3309ae7-f478-4cec-82f0-1eec022959a3.png)

## Node Exporter

![image](https://user-images.githubusercontent.com/94472101/149355811-e60c7fac-7c78-4205-b16e-7acb04f8229c.png)
![image](https://user-images.githubusercontent.com/94472101/149357177-2893d555-2d16-4829-b06b-949bd7368dbf.png)

