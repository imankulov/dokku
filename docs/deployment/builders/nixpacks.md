# Nixpacks

> New as of 0.29.0

The `nixpacks` builder builds apps via [Nixpacks](https://nixpacks.com/), a buildpack alternative.

## Usage

### Detection

This builder is not auto-detected, and must be selected via the `builder:set` command

```shell
dokku builder:set node-js-app selected nixpacks
```

### Supported languages

See the [upstream nixpacks documentation](https://nixpacks.com/docs) for further information on what languages and frameworks are supported.

### Disabling cache

Cache is enabled by default, but can be disabled by setting the `no-cache` property to `true`:

```shell
dokku builder-nixpacks:set node-js-app no-cache true
```

The default value may be set by passing an empty value for the option:

```shell
dokku builder-nixpacks:set node-js-app no-cache
```

The `no-cache` property can also be set globally. The global default is `false`, and the global value is used when no app-specific value is set.

```shell
dokku builder-nixpacks:set --global no-cache true
```

The default value may be set by passing an empty value for the option.

```shell
dokku builder-nixpacks:set --global no-cache
```

### Displaying builder-nixpacks reports for an app

You can get a report about the app's storage status using the `builder-nixpacks:report` command:

```shell
dokku builder-nixpacks:report
```

```
=====> node-js-app builder-nixpacks information
       Builder-nixpacks computed no cache: true
       Builder-nixpacks global no cache:   false
       Builder-nixpacks no cache:          true
=====> python-sample builder-nixpacks information
       Builder-nixpacks computed no cache: false
       Builder-nixpacks global no cache:   false
       Builder-nixpacks no cache:
=====> ruby-sample builder-nixpacks information
       Builder-nixpacks computed no cache: false
       Builder-nixpacks global no cache:   false
       Builder-nixpacks no cache:
```

You can run the command for a specific app also.

```shell
dokku builder-nixpacks:report node-js-app
```

```
=====> node-js-app builder-nixpacks information
       Builder-nixpacks computed no cache: true
       Builder-nixpacks global no cache:   false
       Builder-nixpacks no cache:          true
```

You can pass flags which will output only the value of the specific information you want. For example:

```shell
dokku builder-nixpacks:report node-js-app --builder-nixpacks-no-cache
```

```
true
```
