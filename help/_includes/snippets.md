# Snippets (#snippets)

## Content Copy Known-Issues {#content-copy-known-issues}

You should be aware of the following known issue when using the [content copy functionality.](help/using/content-copy.md)

* If a resource in the source environment is renamed, it can cause the content copy operation to fail due to conflicting UUIDs in the target environment.
  * To avoid this error, instead of renaming resources, first delete them and then recreate with the desired, new resource name.
