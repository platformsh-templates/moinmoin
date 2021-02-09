> ## Archived template
>
> Since Python 2 reached EOL January 2020, this template has been archived. It is no longer receiving regular updates from our team.
>
> You can still use it as a reference, and deploy it on Platform.sh using the button below, so long as we continue to support the [Python 2.7 runtime image](https://docs.platform.sh/languages/python.html#supported).

# Moin Moin for Platform.sh

<p align="center">
<a href="https://console.platform.sh/projects/create-project?template=https://raw.githubusercontent.com/platformsh/template-builder/master/archived/moinmoin/.platform.template.yaml&utm_content=moinmoin&utm_source=github&utm_medium=button&utm_campaign=deploy_on_platform">
    <img src="https://platform.sh/images/deploy/lg-blue.svg" alt="Deploy on Platform.sh" width="180px" />
</a>
</p>

This template builds a Moin Moin wiki on Platform.sh.  The project doesn't include Moin Moin itself; rather, it includes build and deploy scripts that will download Moin Moin on the fly.

Moin Moin is a Python-based Wiki system that uses flat files on disk for storage.

## Features

* Python 2.7
* Automatic TLS certificates
* Moinmoin downloaded on the fly during build

## Post-installation

By default, the front page of the wiki covers language setup, but that can be modified with an editable page by commenting out the line

```python
# page_front_page = u'FrontPage'
```

in `wikiconfig_local.py`. If you would like to change additional settings on the wiki, consult [`wikiconfig.py`](https://github.com/moinwiki/moin-1.9/blob/master/wikiconfig.py) and [`wikiserverconfig.py`](https://github.com/moinwiki/moin-1.9/blob/master/wikiserverconfig.py) on GitHub and include the modified lines in `wikiconfig_local.py` and `wikiserverconfig_local.py` respectively.

## Customizations

The following changes have been made relative to Moin Moin as it is downloaded from the Moin Moin website.  If using this project as a reference for your own existing project, replicate the changes below to your project.

* The `.platform.app.yaml`, `.platform/services.yaml`, and `.platform/routes.yaml` files have been added.  These provide Platform.sh-specific configuration and are present in all projects on Platform.sh.  You may customize them as you see fit.
* The `setup/build.sh` script, run during the build hook, downloads Moin Moin and applies two patches to it.  `editlog.patch` and `eventlog.patch` modify the location of log files to be in a writeable directory.  If running Moin Moin locally, use this script to download and prepare it.
* The `wikiconfig_local.py` file provides configuration for when Moin Moin is run locally.  Modify it as needed.
* The `wikiserverconfig_local.py` file provides configuration for when Moin Moin is run on Platform.sh.  In particular it pulls the port on which to listen from the Platform.sh environment.

## References

* [Moin Moin](https://moinmo.in/)
* [Python on Platform.sh](https://docs.platform.sh/languages/python.html)
