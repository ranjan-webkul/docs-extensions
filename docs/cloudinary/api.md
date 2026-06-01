# REST API

The Cloudinary Connector exposes REST API endpoints so the configuration and product sync can be managed programmatically. All endpoints are protected by UnoPim's API authentication and the connector's API permissions.

## Endpoints

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/cloudinary/configuration` | Retrieve the current Cloudinary configuration. |
| `POST` | `/api/cloudinary/configuration/test` | Test the Cloudinary connection using the saved credentials. |
| `POST` | `/api/cloudinary/products/{id}/sync` | Force a media sync for the given product. |

## Get Configuration

Returns the saved connector settings.

```json
{
    "data": {
        "enabled": true,
        "cloud_name": "your_cloud_name",
        "api_key": "your_api_key",
        "folder": "unopim/products",
        "auto_sync": true
    }
}
```

> [!NOTE]
> The API secret is never returned in the configuration response.

## Test Connection

Validates that the **Cloud Name**, **API Key**, and **API Secret** are present in the saved configuration. If any credential is missing, a validation error is returned; otherwise a success response confirms the connection test completed.

## Sync Product Media

Forces a re-upload of the specified product's image, gallery, and file media to Cloudinary. The response includes the list of synced media. If the product does not exist, a not-found response is returned.

## API Permissions

The following API permissions control access to these endpoints and can be assigned to API roles:

| Permission | Allows |
|---|---|
| **Settings** | Retrieve the Cloudinary configuration. |
| **Update settings** | Run the connection test. |
| **Sync product media** | Trigger a product media sync. |
