---
description: >-
  This page will provide you with the information to add an economy hook to
  fadah!
---

# Adding a Economy Hook

### Adding a Single Currency

```java
public class MyCustomCurrency implements Currency {
    private MyPluginsAPI api;
    
    @Override
    public String getId() {
        return "my_currency";
    }
    
    @Override
    public String getRequiredPlugin() {
        return "MyPlugin";
    }
    
    @Override
    public String getName() {
        return "Super Money";
    }

    @Override
    public void withdraw(OfflinePlayer player, double amountToTake) {
        api.take(player, amountToTake);
    }

    @Override
    public void add(OfflinePlayer player, double amountToAdd) {
        api.give(player, amountToAdd);
    }

    @Override
    public double getBalance(OfflinePlayer player) {
        return api.get(player);
    }

    @Override
    public boolean preloadChecks() {
        api = MyPluginsAPI.getInstance()
        return api != null;
    }
}

```

### Adding a Multi Currency

<pre class="language-java"><code class="lang-java">public class MyMultiCurrency implements MultiCurrency {
    private final List&#x3C;Currency> currencies = new ArrayList&#x3C;>();
    private MyPluginsAPI api;
    
<strong>    @Override
</strong>    public String getId() {
        return "my_plugin";
    }
    
    @Override
    public String getRequiredPlugin() {
        return "MyPlugin";
    }
    
    @Override
    public List&#x3C;Currency> getCurrencies() {
        return currencies;
    }

    @Override
    public boolean preloadChecks() {
        api = MyPluginsAPI.getInstance()
        if (api == null) return false;

        for (String economy : List.of("gems", "tokens")) {
            Currency subCur = new SubCurrency(
                id + "_" + economy,
                economy,
                requiredPlugin,
                (player, amount) -> api.take(p.getUniqueId(), economy, amount),
                (player, amount) -> api.give(p.getUniqueId(), economy, amount),
                player -> api.get(player.getUniqueId(), economy),
                v -> {
                    if (!api.currencyExists(economy)) {
                        System.out.println("-------------------------------------");
                        System.out.println("Cannot enable coins engine currency!");
                        System.out.println("No currency with name: " + eco.economy());
                        System.out.println("-------------------------------------");
                        return false;
                    }
                    return true;
                }
            );
            currencies.add(subCur);
        }
        return true;
    }
}

</code></pre>

### Registering your currency

```java
CurrencyRegistry.register(new MyCustomCurrency());
CurrencyRegistry.register(new MyMultiCurrency());
```
