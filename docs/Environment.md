# Environment

Setting up the MCScript development environment is very easy.
Install the plugin distributed by Spigot and start the server.
If config.yml is generated in plugins/MCScript, it is OK.

Describe script settings in config.yml.

Example
```yaml
ScriptPath: plugins/MCScript/script
Depend:
  - ProtocolLib
SoftDepend:
  - WorldEdit
Ignore:
  - ignore
  - ig/ignore.mcs
Import:
  - java.util.Arrays
  - java.util.Calender
```

#### ScriptPath
Write the path to store the script.
Loads all script files of the specified path.

#### Depend
Write a list of script dependent plugins.
Activate all specified plugins before loading the script. If the plugin cannot be found, loading will stop.

#### SoftDepend
Write a list of script dependent plugins.
Unlike Depend, loading continues even if the plugin is not found.

#### Ignore
Write the path that is not load in ScriptPath.
When loading a script, it is determined whether the relative path from ScriptPath matches from the beginning.

#### Import
Write the class list to be imported in advance.
All scripts can use a specified class.

In MCScript, in addition to all the classes below the org.bukkit package, the following classes are imported by default.
- java.lang.System
- java.lang.Math
- java.lang.Object
- java.lang.StringBuilder
- java.lang.String
- java.lang.Boolean
- java.lang.Character
- java.lang.Number
- java.lang.Byte
- java.lang.Short
- java.lang.Integer
- java.lang.Float
- java.lang.Double