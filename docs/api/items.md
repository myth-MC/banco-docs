# Items

`BancoItem` represents an item that has a value in **banco**'s economy. It can be converted to a Bukkit `ItemStack` with the `BancoItem::asItemStack` method.

## Supporting items from other plugins

Other plugins can make their items compatible with **banco** very easily by creating a record that implements `BancoItem`. Here is a full example:

```java
public record ItemsAdderBancoItem(String identifier, BigDecimal value) implements BancoItem {

    @Override
    public ItemStack asItemStack(int amount) {
        ItemStack itemStack = CustomStack.getInstance(identifier).getItemStack();
        itemStack.setAmount(amount);
        return itemStack;
    }
    
}
```

Server owners can now use `ItemsAdderBancoItem` as a valid item loader:

```yaml title="settings.yml"
  itemRegistry:
  - type: ItemsAdderBancoItem
    identifier: example_identifier
    value: '1'
```

## Getting a `BancoItem` from an `ItemStack`

You can get a `BancoItem` from an `ItemStack` by using the `BancoItemRegistry::get` method:

```java
BancoItemRegistry itemRegistry = banco.getItemRegistry();
BancoItem bancoItem = itemRegistry.get(itemStack);
```

!!! warning
    If there is no `BancoItem` matching the `ItemStack`, `BancoItem` will be null. You must run the necessary checks in your code before proceeding.

You can also check if an `ItemStack` is a valid `BancoItem` with `BancoItemRegistry::isValid`:

```java
boolean isValid = itemRegistry.isValid(itemStack);
```

## Adding a `BancoItem`

You can add a custom `BancoItem` by extending the interface:

```java
public final class CustomItem implements BancoItem {

    private final Material material = Material.STONE;

    private final BigDecimal value = BigDecimal.valueOf("1");

    @Override
    public BigDecimal value() {
        return value;
    }

    @Override
    public ItemStack asItemStack(int amount) {
        return new ItemStack(material, amount);
    }

}
```

Lastly, this `CustomItem` has to be registered:

```java
CustomItem customItem = new CustomItem();
itemRegistry.register(customItem);
```

## Unregistering a `BancoItem`

Although it is not recommended, you may also unregister a `BancoItem` at any time:

```java
itemRegistry.unregister(customItem);
```