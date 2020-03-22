Architecture of the Control Layer
=========================================

MCN
----------------------------------------

The master control node is the root of all network services. It is the only
service allowed to control the other services of the control layer.

Service Controller
----------------------------------------

The service controller is responsible for starting and stopping various
services in the network.

Service Directory
----------------------------------------

The service directory keeps track of all services running in the network and
helps clients to reach the services they have requested.

Service Monitoring
----------------------------------------

Service monitoring keeps track of important health information of the various
services and responsible to alert the operators of any anomalies detected in
the network.
