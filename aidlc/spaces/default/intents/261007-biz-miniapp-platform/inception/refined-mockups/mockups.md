# Refined Mockups

## Screen 1 — Mock Admin Login

Desktop-first centered form with a single `h1`, mock user ID and password fields, primary Login button, and an environment badge. The form exposes loading, success and error states; errors are inline and preserve the user ID. No token or runtime link appears.

## Screen 2 — Mini App List

Application shell with header, navigation, main content and a primary Register Mini App action. The table shows name, code, version, menu permissions, enabled status, forceUpdate and Edit. Loading skeleton, empty state, API error with Retry, and populated state are explicit. Search/filter remain optional and visually secondary.

## Screen 3 — Create/Edit Form

Dedicated page with grouped sections for identity, menu permissions and status. Name, code, URL and version are labeled required fields; menu permissions may be empty. Inline validation sits beside the field, while Save and Cancel remain at the end. Saving disables duplicate submission, preserves values on API error, and returns to the list only after success.

## Responsive behavior

At desktop widths, use a two-column shell with a readable form max width. At tablet widths, collapse navigation and use one column. At narrow widths, table metadata stacks into cards while action labels remain visible.

## Visual direction

Neutral administrative palette, semantic HTML, visible focus ring, text labels paired with status colors, and reusable Button, TextField, Select, Toggle, Alert, StatusBadge, Table and EmptyState components. This is a demo design and does not claim BIZ branding.
