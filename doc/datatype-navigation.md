---
tags:
  - datatype
---
# `Navigation`

<!--dt-desc-start-->
Contains information about current mesh, path, velocity, and settings.
<!--dt-desc-end-->

## Members
<!--dt-members-start-->
### {{ renderMember(type='bool', name='Active') }}

:   Returns true if navigation is currently active

### {{ renderMember(type='bool', name='Paused') }}

:   Returns true if navigation is currently paused

### {{ renderMember(type='bool', name='MeshLoaded') }}

:   Returns true if a mesh is loaded in the current zone

### {{ renderMember(type='bool', name='PathExists', params='parameters') }}

:   Returns true if the specified navigation parameters results in a navigatable path. Navigation parameters are the same parameters that would be passed to /nav

!!! example "nav to target if a path exists"
    ```powershell
    /if ${Navigation.PathExists[target]} {
    /nav target
    }
    ```

### {{ renderMember(type='float', name='PathLength', params='parameters') }}

:   Similar to PathExists, but returns the length of the path if one is found. Navigation parameters are the same parameters that would be passed to /nav

### {{ renderMember(type='int', name='Velocity') }}

:   Returns current velocity of the player, rounded to nearest integer.

### {{ renderMember(type='string', name='Setting', params='<key>') }}

:   Will return the string value of the setting  

!!! example
    ```powershell
    /echo ${Navigation.Setting[OpenDoors]}
    ```

<!--dt-members-end-->

<!--dt-linkrefs-start-->
[bool]: ../macroquest/reference/data-types/datatype-bool.md
[int]: ../macroquest/reference/data-types/datatype-int.md
[string]: ../macroquest/reference/data-types/datatype-string.md
[float]: ../macroquest/reference/data-types/datatype-float.md
<!--dt-linkrefs-end-->
