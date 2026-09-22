# Provider and License

This page covers settings shared by Personal and Team. Open the matching edition guide before using a Team-only feature.

## Provider

A provider supplies the model used by analysis, review, report, or remediation workflows.

### Configure a provider

1. Open **Settings → Providers**.
2. Choose a provider preset.
3. Enter the Base URL, model, and API key in the provider form.
4. Save the provider.
5. Select **Test provider**.
6. Set it as the default provider when the test succeeds.

### Result

The provider appears in the saved provider list and can be selected by an audit or Team workflow.

### Common issues

- **Connection failed:** check the Base URL and network access.
- **Model not found:** use a model name accepted by the selected provider.
- **Authentication failed:** replace the key in the provider form and save again.

## License

1. Open **Settings → License**.
2. Choose the activation or validation action shown by the installed edition.
3. Finish the browser or code step if the official service opens one.
4. Return to the desktop app and refresh the license state.

### Result

The License page shows the current access state and the edition that is authorized.

Development builds can show the activation path without proving a production entitlement. A production license is confirmed only by the official service and the desktop validation result.

### Common issues

- **Activation window does not open:** check that the desktop app is allowed to open the official activation page.
- **Access is still pending:** return to the desktop app and refresh after completing the service step.
- **Wrong edition:** close the app and start the matching Personal or Team installation.
