Distributed Work Controller
===========================

Introduction.
-------------

JumpScale provides the capability to execute tasks on x number of nodes.

Those tasks can be executed in different ways

-   async, task is executed in a [worker](/documentation/Grid/AgentController/Workers)
-   sync, task is executed in the [processmanager](processmanager)
-   on interval, task is executed either in the
    [processmanager](processmanager) or [worker](/documentation/Grid/AgentController/Workers) on the
    specified interval

Architecture
------------

Components
----------

-   [Agentcontroller](/documentation/Grid/AgentController/AgentController)
-   [ProcessManager](ProcessManager)
-   [Worker](/documentation/Grid/AgentController/Workers)

How To
------

-   [Schedule work using agentcontroller](/documentation/Grid/AgentController/ScheduleWork)

