# Player Managed Outfits

This feature allows Job / Gang bosses to manage outfits for their Job / Gang. They will automatically be added to their respective clothing rooms.

### Pre-requisites

- qb-management

**Note:** You **HAVE** to use my version of qb-management until my PR is merged to the official one.

### Setup instructions

- Download my qb-management version from [here](https://github.com/TheiLLeniumStudios/qb-management/tree/dynamic-menuitems)
- Replace the old one with the downloaded one
- Make sure to remove `-dynamic-menuitems` from the folder name (If it exists)
- Apply the SQL schema for the `management_outfits` table from [here](https://raw.githubusercontent.com/iLLeniumStudios/fivem-appearance/main/sql/management_outfits.sql)
- Enable Player Managed outfits by setting `Config.PlayerManagedOutfits` to `true` in `shared/config.lua`
- Restart the server
