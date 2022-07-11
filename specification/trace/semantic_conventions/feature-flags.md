# Semantic conventions for Feature Flags

**Status**: [Experimental](../../document-status.md)

**Span kind:** MUST always be `INTERNAL`.

The **span name** MUST be of the format `<feature_flag.provider_name> <feature_flag.flag_key>` provided that
`feature_flag.provider_name` is available. If `feature_flag.provider_name` is not available, the
span SHOULD be named `Feature Flag <feature_flag.flag_key>`.

<!-- semconv feature_flag -->
| Attribute  | Type | Description  | Examples  | Requirement Level |
|---|---|---|---|---|
| `feature_flag.flag_key` | string | The unique identifier of the feature flag. | `logo-color` | Required |
| `feature_flag.provider_name` | string | The name of the service that performs the flag evaluation. | `Flag Manager` | Recommended |
| `feature_flag.evaluated_variant` | string | The human readable name that identifies the evaluated value. | `red`; `blue`; `green` | Conditionally Required: [1] |
| `feature_flag.evaluated_value` | string | A string representation of the evaluated value. | `ff0000`; `0000ff`; `00ff00` | Conditionally Required: [2] |

**[1]:** A variant should be used if it is available. If the variant is present, feature_flag.evaluated_value should be omitted.

**[2]:** The value should only be used if the variant is not available. How the value is represented as a string should be determined by the implementer.
<!-- endsemconv -->
