---
tags:
  - plugin
---

# MQ2Nav

<!--desc-start-->
MQ2Nav is a pathfinding plugin for MacroQuest. It is made up of two components: The Plugin (MQ2Nav.dll) and the tool for generating navmeshes (MeshGenerator.exe)
<!--desc-end-->

## Commands

<a href="cmd-navigate/">
{% 
  include-markdown "plugins/community-plugins/mq2nav/cmd-navigate.md" 
  start="<!--cmd-syntax-start-->" 
  end="<!--cmd-syntax-end-->" 
%}
</a>
:    {% include-markdown "plugins/community-plugins/mq2nav/cmd-navigate.md" 
        start="<!--cmd-desc-start-->" 
        end="<!--cmd-desc-end-->" 
        trailing-newlines=false 
     %} {{ readMore('plugins/community-plugins/mq2nav/cmd-navigate.md') }}

## Screenshots

### MeshGenerator tool
This is the tool use to generate nav meshes for everquest zones.

![MeshGenerator](screenshots/meshgen-1.png)

### MQ2Nav with path
The MQ2Nav plugin will render an in game path indicating the route that it is currently taking. This can be seen through walls to help navigate tricky terrain

Example: climbing stairs to library in poknowledge
![Navigation Path 1](screenshots/mq2nav-navpath-1.png)

Example: using waypoints to navigate from crescent reach spawn area to Blightfire Moors zone boundary
![Navigation Path 2](screenshots/mq2nav-navpath-2.png)

### MQ2Nav destinations
MQ2Nav allows navigating to various kinds of destinations. It allow allows navigating to targetted door/switch objects and clicking them upon arrival.

Example: Navigating to Freeport POK stone using /doortarget. The destination object is highlighted and visible through walls.
![Navigation Door](screenshots/mq2nav-navpath-door.png)

Example: Navigating to POK stone in Blightfire Moors using in game debug UI to target switch objects (WIP feature).
![Navigation Doors](screenshots/mq2nav-navpath-doors.png)

### MQ2Nav Navmesh Area Types
MQ2Nav supports marking areas of the map, to help customize navigation. In this example, a region of the navmesh has been blocked off, and two areas have been marked red with a higher cost, using a custom area. Also present in this example, the default color of navmesh tiles has been changed to green.

The Areas window can be found in the MeshGenerator tool under the 'Edit' menu.

Example: MeshGenerator with areas tool, placing an unwalkable area and two custom areas with modified cost
![MeshGen Areas](screenshots/meshgen-areas.png)

Example: MeshGenerator with path testing tool, showing how the path will prefer areas with lesser cost.
![MeshGen Areas Test](screenshots/meshgen-areas-test.png)

Example: MQ2Nav will follow the same rules for rendering areas and calculating paths
![Navigation Areas](screenshots/mq2nav-navpath-areas.png)

## Settings

It's best to configure Nav's settings through the user interface, `/nav ui`, but here's an example `config/MQ2Nav.ini`,

```ini
[Settings]
AutoBreak=1
AutoPause=0
AutoReload=1
ShowUI=1
ShowNavPath=1
AttemptUnstuck=0
OpenDoors=1
IgnoreScriptedDoors=1
UseSpawnFloorHeight=1
UseFindPolygonExtents=0
FindPolygonExtentsX=2.000000
FindPolygonExtentsY=4.000000
FindPolygonExtentsZ=2.000000
MapLineEnabled=1
MapLineColor=4278255360
MapLineLayer=3
VisualNavPathBorderColor=0
VisualNavPathHiddenColor=14391348
VisualNavPathVisibleColor=1033457
VisualNavPathLinkColor=14365848
VisualNavPathVisibleOpacity=0.800000
VisualNavPathHiddenOpacity=0.600000
VisualNavPathBorderWidth=0.200000
VisualNavPathLineWidth=0.899999
DebugRenderPathing=0
```

`resources/Zones.ini` is also used by the plugin to identify zones.

## TLO Members

The TLO [Nav](tlo-navigation.md) (or Navigation) includes the following members,
{% include-markdown "plugins/community-plugins/mq2nav/datatype-navigation.md" start="<!--dt-members-start-->" end="<!--dt-members-end-->" %}
{% include-markdown "plugins/community-plugins/mq2nav/datatype-navigation.md" start="<!--dt-linkrefs-start-->" end="<!--dt-linkrefs-end-->" %}

## Exported Functions

The following functions are exported for use by other plugins:

```cpp
// Used to check if MQ2Nav is initialized.
bool IsNavInitialized()

// Used to check if mesh is loaded
bool IsNavMeshLoaded()

// Used to check if a path is active
bool IsNavPathActive()

// Used to check if path is paused
bool IsNavPathPaused()

// Check if path is possible to the specified target
bool IsNavPossible(const char* szLine)

// Check path length
float GetNavPathLength(const char* szLine)

// used to pass mq2nav commands
bool ExecuteNavCommand(const char* szLine)
```