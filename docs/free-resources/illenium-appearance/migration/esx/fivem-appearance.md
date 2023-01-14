---
title: "fivem-appearance (wasabi)"
---

### Migrating Skins

Skins created through fivem-apperance (wasabi) are already backwards compatible with illenium-appearance

### Migrating Outfits

Outfits can easily be migrated by changing the `outfits` table to the illenium-appearance format.

- Rename the table `outfits` to `player_outfits`
- Rename column `identifier` to `citizenid` in `player_outfits` table
- Rename column `name` to `outfitname` in `player_outfits` table
- Rename column `ped` to `model` in `player_outfits` table
- And you're done
- Restart the server before accessing the outfits
