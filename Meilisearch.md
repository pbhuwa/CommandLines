# MeiliSearch Setup and Laravel Integration

## MeiliSearch Setup Commands

### 1. MeiliSearch Endpoint
Verify MeiliSearch is running and accessible by checking the health endpoint:
```
http://127.0.0.1:7700/health
```

### 2. Create an Index
To create an index named `products`, use one of the following commands:

**Using PowerShell:**
```
Invoke-WebRequest -Uri "http://127.0.0.1:7700/indexes" -Method Post -ContentType "application/json" -Body '{"uid": "products"}'
```

**Using cURL:**
```
curl -X POST "http://127.0.0.1:7700/indexes" -H "Content-Type: application/json" --data '{"uid": "products"}'
```

### 3. Verify the Index
Check that the `products` index has been created:

**List all indexes:**
```
GET http://127.0.0.1:7700/indexes
```

**Verify documents in the `products` index:**
```
GET http://127.0.0.1:7700/indexes/products/documents
```

### 4. Enable Sortable Attributes
Enable sorting for the attributes `price` and `created_at` in the `products` index:

**Using cURL:**
```
curl -X PATCH 'http://127.0.0.1:7700/indexes/products/settings' \
     -H 'Content-Type: application/json' \
     --data-binary '{
         "sortableAttributes": ["price", "created_at"]
     }'
```

**Using PowerShell:**
```
Invoke-WebRequest -Uri 'http://127.0.0.1:7700/indexes/products/settings' -Method Patch `
     -Headers @{ "Content-Type" = "application/json" } `
     -Body '{"sortableAttributes": ["price", "created_at"]}'
```

### 5. Enable Filterable Attributes
Enable filtering for attributes like `category_id`, `status`, and others:

**Using cURL:**
```
curl -X PATCH 'http://127.0.0.1:7700/indexes/products/settings' \
     -H 'Content-Type: application/json' \
     --data '{
         "filterableAttributes": ["category_id", "status", "verified", "brand_id", "brand_status", "category.parent_disabled", "category.status"],
         "sortableAttributes": ["score"]
     }'
```

### 6. Set Primary Key
To set the primary key for the `products` index:

**Using cURL:**
```
curl.exe -X POST "http://62.72.42.205:7700/" \
    -H "Content-Type: application/json" \
    --data-binary '{
        "uid": "products",
        "primaryKey": "id"
    }'
```

## MeiliSearch Commands

### 1. Check Indexes
```
curl -H "Authorization: Bearer <YOUR_MASTER_KEY>" http://62.72.42.205:7700/indexes
```

### 2. List Existing Keys
```
curl -H "Authorization: Bearer <YOUR_MASTER_KEY>" http://62.72.42.205:7700/keys
```

### 3. Delete Index
```
curl -X DELETE -H "Authorization: Bearer <YOUR_API_KEY>" http://62.72.42.205:7700/indexes/<index_name>
```

### 4. Create Index
```
curl -X POST -H "Content-Type: application/json" \
     -H "Authorization: Bearer <YOUR_API_KEY>" \
     -d '{
           "uid": "movies",
           "primaryKey": "id"
         }' \
     http://62.72.42.205:7700/indexes
```

### 5. Check Index Status
```
curl -H "Authorization: Bearer <YOUR_API_KEY>" http://62.72.42.205:7700/tasks
```

## Laravel Integration

### Step 1: Install MeiliSearch Client
Install the PHP SDK for MeiliSearch:
```
composer require meilisearch/meilisearch-php
```

### Step 2: Configure MeiliSearch
Add MeiliSearch configuration to your `.env` file:
```
MEILISEARCH_HOST=http://127.0.0.1:7700
```

### Step 3: Service Provider
In `config/app.php`, add the MeiliSearch service provider:
```
use MeiliSearch\Client;

$client = new Client(env('MEILISEARCH_HOST'), env('MEILISEARCH_KEY'));
```

### Step 4: Indexing Data
Use Laravel Eloquent to index your `products` data:
```
use MeiliSearch\Client;

$client = new Client(env('MEILISEARCH_HOST'));
$index = $client->index('products');

// Add or update documents
$products = Product::all()->toArray();
$index->addDocuments($products);
```

### Step 5: Searching Data
Query the `products` index:
```
$results = $index->search('search_term', [
    'filters' => 'status = 1 AND category_id = 10'
]);
```

### Step 6: Customizing Settings
Update settings for the `products` index in Laravel:
```
$index->updateSettings([
    'filterableAttributes' => ['category_id', 'status'],
    'sortableAttributes' => ['price', 'created_at'],
]);
```

## References
- [MeiliSearch Documentation](https://docs.meilisearch.com)
- [MeiliSearch PHP SDK](https://github.com/meilisearch/meilisearch-php)

php artisan scout:import "App\Shop\Products\Product"
php artisan scout:import "App\Shop\Categories\Category"
php artisan scout:import "App\Shop\Brands\Brand"


