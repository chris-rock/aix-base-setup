aix-base-setup Cookbook
=======================

This cookbook installs base GNU applications on AIX. All installed packages are provided by IBM as [AIX Toolbox for Linux Applications](http://www-03.ibm.com/systems/power/software/aix/linux/)

Currently it installs:

- curl
- wget
- zip
- vim
- zsh

Requirements
------------

This cookbook depends on [aix cookbook](https://github.com/opscode-cookbooks/aix)


Usage
-----

As a precondition, you need to install the Chef client.

```bash

# download the cookbooks
wget -O aix.zip https://github.com/opscode-cookbooks/aix/archive/master.zip
unzip aix.zip
mv aix-master /var/chef/cookbooks/aix

wget -O aix-base-setup.zip https://github.com/chris-rock/aix-base-setup/archive/master.zip
unzip aix-base-setup.zip
mv aix-base-setup-master /var/chef/cookbooks/aix-base-setup

cd /var/chef/
cat > solo.json <<EOF
{
    "run_list":[
        "recipe[aix-base-setup]"
    ]
}
EOF

cat > solo.rb <<EOF
root = File.absolute_path(File.dirname(__FILE__))
node_name "localhost"
file_cache_path root
cookbook_path [ root + '/cookbooks', root + '/site-cookbooks' ]
EOF

# Run the cookbook
chef-solo -c solo.rb -j solo.json

```


Contributing
------------

1. Fork the repository on Github
2. Create a named feature branch (like `add_component_x`)
3. Write your change
4. Write tests for your change (if applicable)
5. Run the tests, ensuring they all pass
6. Submit a Pull Request using Github

## License and Authors

* Author:: Christoph Hartmann (<chris@lollyrock.com>)

```text
Copyright:: 2014 Christoph Hartmann

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


