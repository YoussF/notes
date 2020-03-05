## Kubernetes Operators
In this article we are going to **learn** the concepts, then we'll **code** the implementation, then **try it out** against an actual cluster. We also take a look at Scaffold Design, Type, Behavior and launching.

### First, What's an Operator ?

A **Controller** is a loop that reads desired state ("spec"), observed cluser state, and external state, and reconciles the cluster state with the desired state.

An **Operator** is a controller that encodes human operational knowledge. How do i run and manage a specific piece of complex software. All operators are controllers; but not all controllers are operators.

### What is KubeBuilder ?
**KubeBuilder** is a set of tooling and opinions about how to structure custom controller and operators build on top of "controller-runtime" and "controller-tools"
**controller-runtime** wich conntains libraries for building the controller part of your operator, and...
**controller-tools** which contains tools for generating CustomResourceDefinitions, etc for you operator.