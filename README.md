# Introduction

This repository provides alternate index files to use CPAN modules without depending on PAUSE.

Rather than using distribution tarball from PAUSE itself, `play` is relying on GitHub infrastructure to download distributions.

This repo `pause-index` host some index files which can be consumed to download and install most Perl modules.

# List of index files

The index files in this repository are a replacement for the traditional index file `02packages.details.txt.gz` used by CPAN and most/all CPAN clients.

[https://www.cpan.org/modules/02packages.details.txt.gz](https://www.cpan.org/modules/02packages.details.txt.gz)

## module.idx

The `module.idx` file list the last available version of a module. For each module it indicates which distribution/repository provides it.

[https://pause-play.github.io/pause-index/module.idx](https://pause-play.github.io/pause-index/module.idx)

For every module you can know:
- the module version
- the repository(/CPAN distribution) providing this module
- the repository version # FIXME maybe useless...

```
{
 "columns": ["module", "version", "repository", "repository_version"],
 "data": [
    ["A1z::HTML5::Template", "0.22", "A1z-HTML5-Template", "0.22"],
    ["A1z::Html", "0.003", "A1z-Html", "0.003"]
    ...
 ] }
 ```

## distro.idx

The `repositories.idx` file list the last available version of all CPAN distributions.
Each CPAN distribution is available from a repository.

[https://pause-play.github.io/pause-index/repositories.idx](https://pause-play.github.io/pause-index/repositories.idx)

For example `XML-Toolkit` distribution from [CPAN](https://metacpan.org/release/XML-Toolkit) is available on [pause-play/XML-Toolkit](https://github.com/pause-play/XML-Toolkit) repository:
[https://github.com/pause-play/XML-Toolkit](https://github.com/pause-play/XML-Toolkit)

For each distribution you can know:
- last available version
- sha used to download the tarball using the template url
- signature of the tarball

Sample extract:
```
{
 "columns": ["repository", "version", "sha", "signature"],
 "data": [
    ["A1z-HTML5-Template", "0.22", "b7ca5dd0d14445fa39b3cb4a16f876cb7b92818f", "***signature***"],
    ["A1z-Html", "0.003", "68bda645264597f8d9dd6e6f5316bd77d7aa0c7f", "***signature***"]
    ...
 ] }
```

## explicit_versions.idx

The `explicit_versions.idx` file list all versions published of a distribution.
It's useful to get for example an older or TRIAL version.

[https://pause-play.github.io/pause-index/explicit_versions.idx](https://pause-play.github.io/pause-index/explicit_versions.idx)

```
{
 "columns": ["module", "version", "repository", "repository_version", "sha", "signature"],
 "data": [
    ["A1z::HTML5::Template", "0.22", "A1z-HTML5-Template", "0.22", "b7ca5dd0d14445fa39b3cb4a16f876cb7b92818f", "***signature***"],
    ["A1z::Html", "0.003", "A1z-Html", "0.003", "68bda645264597f8d9dd6e6f5316bd77d7aa0c7f", "***signature***"]
    ...
 ] }
```

# Tools

## How to refresh the index

# See Also

Also consider using traditional CPAN Clients, relying on PAUSE index:

- cpan
- [App::cpanminus](https://metacpan.org/pod/App::cpanminus) - get, unpack, build and install modules from CPAN
- [App::cpm](https://metacpan.org/pod/App::cpm) - a fast CPAN moduler installer

# TODO

- [X] use GitHub pages and update idx URLs to use GitHub CDN
- [ ] minimal static website listing all available distribution/packages
- [ ] remove the repository_version from `module.idx`
- [ ] add a `version` field to the `.idx` files
- [ ] add `template_url` field to get the URL to download the tarball
- [ ] do not list trial versions in `distro.idx` file
