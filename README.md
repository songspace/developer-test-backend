# Songspace Technical Test

## Brief
The Songspace engineering team would like for you to implement a backend for managing songs in a basic user catalog.

## Requirements
* Built in PHP (7.2+)
  * Framework use optional, but if used, [Symfony 5](https://symfony.com) or [Laravel](https://laravel.com) preferred
* Database + migrations
  * The database server can MySQL, PostgreSQL, or SQLite
  * Migrations should be in code
* Unit Test Coverage
* Can be fully backend scriptable (via an interactive console), or have a light frontend if desired (using RESTful endpoints)
* Uploaded songs should have a resolvable path on a web server (hint: https://symfony.com/doc/current/setup/symfony_server.html)  
* Full git commit history
  * If developing without Github/Gitlab/ etc., please make sure to package the `.git` folder
* README.md explaining thought process and directions for launching

Use of third-party libraries is allowed through [Composer](https://getcomposer.org).

### Optional Requirements
* Docker
* ID3 Tag Reading (for pre-population of data)

Note: Authentication is not required, it is assumed in all cases that the user is allowed to manipulate "their" catalog, however care should be taken not to return data not associated to the user being queried (i.e. user 1 cannot see or manipulate catalogs or songs owned by user 2)

## Functionality
At a minimum, the backend should support the following constructs:
* Creation of a user
* Creation of a catalog associated to a user
* Creation of a song associated to a catalog
* Deletion of a song in a catalog
* List all songs in a catalog

It should be noted that we are not looking for a perfect solution, but we are interested in your thought process, attention to detail, and decision-making throughout the test.

## Time Limit
We expect the test to take no more than four/five hours to build, however this is for you to decide (we do not take coding time into consideration and respect your personal time 🙂 ).

## Example Workflow (Interactive Console)
```shell
$ php bin/console user:new
Name: Bob
Email: foo@bar.com

User created with user ID 1

$ php bin/console catalog:new --user 1
Name: Example Catalog

Catalog created with catalog ID 1 and associated to foo@bar.com (User ID 1)

$ php bin/console songs:new --catalog 1 --file example.mp3
Title: Example Song
Artist: Example Artist

+-------------+
Song ID: 1
Title Example Song
Artist: Example Artist
Catalog: Example Catalog (Catalog ID 1)
URL: http://localhost:8080/catalog/1/songs/1.mp3
+-------------+

$ php bin/console catalog:songs:list --catalog 1
Listing songs in catalog Example Catalog (Catalog ID 1)

| --------- | ------------ | -------------- | ------------------------------------------- |
| ID        | Title        | Artist         | URL                                         |
| 1         | Example Song | Example Artist | http://localhost:8080/catalog/1/songs/1.mp3 |
| --------- | ------------ | -------------- | ------------------------------------------- |

$ php bin/console songs:delete --song 1
Song 1 deleted from catalog 1
```
