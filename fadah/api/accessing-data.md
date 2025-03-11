---
description: Access data  using the API.
---

# Accessing & Using Data

## Getting Started

You will first need to get the instance of the Fadah API.

<pre class="language-java"><code class="lang-java">import org.bukkit.Bukkit;
import org.bukkit.plugin.java.JavaPlugin;
import info.preva1l.fadah.api.AuctionHouseAPI;

public final class FadahAPIExample extends JavaPlugin {
    private AuctionHouseAPI fadahApi;

    @Override
    public void onEnable() {
<strong>        if (Bukkit.getPluginManager().getPlugin("Fadah") != null) {
</strong><strong>            fadahApi = AuctionHouseAPI.getInstance();
</strong>        }
    }
}
</code></pre>

## Listing Data

Now that you have an instance of the Fadah API we can now access the ListingManager class

```java
import org.bukkit.Bukkit;
import org.bukkit.entity.Player;
import org.bukkit.Material
import org.bukkit.inventory.ItemStack
import org.bukkit.plugin.java.JavaPlugin;

import info.preva1l.fadah.api.AuctionHouseAPI;
import info.preva1l.fadah.api.managers.ListingManager;
import info.preva1l.fadah.records.listing.Listing;
import info.preva1l.fadah.records.listing.ListingBuilder;
import info.preva1l.fadah.currency.CurrencyRegistry;

import java.util.List;

public final class FadahAPIExample extends JavaPlugin {
    @Override
    public void onEnable() {
        ListingManager manager = AuctionHouseAPI.getInstance().listingManager();
        
        // Getting listings
        List<Listing> listings = manager.all();
        
        // Creating a listing
        Currency currency = CurrencyRegistry.getAll().getFirst();
        Player player = Bukkit.getPlayer("Preva1l");
        ItemStack item = player.getInventory().getItemInMainHand();
        player.getInventory().setItemInMainHand(new ItemStack(Material.AIR));
        manager.listingBuilder(player)
                .price(4_500_000) // 4.5 Million
                .tax(3.5) // This is a percentage, so 3.5%, the default is 0%
                .currency(currency) // By default this is the same as what we have it
                .length(2 * 60 * 60 * 1000) // 2 Hours, this is also a default value
                .itemStack(item)
                .biddable(false) // this is false by default, bidding is still W.I.P.
                .toPost() // theres alot more options you can change in this section
                .postAdvert(true)
                .buildAndSubmit().thenAccept(result -> {
                    if (!result.successful()) {
                        player.sendMessage(
                            "Failed to post listing! " + result.message()
                        );
                        player.getInventory().setItemInMainHand(item);
                        return;
                    }
                    
                    player.sendMessage("Listing Posted!");
                });
    }
}
```

