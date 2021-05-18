---
title: Edge Extension Flow
description: Learn how the components of an Adobe Experience Platform Launch edge extension interact with each other at runtime.
exl-id: 1c026502-5d78-4ada-961b-c323125f8cfe
---
# Edge extension flow

In edge extensions, each condition, action, and data element type has both a view which allows users to modify settings and a library module to act upon those user-defined settings.

As the following high-level diagram shows, the extension's action type view is shown inside an iframe within the application integrated with Adobe Experience Platform Launch. The user then uses the view to modify settings which are then saved to Platform Launch's data storage. When the Platform Launch runtime library is built, both the extension's action type library module as well as the user-defined settings will be included in the runtime library that gets deployed to the edge node. At runtime, Platform Launch injects the user-defined settings into the library module.

![extension flow diagram](../images/flow/edge/event-processing-flow.png)

In the following diagram you can see the link between events, conditions and actions inside the rule processing flow.

![rule processing flow diagram](../images/flow/edge/rule-processing-flow.png)

The rule processing flow contains the following phases:

1. The `settings` and the `trigger` method are provided to the event library module at startup.
1. When the event library module determines the event has occurred, the event library module calls `trigger`.
1. Platform Launch passes `settings` into the rule’s condition-type library modules where conditions are then evaluated.
1. Each condition type returns whether a condition evaluates to true.
1. If all conditions pass, the rule’s actions are executed.
