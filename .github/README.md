# ans_role_config_automatic_scanning

Configure automatic scanner discovery and IPP Everywhere driverless scanning.

[![Release](https://img.shields.io/github/release/digimokan/ans_role_config_automatic_scanning.svg?label=release)](https://github.com/digimokan/ans_role_config_automatic_scanning/releases/latest "Latest Release Notes")
[![License](https://img.shields.io/badge/license-MIT-blue.svg?label=license)](LICENSE.md "Project License")

## Table Of Contents

* [Purpose](#purpose)
* [Requirements](#requirements)
* [Supported Operating Systems](#supported-operating-systems)
* [Quick Start](#quick-start)
    * [Use From Playbook](#use-from-playbook)
* [Contributing](#contributing)

## Purpose

* Configure automatic scanner discovery, using the [SANE](http://www.sane-project.org/)
  scan client.

* Configure discovered scanners for use, using
  [IPP Everywhere](https://www.pwg.org/ipp/everywhere.html) "driverless"
  scanning protocol.

## Requirements

* Scanner discovery requires that scanner is connected via the local network,
  and _not_ via USB connection to the host machine.

* Scanner discovery requires that scanner reside on the _same IP subnet_ as the
  host machine.

* Scanners must support the
  [IPP Everywhere](https://www.pwg.org/ipp/everywhere.html) "driverless"
  scanning protocol.

* See the following resources to check IPP Everywhere support for a scanner:

    * [IPP Everywhere Official Supported Printer List](https://www.pwg.org/printers/)
      (may not be fully up-to-date)

    * [Apple AirPrint Official Supported Printer List](https://support.apple.com/en-us/HT201311#printers)
      (extensive list, and it's usable, since AirPrint depends on IPP Everywhere)

* After running this role, installing a scanning application such as
[Simple-Scan](https://gitlab.gnome.org/GNOME/simple-scan) is required.

## Supported Operating Systems

* Arch Linux.
* FreeBSD.

## Quick Start

### Use From Playbook

1. Create `requirements.yml` in ansible project root, and add this content:

   ```yaml
   # requirements.yml
   - src: https://github.com/digimokan/ans_role_config_automatic_scanning
   ```

2. From the project root directory, install/download the role:

   ```shell
   $ ansible-galaxy install --role-file requirements.yml --roles-path ./roles --force-with-deps
   ```

   * _NOTE:_ `--force-with-deps` _ensures subsequent calls download updates_

3. Include the role like any local role, from the project playbook:

   ```yaml
   # playbook.yml
   - hosts: localhost
     connection: local
     tasks:
       - name: "Configure automatic scanner discovery and driverless scanning"
         ansible.builtin.include_role:
           name: ans_role_config_automatic_scanning
   ```

## Contributing

* Feel free to report a bug or propose a feature by opening a new
  [Issue](https://github.com/digimokan/ans_role_config_automatic_scanning/issues).
* Follow the project's [Contributing](CONTRIBUTING.md) guidelines.
* Respect the project's [Code Of Conduct](CODE_OF_CONDUCT.md).

