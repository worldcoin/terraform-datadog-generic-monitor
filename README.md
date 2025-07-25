# Fork kabisa/terraform-datadog-generic-monitor repository, which is no longer maintained.

We use it to monitor clusters, and module has deprecations which we need to fix before deprecation turns into error in next provider upgrade.

This module is a base module for most of our datadog alerts.
A good example use can be found [here](https://github.com/kabisa/terraform-datadog-system)

## Getting Started

Pre-commit:
   - Install [pre-commit](http://pre-commit.com/). E.g. `brew install pre-commit`.
   - Run `pre-commit install` in this repo. (Every time you clone a repo with pre-commit enabled you will need to run the pre-commit install command)
   - That’s it! Now every time you commit a code change (`.tf` file), the hooks in the `hooks:` config `.pre-commit-config.yaml` will execute.

<!-- BEGIN_TF_DOCS -->
## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_datadog"></a> [datadog](#requirement\_datadog) | ~> 3.12 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_datadog"></a> [datadog](#provider\_datadog) | ~> 3.12 |

## Modules

No modules.

## Resources

| Name | Type |
|------|------|
| [datadog_monitor.generic_datadog_monitor](https://registry.terraform.io/providers/DataDog/datadog/latest/docs/resources/monitor) | resource |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_additional_tags"></a> [additional\_tags](#input\_additional\_tags) | Additional tags to set on the monitor. Good tagging can be hard but very useful to make cross sections of the environment. Datadog has a few default tags. https://docs.datadoghq.com/getting_started/tagging/ is a good place to start reading about tags | `list(string)` | `[]` | no |
| <a name="input_alert_message"></a> [alert\_message](#input\_alert\_message) | Message to be sent when the alert threshold is hit | `string` | n/a | yes |
| <a name="input_alerting_enabled"></a> [alerting\_enabled](#input\_alerting\_enabled) | If set to false no alerts will be sent based on this monitor | `bool` | `true` | no |
| <a name="input_anomaly_recovery_window"></a> [anomaly\_recovery\_window](#input\_anomaly\_recovery\_window) | recovery\_window value, e.g. last\_15m Can only be used for anomaly monitors. https://registry.terraform.io/providers/DataDog/datadog/latest/docs/resources/monitor#nested-schema-for-monitor_threshold_windows | `any` | `null` | no |
| <a name="input_anomaly_trigger_window"></a> [anomaly\_trigger\_window](#input\_anomaly\_trigger\_window) | trigger\_window value, e.g. last\_15m Can only be used for anomaly monitors. https://registry.terraform.io/providers/DataDog/datadog/latest/docs/resources/monitor#nested-schema-for-monitor_threshold_windows | `any` | `null` | no |
| <a name="input_auto_resolve_time_h"></a> [auto\_resolve\_time\_h](#input\_auto\_resolve\_time\_h) | Time of hours after which a triggered monitor that receives no data is automatically resolved. | `number` | `null` | no |
| <a name="input_critical_recovery"></a> [critical\_recovery](#input\_critical\_recovery) | n/a | `number` | `null` | no |
| <a name="input_critical_threshold"></a> [critical\_threshold](#input\_critical\_threshold) | n/a | `number` | `null` | no |
| <a name="input_custom_message"></a> [custom\_message](#input\_custom\_message) | This field give the option to put in custom text. Both 'note' and 'docs' are prefixed in the template with 'note:' and 'docs:' respectively. 'custom\_message' allows for free format | `string` | `""` | no |
| <a name="input_docs"></a> [docs](#input\_docs) | Field in the alert message that can be used to document why the alert was sent or what to do. It's best to include links to authoritative resources about what's being monitored. Try to capture why and what the engineer should do with this message | `string` | `""` | no |
| <a name="input_enabled"></a> [enabled](#input\_enabled) | If set to false the monitor resource will not be created | `bool` | `true` | no |
| <a name="input_env"></a> [env](#input\_env) | This refers to the environment or which stage of deployment this monitor is checking. Good values are prd, acc, tst, dev... | `string` | n/a | yes |
| <a name="input_name"></a> [name](#input\_name) | Name that the monitor should get. Will be automatically prefixed with the Service name. Also name\_suffix and name\_prefix have an effect on the eventual name. It's best set this property to a value that best describes the concern you're trying to cover with the monitor. Eg. Connection Available | `string` | n/a | yes |
| <a name="input_name_prefix"></a> [name\_prefix](#input\_name\_prefix) | Can be used to prefix to the Monitor name | `string` | `""` | no |
| <a name="input_name_suffix"></a> [name\_suffix](#input\_name\_suffix) | Can be used to suffix to the Monitor name | `string` | `""` | no |
| <a name="input_new_group_delay"></a> [new\_group\_delay](#input\_new\_group\_delay) | Time (in seconds) to skip evaluations for new groups. https://registry.terraform.io/providers/DataDog/datadog/latest/docs/resources/monitor | `number` | `null` | no |
| <a name="input_no_data_message"></a> [no\_data\_message](#input\_no\_data\_message) | Message to be sent when the monitor is no longer receiving data | `string` | `""` | no |
| <a name="input_no_data_timeframe"></a> [no\_data\_timeframe](#input\_no\_data\_timeframe) | n/a | `number` | `null` | no |
| <a name="input_note"></a> [note](#input\_note) | Field in the alert message that can be used to bring something to the attention of the engineer handling the alert | `string` | `""` | no |
| <a name="input_notification_channel"></a> [notification\_channel](#input\_notification\_channel) | Channel to which datadog sends alerts, will be overridden by alerting\_enabled if that's set to false | `string` | `""` | no |
| <a name="input_notify_no_data"></a> [notify\_no\_data](#input\_notify\_no\_data) | Do you want an alert when the monitoring stops sending data? | `bool` | `false` | no |
| <a name="input_ok_threshold"></a> [ok\_threshold](#input\_ok\_threshold) | n/a | `number` | `null` | no |
| <a name="input_priority"></a> [priority](#input\_priority) | Number from 1 (high) to 5 (low). | `number` | n/a | yes |
| <a name="input_query"></a> [query](#input\_query) | Query that's based on a metric to be used to raise an alert | `string` | n/a | yes |
| <a name="input_recovery_message"></a> [recovery\_message](#input\_recovery\_message) | Recovery message to be sent when the alert threshold is no longer hit | `string` | `""` | no |
| <a name="input_require_full_window"></a> [require\_full\_window](#input\_require\_full\_window) | n/a | `bool` | `true` | no |
| <a name="input_restricted_roles"></a> [restricted\_roles](#input\_restricted\_roles) | A list of unique role identifiers to define which roles are allowed to edit the monitor. | `list(string)` | `[]` | no |
| <a name="input_service"></a> [service](#input\_service) | Service name of what you're monitoring. This also sets the service:<service> tag on the monitor | `string` | n/a | yes |
| <a name="input_service_display_name"></a> [service\_display\_name](#input\_service\_display\_name) | n/a | `string` | `null` | no |
| <a name="input_type"></a> [type](#input\_type) | n/a | `string` | `"metric alert"` | no |
| <a name="input_warning_recovery"></a> [warning\_recovery](#input\_warning\_recovery) | n/a | `number` | `null` | no |
| <a name="input_warning_threshold"></a> [warning\_threshold](#input\_warning\_threshold) | n/a | `number` | `null` | no |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_alert_id"></a> [alert\_id](#output\_alert\_id) | n/a |
<!-- END_TF_DOCS -->
