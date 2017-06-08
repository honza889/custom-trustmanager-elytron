Demo: Custom Trust Manager for WildFly (Elytron)
================================================

Compile
-------

        mvn package

Add module into WildFly
-----------------------

        bin/jboss-cli.sh
        module add --name=jk.demo.mytrustmanager --resources=mytrustmanager-1.0-SNAPSHOT.jar --dependencies=javax.api

Add provider and TrustManager into configuration
------------------------------------------------

        /subsystem=elytron/provider-loader=myloader:add(module=jk.demo.mytrustmanager)
        /subsystem=elytron/trust-manager=mymanager:add(algorithm=MyAlgorithm,providers=myloader,key-store=ks)

