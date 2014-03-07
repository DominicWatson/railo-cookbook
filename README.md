Railo Cookbook
=================
 [![Build Status](https://secure.travis-ci.org/opscode-cookbooks/railo.png?branch=master)](http://travis-ci.org/opscode-cookbooks/railo)

This cookbook installs Railo (right now on tomcat)

Requirements
------------

The cookbook has been tested on Ubuntu 12.04, but should work on most platforms where Java 1.6 works.

### Platforms
- Ubuntu

### Cookbooks
- java
- tomcat

And the dependencies of the java and tomcat cookbooks

Attributes
----------
* `node['railo']['app_server']` Type of web application server (currently only tomcat)
* `node['railo']['user']['id']` User name
* `node['railo']['major_version']` Major version of Railo, default `4`
* `node['railo']['minor_version']` Minor version of Railo, default `1`
* `node['railo']['port']` The Railo/Tomcat port, default `8080`
* `node['railo']['base_installation_directory']` Root directory where the /railo/lib directories will be installed, default `/opt`
* `node['railo']['config_dir']` Full path to the railo configuration directory where the /server and /web directories will be created by Railo, default `/var/lib/railo/config`

Usage
-----
Just include `recipe[railo]` in your node's `run_list` and configure the java and tomcat cookbooks:

```json
{
    "name": "railo-server",
    "description": "A Railo server based on Tomcat",
    "json_class": "Chef::Role",
    "default_attributes": {
        "java": {
            "jdk_version": "7"
        },
        "tomcat": {
            "base_version": "7",
            "deploy_manager_apps": false
        },
        "railo": {
            "major_version": "4",
            "minor_version": "2"
        }
    },
    "override_attributes": {
    },
    "chef_type": "role",
    "run_list": [
        "recipe[railo]"
    ]
}
```

Running the tests
-----------------

There is not tests infrastructure setup yet, feel free to start

Contributing
------------

1. Fork the repository on Github
2. Create a named feature branch (like `add_component_x`)
3. Write you change
4. Write tests for your change
5. Run the tests, ensuring they all pass
6. Submit a Pull Request

License & Authors
-----------------
- Author:: Roland Ringgenberg (<roland.ringgenberg@ringgi.net>)

```text
Copyright:: RRTechnologies

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```