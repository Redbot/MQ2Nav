---
tags:
  - command
---

# /navigate

## Syntax

<!--cmd-syntax-start-->
```eqcommand
/navigate {ui | pause | stop | reload | help}
/navigate {target | <spawn search> | waypoint <name> | door | item} [options]
/navigate loc <coordinates> [options]  
/navigate {recordwaypoint <name>}
```
<!--cmd-syntax-end-->

## Description

<!--cmd-desc-start-->
Navigates your character to locations, spawns, way-points and more.  
Common abbreviation: <span class=accent>/nav</span>
<!--cmd-desc-end-->

## Options

### navigational commands

``target``
:   Create a new navigation path to the current target.
    
    !!! example "`/nav target`"

``id <#>``
:   Create a new navigation path to the spawn with the specified ID.
    
    !!! example "`/nav id ${Target.ID}`"

``spawn <Spawn search> | <option>``
:   Invoke [Spawn search](../../../reference/general/spawn-search.md) to find and navigate to a spawn. Provide navigation options after a `|` (pipe).
    
    !!! example "`/nav spawn "Spiderling" | distance=5 lineofsight=off`"

``waypoint <waypoint>``  |  ``wp <waypoint>``
:   Create a new navigation path to the given waypoint.
    
    !!! example "`/nav wp "My Waypoint Name"`"

``door [<ItemName> | id <#>] [click]``
:   Create a new navigation path to the given door/object target. If `click` is specified, interact with the object upon arrival. If no name or id is provided, the current doortarget will be used.
    
    !!! example "`/nav door "Door Name" click`"

``item [click]``
:   Navigate to the targeted ground item, if any. Behaves like `door`. If `click` is specified, click it on arrival.
    
    !!! example "`/nav item click`"

``loc[yxz] Y X Z``
:   Create a new navigation path to the given Y X Z coordinates. These match `/loc` and `${Me.Loc}`.

``locxyz X Y Z``
:   Create a new navigation path to the given X Y Z coordinates. These match `${Me.EQLoc}` and `${Me.X} ${Me.Y} ${Me.Z}`.
    
    !!! example "`/nav locxyz 100 200 300`"

``locyx Y X``  |  ``locxy X Y``
:   Navigate to 2D coordinates; Z will be resolved to the nearest valid height.

``pause``
:   Toggle pause on the current navigation path.

``stop``
:   Stop following the current navigation path.

### navmesh commands

``reload``
:   Reload the current navmesh for the zone.
    
    !!! example "`/nav reload`"

### utility commands

``help``
:   Show in-game `/nav` command help.

``ui``
:   Toggle the MQ2Nav Tools UI window.
    
    !!! example "`/nav ui`"

``recordwaypoint "<waypoint name>" ["<waypoint description>"]``  |  ``rwp ...``
:   Create a waypoint at the current location.
    
    !!! example "`/nav rwp "My Waypoint Name" "This is a description of my waypoint"`"

``listwp``
:   List waypoints for the current zone.
    
    !!! example "`/nav listwp`"

``save``  |  ``load``
:   Save or load settings to/from the config file.
    
    !!! example "`/nav save`"

``setopt [<option> | reset]``
:   Set default values for navigation options used by commands. Pass `reset` to restore defaults.

``ini <key> <value>``
:   Write a setting to the ini and reload settings.

## Navigation options

``distance=<num>``
:   Set the distance to navigate from the destination. Abbreviation: <span class=accent>dist</span>.
    
    !!! example "`/nav target distance=5`"
    
    *this can be added to navigation commands above to alter their behavior*

``lineofsight=<on|off>``
:   when using distance, require visibility of target. Default is on. Abbreviation: <span class=accent>los</span>
    
    *this can be added to navigation commands above to alter their behavior*

``log=<level>``
:   Adjust log level for command. can be trace, debug, info, warning, error, critical, or off. The default is info.
    
    !!! example "`/nav target distance=15 log=debug`"
    
    *this can be added to navigation commands above to alter their behavior*

``paused``
:   Start navigation in a paused state.
    
    !!! example "`/nav target paused`"
    
    *this can be added to navigation commands above to alter their behavior*

``notrack``
:   disable tracking of spawn movement. By default, when navigating to a spawn, the destination location will track the spawn's position. This disables that behavior.
    
    !!! example "`/nav target notrack`"
    
    *this can be added to navigation commands above to alter their behavior*

``facing=<forward|backward>``
:   face forward or backward while moving.
    
    !!! example "`/nav target facing=backward`"
    
    *this can be added to navigation commands above to alter their behavior*

``tag=<text>``
:   attach an arbitrary tag to the command; exposed to observers and APIs.
    
    *this can be added to navigation commands above to alter their behavior*

 