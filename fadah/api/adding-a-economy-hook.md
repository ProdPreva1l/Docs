---
description: >-
  This page will provide you with the information to add an economy hook to
  fadah!
---

# Adding a Economy Hook

### Adding a Single Currency

```java
public class MyCustomCurrency implements Currency {
    @Getter private final String id = "custom";
    @Getter private final String requiredPlugin = "MyPlugin";
    @Getter private final String name = "Super Money";

    private MyPluginsAPI api;

    @Override
    public void withdraw(OfflinePlayer player, double amountToTake) {
        api.withdrawPlayer(player, amountToTake);
    }

    @Override
    public void add(OfflinePlayer player, double amountToAdd) {
        api.depositPlayer(player, amountToAdd);
    }


    @Override
    public double getBalance(OfflinePlayer player) {
        return api.getBalance(player);
    }

    @Override
    public boolean preloadChecks() {
        api = MyPluginsAPI.getInstance()
        return api != null;
    }
}

```

### Adding a Multi Currency

```java
public class MyMultiCurrency implements MultiCurrency {
    private final String id = "my_plugin";
    private final String name = "Skibidi Money";
    private final String requiredPlugin = "MyPlugin";
    private final List<Currency> currencies = new ArrayList<>();

    private MyPluginsAPI api;

    @Override
    public boolean preloadChecks() {
        for (String economy : List.of("gems", "tokens")) {
            Currency subCur = new SubCurrency(id + "_" + eco, eco, requiredPlugin) {
                @Override
                public void withdraw(OfflinePlayer player, double amountToTake) {
                    api.take(player, amountToTake);
                }

                @Override
                public void add(OfflinePlayer player, double amountToAdd) {
                    api.add(player, amountToAdd);
                }

                @Override
                public double getBalance(OfflinePlayer player) {
                    return api.get(player);
                }

                @Override
                public boolean preloadChecks() {
                    api = MyPluginsAPI.getInstance()
                    if (api == null) {
                        System.out.println("-------------------------------------");
                        System.out.println("Cannot enable myplugin currency!");
                        System.out.println("No currency with name: " + eco.economy());
                        System.out.println("-------------------------------------");
                        return false;
                    }
                    return true;
                }
            };
            currencies.add(subCur);
        }
        return true;
    }
}

```

### Registering your currency

```java
// Single
CurrencyRegistry.register(new MyCustomCurrency());

// Multi
CurrencyRegistry.registerMulti(new MyMultiCurrency());
```
