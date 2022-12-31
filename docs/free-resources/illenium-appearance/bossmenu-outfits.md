# Boss Managed Outfits

This feature allows Job / Gang bosses to manage outfits for their Job / Gang. They will automatically be added to their respective clothing rooms.

### Pre-requisites

- qb-management

**Note:** You **HAVE** to update to the latest version of qb-management or it will not work.

### Setup instructions

- Download the latest qb-management from [here](https://github.com/qbcore-framework/qb-management)
- Delete the old one and add the new one in your resources
- Make sure to remove `-main` from the folder name (If it exists)
- Apply the SQL schema for the `management_outfits` table from [here](https://raw.githubusercontent.com/iLLeniumStudios/illenium-appearance/main/sql/management_outfits.sql)
- Enable Player Managed outfits by setting `Config.BossManagedOutfits` to `true` in `shared/config.lua`
- Restart the server
