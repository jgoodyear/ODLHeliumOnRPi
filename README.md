ODLHeliumOnRPi
==============

OpenDaylight Helium on Raspberry Pi

This project contains sample configurations for OpenDaylight Helium's
Karaf and Setenv scripts.

It also contains some suggestions for RPi perfomance tweaks to obtain
a stable Helium experience.

Note: This project is purely for having fun for OpenDaylight on the RPi platform.


Setting up Helium for testing
-----------------------------

 We need odl-openflowplugin-flow-services, and odl-openflowplugin-drop-test installed. Installing flow services all at once can over tax the RPi, so install the features parts one at a time. Note: Some bundles may need manual resolve and start bundle. At the end of this process we enable dropallpacketsrpc. 

1. feature:install odl-flow-model
2. feature:install odl-mdsal-broker
3. feature:install odl-flow-services
4. feature:install odl-openflowplugin-flow-services
5. feature:install odl-openflowplugin-drop-test
6. drop-test:dropallpacketsrpc on
