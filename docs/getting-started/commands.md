# Commands

## For administrators

|                                 | Description                                   | Permission   |
|---------------------------------|-----------------------------------------------|--------------|
| /banco                          | Displays information about banco              | banco.admin  |
| /banco reload                   | Reloads settings                              | banco.admin  |
| /banco set <username> <amount>  | Sets <username>'s account balance to <amount> | banco.admin  |
| /banco give <username> <amount> | Deposits <amount> into <username>'s account   | banco.admin  |
| /banco take <username> <amount> | Withdraws <amount> from <username>'s account  | banco.admin  |

## For players

|                                 | Description                                   | Permission   |
|---------------------------------|-----------------------------------------------|--------------|
| /balance                        | Shows your account's balance                  | banco.user   |
| /balance <username>             | Shows <username> account's balance            | banco.user   |
| /pay <username> <amount>        | Pays <amount> to <username>                   | banco.user   |

!!! note "Note for administrators"
    Commands `/balance` and `/pay` can be disabled by modifying `settings.yml`.