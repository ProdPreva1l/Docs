---
Plugin Permissions & Commands: Here you will find the plugin commands, their permissions and their uses.
---

# Commands & Permissions

## Commands

| Command               | Permission              | Command Description                                  |
| --------------------- | ----------------------- | ---------------------------------------------------- |
| /ah                   | `fadah.use`             | Opens Auction House menu.                            |
| /ah help              | `fadah.help`            | Displays a help message with main commands.          |
| /ah sell \<price>     | `fadah.use`             | Opens Auction House sell menu.                       |
| /ah toggle            | `fadah.toggle-status`   | Enables/Disables Fadah.                              |
| /ah reload            | `fadah.reload`          | Reloads the plugin.                                  |
| /ah profile \[player] | `fadah.profile`         | Open yours or another players profile.               |
| /ah expired \[player] | `fadah.expired-items`   | Open yours or another players expired auctions.      |
| /ah redeem \[player]  | `fadah.collection-box`  | Open yours or another players collection box.        |
| /ah active \[player]  | `fadah.active-listings` | Open yours or another players active listings.       |
| /ah history \[player] | `fadah.history`         | Open yours or another players Auction House history. |

## Permissions

{% hint style="warning" %}
Permissions that have an \[amount] are currently not weighted. \
The plugin will use the highest number.
{% endhint %}

| Permission                     | Permission Description                                                                  |
| ------------------------------ | --------------------------------------------------------------------------------------- |
| `fadah.max-listings.[amount]`  | How many items the user can list on the auction house at any one time.                  |
| `fadah.listing-tax.[amount]`   | The percent a user should be taxed from the products price. (Do not include the % sign) |
| `fadah.advert-price.[amount]`  | How much an advert should cost for the player.                                          |
| `fadah.manage.profile`         | Allows the user to manage other peoples profiles.                                       |
| `fadah.manage.active-listings` | Allows the user to manage other peoples listings.                                       |
| `fadah.manage.expired-items`   | Allows the user to manage other peoples expired items.                                  |
| `fadah.manage.collection-box`  | Allows the user to manage other peoples collection box.                                 |
