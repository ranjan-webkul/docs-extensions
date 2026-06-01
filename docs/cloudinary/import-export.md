# Import & Export

The Cloudinary Connector integrates with UnoPim's data transfer pipeline so that product media stays in sync during bulk imports and is delivered as Cloudinary URLs during exports.

## Product Import

When products are imported through a CSV or XLSX file, the connector hooks into the import pipeline:

- After each import batch is saved, media belonging to the imported products is uploaded to Cloudinary.
- Both locally stored paths and public URLs referenced in the import file are handled.
- Uploads only run when the connector is **enabled** and **Auto Sync** is turned on.

This means media coming in through a bulk import is treated the same as media added manually — it is uploaded to Cloudinary and tracked against the product.

> [!NOTE]
> As with automatic sync, a queue worker must be running so the import-triggered uploads are processed.

## Product Export

When products are exported, the connector replaces local media paths with their Cloudinary URLs in the exported file.

- **Image**, **gallery**, and **file** attribute columns are filled with the Cloudinary URL for each asset.
- If an asset has no Cloudinary URL yet, the original path is exported as a fallback.
- When the **With Media** export option is selected, the underlying media files are also copied into the export, alongside the Cloudinary URLs.

This ensures exported catalogs reference your optimized, cloud-hosted media rather than local storage paths.
