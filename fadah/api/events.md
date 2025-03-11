---
description: Listen for Events via the API.
---

# Events

## Getting started

First setup your listeners.

<pre class="language-java" data-title="FadahAPIExample.java"><code class="lang-java">import org.bukkit.plugin.java.JavaPlugin;
import org.bukkit.Bukkit;
<strong>
</strong><strong>public final class FadahAPIExample extends JavaPlugin {
</strong>
    @Override
    public void onEnable() {
        if (Bukkit.getPluginManager().getPlugin("Fadah") != null) {
            Bukkit.getPluginManager().registerEvents(new FadahAPIExampleListener(), this);
        }
    }
}
</code></pre>

{% code title="FadahAPIExampleListener.java" %}
```java
import org.bukkit.event.Listener;
import org.bukkit.event.EventHandler;

public class FadahAPIExampleListener implements Listener {
    // Add listeners here.
}
```
{% endcode %}

Now you can add your listeners!

## ListingCreateEvent

This event is cancellable and accepts a reason to show the player.

{% code title="FadahAPIExampleListener.java" %}
```java
public class FadahAPIExampleListener implements Listener {
    @EventHandler
    public void onListingStart(ListingCreateEvent e) {
        if (e.getPlayer().getName().equalsIgnoreCase("IhateFadah")) {
            e.setCancelReason("Nuh uh!");
            e.setCancelled(true);
        }
    }
}
```
{% endcode %}

## ListingEndEvent

<pre class="language-java" data-title="FadahAPIExampleListener.java"><code class="lang-java"><strong>public class FadahAPIExampleListener implements Listener {
</strong>    @EventHandler
    public void onListingEnd(ListingEndEvent e) {
        if (e.getReason() == ListingEndReason.CANCELLED_ADMIN) {
            Player player = Bukkit.getPlayer(e.getListing().getOwner());
            if (player == null) return;
            player.sendMessage("An admin has cancelled your listing!");
        }
    }
}
</code></pre>

## ListingPurchaseEvent

{% code title="FadahAPIExampleListener.java" %}
```java
public class FadahAPIExampleListener implements Listener {
    @EventHandler
    public void onListingPurchase(ListingPurchaseEvent e) {
        Player player = Bukkit.getPlayer(e.getListing().getOwner());
        if (player == null) return;
        player.sendMessage("%s has purchased your listing!"
                .formatted(e.getBuyer().getName()));
    }
}
```
{% endcode %}
