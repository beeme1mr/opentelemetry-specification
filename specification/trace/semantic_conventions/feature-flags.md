# Semantic conventions for Feature Flags

**Status**: [Experimental](../../../document-status.md)

<!-- Re-generate TOC with `markdown-toc --no-first-h1 -i` -->

<!-- toc -->

- [General Attributes](#general-attributes)
- [Provider Attributes](#provider-attributes)
- [Evaluated Attributes](#evaluated-attributes)

<!-- tocstop -->

**Span kind:** MUST always be `INTERNAL`.

Span `name` should be a combination of the provider name and the name of the function used when evaluating the flag, separated by a hyphen. For example, `unleash - isEnabled` or `my flag eval - getBoolValue`.

## General Attributes

This section describes the general attributes that are used for flag evaluation.

<!-- semconv feature_flag -->
| Attribute  | Type | Description  | Examples  | Required |
|---|---|---|---|---|
| `feature_flag.flag_key` | string | The unique identifier of the feature flag. | `show-new-logo` | Yes |
<!-- endsemconv -->

## Provider Attributes

This section describes the provider that was used to perform the flag evaluation.

<!-- semconv feature_flag.provider -->
| Attribute  | Type | Description  | Examples  | Required |
|---|---|---|---|---|
| `feature_flag.provider.name` | string | The name of the provider performing the flag evaluation. | `Flag Manager` | Yes |
| `feature_flag.provider.management_url` | string | The URL used to manage the feature flag in the provider. | `http://localhost:4200/flags/1` | No |
<!-- endsemconv -->

## Evaluated Attributes

This section describes how flag evaluations can be represented on a span.

<!-- semconv feature_flag.evaluated -->
| Attribute  | Type | Description  | Examples  | Required |
|---|---|---|---|---|
| `feature_flag.evaluated.variant` | string | The name associated with the evaluated value. | `reverse` | Conditional [1] |
| `feature_flag.evaluated.value` | string | A string representation of the evaluated value. | `true`; `red`; `on` | Conditional [2] |

**[1]:** A variant should be used if it is available. If the variant is present, feature_flag.evaluated.value should be omitted.

**[2]:** The value should only be used if the variant is not available. How the value is represented as a string should be determined by the implementer.
<!-- endsemconv -->
