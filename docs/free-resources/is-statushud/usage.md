# Usage

```lua title="example.lua"
    -- Show Status Hud
    -- exports['is-statushud']:Show(title, values)

    exports['is-statushud']:Show("Area Dominance", {
        "Gang: Ballas",
        "Influence: %100",
    })

    -- Hide Status Hud
    exports['is-statushud']:Hide()
```

!!! note

    You can update the existing status by just passing in the new values and title