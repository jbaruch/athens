---
title: Configuring Upstream Proxy to use Go modules repository
description: How to Fetch modules directly from a Go modules repository such as GoCenter
weight: 1
---

The upstream proxy used when fetching modules directly is by default the actual source, e.g github.com. This can be configured to use a modules repository like JFrog GoCenter.

1. Create a filter file (e.g `/usr/local/lib/UpstreamFilter`) with letter `D` in first line. //TODO Explain why D?

    ```
    # FilterFile for fetching modules directly from upstream
    D
   ```

1. //TODO where is this config file? How do I know if I use one?

    If you are not using a config file, create a new config file (based on the sample `config.dev.toml` and edit values to match your environment).
    Additionally (//TODO "additionally" to what?) in the config file, set the following parameters as suggested:

    ```
    FilterFile = "/path/to/UpstreamFilter"
    GlobalEndpoint = "https://linktoyourupsteam" 
    ```

1. Restart Athens specifying the new config file. //TODO you asked to create a new config file only if one doesn't use a config, so it won't be new

    ```
    /proxy  -config_file <path-to new-configfile>
    ```

1. Configure your environment to work with Athens and run an example build as specified in Getting Started. If you see messages display status code `303`, Athens is redirecting to the upstream you specified.
