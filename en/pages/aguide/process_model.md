# Process Modeling 

## Process Diagram 

A process diagram is a visualized model consisting of Tasks, Actions, Roles and Routes. For example a simple expense process is modeled as follows;

__Leave Request__
Defines the start task of the process. Employee can save or submit a leave request.

__Manager Approval__
Defines the first approval task of the process. Manager can confirm or reject the request. If rejected, the process is routed back to the employee. 

__HR Approval__
Defines the second approval task of the process. Human Resources can confirm or reject the request, and if HR confirms the request, confirmed request is recorded into HR database, else if rejected, the process is routed back to the manager.

__Inform Employee__
Defines the inform employee task of the process. Employee can select OK and finish the process.

## Diagram Language

BPMN or similar notations are generally contain technical terms like "if", "split", "explicit join" activities and require some skills to understand diagram. Emakin uses own process notation to describe processes to achieve understand processes by everyone without any education or skills needed.

According to diagram above:

* Green box identifies the start (initiator) task of pool.

* Orange boxes identify the intermediate task of pool.

* Each gray box that connected to tasks identifies the action as result of task that assigned user can select.

* Lines between actions and tasks identify the routes to next task in process. If no route is found process is terminated with selected action.


__You can learn how to build a process by watching this video :__

<iframe width="400" height="400" src="https://www.youtube.com/embed/9HhSKT2Ip84" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>


## Pools

Pool is a container of diagram. Most of the business processes require more than one diagram for different operations. For example advance request and expense payment diagrams can be defined in one process. 

For a pool, you can configure following:

__Name__
Identifies the pool. This information used only for process designers and are not visible by users.

__Default Form__
Default selected form to show users if task does not specify any form.

__Data Root__
Root data element be used from data model. Different pools may share same root element if needed.

__Is Administrative ?__
Check this option if pool is used only for administrative operations. When checked pool accessed only by user has "write" permission on process or is admin. For example; You may need to create an Options diagram to set process preferences.

__Is Anonymously Accessible ?__
Check this option to allow anonymous (non-logged in) users. This option also requires anonymous access permission on domain preferences.

__Documentation URL__
Documentation URL address is used to link process documentation.

__Support URL__
Support URL address is used to link support site.

After pool is created you can configure the tasks, roles and routes from graphical designer.

Pool also contains following properties:

### Open Script

Script to be executed for every new instances just before first task. This script may be useful to assign dynamically changing default values. (ex: assign current date to form value) Please refer to scripting section for more detail.

### Closing Script

Script to be executed for every normally closed (by user action or deadline) instances. This script may be useful for export process data to any external system. Please refer to scripting section for more detail.

### Terminating Script

Script to be executed for terminated (forced by administrative or system) instances. Please refer to scripting section for more detail.

### Templates

List of message templates to be used for mail notifications. More information can be found at Message Templates section.

### Variables

List of variables to use in scripting environment. Variables are used to define and easy to update static values to use in rule validations, formulas etc. Defined variables can be accessed with $ sign prefix. Example: $ExpenseLimit

Variable values can be override with Task definitions to update value in only task scope. Example: $AllowPriceChange can set to false in pool definition and can be set to true for administrative type tasks to disable on rule validation.

