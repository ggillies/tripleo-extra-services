Skydive
=======

This directory contains the TripleO services and environment files/roles data needed to enable
skydive (http://skydive-project.github.io/skydive/) on the overcloud environment. Skydive
is installed and run inside of docker, for ease of deployment and management. If you wish to
control the skydive agent or analyzer service on the overcloud machines, you can use standard
systemd e.g.

systemctl stop docker-skydive-analyzer
systemctl restart docker-skydive-agent

Note that a special skydive-analyzer role has been defined to run the skydive analyzer software
(which stores and displays the data). If you have network isolation enabled, you will need to
create and define a new nic-config for the SkydiveAnalyzer role, and define it's networking as
needed. The analyzer ui will be exposed on port 8082 on all interfaces, so typically you want
the analyzer host to be connected to internal_api (which by default is used by traffic between
agent and analyzer) and also either the external or management networks, which ever you plan
on using to access the ui itself
