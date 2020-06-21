# Instance Setup

> This guide details the very easy process of setting up a Spacebin server instance.

This is a quick guide on how to setup a basic spacebin API instance.

## **Prerequisites**

* A modern system with decent specifications.
* Git ([see here](https://git-scm.com/downloads)).
* Node.js 10, 12, or 14 ([see here](https://nodejs.org/en/download/)).
* Yarn. (`npm install -g yarn`, or [see here](classic.yarnpkg.com/en/docs/install))
* A database supported by TypeORM. (MySQL, MariaDB, PostgreSQL, CockroachDB, SQLite, Microsoft SQL Server, Oracle DB, SAP Hana, sql.js, MongoDB)

### 1. Download the Spacebin code.

```console
$ git clone https://github.com/spacebin-org/server.git spacebin
$ cd spacebin
```

### 2. Configuring Spacebin.

The defaults will probably be mostly fine but it's never a bad idea to double check.

### Database Setup

> Before continuing you must setup your database. The following instructions explain how:

The database configuration object contain the only required information for configuring your database.

When configuring, do not change the following values:

```js
{
  synchronize: true,
  logging: false,
  entities: [
    Document
  ]
}
```

Changing these is either highly unrecommended or **will** break your instance, you almost never need to change them.

The only values you do need to change are ones related to database authentication. You can view all available connection options on [this page of the TypeORM documentation](https://typeorm.io/#/connection-options/postgres--cockroachdb-connection-options). Simply find the instructions for your database and configure.

### 3. Installing packages

```console
$ yarn
```

#### 3.1. Installing database packages

Spacebin doesn't have database packages pre-installed, therefore you must install them before proceeding. They are just NPM packages, nothing special is happening.

```bash
$ yarn add (mongodb | mysql | pg | sqlite3 | mssql | sql.js | oracledb)
```

### 5. Finishing off

```console
$ yarn start
```

After running `yarn start`, (baring any issues in the installation process) you'll be able to see a Spacebin instance live at your configured URL, by default that's `0.0.0.0:7777`.
