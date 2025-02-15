<!--
  ~ Copyright (c) 2023-2024 Arista Networks, Inc.
  ~ Use of this source code is governed by the Apache License 2.0
  ~ that can be found in the LICENSE file.
  -->

# Semantic Versioning

The AVD project follows Semantic Versioning ([SemVer](https://semver.org/)).

This document describes which attributes and APIs are stable and follow SemVer and which ones may change between minor releases.

## Ansible Collection (arista.avd)

All roles input variables follow SemVer. Any breaking changes will, at a minimum, be communicated with a deprecation notice in the previous release, except for the ones resulting from a bug fix that will be documented in the release notes. Keys will then be documented as removed in the next major release.

### Roles

| Roles | Inputs Follow SemVer | Outputs Follow SemVer | Notes |
| ----- | :------------------: | :-------------------: | ----- |
| `eos_designs` + `eos_cli_config_gen`<br>EOS CLI configuration | ✅ | ✅ | When leveraging `eos_designs` with `eos_cli_config_gen`, the resulting EOS CLI configuration generated from `eos_cli_config_gen` will be maintained, unless in rare cases when addressing a bug. |
| `eos_designs`<br>Structured configuration | ✅ | ✘ | eos_designs `structured_configuration` may change between minor releases.<br>Structured configuration can change to use new keys when keys are deprecated in the `eos_cli_config_gen` role. |
| `eos_designs`<br>Documentation | ✅ | ✘ | Fabric documentation artifacts may change between minor releases.<br>Breaking changes to CSV output will be communicated in the release notes. |
| `eos_designs`<br>`avd_switch_facts` or `switch.*` | ✅ | ✘ | The `switch.*` and `avd_switch_facts` are internal datamodels used for sharing data between various stages of `eos_designs`. They **should not** be used in custom templates for interface descriptions or IP addressing, since they are subject to change without notice. |
| `eos_cli_config_gen`<br>EOS configuration | ✅ | ✅ | EOS configuration generated by `eos_cli_config_gen` follows SemVer.<br>Breaking changes may occur in rare cases when addressing a bug.<br>Reordering of the CLI output may occur but without impacting the resulting configuration on EOS. |
| `eos_cli_config_gen`<br>Documentation | ✅ | ✘ | Device documentation artifacts may change during minor releases.|
| `cvp_configlet_upload` | ✅ | ✅ | |
| `eos_config_deploy_cvp` | ✅ | ✘ | Structured configuration output may change during minor releases to accommodate changes in the ansible-cvp collection. <br>The resulting CloudVision configuration will be maintained, unless in rare cases, when addressing a bug.<br>Breaking changes will be communicated in the release notes. |
| `cv_deploy` | ✅ | ✅ | The resulting CloudVision configuration will be maintained, unless in rare cases, when addressing a bug. |
| `eos_config_deploy_eapi` | ✅ | ✅ | |
| `eos_validate_state` | ✅ | ✘ | The generated reports and other artifacts may change between minor releases.<br>Breaking changes to CSV outputs will be communicated in the release notes.|
| `dhcp_provisioner` | ✅ | ✘ | Structured configuration output may change during minor releases to accommodate changes in the ansible-cvp collection.<br>The resulting DHCP configuration will be maintained, unless in rare cases, when addressing a bug. |
| `build_output_folders` | ✅ | ✅ | |

### Plugins

| Plugins | Inputs Follow SemVer | Outputs Follow SemVer | Notes |
| ------- | :------------------: | :-------------------: | ----- |
| Filter: `add_md_toc` | ✅ | ✅ | |
| Filter: `decrypt` | ✅ | ✅ | |
| Filter: `default` | ✅ | ✅ | |
| Filter: `encrypt` | ✅ | ✅ | |
| Filter: `hide_passwords` | ✅ | ✅ | |
| Filter: `is_in_filter` | ✅ | ✅ | |
| Filter: `list_compress` | ✅ | ✅ | |
| Filter: `natural_sort` | ✅ | ✅ | |
| Filter: `range_expand` | ✅ | ✅ | |
| Filter: `snmp_hash` | ✅ | ✅ | |
| Filter: `status_render` | ✅ | ✅ | |
| Action: `configlet_build_config` | ✘ | ✘ | Internal plugin, not intended for external use. |
| Action: `cv_workflow` | ✅ | ✅ | The resulting CloudVision configuration will be maintained, unless in rare cases, when addressing a bug. |
| Action: `eos_designs_facts` | ✘ | ✘ | Internal plugin, not intended for external use.  |
| Action: `eos_designs_structured_config` | ✘ | ✘ | Internal plugin, not intended for external use. |
| Action: `eos_validate_state_reports` | ✘ | ✘ | Internal plugin, not intended for external use. |
| Action: `eos_validate_state_runner` | ✘ | ✘ | Internal plugin, not intended for external use. |
| Action: `inventory_to_container` | ✘ | ✘ | Internal plugin, not intended for external use. |
| Action: `set_vars` | ✅ | ✅ | |
| Action: `verify_requirements` | ✘ | ✘ | Internal plugin, not intended for external use. |
| Test: `contains` | ✅ | ✅ | |
| Test: `defined` | ✅ | ✅ | |
| Test: `global_vars` | ✅ | ✅ | |

## PyAVD

All functions input variables follow SemVer. Any breaking changes will, at a minimum, be communicated with a deprecation notice in the previous release, except for the ones resulting from a bug fix that will be documented in the release notes. Keys will then be documented as removed in the next major release.

!!! warning

    Internal/undocumented code is not covered by SemVer. Changes may not be documented in release notes.

| Functions | Inputs Follow SemVer | Outputs Follow SemVer | Notes |
| --------- | :------------------: | :-------------------: | ----- |
| `validate_inputs()` | ✅ | ✅ | |
| `get_avd_facts()` | ✅ | ✘  | `avd_facts` output may change between minor releases. |
| `get_device_structured_config()` | ✅ | ✘  | `structured_configuration` may change between minor releases.<br>Structure config can change to use new keys when keys are deprecated in the `get_device_config()` function.<br>The resulting EOS CLI configuration generated from the `get_device_config()` function will be maintained, unless in rare cases when addressing a bug. |
| `validate_structured_config()` | ✅ | ✅ | |
| `get_device_config()` | ✅ | ✅ | EOS CLI configuration generated from eos_cli_config_gen follows SemVer.<br> Breaking changes may occur in rare cases when addressing a bug.<br> Reordering of the CLI output may occur but without impacting the resulting configuration on EOS. |
| `get_device_doc()` | ✅ | ✘  | Device documentation artifacts may change during minor releases. |
