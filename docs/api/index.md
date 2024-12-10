## Setting everything up

Before starting to use the API, you will have to add the JitPack repository and the dependency to your project:

```xml
<repositories>
	<repository>
        <id>jitpack.io</id>
        <url>https://jitpack.io</url>
    </repository>
</repositories>

<dependencies>
	<dependency>
		<groupId>com.github.myth-MC.banco</groupId>
        <artifactId>banco-api</artifactId>
        <version>VERSION</version>
	</dependency>
</dependencies>
```

You can now get the Banco instance by using the `Banco` class:

```java
Banco banco = Banco.get();
```

This instance provides access to every function in the plugin.