# NetworkPolicy test and demonstration role

This role will test and demonstrate the operation of networkPolicy objects
that have been added to the OpenShift Container Platform (OCP) new project
request template.  There are 3 networkPolicy objects:
* deny-by-default
** This policy denies all traffic that doesn't match another policy
* allow-from-same-namespace
** This policy allows connections from pods withing the same project / namespace
* allow-from-openshift-ingress
** This policy allows connections from the OCP ingress routers

## demo_network_policy Role Operation

* Create two projects and verify that the 3 networkPolicy objects are present in
in each project.
* Remove the networkPolicy objects from the first project
* Create two applications in each project
* Demonstrate that within each project, the two pods can communicate with each other.
** In the first project this demonstrates that pods within the same namespace can communicate
with each other without networkPolicy objects in place.
** In the second project this demonstrates that pods within the same namespace can communicate
with each other when the 3 networkPolicy objects exist (in particular allow-from-same-namepspace).
* Demonstrate that pods in the second project can communicate with pods in the first project.
** This demonstrates that pods in the project that does not have the networkPolicy
objects in place can be  reached from other projects/namespaces.
* Demonstrate that pods in the first project cannot communicate with pods in the second project.
** This demonstrates that pods in the project that has networkPolicy
objects in place cannot be  reached from other projects/namespaces due to the presence of the deny-by-default object.
* Demonstrate that routes can be used to reach pods in each project
** This demonstrates that pods in the first project without networkPolicy objects can be reached
from outside the OCP cluster if a route is defined.
** This demonstrates that pods in the second projects with the networkPolicy (in particular all-from-openshift-ingress) objects can be reached
from outside the OCP cluster if a route is defined.
