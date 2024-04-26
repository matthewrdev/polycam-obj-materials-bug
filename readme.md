## Polycam v3.4.5 - OBJ export bug

### Description

In the 3.4.5 version of PolyCam, when I export an OBJ via the iOS app (untested in Web or Android), the outputed OBJ file's material does not correctly map texture assets.

For example, the following material is exported in a pre-3.4.5 version of the app:
```
# Created by Polycam
# object name: textured
newmtl textured_0
Ka 0.000 0.000 0.000
Kd 1.000 1.000 1.000
Ks 0.000 0.000 0.000
Tr 0.000000
illum 1
Ns 1.000000
map_Kd textured_0_32KafmqO.jpg
```

And post 3.4.5, the following material is exported:

```
# Created by Polycam
# object name: textured
newmtl textured_0
Ka 0.000 0.000 0.000
Kd 1.000 1.000 1.000
Ks 0.000 0.000 0.000
Tr 0.000000
illum 1
Ns 1.000000
map_Kd not_found
```

Please note that the `map_Kd` line in 3.4.5 **does not** correctly reference the corresponding jpg texture asset.

Please see included files in this repository.

### Steps To Reproduce

 * Upgrade the Polycam iOS app to 3.4.5.
 * Create a new scan using the LiDAR scanner.
 * Process the scan (I believe our example was a **space** but cannot confirm).
 * Export the scan as an OBJ.

### Expected Result

When I export an OBJ file through the Polycam app, the resultant OBJ's material file should have materials mapped correctly.

For example:

```
map_Kd textured_0_32KafmqO.jpg
```

### Actual Result

When I export an OBJ file through the Polycam app, the resultant OBJ's material file does not have materials mapped correctly.

For example:

```
map_Kd not_found
```

### Additional Feedback

When an OBJ is exported via PolyCam, please include the following meta-data in the OBJ header comments:

  * The version of Polycam that generated the OBJ.
  * The platform of Polycam that generated the OBJ (Web, Android, iOS etc).

EG:

```
```

This additional meta-data will help to diagnose any future OBJ exporting bugs.
