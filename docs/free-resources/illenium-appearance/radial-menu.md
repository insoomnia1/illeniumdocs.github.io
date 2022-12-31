# Enabling RadialMenu

!!! information

    Radial Menu and qb-target are mutually exclusive and qb-target has priority over Radial Menu

To enable Radial Menu, follow these instructions:

- Set the following configuration in `shared/config.lua`:

```lua title="shared/config.lua"
Config.UseTarget = false

Config.UseRadialMenu = true
```

- Restart your server
