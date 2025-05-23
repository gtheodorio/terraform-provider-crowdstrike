---
page_title: "crowdstrike_default_prevention_policy_windows Resource - crowdstrike"
subcategory: "Prevention Policy"
description: |-
  This resource allows you to manage the default prevention policy for Windows hosts. Prevention policies allow you to manage what activity will trigger detections and preventions on your hosts. Destruction of this resource will not delete the default prevention policy or remove any configured settings.
  API Scopes
  The following API scopes are required:
  Prevention policies | Read & Write
---

# crowdstrike_default_prevention_policy_windows (Resource)

This resource allows you to manage the default prevention policy for Windows hosts. Prevention policies allow you to manage what activity will trigger detections and preventions on your hosts. Destruction of this resource *will not* delete the default prevention policy or remove any configured settings.

## API Scopes

The following API scopes are required:

- Prevention policies | Read & Write


## Example Usage

```terraform
terraform {
  required_providers {
    crowdstrike = {
      source = "registry.terraform.io/crowdstrike/crowdstrike"
    }
  }
}

provider "crowdstrike" {
  cloud = "us-2"
}


resource "crowdstrike_default_prevention_policy_windows" "default" {
  description     = "managed by terraform"
  ioa_rule_groups = []
  adware_and_pup = {
    "detection"  = "MODERATE"
    "prevention" = "CAUTIOUS"
  }
  cloud_anti_malware_microsoft_office_files = {
    detection  = "MODERATE"
    prevention = "DISABLED"
  }
  cloud_anti_malware = {
    "detection"  = "MODERATE"
    "prevention" = "CAUTIOUS"
  }
  cloud_anti_malware_user_initiated = {
    "detection"  = "MODERATE"
    "prevention" = "CAUTIOUS"
  }
  sensor_anti_malware = {
    "detection"  = "MODERATE"
    "prevention" = "CAUTIOUS"
  }
  sensor_anti_malware_user_initiated = {
    "detection"  = "MODERATE"
    "prevention" = "CAUTIOUS"
  }
  extended_user_mode_data = {
    "detection" = "MODERATE"
  }
  usb_insertion_triggered_scan                   = true
  application_exploitation_activity              = true
  additional_user_mode_data                      = true
  notify_end_users                               = true
  advanced_remediation                           = true
  backup_deletion                                = true
  bios_deep_visibility                           = true
  chopper_webshell                               = true
  code_injection                                 = true
  credential_dumping                             = true
  cryptowall                                     = true
  custom_blocking                                = true
  detect_on_write                                = true
  drive_by_download                              = true
  driver_load_prevention                         = true
  interpreter_only                               = true
  engine_full_visibility                         = true
  enhanced_exploitation_visibility               = true
  enhanced_dll_load_visibility                   = true
  enhanced_ml_for_larger_files                   = true
  file_encryption                                = true
  file_system_access                             = true
  force_aslr                                     = true
  force_dep                                      = true
  heap_spray_preallocation                       = true
  null_page_allocation                           = true
  seh_overwrite_protection                       = true
  hardware_enhanced_exploit_detection            = true
  http_detections                                = true
  redact_http_detection_details                  = true
  intelligence_sourced_threats                   = true
  javascript_via_rundll32                        = true
  locky                                          = true
  memory_scanning                                = true
  memory_scanning_scan_with_cpu                  = true
  microsoft_office_file_suspicious_macro_removal = true
  on_write_script_file_visibility                = true
  prevent_suspicious_processes                   = true
  quarantine_and_security_center_registration    = true
  quarantine_on_removable_media                  = true
  quarantine_on_write                            = true
  script_based_execution_monitoring              = true
  sensor_tampering_protection                    = true
  suspicious_registry_operations                 = true
  suspicious_scripts_and_commands                = true
  upload_unknown_executables                     = true
  upload_unknown_detection_related_executables   = true
  volume_shadow_copy_audit                       = true
  volume_shadow_copy_protect                     = true
  vulnerable_driver_protection                   = true
  windows_logon_bypass_sticky_keys               = true
  file_system_containment                        = true
}

output "default_prevention_policy_windows" {
  value = crowdstrike_default_prevention_policy_windows.default
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `ioa_rule_groups` (Set of String) IOA Rule Group to attach to the prevention policy.

### Optional

- `additional_user_mode_data` (Boolean) Whether to enable the setting. Allows the sensor to get more data from a user-mode component it loads into all eligible processes, which augments online machine learning and turns on additional detections. Recommend testing with critical applications before full deployment.
- `advanced_remediation` (Boolean) Whether to enable the setting. Perform advanced remediation for IOA detections to kill processes, quarantine files, remove scheduled tasks, and clear and delete ASEP registry values.
- `adware_and_pup` (Attributes) Use cloud-based machine learning informed by global analysis of executables to detect and prevent adware and potentially unwanted programs (PUP) for your online hosts. (see [below for nested schema](#nestedatt--adware_and_pup))
- `application_exploitation_activity` (Boolean) Whether to enable the setting. Creation of a process, such as a command prompt, from an exploited browser or browser flash plugin was blocked.
- `backup_deletion` (Boolean) Whether to enable the setting. Deletion of backups often indicative of ransomware activity.
- `bios_deep_visibility` (Boolean) Whether to enable the setting. Provides visibility into BIOS. Detects suspicious and unexpected images. Recommend testing to monitor system startup performance before full deployment.
- `chopper_webshell` (Boolean) Whether to enable the setting. Execution of a command shell was blocked and is indicative of the system hosting a Chopper web page.
- `cloud_anti_malware` (Attributes) Use cloud-based machine learning informed by global analysis of executables to detect and prevent known malware for your online hosts. (see [below for nested schema](#nestedatt--cloud_anti_malware))
- `cloud_anti_malware_microsoft_office_files` (Attributes) Identifies potentially malicious macros in Microsoft Office files and, if prevention is enabled, either quarantines the file or removes the malicious macros before releasing the file back to the host (see [below for nested schema](#nestedatt--cloud_anti_malware_microsoft_office_files))
- `cloud_anti_malware_user_initiated` (Attributes) For online hosts running on-demand scans initiated by end users, use cloud-based machine learning informed by global analysis of executables to detect and prevent known malware. (see [below for nested schema](#nestedatt--cloud_anti_malware_user_initiated))
- `code_injection` (Boolean) Whether to enable the setting. Kill processes that unexpectedly injected code into another process. Requires additional_user_mode_data to be enabled.
- `credential_dumping` (Boolean) Whether to enable the setting. Kill suspicious processes determined to be stealing logins and passwords. Requires additional_user_mode_data to be enabled.
- `cryptowall` (Boolean) Whether to enable the setting. A process associated with Cryptowall was blocked.
- `custom_blocking` (Boolean) Whether to enable the setting. Block processes matching hashes that you add to IOC Management with the action set to "Block" or "Block, hide detection".
- `description` (String) Description of the prevention policy.
- `detect_on_write` (Boolean) Whether to enable the setting. Use machine learning to analyze suspicious files when they're written to disk. To adjust detection sensitivity, change Anti-malware Detection levels in Sensor Machine Learning and Cloud Machine Learning.
- `drive_by_download` (Boolean) Whether to enable the setting. A suspicious file written by a browser attempted to execute and was blocked.
- `driver_load_prevention` (Boolean) Whether to enable the setting. Block the loading of kernel drivers that CrowdStrike analysts have identified as malicious. Available on Windows 10 and Windows Server 2016 and later.
- `engine_full_visibility` (Boolean) Whether to enable the setting. Provides visibility into malicious System Management Automation engine usage by any application. Requires interpreter_only to be enabled.
- `enhanced_dll_load_visibility` (Boolean) Whether to enable the setting. For hosts running Windows Server, increases sensor visibility of loaded DLLs. Improves detection coverage and telemetry, but may cause a small performance impact. Recommend testing with critical applications before full deployment.
- `enhanced_exploitation_visibility` (Boolean) Whether to enable the setting. For hosts running Windows 10 1809 and Server 2019 and later, provides additional visibility into common exploitation techniques used to weaken or circumvent application security.
- `enhanced_ml_for_larger_files` (Boolean) Whether to enable the setting. Expand ML file size coverage. Existing ML level settings apply.
- `extended_user_mode_data` (Attributes) Allows the sensor to get more data from a user-mode component it loads into all eligible processes, which augments online machine learning and turns on additional detections. Recommend testing with critical applications before full deployment. (see [below for nested schema](#nestedatt--extended_user_mode_data))
- `file_encryption` (Boolean) Whether to enable the setting. A process that created a file with a known ransomware extension was terminated.
- `file_system_access` (Boolean) Whether to enable the setting. A process associated with a high volume of file system operations typical of ransomware behavior was terminated.
- `file_system_containment` (Boolean) Whether to enable the setting. File System Containment will be enabled, this will allow prevention capabilities to automatically contain file system activity.  When disabled each user under active containment will be released and the File System Containment will enter a disabled mode
- `force_aslr` (Boolean) Whether to enable the setting. An Address Space Layout Randomization (ASLR) bypass attempt was detected and blocked. This may have been part of an attempted exploit. Requires additional_user_mode_data to be enabled.
- `force_dep` (Boolean) Whether to enable the setting. A process that had Force Data Execution Prevention (Force DEP) applied tried to execute non-executable memory and was blocked. Requires additional_user_mode_data to be enabled.
- `hardware_enhanced_exploit_detection` (Boolean) Whether to enable the setting. Provides additional visibility into application exploits by using CPU hardware features that detect suspicious control flows. Available only for hosts running Windows 10 (RS4) or Windows Server 2016 Version 1803 or later and Skylake or later CPU.
- `heap_spray_preallocation` (Boolean) Whether to enable the setting. A heap spray attempt was detected and blocked. This may have been part of an attempted exploit. Requires additional_user_mode_data to be enabled.
- `http_detections` (Boolean) Whether to enable the setting. Allows the sensor to monitor unencrypted HTTP traffic and certain encrypted HTTPS traffic on the sensor for malicious patterns and generate detection events on non-Server systems.
- `intelligence_sourced_threats` (Boolean) Whether to enable the setting. Block processes that CrowdStrike Intelligence analysts classify as malicious. These are focused on static hash-based IOCs.
- `interpreter_only` (Boolean) Whether to enable the setting. Provides visibility into malicious PowerShell interpreter usage. For hosts running Windows 10, Script-Based Execution Monitoring may be used instead.
- `javascript_via_rundll32` (Boolean) Whether to enable the setting. JavaScript executing from a command line via rundll32.exe was prevented.
- `locky` (Boolean) Whether to enable the setting. A process determined to be associated with Locky was blocked.
- `memory_scanning` (Boolean) Whether to enable the setting. Provides visibility into in-memory attacks by scanning for suspicious artifacts on hosts with the following: an integrated GPU and supporting OS libraries, Windows 10 v1607 (RS1) or later, and a Skylake or newer Intel CPU.
- `memory_scanning_scan_with_cpu` (Boolean) Whether to enable the setting. Allows memory scanning to use the CPU or virtual CPU when an integrated GPU is not available. All Intel processors supported, requires Windows 8.1/2012 R2 or later.
- `microsoft_office_file_suspicious_macro_removal` (Boolean) Whether to enable the setting. Identifies potentially malicious macros in Microsoft Office files and, if prevention is enabled, either quarantines the file or removes the malicious macros before releasing the file back to the host
- `notify_end_users` (Boolean) Whether to enable the setting. Show a pop-up notification to the end user when the Falcon sensor blocks, kills, or quarantines. These messages also show up in the Windows Event Viewer under Applications and Service Logs.
- `null_page_allocation` (Boolean) Whether to enable the setting. Allocating memory to the NULL (0) memory page was detected and blocked. This may have been part of an attempted exploit. Requires additional_user_mode_data to be enabled.
- `on_write_script_file_visibility` (Boolean) Whether to enable the setting. Provides improved visibility into various script files being written to disk in addition to clouding a portion of their content.
- `prevent_suspicious_processes` (Boolean) Whether to enable the setting. Block processes that CrowdStrike analysts classify as suspicious. These are focused on dynamic IOAs, such as malware, exploits and other threats.
- `quarantine_and_security_center_registration` (Boolean) Whether to enable the setting. Quarantine executable files after they’re prevented by NGAV. When this is enabled, we recommend setting anti-malware prevention levels to Moderate or higher and not using other antivirus solutions. CrowdStrike Falcon registers with Windows Security Center, disabling Windows Defender.
- `quarantine_on_removable_media` (Boolean) Whether to enable the setting. Quarantine executable files after they’re prevented by NGAV.
- `quarantine_on_write` (Boolean) Whether to enable the setting. Use machine learning to quarantine suspicious files when they're written to disk. To adjust quarantine sensitivity, change Anti-malware Prevention levels in Sensor Machine Learning and Cloud Machine Learning.
- `redact_http_detection_details` (Boolean) Whether to enable the setting. Remove certain information from HTTP Detection events, including URL, raw HTTP header and POST bodies if they were present. This does not affect the generation of HTTP Detections, only additional details that would be included and may include personal information (depending on the malware in question). When disabled, the information is used to improve the response to detection events. Has no effect unless HTTP Detections is also enabled.
- `script_based_execution_monitoring` (Boolean) Whether to enable the setting. For hosts running Windows 10 and Servers 2016 and later, provides visibility into suspicious scripts and VBA macros in Office documents. Requires Quarantine & Security Center Registration toggle to be enabled.
- `seh_overwrite_protection` (Boolean) Whether to enable the setting. Overwriting a Structured Exception Handler (SEH) was detected and may have been blocked. This may have been part of an attempted exploit. Requires additional_user_mode_data to be enabled.
- `sensor_anti_malware` (Attributes) For offline and online hosts, use sensor-based machine learning to identify and analyze unknown executables as they run to detect and prevent malware. (see [below for nested schema](#nestedatt--sensor_anti_malware))
- `sensor_anti_malware_user_initiated` (Attributes) For offline and online hosts running on-demand scans initiated by end users, use sensor-based machine learning to identify and analyze unknown executables to detect and prevent malware. (see [below for nested schema](#nestedatt--sensor_anti_malware_user_initiated))
- `sensor_tampering_protection` (Boolean) Whether to enable the setting. Blocks attempts to tamper with the sensor. If disabled, the sensor still creates detections for tampering attempts but doesn’t block them. Disabling not recommended.
- `suspicious_registry_operations` (Boolean) Whether to enable the setting. Block registry operations that CrowdStrike analysts classify as suspicious. Focuses on dynamic IOAs, such as ASEPs and security config changes. The associated process may be killed.
- `suspicious_scripts_and_commands` (Boolean) Whether to enable the setting. Block execution of scripts and commands that CrowdStrike analysts classify as suspicious. Requires Interpreter-Only and/or Script-Based Execution Monitoring.
- `upload_unknown_detection_related_executables` (Boolean) Whether to enable the setting. Upload all unknown detection-related executables for advanced analysis in the cloud.
- `upload_unknown_executables` (Boolean) Whether to enable the setting. Upload all unknown executables for advanced analysis in the cloud.
- `usb_insertion_triggered_scan` (Boolean) Whether to enable the setting. Start an on-demand scan when an end user inserts a USB device. To adjust detection sensitivity, change Anti-malware Detection levels in On-Demand Scans Machine Learning.
- `volume_shadow_copy_audit` (Boolean) Whether to enable the setting. Create an alert when a suspicious process deletes volume shadow copies. Recommended: Use audit mode with a test group to try allowlisting trusted software before turning on Protect.
- `volume_shadow_copy_protect` (Boolean) Whether to enable the setting. Prevent suspicious processes from deleting volume shadow copies. Requires volume_shadow_copy_audit.
- `vulnerable_driver_protection` (Boolean) Whether to enable the setting. Quarantine and block the loading of newly written kernel drivers that CrowdStrike analysts have identified as vulnerable. Available on Windows 10 and Windows 2016 and later. Requires driver_load_prevention.
- `windows_logon_bypass_sticky_keys` (Boolean) Whether to enable the setting. A command line process associated with Windows logon bypass was prevented from executing.

### Read-Only

- `id` (String) Identifier for the prevention policy.
- `last_updated` (String) Timestamp of the last Terraform update of the resource.

<a id="nestedatt--adware_and_pup"></a>
### Nested Schema for `adware_and_pup`

Required:

- `detection` (String) Machine learning level for detection.
- `prevention` (String) Machine learning level for prevention.


<a id="nestedatt--cloud_anti_malware"></a>
### Nested Schema for `cloud_anti_malware`

Required:

- `detection` (String) Machine learning level for detection.
- `prevention` (String) Machine learning level for prevention.


<a id="nestedatt--cloud_anti_malware_microsoft_office_files"></a>
### Nested Schema for `cloud_anti_malware_microsoft_office_files`

Required:

- `detection` (String) Machine learning level for detection.
- `prevention` (String) Machine learning level for prevention.


<a id="nestedatt--cloud_anti_malware_user_initiated"></a>
### Nested Schema for `cloud_anti_malware_user_initiated`

Required:

- `detection` (String) Machine learning level for detection.
- `prevention` (String) Machine learning level for prevention.


<a id="nestedatt--extended_user_mode_data"></a>
### Nested Schema for `extended_user_mode_data`

Required:

- `detection` (String) Machine learning level for detection.


<a id="nestedatt--sensor_anti_malware"></a>
### Nested Schema for `sensor_anti_malware`

Required:

- `detection` (String) Machine learning level for detection.
- `prevention` (String) Machine learning level for prevention.


<a id="nestedatt--sensor_anti_malware_user_initiated"></a>
### Nested Schema for `sensor_anti_malware_user_initiated`

Required:

- `detection` (String) Machine learning level for detection.
- `prevention` (String) Machine learning level for prevention.

## Import

Import is supported using the following syntax:

```shell
# The linux default prevention policy can be imported by specifying the id.
terraform import crowdstrike_default_prevention_policy_linux.default 7fb858a949034a0cbca175f660f1e769
```
