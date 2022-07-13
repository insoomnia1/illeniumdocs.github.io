---
title: Disabling Components / Props
---

You can disable any Component / Prop using `shared/config.lua` if you have some clothing as items.

- For example if you want to disable Masks then you can change `Masks` value to `true` under `Config.DisableComponents`. It should look like this:

```lua title="shared/config.lua"
Config.DisableComponents = {
    Masks = true,
    UpperBody = false,
    LowerBody = false,
    Bags = false,
    Shoes = false,
    ScarfAndChains = false,
    BodyArmor = false,
    Shirts = false,
    Decals = false,
    Jackets = false
}
```

- For example if you want to disable Watches then you can change `Watches` to `true` under `Component.DisableProps`. It should look like this:

``` lua title="shared/config.lua"
Config.DisableProps = {
    Hats = false,
    Glasses = false,
    Ear = false,
    Watches = true,
    Bracelets = false
}
```
