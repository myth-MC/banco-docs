# Accounts

An `Account` stores a player's UUID and its balance amount. It is loaded from banco's database each time the server starts or a reload is triggered into the `AccountManager`.

You can deposit or withdraw a specific amount of money from an account by using banco's `AccountManager`:

## Getting an `Account` by UUID
You can get an `Account`by getting the `AccountManager`from the previously retrieved Banco instance:

```java
AccountManager accountManager = banco.getAccountManager();
```

Now you can get an account matching a player's UUID by doing this:

```java
Account account = accountManager.get(uuid);
```

!!! warning
    If there is no `Account` matching the UUID, `Account` will be null. You must run the necessary checks in your code before proceeding.

## Depositing money into an account

Now that you have an `Account` you can deposit a specific amount of money into it. This amount must be a BigDecimal.

```java
BigDecimal amount = BigDecimal.valueOf("-1.5");
accountManager.deposit(account, amount);
```

## Withdrawing money from an account

You can also withdraw money by using the method `AccountManager::withdraw`:

```java
accountManager.withdraw(account, amount);
```