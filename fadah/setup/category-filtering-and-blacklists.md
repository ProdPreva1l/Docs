---
description: How to setup categories and blacklisted items
---

# Category Filtering & Blacklists

Category filters and blacklists use the same system internally.\
Strings check for booleans (true or false) and are parsed using javascript.\
You can use any javascript methods that are for comparison and you can use the following placeholders:

`%lore%` `%name%` `%amount%` `%material%`

Some examples would be:\
`%lore%.includes("Mythical Item")` would match true if the items lore has "Mythical Item" anywhere in it.\
You can also use logical operators (such as && and ||) for example: `%name% == "Custom Item" && %amount% >= 3` would match if the name is "Custom Item" and there is 3 items in the stack.

### Additional Hooks

Some hooks are also added for more filtering options.\
Currently there is; EcoItems.

#### EcoItems

`%ecoitems_id%`&#x20;
