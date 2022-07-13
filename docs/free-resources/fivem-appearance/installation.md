### Remove Old Clothing Resources

- Delete `qb-clothing` or `fivem-appearance` from your resources folder
- Delete any tattoo shop resources e.g., `qb-tattooshop` from your resources folder

### Download fivem-appearance

- Go to the latest release: [here](https://github.com/iLLeniumStudios/fivem-appearance/releases/latest)
- Download `fivem-appearance.zip` from the release


### Add it to your server

- Open `fivem-appearance.zip` and copy the `fivem-appearance` folder to your server's `resources` folder
- Add `setr fivem-appearance:locale "en"` in your server.cfg
- Put `ensure fivem-appearance` right after `ensure qb-core` in your server.cfg
- Delete the table `player_outfits` from your database
- Apply the SQL file located [here](https://github.com/iLLeniumStudios/fivem-appearance/blob/main/sql/player_outfits.sql) to your database to have the new `player_outfits` table created
- Restart your server
