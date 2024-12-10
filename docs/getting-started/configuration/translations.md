# Translations

**banco** automatically translates messages based on the user’s language preferences. Currently, it supports the following languages:

|                              | Locale    | Author          |
|------------------------------|-----------|-----------------|
| Catalan (Spain)              | ca_ES     | U8092           |
| English (United States)      | en_US     | U8092           |
| Spanish (Spain)              | es_ES     | U8092           |
| German (Germany)             | de_DE     | Loapu           |
| Brazilian Portuguese         | pt_BR     | Redyiel         |
| Russian (Russia)             | ru_RU     | deltathebuilder | 
| Simplified Chinese           | zh_CN     | SnowCutieOwo    |

## Overriding language keys

Starting with version 0.5, language keys can be globally overriden by editing `plugins/banco/lang/overrides.properties`. This feature is beneficial for users seeking to support additional languages that are currently not implemented.

```yaml
#
# You can use this file to override language keys
#
# Keys: https://github.com/myth-MC/banco/blob/main/common/src/main/resources/i10n_en_US.properties
#
# Please, consider contributing your translations by opening a pull request in our GitHub repo.
#
# Usage example:
# banco.errors.not-enough-arguments=No hi ha suficients arguments.
#

banco.errors.not-enough-arguments=No hi ha suficientes arguments.
banco.errors.invalid-command=Comanda invàlida.
banco.errors.player-not-found=No s'ha pogut trobar a {0}.
banco.errors.invalid-value={0} no és un valor correcte.
banco.errors.not-enough-funds=No tens suficients diners a l'inventari.

# ...
```

!!! note
    Please, consider contributing to our translation project by opening a pull request in [our GitHub repository](https://github.com/myth-MC/banco). You can also open a thread in #banco-support in our [Discord](https://discord.gg/bpkwdzREcR).