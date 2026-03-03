# notification-widget
Home screen chat widget that shows one specific chatbot message.

## Message skip filter (how to use)

The widget can ignore noisy chatbot payloads (for example pasted HTML snippets like:
`https://www.axa-gulf.com/en<span ... class="ng-binding aegov-file-uploaded" ...>`).

### Default behavior

`notifications.html` already skips messages containing:

- `https://www.axa-gulf.com/en`
- `aegov-file-uploaded`

### Customize skip patterns

Before the widget script runs, set a global array named
`window.NOTIFICATION_WIDGET_SKIP_PATTERNS`.

Example:

```html
<script>
  window.NOTIFICATION_WIDGET_SKIP_PATTERNS = [
    'https://www.axa-gulf.com/en',
    'aegov-file-uploaded',
    'another-noisy-token'
  ];
</script>
```

If an incoming message contains any configured pattern (case-insensitive), the widget
shows **Filtered** and does not render that noisy content.
