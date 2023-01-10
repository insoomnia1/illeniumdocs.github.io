---
title: Qbox-project/qb-multicharacter
---

- Replace `qb-multicharacter:callback:UpdatePreviewPed` server callback on Line: 121 of qb-multicharacter/server/main.lua with this:

```lua
lib.callback.register('qb-multicharacter:callback:UpdatePreviewPed', function(source, CitizenID)
    local Ped = MySQL.single.await('SELECT * FROM playerskins WHERE citizenid = ?', {CitizenID})
    local PlayerData = MySQL.single.await('SELECT * FROM players WHERE citizenid = ?', {CitizenID})
    if not Ped or not PlayerData then return end
    Charinfo = json.decode(PlayerData.charinfo)
    return Ped.skin, joaat(Ped.model), Charinfo.gender
end)
```

- Replace the `previewPed` NUI callback on Line: 132 of qb-multicharacter/client/main.lua with this:

```lua
RegisterNUICallback('previewPed', function(Ped, cb)
    local CID = Ped.Data and Ped.Data.citizenid or nil
    Clothing, Model, Gender = lib.callback.await('qb-multicharacter:callback:UpdatePreviewPed', false, CID)
    if Model then
        local CurrentModel = GetEntityModel(cache.ped)
        if CurrentModel ~= `mp_m_freemode_01` and Gender == 0 then
            while not HasModelLoaded(Model) do RequestModel(Model) Wait(0) end
            SetPlayerModel(cache.playerId, Model)
        elseif CurrentModel ~= `mp_f_freemode_01` and Gender == 1 then
            while not HasModelLoaded(Model) do RequestModel(Model) Wait(0) end
            SetPlayerModel(cache.playerId, Model)
        end
        SetModelAsNoLongerNeeded(Model)
        cache:set('ped', PlayerPedId())
    end
    if Clothing then
        exports["illenium-appearance"]:setPedAppearance(cache.ped, json.decode(Clothing))
    else
        RandomClothes(cache.ped)
    end
    cb('ok')
end)
```
