# AMQ7 setup
Following the Docs reference below, I've managed to successfully set up a AMQ7 StatefulSet cluster with file-based persistence and SSL. I can connect and use the AMQ management console to ONE pod, usually pod 0.

However I have two issues :

   1. I can only ever connect to ONE pod, docs say I should be able to change the subdomain of the URL I'm using and the OCP router etc, with route me to the pod I ask for:

      * https://broker-amq-0.broker-amq-headless.amq7.svc to broker 0
      * https://broker-amq-1.broker-amq-headless.amq7.svc to broker 1
      * https://broker-amq-2.broker-amq-headless.amq7.svc to broker 2

      However OCP is not respecting the subdomain change, and always sending me back to the same pod.

      I have set ROUTER_ALLOW_WILDCARD_ROUTES=true.

Does anyone have any experience of this ?

   2. Inside the conneccted AMQ console, is a "Connect" tab that shows a page that should allow connection to other brokers. This does not work either. Does anyone have any experience of this ?

   3. Finally in the docs it says this :
```
NOTE
In future releases each pod will have its own integrated console available through the pod details page. This is resolved by using wildcard routing to expose each broker on its own hostname.
```
Does any one know when this will happen or have any idea about the product roadmap?

## References
### Red Hat Docs

https://access.redhat.com/documentation/en-us/red_hat_amq/7.2/html-single/deploying_amq_broker_on_openshift_container_platform

### Deploy clustered, persistent SSL AMQ 7

https://access.redhat.com/documentation/en-us/red_hat_amq/7.2/html-single/deploying_amq_broker_on_openshift_container_platform/index#clustered_broker-ssl-broker-ocp

### Configuring AMQ console for StatefulSet

https://access.redhat.com/documentation/en-us/red_hat_amq/7.2/html-single/deploying_amq_broker_on_openshift_container_platform/index#creating_a_route_for_the_management_console_2

### Templates (as of 5/02/19)

https://github.com/jboss-container-images/jboss-amq-7-broker-openshift-image/tree/72-1.2.GA/templates
