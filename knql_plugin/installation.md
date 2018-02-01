---
layout: page
title: KNQL Plugin - Installation
description: Installation and Configuration
---

Find the release that supports your version. The release numbers for this plugin mimic those of Kibana. So the 5.6.6 release of Kibana should use the 5.6.6-1.0.0 version of this plugin. To install this plugin:

1. Get a command line prompt in the home directory of your Kibana release
2. Find the url for this plugin's supported build for your release of Kibana. For example the supported version of this plugin for current release of Kibana 5.6.6 is [](https://github.com/ppadovani/KibanaNestedSupportPlugin/releases/download/5.6.6-1.0.0/nested-fields-support-5.6.6-1.0.0.zip).
3. Issue this command: bin/kibana-plugin install ["url-to-plugin-release-zip"]()

## X-Pack Installation ##

If you are using x-pack with Kibana, you must configure a new role that gives access 
to the index mappings elasticsearch API. In order to do so, login to Kibana with a
user that has administrative authority. Then create a new role that is configured
like:

![Role Configuration](img/role-configuration.png)

Once the role is configured, assign the role to the user that has authority to
manage Kibana. **NOTE** You cannot add this new role to the out of the box users
created by x-pack, and you cannot activate nested support for an index without 
this role.
