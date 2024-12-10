# Adding or removing items

**banco** comes with a very simple and flexible emerald-based economy setup that fits almost any survival server. You can, however, create a new setup very easily by editing `settings.yml`.

## Basic configuration

```yaml title="settings.yml"
  itemRegistry:
  - type: vanilla
    material: GOLD_INGOT
    value: '1'
  - type: vanilla
    material: GOLD_BLOCK
    value: '9'
```

!!! note "Explanation"
    This is how a simple gold-based economy setup would look like. You can see a full list with every accepted material ID by clicking [here](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html).

### `type`
Type of this item. Use `vanilla` if you want to follow this guide. Otherwise, see [Using custom items from external plugins](#using-custom-items-from-external-plugins)

??? Example
    ```yaml
    type: vanilla
    ```

### `material`
Material ID of this item.

??? Example
    ```yaml
    material: IRON_INGOT
    ```

### `value`
Economical value that this item will have. It can contain decimal numbers.

??? Example
    ```yaml
    value: '0.1'
    ```

## Customizing vanilla items

You can also customize items with display names, lores, custom model data and other options.

```yaml title="Example showcasing every configurable option"
  itemRegistry:
  - type: vanilla
    material: PLAYER_HEAD
    value: '576'
    # Custom tags have to be put in the section below
    customization:
      displayName: <green>Bag of Emerald Blocks</green>
      lore:
      - <gray>Holds <green>64x Emerald Blocks</green></gray>
      customModelData: 1009
      glowEffect: false
      headTextureUrl: http://textures.minecraft.net/texture/31d827a5decb0ae730abb69617776e1894f2bdb46968540433115d3688fbac38
      # Attributes
      attributes:
      - key: minecraft:movement_speed
        amount: -0.05
        operation: MULTIPLY_SCALAR_1
        group: ANY
```

!!! note "Explanation"
    This is a bag of emerald blocks made by using a custom texture player head. It slows down the player holding it by 5% of their total movement speed. Tag `customModelData` does not do anything in this case, it is there for demonstration purposes.

### `displayName`
Display name of this item. It can be formatted with [MiniMessage tags](https://docs.advntr.dev/minimessage/format.html).

??? Example
    ```yaml
    displayName: <rainbow>Example Item
    ```

### `lore`
Lore or description that will be shown when hovering over this item. It can be formatted with [MiniMessage tags](https://docs.advntr.dev/minimessage/format.html) and contain multiple lines.

??? Example
    ```yaml
    lore:
    - <font:myfont:custom_font>Uses a custom font from a resource pack</font>
    - <red>Line 2</red>
    ```

### `customModelData`
Custom model data can be used for changing an item's appearance. It must be a number.

??? Example
    ```yaml
    customModelData: 10007
    ```

### `glowEffect`
Makes this item look like an enchanted item. Must be `true` or `false`.

??? Example
    ```yaml
    glowEffect: true
    ```

### `headTextureUrl`
When `material` is set to `PLAYER_HEAD`, you can customize how the head texture will look like by providing an URL to a skin file.

??? Example
    ```yaml
    headTextureUrl: http://textures.minecraft.net/texture/31d827a5decb0ae730abb69617776e1894f2bdb46968540433115d3688fbac38
    ```

### `attributes`
Attributes are values that determine certain properties in Minecraft. You can see a full list [here](https://minecraft.wiki/w/Attribute).

- `key`: Namespaced key of the attribute to modify.
- `amount`: +- amount that will be applied to this modification.
- `operation`: [Operation](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/attribute/AttributeModifier.Operation.html) to perform on this attribute.
- `group`: [Equipment slot group](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/inventory/EquipmentSlotGroup.html) that will activate this modification.

??? Example
    ```yaml
    attributes:
    - key: minecraft:movement_speed
      amount: -0.05
      operation: MULTIPLY_SCALAR_1
      group: ANY
    ```

## Using custom items from external plugins

Starting with version 1.0, **banco** also supports items provided by third party plugins such as ItemsAdder, Oraxen or Nova. [Other plugins](../compatibility/other-plugins.md) contains a detailed explanation on how to do this.