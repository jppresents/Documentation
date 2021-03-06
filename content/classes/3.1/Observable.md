---
TAGS:
---
## Description

class [Observable](/classes/3.1/Observable)

The [Observable](/classes/3.1/Observable) class is a simple implementation of the [Observable](/classes/3.1/Observable) pattern.

There's one slight particularity though: a given [Observable](/classes/3.1/Observable) can notify its observer using a particular mask value, only the Observers registered with this mask value will be notified.

This enable a more fine grained execution without having to rely on multiple different [Observable](/classes/3.1/Observable) objects.

For instance you may have a given [Observable](/classes/3.1/Observable) that have four different types of notifications: Move (mask = 0x01), Stop (mask = 0x02), Turn Right (mask = 0X04), Turn Left (mask = 0X08).

A given observer can register itself with only Move and Stop (mask = 0x03), then it will only be notified when one of these two occurs and will never be for Turn Left/Right.

## Constructor

## new [Observable](/classes/3.1/Observable)(onObserverAdded)



#### Parameters
 | Name | Type | Description
---|---|---|---
optional | onObserverAdded |  | observer | [Observer](/classes/3.1/Observer)&lt;T&gt; | 

 | 
## Methods

### add(callback, mask, insertFirst, scope) &rarr; Nullable&lt;[Observer](/classes/3.1/Observer)&lt;T&gt;&gt;

Create a new [Observer](/classes/3.1/Observer) with the specified callback

#### Parameters
 | Name | Type | Description
---|---|---|---
 | callback |  | eventData | T | 
 | eventState | [EventState](/classes/3.1/EventState) | 

 |  the callback that will be executed for that [Observer](/classes/3.1/Observer)
optional | mask | number |  the mask used to filter observers
optional | insertFirst | boolean |  if true the callback will be inserted at the first position, hence executed before the others ones. If false (default behavior) the callback will be inserted at the last position, executed after all the others already present.
### remove(observer) &rarr; boolean

Remove an [Observer](/classes/3.1/Observer) from the [Observable](/classes/3.1/Observable) object

#### Parameters
 | Name | Type | Description
---|---|---|---
 | observer | Nullable&lt;[Observer](/classes/3.1/Observer)&lt;T&gt;&gt; |  the instance of the [Observer](/classes/3.1/Observer) to remove. If it doesn't belong to this [Observable](/classes/3.1/Observable), false will be returned.

### removeCallback(callback) &rarr; boolean

Remove a callback from the [Observable](/classes/3.1/Observable) object

#### Parameters
 | Name | Type | Description
---|---|---|---
 | callback |  | eventData | T | 
 | eventState | [EventState](/classes/3.1/EventState) | 

### notifyObservers(eventData, mask, target, currentTarget) &rarr; boolean

Notify all Observers by calling their respective callback with the given data

Will return true if all observers were executed, false if an observer set skipNextObservers to true, then prevent the subsequent ones to execute

#### Parameters
 | Name | Type | Description
---|---|---|---
 | eventData | T | 
optional | mask | number | 
optional | target | any | 
### notifyObserver(observer, eventData, mask) &rarr; void

Notify a specific observer

#### Parameters
 | Name | Type | Description
---|---|---|---
 | observer | [Observer](/classes/3.1/Observer)&lt;T&gt; | 
 | eventData | T | 
optional | mask | number | 
### hasObservers() &rarr; boolean

return true is the [Observable](/classes/3.1/Observable) has at least one [Observer](/classes/3.1/Observer) registered
### clear() &rarr; void

Clear the list of observers
### clone() &rarr; [Observable](/classes/3.1/Observable)&lt;T&gt;

Clone the current observable
### hasSpecificMask(mask) &rarr; boolean

Does this observable handles observer registered with a given mask

@return {boolean} whether or not one observer registered with the given mask is handeled

#### Parameters
 | Name | Type | Description
---|---|---|---
optional | mask | number | 

