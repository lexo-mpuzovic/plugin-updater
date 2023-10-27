# Plugin updater

WordPress plugin updater for self-hosted plugins.

---
## Versioning
Release tags are created with Semantic versioning in mind. Commit messages were following convention of [Conventional Commits](https://www.conventionalcommits.org/).

---
## Compatibility
- WordPress version `>=4.7`. Tested and works fine up to `6.3.2`.
- PHP version `>=7.4.1`. Tested and works fine up to `8.2.10`.

---
## Installation

```bash
composer require lexo/plugin-updater`
```

---

## Default values

```php
private array $args = [
    'basename'          => '',
    'slug'              => '',
    'version'           => '',
    'remote_path'       => '',
    'remote_args'       => [
        'timeout' => 10,
        'headers' => [
            'Accept' => 'application/json'
        ]
    ],
    'cache_key'         => 'custom_cache_key_update',
    'cache_expiration'  => DAY_IN_SECONDS,
    'cache'             => true,
];
```
---

## Setter methods

All methods are chainable. At th end call `run()` method.

- ##### `setBasename(string $basename): PluginUpdater`
- ##### `setSlug(string $slug): PluginUpdater`
- ##### `setVersion(string $version): PluginUpdater`
- ##### `setRemotePath(string $remote_path): PluginUpdater`
- ##### `setRemoteArgs(array $remote_args): PluginUpdater`
- ##### `setCacheKey(string $cache_key): PluginUpdater`
- ##### `setCacheExpiration(float $cache_expiration): PluginUpdater`
- ##### `setCache(bool $cache): PluginUpdater`
---

## Usage example

```php
(new PluginUpdater())
    ->setBasename(BASENAME)
    ->setSlug(PLUGIN_SLUG)
    ->setVersion(VERSION)
    ->setRemotePath('https://website.tld/path/info.json')
    ->setCacheKey(CACHE_KEY)
    ->setCacheExpiration(12 * HOUR_IN_SECONDS)
    ->setCache(true)
    ->run();
```
---
## JSON file
The file `info.json` can be called however you like but it need to be a valid JSON file. It's structure should be like this:

```json
{
    "name": "Plugin name",
    "slug": "plugin-slug",
    "author": "<a href='https://www.domain.tld/'>Author Name</a>",
    "author_profile": "https://www.domain.tld/",
    "donate_link": "https://www.domain.tld/",
    "version": "1.2.3",
    "download_url": "https://website.tld/path/plugin-slug-1.2.3.zip",
    "requires": "4.7",
    "tested": "6.0.2",
    "requires_php": "7.4.1",
    "sections": {
        "description": "Lorem ipsum description",
        "changelog": "Lorem ipsum changelog"
    },
    "banners": {
        "low": "https://website.tld/path/banner-772x250.jpg",
        "high": "https://website.tld/path/banner-1544x500.jpg"
    }
}
```

---

## Filters

#### - `{slug}/plugin_sections`
*Parameters*
```php
apply_filters('{slug}/plugin_sections', $args);
```
- $args (array) Sections which will be used in update info popup.
