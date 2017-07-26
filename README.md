# kitchen-vcenter

[![Gem Version](https://badge.fury.io/rb/kitchen-vcenter.svg)](https://rubygems.org/gems/kitchen-vcenter)
[![Build Status](https://travis-ci.org/chef/kitchen-vcenter.svg?branch=master)](https://travis-ci.org/chef/kitchen-vcenter)
[![Dependency Status](https://gemnasium.com/chef/kitchen-vcenter.svg)](https://gemnasium.com/chef/kitchen-vcenter)
[![Inline docs](http://inch-ci.org/github/chef/kitchen-vcenter.svg?branch=master)](http://inch-ci.org/github/chef/kitchen-vcenter)

Please refer to the [CHANGELOG](CHANGELOG.md) for version history and known issues.

## Requirements

- Chef 13.0 higher
- Ruby 2.3.3 or higher

## Installation

Using [ChefDK](https://downloads.chef.io/chef-dk/), simply install the Gem:

```bash
chef gem install kitchen-vcenter
```

## Usage

A sample `.kitchen.yml` file, details are below.

```yml
driver:
  name: vcenter
  vcenter_username: <%= ENV['VCENTER_USER'] || "administrator@vsphere.local" %>
  vcenter_password: <%= ENV['VCENTER_PASSWORD'] || "P@ssw0rd!" %>
  vcenter_host: vcenter.chef.io
  vcenter_disable_ssl_verify: true
  driver_config:
    targethost: 172.16.20.41
    template: ubuntu1604
    datacenter: "Datacenter"
```

### Required parameters:

The following parameters should be set in the main `driver_config` section as they are common to all platforms.

 - `vcenter_username` - Name to use when connecting to the vSphere environment
 - `vcenter_password` - Password associated with the specified user
 - `vcenter_host` - Host against which logins should be attempted
 - `vcenter_disable_ssl_verify` - Whether or not to disable SSL verification checks. Good when using self signed certificates. Default: false

The following parameters should be set in the `driver_config` for the individual platform.

 - `targethost` - Host on which the new virtual machine should be created
 - `template` - Template or virtual machine to use when cloning the new machine
 - `datacenter` - Name of the datacenter to use to deploy into

### Optional Parameters

The following optional parameters should be used in the `driver_config` for the platform.

 - `folder` - Folder into which the new machine should be stored. If specified the folder _must_ already exist

## Contributing

For information on contributing to this project see <https://github.com/chef/chef/blob/master/CONTRIBUTING.md>

## Development

* Report issues/questions/feature requests on [GitHub Issues][issues]

Pull requests are very welcome! Make sure your patches are well tested.
Ideally create a topic branch for every separate change you make. For
example:

1. Fork the repo
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Run the tests and rubocop, `bundle exec rake spec` and `bundle exec rake rubocop`
4. Commit your changes (`git commit -am 'Added some feature'`)
5. Push to the branch (`git push origin my-new-feature`)
6. Create new Pull Request


## License

Author:: Russell Seymour ([rseymour@chef.io](mailto:rseymour@chef.io))

Author:: JJ Asghar ([jj@chef.io](mailto:jj@chef.io))

Copyright:: Copyright (c) 2017 Chef Software, Inc.

License:: Apache License, Version 2.0

```text
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