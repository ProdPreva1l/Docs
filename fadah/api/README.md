---
description: >-
  The Developer API for Fadah is very extensive, these docs aim to cover it
  fully!
---

# Developer API

## Useful Resources

JavaDocs: [https://repo.preva1l.info/javadoc/releases/info/preva1l/fadah/API/latest](https://repo.preva1l.info/javadoc/releases/info/preva1l/fadah/API/latest)\
Support Server: [https://discord.gg/4KcF7S94HF/](https://discord.gg/4KcF7S94HF)

## Getting Started

To get started with the API you must add it to your Maven / Gradle Project.

Replace LATEST-VERSION with the version found below.

<figure><img src="https://badge.fury.io/gh/Finally-A-Decent%2FFadah.svg" alt=""><figcaption></figcaption></figure>

{% tabs %}
{% tab title="Maven" %}
```xml
<repositories>
    <repository>
        <id>FinallyADecent</id>
        <url>https://repo.preva1l.info/releases/</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>info.preva1l.fadah</groupId>
        <artifactId>API</artifactId>
        <version>LATEST-VERSION</version>
        <scope>provided</scope>
    </dependency>
</dependencies>
```
{% endtab %}

{% tab title="Gradle (Groovy)" %}
```gradle
repositories {
    maven { url 'https://repo.preva1l.info/releases' }
}

dependencies {
    compileOnly 'info.preva1l.fadah:API:LATEST-VERSION'
}
```
{% endtab %}

{% tab title="Gradle (Kotlin)" %}
```gradle
repositories {
    maven("https://repo.preva1l.info/releases/")
}

dependencies {
    compileOnly("info.preva1l.fadah:API:LATEST-VERSION")
}
```
{% endtab %}
{% endtabs %}

### Depending on Fadah

{% code title="plugin.yml" %}
```yaml
name: "FadahAPIExample"
version: "1.0"
api-version: "1.20"
main: me.developer.FadahAPIExample

depend:
  - "Fadah"
```
{% endcode %}

## Next Steps

{% content-ref url="accessing-data.md" %}
[accessing-data.md](accessing-data.md)
{% endcontent-ref %}

{% content-ref url="events.md" %}
[events.md](events.md)
{% endcontent-ref %}

{% content-ref url="economy.md" %}
[economy.md](economy.md)
{% endcontent-ref %}
