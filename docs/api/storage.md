# Storage

**banco** provides a `BancoStorage` interface that you can implement to support other inventories (backpacks, vaults, banks...). There is also `BancoInventory` and `BancoContainer` which already contain all the logic to add and remove items.

## Registering a `BancoStorage`

An instance of `BancoStorage` has to be registered in the `BancoStorageRegistry` for it to work.

```java
BancoInventory customInventory = new CustomInventory();
BancoContainer customContainer = new CustomContainer();

BancoStorageRegistry storageRegistry = banco.getStorageRegistry();
storageRegistry.register(
    customInventory, customContainer
);
```

## Unregistering a `BancoStorage`

Unregistering a `BancoStorage` at any time is also possible with the `BancoStorageRegistry::unregister` method, giving developers more control over their implementations.

```java
storageRegistry.unregister(
    customInventory, customContainer
);
```

## Friendly names

`friendlyName()` can be overriden in any `BancoStorage` implementation. This friendly name gives server owners the possibility of giving priority to your add-on in their `settings.yml`. For example:

```java title="CustomInventory.java"
public final class CustomInventory {

    @Override
    public String friendlyName() {
        return "CUSTOM_INVENTORY";
    }

    ...

}
```

```yaml title="settings.yml"
currency:
  inventoryOrder:
  - CUSTOM_INVENTORY # CUSTOM_INVENTORY will be given priority to add/remove balance
  - BUNDLE
  - PLAYER_INVENTORY
  - ENDER_CHEST
```

## `BancoStorage`

An interface that must be implemented with:

- `value(uuid)`, which returns uuid's stored balance
- `add(uuid, amount)`, which adds `amount` to `uuid`'s instance of this storage
- `remove(uuid, amount)`, which removes `amount` from `uuid`'s instance of this storage

<div class="grid cards" markdown>

-   :material-check:{ .lg .middle } __Pros__

    ---

    :octicons-arrow-right-24: Gives developers more control over their storage implementations

    :octicons-arrow-right-24: Generally more stable

-   :material-close:{ .lg .middle } __Cons__

    ---

    :octicons-arrow-right-24: Developers have to code their own logic to add and remove balance

</div>

## `BancoInventory`

An abstract class that must be extended with:

- `get(uuid)`, which returns uuid's `Inventory`

<div class="grid cards" markdown>

-   :material-check:{ .lg .middle } __Pros__

    ---

    :octicons-arrow-right-24: Easiest to implement

    :octicons-arrow-right-24: Uses native Bukkit API

-   :material-close:{ .lg .middle } __Cons__

    ---

    :octicons-arrow-right-24: Needs a valid Bukkit `Inventory` that is stored properly

</div>

## `BancoContainer`

An abstract class that must be extended with:

- `get(uuid)`, which returns a list containing every stored ItemStack
- `addItem(uuid, item)`, which adds `item` into this container and returns items that could not be added
- `removeItem(uuid, item)`, which removes `item` from this container

<div class="grid cards" markdown>

-   :material-check:{ .lg .middle } __Pros__

    ---

    :octicons-arrow-right-24: Works for almost any use case

-   :material-close:{ .lg .middle } __Cons__

    ---

    :octicons-arrow-right-24: More prone to changes

</div>