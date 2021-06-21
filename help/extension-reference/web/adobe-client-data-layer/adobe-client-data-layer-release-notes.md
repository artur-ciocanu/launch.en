# Releases notes

## Version 2.0.2

* Loading the ACDL core library (version 2.0.2)
* Version 2.0.0 of the ACDL core library removed the ability to leverage event.beforeState and event.afterState. As such, we have modified these objects to always return empty objects. Implementations that rely on this functionality will need to be updated when moving to this version.

## Version 1.1.3

* Loading the ACDL core library (version 1.1.3)


## Version 1.1.2

On the initial release, the following functionality will be provided by the Launch Extension:

* Loading the ACDL core library (version 1.1.1)
* Renaming the Adobe Data Layer
* Events:
  * Listening to all events
  * Listening to all data pushed
  * Listening to a specific event pushed\
  All event can be listen for different scope.
* Data Elements creation:
  * Computed State : Global or Specific state
  * Data Layer Size
* Actions:
  * Reset the data layer size (keeping the latest Computed State)
  * Push object to the Data Layer
