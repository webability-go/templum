# Templum
A 2D javascript foundation framework for games and applications

# Manual

## Screens

The screens interface allow to create objects that will control full or part of the visible screen to interact with the user.
There are 3 types of screens:
- The full screen is an object that takes the full available area on screen to display its content.
- The pop if an object that will be put on the top of screen to ask a choice or to alert something to the user.
- The takeover is an object that will be put on top of anything else and control/capture user interaction, but without removing lower layers.

There can be only one full screen at the same time, even if you define many full screen objects
There can be only one pop at the same time, even if you define many pop objects. The pop objects can be enqueued and will appear one after another.
There can be only one takeover at the same time, even if you define many take over objects.

Every screen object have a unique ID that cannot be repeated

The screens work on 3 layers:

lower layer: fulls creen
middle layer: pop screen
top layer: takeover screen

### Full

+ Create a full screen object:

```
o = TMPLM.createFullScreen("id");
```

+ Show a full screen object:
All other full screen will be hidden. Takeover will also be hidden.
 
```
TMPLM.showFullScreen("id");
```

+ Hide the current full screen object (lets and empty screen): 
All take over screen will also be hidden.

```
TMPLM.hideFullScreen();
```

+ Destroy a full screen object

```
TMPLM.destroyFullScreen("id");
```

### Pop

+ Create a pop object:

```
o = TMPLM.createPopScreen("id");
```

+ Enqueue a pop object:

```
TMPLM.addPopQueue(object|"id");
```

+ Remove a pop object from the queue

```
TMPLM.removePopQueue(object|"id");
```

+ Flush queue:

```
TMPLM.flushPopQueue(object);
```

+ Block queue to be shown:
If the queue is shown on screen, it will be hidden meanwhile it is locked.

```
TMPLM.lockPopQueue(object);
```

+ Authorize queue to be shown:
If the Show has been called while it is locked, the queue will be shown.

```
TMPLM.unlockPopQueue(object);
```

+ Show enqueued pop objects:
If the queue is locked, it will wait to unlock to be shown.

```
TMPLM.showPopQueue(object);
```

+ Destroy a pop object:
If the pop is enqueued, it will be removed from the queue.

```
TMPLM.destroyTakeOverScreen("id");
```

### Takeover


+ Create a takeover object:

```
o = TMPLM.createTakeOverScreen("id");
```

+ Show a takeover screen object:
All other takeover will be hidden.

```
TMPLM.showTakeOverScreen("id");
```

+ Destroy a takeover object

```
TMPLM.destroyTakeOverScreen("id");
```


