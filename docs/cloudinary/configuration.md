# Configuration

After installing the UnoPim Cloudinary Connector, users with the required permissions can configure the connection to Cloudinary and control how product media is synchronized.

## Open the Configuration Screen

Navigate to the left-side menu and select **Cloudinary**. This opens the **Cloudinary Connector Configuration** screen.

![Cloudinary Configuration](assets/configuration/cloudinary-configuration.png)

## General Settings

The configuration form holds all connection and sync settings in one place.

| Field | Description |
|---|---|
| **Enable Connector** | Turns the Cloudinary integration on or off. When disabled, no media is uploaded to or served from Cloudinary. |
| **Auto Sync** | When enabled, product media is automatically uploaded to Cloudinary whenever a product is created, updated, or imported. |
| **Cloud Name** | Your Cloudinary cloud name. Required when the connector is enabled. |
| **API Key** | Your Cloudinary API key. Required when the connector is enabled. |
| **API Secret** | Your Cloudinary API secret. Required when the connector is enabled. Stored as a password field. |
| **Folder Name** | The Cloudinary folder where uploaded assets are stored. Defaults to `unopim/products`. |

![General Settings](assets/configuration/general-settings.png)

> [!NOTE]
> The **Cloud Name**, **API Key**, and **API Secret** are required only when the connector is enabled. You can find these credentials in your Cloudinary account dashboard.

## Saving the Configuration

After entering your credentials and choosing your sync options, click **Save Configuration**. A success message confirms the settings were saved.

![Save Configuration](assets/configuration/save-configuration.png)

The saved configuration is stored in the `cloudinary_configurations` table and takes precedence over any defaults set in the `.env` file.

## Access Control List | Permissions for Cloudinary

Admins can control who is allowed to view and update the Cloudinary configuration by navigating to **Settings > Roles > Create Role**.

Under the **Cloudinary** section, the following permissions are available:

| Permission | Allows the user to |
|---|---|
| **Settings** | View the Cloudinary Connector configuration screen. |
| **Update settings** | Save and update the Cloudinary configuration. |
| **Sync product media** | Manually trigger a media sync for an individual product. |

![Cloudinary Permissions](assets/configuration/permissions.png)

Assign these permissions to the relevant roles, then assign those roles to users so only authorized team members can manage the Cloudinary integration.
