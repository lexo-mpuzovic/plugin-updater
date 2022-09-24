# Plugin updater

WordPress plugin updater

---
## Versioning
Release tags are created with Semantic versioning in mind. Commit messages were following convention of [Conventional Commits](https://www.conventionalcommits.org/).

---
## Compatibility
- WordPress version `>=4.7`. Tested and works fine up to `6.0.2`.
- PHP version `>=7.4.1`. Tested and works fine up to `8.1.9`.

---
## Installation

`composer require lexo/plugin-updater`

---

## Default values

```
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
## Filters

#### - `acf-image-focus/plugin_sections`
*Parameters*
`apply_filters('acf-image-focus/plugin_sections', $args);`
- $args (array) Sections which will be used in update info popup.
