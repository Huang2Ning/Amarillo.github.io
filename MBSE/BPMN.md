# BPMN
## BPMN Elements

## Comparison of BPMN Process and UML Activities
This section is excerpted from the [Sparx System](https://sparxsystems.com/enterprise_architect_user_guide/15.2/model_simulation/bpmn_simulation_comparison.html).

The execution and simulation of BPMN models have a number of differences from the execution and simulation of UML Activity diagrams. The mapping of similar concepts, and the differences between the two methods of expressing the behavior of a system, are presented here.

| UML Activity | BPMN Process |
| ---- | ---- |
| The starting point is defined by an Initial Node. No method of specifying why the Activity was started is available. | The starting point is defined by a Start Event. This implies a specific cause for the Activity to start, although it could be unspecified. |
| The basic behavior unit in an Activity is the Action element. UML provides many different forms of Actions, although the simulation makes use of a small subset of these. | The basic behavior unit in an Activity is the Activity element. A number of different Task Types are available. These typically describe different methods of execution (for example Manual) as opposed to what happens. |
| A Control Flow is used to connect the elements on an Activity diagram. A distinguishing feature is that only a single Control Flow can be followed from any node, except for an explicit Fork Node. To restrict flow on a Control Flow, add a Guard. | A Sequence Flow is used to connect the elements on a Business Process diagram. These differ from UML Activity diagrams in that all valid sequence flows are taken by default. To restrict flow on a Sequence Flow set the conditionType Tagged Value to 'Expression' and create the script in the conditionExpression Tagged Value. |
| A Decision node is used to explicitly model a decision being made. A Merge node, which uses the same syntax is used when the potential flows are combined back into one. | A Gateway node set to 'Exclusive' is used when a single path must be selected. It is also used to combine the potential flows again. A direction can be specified as 'Converging' or 'Diverging' to explicitly select between the two modes. |
| A Fork node is used to concurrently execute multiple nodes, while a Join node, using the same syntax is used to wait for all incoming flows to become available and leave with a single flow. | A Gateway node set to 'Parallel' is used to explicitly model concurrent execution of multiple nodes. It is also used to wait for all incoming flows to become available and leave with a single flow. A direction can be specified as 'Converging' or 'Diverging' to explicitly select between the two modes. |
| There is no allowance for concurrently executing only some outputs from a node for UML Activities. If you needed this you add later Control Flows with the appropriate Guards. | A Gateway node set to Inclusive is used to explicitly model the situation where all outgoing flows with a true condition are executed concurrently.
| A Call Behavior Action is used when behavior needs to be further decomposed by referring to an external activity. | Activity elements are set as a CallActivity Sub-Process when behavior needs to be further decomposed by referring to an external activity. |
| Activity Action Call Behavior Action. | Activity elements are set as an Embedded Sub-Process when behavior needs to be further decomposed without referring to an external activity. |
