# Cloudinary Connector

Store Link: [View on Webkul Store](https://store.webkul.com/unopim-cloudinary-connector.html)

The **Cloudinary Connector** extension integrates UnoPim with [Cloudinary](https://cloudinary.com/), a cloud-based media management platform. It automatically uploads your product images, galleries, and files to Cloudinary and serves them through Cloudinary's optimized delivery network. Media stays in sync as products are created, updated, imported, or deleted, so your catalog always points to fast, cloud-hosted assets without manual uploads. Connector credentials are managed from a dedicated configuration screen, and a one-click sync is available for any individual product.

## How it works

```
Product image/file added in UnoPim
            ↓
   Saved to local storage
            ↓
Auto Sync queues an upload job
            ↓
   File uploaded to Cloudinary
            ↓
Cloudinary URL stored on the product
            ↓
Grids, listings & exports serve the Cloudinary URL
```

Every upload is recorded against the product, so deletes and re-syncs stay consistent and existing media is never uploaded twice.

## Key features

- Automatically upload product images, galleries, and files to Cloudinary.
- Serve Cloudinary URLs in product grids, listings, and base/gallery image displays.
- Sync media in the background using queued jobs so the admin stays responsive.
- Manually re-sync any single product on demand.
- Keep media consistent — uploads are tracked, and removed media is deleted from Cloudinary.
- Sync media that comes in through CSV/XLSX product imports.
- Export product media as Cloudinary URLs.
- Configure a custom Cloudinary folder for all uploaded assets.
- Manage everything through a dedicated configuration screen with role-based permissions.
- Access configuration and sync actions through the REST API.

## What gets synced

| Attribute type | Synced |
|---|---|
| **Image** | Yes |
| **Gallery** | Yes |
| **File** | Yes |

Media can be a locally stored file or a public URL — both are uploaded to Cloudinary.

## Requirements

- **UnoPim**: 2.0.0
- **PHP**: 8.3+
- **Laravel**: 12.x
- A **Cloudinary** account with a Cloud Name, API Key, and API Secret.
