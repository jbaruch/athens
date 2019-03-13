---
title: Configuring Upstream Proxy to use modules repository
description: How to Fetch modules directly from a modules repository like JFrog GoCenter
weight: 1
---

The upstream proxy used when fetching modules directly is by default the actual source, e.g github.com. This can be configured to use a modules repository like JFrog GoCenter.

1. Create a filter file (e.g /usr/local/lib/FilterForGoCenter) with letter "D" in first line.

```
# FilterFile for fetching modules directly from upstream
D
```
2. If you are not using a config file, create a new config file (based on the sample config.dev.toml and edit values to match your environment).
Additionally in the config file, set the following parameters as suggested:

```
FilterFile = "/usr/local/lib/FilterForGoCenter"
GlobalEndpoint = "https://gocenter.io"
```

3. Restart Athens specifying the new config file.

e.g **.```
/proxy  -config_file <path-to new-configfile>
```**
You should see


INFO[0000] Exporter not specified. Traces won't be exported

2019-03-14 14:11:58.492060 I | Starting application at port :3000

4. To verify, follow the same instructions to get up the go environment variable:

              GO111MODULE=on, and
              GOPROXY=http://127.0.0.1:3000

And go through the same walkthrough example.

5. If you see messages display status code [303], Athens is redirecting to GoCenter.

6. If you get 404, it means the module is not found in GoCenter repository. Please access GoCenter via https://gocenter.io and add your module for inclusion,
