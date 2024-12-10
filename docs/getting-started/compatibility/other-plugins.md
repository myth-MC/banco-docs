# Compatibility with 3rd party plugins

Starting with version 1.0, **banco** offers native compatibility for a wide range of third-party plugins:

## Custom Items

**banco** will recognize and use items provided by these plugins as long as you configure their ID in `settings.yml`:

<div class="annotate" markdown>

- [x] ItemsAdder (1) 
- [x] Oraxen (2)
- [x] MythicMobs (3)
- [x] Nova (4)

</div>

1.  Type: `itemsadder`
2.  Type: `oraxen`
3.  Type: `mythicmobs`
4.  Type: `nova`

### Example set-up using ItemsAdder

``` yaml title="settings.yml"
itemRegistry:
- type: itemsadder # (1)!
  identifier: example_identifier # (2)!
  value: '1' # (3)!
```

1.  You can see **types** by clicking on the annotations attached above
2.  ID of this item in ItemsAdder's configuration
3.  Economical value that this item will hold

## Placeholders

### PlaceholderAPI

- **%banco_balance%** - player's balance
- **%banco_symbol%** - currency symbol
- **%banco_name_singular%** - currency name in singular
- **%banco_name_plural%** - currency name in plural
- **%banco_version%** - current banco version

### [social](https://github.com/myth-MC/social)

- Adds keyword [balance] to show formatted balance in the chat

