openshift-neo4j-cart
====================

#### Bjönd Systems Inc.

### Embeddable OpenShift cartridge for the Neo4j graph database.


* HA mode but single instance (core) implementation.
* Can run embedded in non-scaling mode and as a service (separate gear) in scaling mode.
* This implementation does not itself scale beyond a single core and has a Min-Max == 1.
* I'm not sufficiently fly with Openshift to create a clustered scalable gear. 


### Logs
When running the logs are in the standard places:

```shell
./versions/<current_version/data/log/*.log
./versions/<current_version/data/graph.db/messages.log
```

### Upgrade
To upgrade or otherwise change the Neo4j version:

* Install the enterprise version of Neo4j beneath ./versions with the subdirectory set to the version number.
* Change the version number within ./metadata/manifest.yml


That's it. You should be good to go. 




