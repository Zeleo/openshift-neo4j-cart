
![](https://raw.githubusercontent.com/Bjond/openshift-neo4j-cart/master/images/BjondHealthLOGO-WhiteGrey.png "Bjönd Health Inc.")


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



### Usage of Bjönd custom Neo4j

To create a Neo4j gear with our custom cartridge:

```Shell
rhc create-app -n bjondinc <appname> https://raw.github.com/Bjond/openshift-neo4j-cart/master/metadata/manifest.yml jboss-wildfly-8

Example:
rhc create-app -n bjondinc testneo4j https://raw.github.com/Bjond/openshift-neo4j-cart/master/metadata/manifest.yml jboss-wildfly-8
```

To delete a Neo4j gear via RHC which is probably safer:

```Shell
rhc app delete -n bjondinc testneo4j
```

To combine the two and add scaling:

```Shell
rhc app delete -n bjondinc testneo4j ; rhc create-app --scaling -n bjondinc testneo4j https://raw.github.com/Bjond/openshift-neo4j-cart/master/metadata/manifest.yml jboss-wildfly-8
```

You may add the *--scaling* after argument after *rhc create-app* if you wish to use a scaling application.

Perform the following to find the ssh access path for the background Neo4j gears:

```Shell
rhc app show -n bjondinc -a testneo4j --gears
```


### Go with God

That's it. You should be good to go. 




