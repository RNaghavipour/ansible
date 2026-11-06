Prometheus
==========

Using this role can deploy Prometheus with configs and alert rule files in a server.

Requirements
------------

Internet or private registry access is needed to pull the Prometheus image. Also this role will include all alert rules
files that their name start with "alerts". These files must be place in files directory.


Role Variables
--------------

- prometheus_path: The path that want to deploy Prometheus.
- prometheus_image: Image repository, name and tag to deploy Prometheus from it.
- prometheus_container_name: Container name of the deployed Prometheus.
- prometheus_local_data: If don't want to use Docker volume, set the value to true. This way data will save in a directory
  in the prometheus_path path.
- prometheus_port: Which host port should Prometheus be exposed.
- prometheus_remote_write: Enable remote-write feature or not.

Dependencies
------------

Nothing.


Example Playbook
----------------
- name: Deploy prometheus
  hosts: master
  gather_facts: false
  become: true
  roles:
    - name: prometheus
      vars:
        prometheus_path: "/opt/monitoring/prometheus"
        prometheus_image: "prom/prometheus:v3.7.2"
        prometheus_container_name: "prometheus"
        prometheus_port: 9090
