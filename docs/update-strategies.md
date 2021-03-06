## This doc is still under development

* `all` strategy uses `version` passed to options as a cache tag. When version changes, old version cache is removed and new files are downloaded. Of course if files has same name were not changed (304 status returned), then probably browser won't download them again and will just update cache.
* `changed` strategy is more advanced than `all` or `hash`. To work properly it requires output assets to have unique names between compilations, e.g. _file's unique hash_ in its name. **With this strategy enabled, `index.html` file (or other files without dynamic name) should be placed in `main` section of the cache, otherwise they won't be revalidated**.
  * For `ServiceWorker` this means that only new files will be downloaded and missing files deleted from the cache.
  * For `AppCache` it's basically same as previous strategies since `AppCache` revalidates all the assets. 304 HTTP status rule of course still works.