# Installation

### 1. Merge the package files

Unzip the extension package and merge the `packages/` folder into your Unopim project root.

### 2. Register the service provider

The Cloudinary Connector is auto-discovered through its `composer.json`, but you can also register it explicitly in `bootstrap/providers.php`:

```php
use Webkul\Cloudinary\Providers\CloudinaryServiceProvider;

return [
    // ...existing providers...
    CloudinaryServiceProvider::class,
];
```

> [!NOTE]
> This registers `CloudinaryServiceProvider` in Laravel so the module can bootstrap its routes, views, event listeners, media bindings, and package configuration during application startup.

### 3. Update Composer autoload

In `composer.json`, add under `autoload.psr-4`:

```json
"Webkul\\Cloudinary\\": "packages/Webkul/Cloudinary/src"
```

### 4. Run installation commands

Run these in order:

```bash
composer dump-autoload
php artisan optimize:clear
php artisan migrate
```

Command purpose:

- `composer dump-autoload`: Regenerates Composer's autoloader mapping to include the newly added namespace.
- `php artisan optimize:clear`: Clears all cached files (bootstrap, configuration, routes, and views) to load the new changes.
- `php artisan migrate`: Runs the package migration that creates the `cloudinary_configurations` table.

### 5. Build front-end assets

```bash
npm install
npm run build
```

| Command | Purpose |
|---|---|
| `npm install` | Installs frontend dependencies required by the Cloudinary package UI. |
| `npm run build` | Builds Cloudinary frontend assets for production/admin usage. |

### 6. Configure Cloudinary credentials (optional defaults)

Connector credentials are normally managed from the admin **Configuration** screen, but you can also provide defaults in `.env`:

```bash
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret
CLOUDINARY_ENABLED=true
CLOUDINARY_AUTO_SYNC=true
CLOUDINARY_FOLDER=unopim/products
```

> [!NOTE]
> Values saved through the admin Configuration screen take precedence over these `.env` defaults. The `.env` values are only used as fallbacks when no configuration has been saved.

### 7. Start the queue worker

Auto Sync uploads run as queued jobs (`UploadProductImageJob`). Keep a worker running so media is pushed to Cloudinary in the background:

```bash
php artisan queue:work
```

| Command | Purpose |
|---|---|
| `php artisan queue:work` | Starts a queue worker to process Cloudinary background upload jobs. |

### 8. Verify

Open the Unopim admin panel — a **Cloudinary** section should appear in the sidebar, linking to the **Cloudinary Connector Configuration** screen.
