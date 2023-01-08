---
title: "Blacklisting"
---

!!! important

    If you want to use ACE permissions, then follow the steps below before adding
    blacklist configuration

### Enabling ACE permissions

- Add `add_ace resource.illenium-appearance command.list_aces allow` to server.cfg
- Set `Config.EnableACEPermissions` to `true` in `shared/config.lua`

### Example of creating ACEs

Lets say you want to create an ACE for VIP players and assign players to it, you can add the following in your server.cfg:

```lua
add_ace group.vip vip allow
add_principal identifier.license:xxxxxxxxxxxxxxxxxx group.vip
```

Add the above `add_principal` line for every player that you want to give the vip ACE role and change the license to that player's license
