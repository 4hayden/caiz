
Project Structure 
--------------

  * [**Business Model**] - Caizcorp.com - a Optronic and Optoelectronics manufacturer with over 100 staff, with a local HQ and 
  various distribution networks across the globe. Key requirement is highly customizable role
  hierarchy control for the same products, which are distributed in different regions and by different channels. 

  * [**Bundles**] - Popular bundles such as fos/sonata/nelmio are used for rapid prototyping, and some others
  (doctrineextra/fosrest) are intentionally not used for demonstration. For example, the file/image uploading, helpers, 
  security and most part of the api endpoints are handled manually. 

  * [**Environment Setup**] -  A separate Testing environment can be accessed in console with '-e test' flag. A separate 
  config file (config_bundles.yml) are created for third party libraries.

  * [**Api Conventions**] - Follows basic IETF RFCs or drafts without Swagger. For example, hateoas with hal+json, token 
  manual handling using RFC 7519 jwt.

  * [**Tests**] - Codeception is used for managing/centralizing. Acceptance Tests are automated with Selenium WebDriver 
  and Mozilla GeckoDriver. Api/Functional tests and Unit tests are also created based on BDD/TDD principles.
  



**1)** Use [Composer](https://getcomposer.org/).

**2)** Install the composer dependencies:


```bash
composer install
```

**3)** Load up database and fixtures:

Make sure `app/config/parameters.yml` is correct for your database
credentials. Then:

```bash
php app/console doctrine:database:create
php app/console doctrine:migrations:migrate
php app/console doctrine:fixtures:load
```
You also need to repeat the above for the **test environment** by appending the flag '-e test'. 

The test DB are populated by the Codeception DB module (automatically loading /tests/_data/dump.sql). 

**4)** Start up the built-in PHP web server:

```bash
php app/console server:run
```

The site can be accessed at http://localhost:8000.

**5)** Make sure [Selenium WebDriver](http://www.seleniumhq.org/) and one of [Browser Drivers](http://www.seleniumhq.org/download/) 
are installed for the Acceptance tests. 

Run all tests with:

```bash
bin/codecept run 
```

Or run individual test suite by appending the suite flag such as 'api' or 'functional'. Details can be seen by using
 '--steps' or '--debug'
 
