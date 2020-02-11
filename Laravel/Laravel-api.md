## Create boilerplate for a resource
```bash
# Generate model, migration and factory
  docker exec nimbl-dev-php-container php artisan make:model Invoice -m -f
  # Generate Api Controller
  docker exec nimbl-dev-php-container php artisan make:controller InvoiceController --api
  # Generate Database Seeder
  docker exec nimbl-dev-php-container php artisan make:seeder InvoicesTableSeeder
  # Generate API Resource
  docker exec nimbl-dev-php-container php artisan make:resource InvoiceResource
  # Generate API ResourceCollection
  docker exec nimbl-dev-php-container php artisan make:resource InvoiceCollection
```

