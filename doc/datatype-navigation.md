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
/// member | bool Active
Returns true if navigation is currently active
///

/// member | bool Paused
Returns true if navigation is currently paused
///

/// member | bool MeshLoaded
Returns true if a mesh is loaded in the current zone
///

/// member | bool PathExists[parameters]
Returns true if the specified navigation parameters results in a navigatable path. Navigation parameters are the same parameters that would be passed to /nav
///

!!! example "nav to target if a path exists"
    ```powershell
    /if ${Navigation.PathExists[target]} {
    /nav target
    }
    ```

/// member | float PathLength[parameters]
Similar to PathExists, but returns the length of the path if one is found. Navigation parameters are the same parameters that would be passed to /nav
///

/// member | int Velocity
Returns current velocity of the player, rounded to nearest integer.
///

/// member | string Setting[<key>]
    label: Setting[key]
Will return the string value of the setting  
///

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
