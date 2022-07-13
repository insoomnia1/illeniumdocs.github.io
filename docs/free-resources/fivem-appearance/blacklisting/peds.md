---
title: "Blacklisting Peds"
weight: 2
---

fivem-appearance supports blacklisting peds based on the following criterion:

- Jobs
- Gangs
- ACEs

The way it works is that you need to add the ped blacklist configuration to `peds.json`.  The default file contains all the ped models without any blacklisting. For example if you want to limit following peds:

```title="Example"
a_f_m_beach_01, a_f_m_bevhills_01, a_f_m_bevhills_02 => "police" job
a_f_m_bodybuild_01 => "vagos" gang
a_f_m_downtown_01 => "admin" ace
a_f_m_skidrow_01 => "police" job, "ballas" gang
```

To do this, you first need to remove all these peds from the `peds` list which doesn't have any filters / limits defined (The default one provided in `peds.json`).

Here is how the JSON file will look like, for such configuration (**Note:** The `...` should be the list of all peds that you want to be accessible to everyone):

```json title="peds.json"
{
  "pedConfig": [
    {
      "peds": [...]
    },
    {
      "peds": ["a_f_m_beach_01", "a_f_m_bevhills_01", "a_f_m_bevhills_02"],
      "jobs": ["police"],
    },
    {
      "peds": ["a_f_m_bodybuild_01"],
      "gangs": ["vagos"],
    },
    {
      "peds": ["a_f_m_downtown_01"],
      "aces": ["admin"],
    },
    {
      "peds": ["a_f_m_skidrow_01"],
      "jobs": ["police"],
      "gangs": ["ballas"]
    }
  ]
}
```
