---
title: "Blacklisting Clothes / Hair"
---

illenium-appearance supports blacklisting clothes / hair based on the following criterion:

- Jobs
- Gangs
- ACEs

The way it works is that you need to add the blacklist configuration to `shared/blacklist.lua`.  The default file contains all the component names that you can choose to blacklist. For example if you want to blacklist following items:

```title="Example"
Jackets: 10, 12, 13, 18 (All Textures)
Jackets: 11 (Texture: 1, 2, 3)
Masks: 10, 11, 12, 13 (All Textures)
Masks: 14 (Texture: 5, 7, 10, 12, 13)
Jackets: 25, 30, 35 (Accessible only to "police" job)
Hats: 41, 42, 45 (Accessible only to "ballas" gang)
Scarfs & Chains: 5, 6, 7 (Accessible only to "vip" ACE)
Hair: 15 (All textures)
```

Here is how the config would look like, for the above:

```lua title="shared/blacklist.lua"
Config.Blacklist = {
    male = {
        hair = {
            {
                drawables = {15}
            }
        },
        components = {
            masks = {
                {
                    drawables = {10, 11, 12, 13}
                },
                {
                    drawables = {14},
                    textures = {5, 7, 10, 11, 12, 13}
                }
            },
            upperBody = {},
            lowerBody = {},
            bags = {},
            shoes = {},
            scarfAndChains = {
                {
                    drawables = {5, 6, 7},
                    aces = {"vip"}
                }
            },
            shirts = {},
            bodyArmor = {},
            decals = {},
            jackets = {
                {
                    drawables = {11},
                    textures = {1, 2, 3}
                },
                {
                    drawables = {10, 12, 13, 18}
                },
                {
                    drawables = {25, 30, 35},
                    jobs = {"police"}
                }
            }
        },
        props = {
            hats = {
                {
                    drawables = {41, 42, 45},
                    gangs = {"ballas"}
                }
            },
            glasses = {},
            ear = {},
            watches = {},
            bracelets = {}
        }
    },
    female = {
        components = {
            masks = {},
            upperBody = {},
            lowerBody = {},
            bags = {},
            shoes = {},
            scarfAndChains = {},
            shirts = {},
            bodyArmor = {},
            decals = {},
            jackets = {}
        },
        props = {
            hats = {},
            glasses = {},
            ear = {},
            watches = {},
            bracelets = {}
        }
    }
}

```

You can separately blacklist male and female clothes. Just put them under the right section in the config and you should be good to go.
