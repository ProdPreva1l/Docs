---
description: For help setting up an external database.
---

# Database

## Prerequisites (Requirements)

You must have a MySQL, MariaDB or MongoDB server setup.\
The server should be running on the latest version. (Help on finding a host is at the bottom)

## Configuration

Find the `config.yml` file in `plugins/Fadah/` and scroll down the `database` section.

Following the example below.\
Replace `<username>` with your database username. etc...

{% tabs %}
{% tab title="MySQL" %}
{% code title="config.yml" %}
```yaml
database:
  # Supported: SQLITE, MYSQL, MARIADB, MONGO
  type: "MYSQL"
  # Below is not required for SQLITE
  # For MySQL and MariaDB, uri must be a JDBC uri
  uri: "jdbc:mysql://<username>:<password>@<hostname>:<port>/Fadah"
  database: "Fadah"
```
{% endcode %}
{% endtab %}

{% tab title="MariaDB" %}
{% code title="config.yml" %}
```yaml
database:
  # Supported: SQLITE, MYSQL, MARIADB, MONGO
  type: "MARIADB"
  # Below is not required for SQLITE
  # For MySQL and MariaDB, uri must be a JDBC uri
  uri: "jdbc:mariadb://<username>:<password>@<hostname>:<port>/Fadah"
  database: "Fadah"

```
{% endcode %}
{% endtab %}

{% tab title="MongoDB" %}
{% code title="config.yml" %}
```yaml
database:
  # Supported: SQLITE, MYSQL, MARIADB, MONGO
  type: "MONGO"
  # Below is not required for SQLITE
  # For MySQL and MariaDB, uri must be a JDBC uri
  uri: "mongodb://<username>:<password>@<hostname>:<port>/?authSource=admin"
  database: "Fadah"
```
{% endcode %}
{% endtab %}

{% tab title="MongoDB (Atlas)" %}
{% code title="config.yml" %}
```yaml
database:
  # Supported: SQLITE, MYSQL, MARIADB, MONGO
  type: "MONGO"
  # Below is not required for SQLITE
  # For MySQL and MariaDB, uri must be a JDBC uri
  uri: "mongodb+srv://<username>:<password>@<hostname>/?retryWrites=true&w=majority&appName=myapp"
  database: "Fadah"
```
{% endcode %}
{% endtab %}
{% endtabs %}

Once you have completed the configuration, fully restart your Minecraft server and you will now be connected!

## Database Hosting

Most Minecraft hosting plans come with an included MySQL database. You can use this.\
However if you do not have access to said database with your host here are some you can use.

### MySQL

Google Cloud: [https://cloud.google.com/mysql/mysql-hosting](https://cloud.google.com/mysql/mysql-hosting)\
Digital Ocean: [https://www.digitalocean.com/products/managed-databases-mysql](https://www.digitalocean.com/products/managed-databases-mysql)

### MariaDB

CloudWays: [https://www.cloudways.com/en/mariadb-hosting.php](https://www.cloudways.com/en/mariadb-hosting.php)\
Amazon Web Services: [https://aws.amazon.com/rds/mariadb/](https://aws.amazon.com/rds/mariadb/)

### MongoDB

MongoDB Atlas: [https://www.mongodb.com/products/platform/atlas-database](https://www.mongodb.com/products/platform/atlas-database)\
(Normal MongoDB is self hosted only)
