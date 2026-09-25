# GRID --- Google-linked Report & Input Dashboard

**Configure. Submit. Report. Sync.**

GRID is a lightweight, mobile-first dashboard for submitting data
through a Google Form and viewing configured reports from a linked
Google Sheet.

It is designed as a standalone Progressive Web App (PWA), with
configuration stored locally in the browser and optional Google access
for reports and Drive synchronization.

## What GRID does

GRID keeps the input and reporting experience simple:

-   **Home** --- Fill in configured fields and submit an entry directly
    to a Google Form.
-   **Report** --- Read data from a linked Google Sheet and display it
    using the configured rows, columns, values and filters.
-   **Settings** --- Configure the Google Form, Google Sheet, form
    fields, default values and report layout.
-   **Sync** --- Optionally synchronize GRID configuration with Google
    Drive.
-   **About** --- View installation, privacy, sharing, legal, version
    and app information.

## Core features

-   🏠 **Home** --- Dynamically generated from the fields configured in
    Settings.
-   ➕ **Form fields** --- Define field labels, data types, Google Form
    entry IDs, required status and Sheet column headers.
-   🔽 **Default values** --- Configure the values that appear in Home
    dropdowns. Values can be added, removed and reordered.
-   📋 **Google Form submission** --- Submit Home entries directly to
    the configured Google Form using its `entry.NNNNNNN` field IDs.
-   📊 **Google Sheet reports** --- Fetch data from the linked Google
    Sheet when needed and build the report from the configured Sheet
    data.
-   🔎 **Report configuration** --- Configure Rows, Columns, Filters and
    the report Value field.
-   📌 **Column values** --- Select multiple values for the configured
    report column.
-   ➕ **Numeric aggregation** --- Configure Sum, Average, Count or
    Distinct Count for numeric report fields.
-   💾 **JSON backup** --- Export the complete GRID configuration to a
    JSON file and import it again later.
-   ☁️ **Google Drive sync** --- Optional synchronization of GRID
    configuration with your own Google Drive.
-   📱 **PWA** --- Install GRID on supported devices and use the
    application as a standalone app.
-   🌓 **Light theme** --- GRID uses a clean light interface designed
    for mobile and desktop use.

## How Google Form submission works

GRID does not need to read the Google Form to submit an entry.

The Form URL is configured in **Settings → Links**. Each GRID field is
associated with the corresponding Google Form `entry.NNNNNNN` ID in
**Settings → Form Fields**.

When the user submits Home, GRID sends the entered values to the Google
Form's response endpoint.

Example:

``` text
Month        → entry.505600733
Name         → entry.1276013773
Reason/Cause → entry.1255799336
Amount       → entry.1327223822
```

The actual entry IDs depend on the Google Form being configured.

## Form fields and default values

GRID starts without application-specific fields or sample data.

Everything is configured by the user.

Go to:

**Settings → Form Fields**

You can configure:

-   Field label
-   Data type
-   Google Form entry ID
-   Exact Google Sheet column header
-   Required / optional status
-   Minimum value for numeric fields

After the fields are configured, use **Default values shown on Home** to
define the values displayed by Home.

For example:

``` text
Month
  Sep-26
  Oct-26
  Nov-26

Name
  Krishna
  Naren
  Dwani
  Deepti
```

The Home screen is generated from this configuration. Nothing specific
such as Month, Name or Reason/Cause is hardcoded into the application.

Default values can be:

-   Added
-   Deleted
-   Reordered with ▲ / ▼
-   Saved as part of the GRID configuration

## Report

The Report section uses the linked Google Sheet as its data source.

GRID does not continuously read the Sheet.

The user explicitly fetches the Sheet data when report configuration or
reporting data needs to be refreshed.

The report can be configured using:

-   **Rows** --- single selection
-   **Columns** --- single selection
-   **Column values** --- multiple selections
-   **Filters** --- single selection
-   **Value** --- numeric field
-   **Aggregation** --- Sum, Average, Count or Distinct Count

Aggregation applies to numeric fields.

The report configuration is stored locally with the rest of the GRID
settings.

## Data & privacy

GRID's local configuration is stored in the browser on the device where
it is used.

GRID does not require a server for its core configuration and Home
form-submission experience.

Google access is used only for features that require Google services,
such as:

-   Reading the linked Google Sheet for Report
-   Google Drive synchronization

Google authentication is not required merely to configure the local Form
Fields or Default Values.

The application does not continuously poll the Google Sheet.

## JSON backup and restore

Use:

**Settings → Sync → Export .json**

to save the configured GRID settings.

The exported configuration can include:

-   Google Form link
-   Google Sheet link
-   Form title
-   Form fields
-   Entry IDs
-   Data types
-   Required settings
-   Sheet column headers
-   Default values
-   Report configuration
-   Aggregation settings
-   Filters
-   Serial-number preference
-   Other GRID configuration settings

Google authentication credentials/tokens are not included in the
configuration backup.

To restore a configuration, use:

**Settings → Sync → Import .json**

## Resetting GRID

**Reset App Data** is available under:

**Settings → Sync**

Resetting the application removes the locally stored GRID configuration
from the current browser/device.

It does not delete the linked Google Form or Google Sheet.

After resetting, GRID can be configured again from the beginning or
restored using a JSON backup.

## Google Drive synchronization

Google Drive synchronization is optional.

When enabled, GRID can synchronize its configuration with the user's
Google Drive.

The Google Drive connection is separate from the public Home submission
experience.

If GRID is forked or deployed under a different web origin, the
deployment should use an OAuth Client ID configured for that deployment.

## Installing GRID

When hosted over HTTPS, GRID can be installed as a PWA on supported
browsers.

On Android/Chrome:

1.  Open the hosted GRID URL.
2.  Use the browser's **Add to Home screen / Install app** option.
3.  Launch GRID from the installed app icon.

The PWA service worker provides the application's offline shell and
update mechanism.

## Sharing / forking GRID

GRID is designed as a standalone web application and can be hosted on
services such as GitHub Pages.

For a separate deployment:

1.  Fork or copy the GRID project.
2.  Host the application over HTTPS.
3.  Configure the OAuth Client ID for the new deployment if Google
    services are required.
4.  Deploy `index.html` together with the service worker.
5.  Open the hosted URL and configure the application under Settings.

Each deployment can have its own Google Form, Google Sheet and Drive
configuration.

## Google OAuth setup for your own deployment

If a separate GRID deployment needs Google Sheet access or Google Drive
synchronization, create an OAuth Client ID for that deployment.

Typical setup:

1.  Open Google Cloud Console.
2.  Create or select a Google Cloud project.
3.  Enable the required Google APIs.
4.  Configure the OAuth consent screen.
5.  Create an OAuth Client ID for a Web application.
6.  Add the deployed site's authorized JavaScript origin.
7.  Put the appropriate Client ID in the GRID deployment.
8.  Deploy and test Google connection from **Settings → Sync**.

The OAuth configuration should belong to the deployment owner and should
be configured for the actual URL where GRID is hosted.

## Version

**GRID 1.0.0**

Google-linked Report & Input Dashboard

## License

License information can be added here when the GRID project's licensing
terms are finalized.
