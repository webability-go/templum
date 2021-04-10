# Templum
A 2D javascript foundation framework for games and applications

# Manual

## Interfaces

The interface system allow to create objects that will control full or part of the visible screen to interact with the user.
There are 3 types of interfaces:
- The full screen is an interface that takes the full available area on screen to display its content.
- The popup if an interface that will be put on the top of screen to ask a choice or to alert something to the user, without removint lower layers.
- The takeover is an object that will be put on top of anything else and control/capture user interaction, but without removing lower layers.

There can be only one full screen at the same time, even if you define many full screen objects
There can be only one popup at the same time, even if you define many popup interfaces. The popup interfaces can be enqueued and will appear one after another.
There can be only one takeover at the same time, even if you define many take over objects.

Every interface object have a unique ID that cannot be repeated.

The interfaces work on 3 layers:

lower layer: full screen interfaces. zIndex set to 0.
middle layer: popup interfaces. zIndex set to 100.
top layer: takeover interfaces. zIndex set to 200.

### Control functions:

+ Create an interface:

```
itffs = TMPLM.interfaces.createInterface(id, "full", template, language);
itfpp = TMPLM.interfaces.createInterface(id, "popup", template, language);
itfto = TMPLM.interfaces.createInterface(id, "takeover", template, language);
```

id is the unique ID of the interface, it is a string
template is a WA.XTemplate object
language is a WA.XLanguage object
itf is a TMPLM.interfaces.interface object

+ Switch to full screen object:
All other full screen will be hidden. Takeover will also be hidden, except if it's already the current one.
 
```
TMPLM.interfaces.show(itf|id);
```

id is the unique ID of the interface, or itf is the object of the interface

+ Hide the interface object (lets an empty screen if it's a full screen): 

```
TMPLM.interfaces.hide(itf|id);
```

+ Destroy an interface object

```
TMPLM.interfaces.destroy(object|"id");
```

### Queue


+ Enqueue a pop object:

```
TMPLM.interfaces.addPopQueue(object|"id");
```

+ Remove a pop object from the queue

```
TMPLM.interfaces.removePopQueue(object|"id");
```

+ Flush queue:

```
TMPLM.interfaces.flushPopQueue(object);
```

+ Block queue to be shown:
If the queue is shown on screen, it will be hidden meanwhile it is locked.

```
TMPLM.interfaces.lockPopQueue(object);
```

+ Authorize queue to be shown:
If the Show has been called while it is locked, the queue will be shown.

```
TMPLM.interfaces.unlockPopQueue(object);
```

+ Show enqueued pop objects:
If the queue is locked, it will wait to unlock to be shown.

```
TMPLM.interfaces.showPopQueue(object);
```


### Public attributes

```
TMPLM.interfaces.fullid string  // id of active full screen
TMPLM.interfaces.full {}  // id => objects of full screen
TMPLM.interfaces.popupid string  // id of active popup if any
TMPLM.interfaces.popup {}  // id => objects of popup
TMPLM.interfaces.popupqueue []  // list of popup objects to show
TMPLM.interfaces.takeoverid string  // id of active takeover
TMPLM.interfaces.takeover {}  // id => objects of takeover
```

### Interface Object

```
TMPLM.interfaces.full()
{
  screentype string
  id string
  template
  language
  node DOMNode
}
```



