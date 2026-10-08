# Design System Mapping

| Need | Component pattern | Rule |
|---|---|---|
| Form input | TextField + FieldMessage | visible label, required marker, described-by error |
| Boolean config | Toggle | text state Bật/Tắt and keyboard operation |
| Collection | Table / stacked cards | column headers on desktop, readable cards on tablet |
| Feedback | Alert + live region | message uses text and status semantics |
| Progress | Skeleton + disabled action | scoped to the loading region |
| Empty/error | EmptyState / ErrorState | clear next action and Retry |

Tokens: 8px spacing scale, 16px base text, 4px radius, high-contrast foreground/background, and a visible 2px focus outline.
