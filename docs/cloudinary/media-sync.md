# Media Synchronization

Once the connector is enabled and configured, the Cloudinary Connector keeps your product media in sync with Cloudinary. Synchronization happens automatically in the background and can also be triggered manually for any product.

## Automatic Sync

When **Auto Sync** is enabled, the connector listens for product events and uploads media to Cloudinary without any manual action.

| Event | What happens |
|---|---|
| **Product created** | A background job uploads any image, gallery, or file media to Cloudinary. |
| **Product updated** | New media is uploaded, and media removed from the product is deleted from Cloudinary. |
| **Product deleted** | All of the product's Cloudinary media is deleted from Cloudinary. |
| **Product imported** | Media that arrives through a product import is uploaded after the import batch is saved. |

Uploads are dispatched as queued jobs, so the admin panel stays responsive while media is pushed to Cloudinary in the background.

> [!NOTE]
> A queue worker (`php artisan queue:work`) must be running for automatic uploads to be processed.

### How media is tracked

Each uploaded asset is recorded against the product, storing the Cloudinary **public ID**, **URL**, **version**, the source attribute, and a timestamp. This tracking ensures:

- Media that already exists on Cloudinary is not uploaded again.
- Media removed from a product is also removed from Cloudinary.
- Both locally stored files and public URLs are handled correctly.

## Manual Sync

You can re-synchronize a single product's media at any time. This is useful after changing credentials, recovering missing media, or forcing a refresh of already-synced assets.

A user with the **Sync product media** permission can trigger a forced sync for a product, which re-uploads its image, gallery, and file media to Cloudinary regardless of whether it was synced before.

![Manual Product Sync](assets/sync/manual-sync.png)

On success, a confirmation message is shown:

> Product media synchronized with Cloudinary.

If the sync fails (for example, due to invalid credentials), an error message is shown and the failure is logged for review.

## Serving Cloudinary URLs

Once media is synced, the connector automatically serves Cloudinary URLs in place of local storage URLs throughout the admin panel:

- **Product grid** — image and gallery thumbnails prefer the Cloudinary URL.
- **Product listings** — base and gallery images are served from Cloudinary when available.
- **On-demand sync** — if a product image is displayed but not yet synced, the connector uploads it to Cloudinary and serves the new URL.

If a Cloudinary URL is not available for a given asset, the connector gracefully falls back to the original local storage URL, so images are always displayed.
