---
title: Type
updated: 2021-03-26
---

## Objective  

The `type` key defines the base container image that will be used to run the application.  There is a separate base container image for each primary language for the application, often in multiple versions.  

## Supported types

Available languages and their supported versions include:

| **Language** | **`runtime`** | **Supported `version`** |
|----------------------------------|---------------|-------------------------|
| [C#/.Net Core](/pages/web_cloud/web_paas_powered_by_platform_sh/languages/c_net_core/languages-dotnet) | `dotnet` | 2.0, 2.1, 2.2, 3.1 |
| [Elixir](/pages/web_cloud/web_paas_powered_by_platform_sh/languages/elixir/languages-elixir) | `elixir` | 1.9, 1.10 |
| [Go](/pages/web_cloud/web_paas_powered_by_platform_sh/languages/go/languages-go) | `golang` | 1.11, 1.12, 1.13, 1.14, 1.15 |
| [Java](/pages/web_cloud/web_paas_powered_by_platform_sh/languages/java/languages-java) | `java` | 11, 12, 8, 13, 14 |
| [Lisp](/pages/web_cloud/web_paas_powered_by_platform_sh/languages/lisp/languages-lisp) | `lisp` | 1.5 |
| [Node.js](/pages/web_cloud/web_paas_powered_by_platform_sh/languages/node_js/languages-nodejs) | `nodejs` | 6, 8, 10, 12, 14 |
| [PHP](/pages/web_cloud/web_paas_powered_by_platform_sh/languages/php/languages-php) | `php` | 7.3, 7.4, 8.0 |
| [Python](/pages/web_cloud/web_paas_powered_by_platform_sh/languages/python/languages-python) | `python` | 2.7, 3.5, 3.6, 3.7, 3.8, 3.9 |
| [Ruby](/pages/web_cloud/web_paas_powered_by_platform_sh/languages/ruby/languages-ruby) | `ruby` | 2.3, 2.4, 2.5, 2.6, 2.7 |

## Example configuration

```yaml   
type: 'php:8.0'
```  

## Runtime

The `.platform.app.yaml` file also supports a `runtime` key that allows selected customizations to the language runtime. As those possibilities vary by language, please see the appropriate language documentation.

* [PHP](/pages/web/web-paas/languages-php#runtime-configuration)
