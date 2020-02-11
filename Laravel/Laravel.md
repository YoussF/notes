## Artisan
```bash
make:channel         Create a new channel class
make:command         Create a new Artisan command

make:controller PostController            # Make post controller
--resource                                # Create resourceful Pose Controller
--api                                     # Create api Pose Controller
--invokable                               # Create invokable Controller
--model                                   # Create controller with associated model


make:event           Create a new event class
make:exception       Create a new custom exception class
make:factory         Create a new model factory
make:job             Create a new job class
make:listener        Create a new event listener class
make:mail            Create a new email class

make:middleware CheckUserAge              # Create a user age checking controller

make:migration create_users_table
--create=tableName                        # Set custom name for table
--table=tableName                         # Set custom name for table

make:model Post                           # Make post mopdel
-m, --migration                           # Create model with associated migration file
-c, --Controller                          # Create model with associated Controller
-r, --resourcefull                        # create model with associated resourceful Controller
-f, --factory                             # create model with associated factory
-a, --all                                 # Generate all of the above: a migration, factory
                                          # and resource controller for the model.
--force                                   # Create the class even if the model already exists.
--pivot                                   # Indicates if the generated model should be a custom intermediate table model.

make:notification    Create a new notification class
make:observer        Create a new observer class
make:policy          Create a new policy class
make:provider        Create a new service provider class
make:request         Create a new form request class
make:resource        Create a new resource
make:rule            Create a new validation rule

make:seeder UserTableSeeder               # Make user database table seeder

make:test            Create a new test class
```

# Composer
```bash
composer create-project laravel/laravel folder_name
composer install
composer update
composer dump-autoload [--optimize]
composer self-update
```

## Eloquent
```php
<?
// Find record id
App\User::find(1);
// Find record id or throw not found Exception
App\User::findOrFail(1);
# Find any mathcing records ids
App\User::find([1, 2, 3]);
# Find mathcing records ids or thow not found Exception if any is missing
App\User::findOrFail([1, 2, 3]);
# Load model with relationships
App\User::with('posts.comments')->findOrFail(300)
App\Compagny::with(['account.owner','contacts'])->find(1)
# Filter Query
App\User::where('active', 1);
# Multiple filters
App\User::where([
    ['column_1', '=', 'value_1'],
    ['column_2', '<>', 'value_2']
])
# Query for count aggregate
App\User::where('active', 1)->count();
# Query for max aggregate
App\User::where('active', 1)->max('price');
# Query for min aggregate
App\User::where('active', 1)->min('price');
# Query for average aggregate
App\User::where('active', 1)->avg('price');
# Query for sum aggregate
App\User::where('active', 1)->sum('price');


# Once we have made the attributes mass assignable
namespace App;
use Illuminate\Database\Eloquent\Model;
class User extends Model
{ protected $fillable = ['name'];}

# Update record
$user = App\User::find(1);
$user->name = 'New user name';
$user->save();
# Mass Updates records
App\Post::where('active', 1)
          ->where('Category', 'UX')
          ->update(['active' => 0]);
# Create method returns the saved model instance:
App\User::create(['name' => 'Flight 10']);
# fill method to populate new instance with an array of attributes
$flight->fill(['name' => 'Flight 22']);
# Delete a model
App\User::find(1)->delete();
# Deleting An Existing Model By Key
App\User::destroy(1);
App\User::destroy(1, 2, 3);
App\User::destroy([1, 2, 3]);
App\User::destroy(collect([1, 2, 3]));
# Deleting Models By Query
App\User::where('active', 0)->delete();
# Soft Deleting
use SoftDeletes;                                  // In model
$table->softDeletes();                            // In migration file
$flight->trashed()                                // Check if softDeleted
# Including Soft Deleted Models  in queries
$flights = App\Flight::withTrashed()
                ->where('account_id', 1)
                ->get();
# withTrashed method may also be used on a relationship query
$flight->history()->withTrashed()->get();
# Retrieving Only Soft Deleted Models
$flights = App\Flight::onlyTrashed()
                ->where('airline_id', 1)
                ->get();
# Restoring Soft Deleted Models
$flight->restore();
# Quickly restore multiple models
App\Flight::withTrashed()
        ->where('airline_id', 1)
        ->restore();
# Permanently Deleting Models
// Force deleting a single model instance...
$flight->forceDelete();
// Force deleting all related models...
$flight->history()->forceDelete();
```

## Cashier
```php
<?
// Create a stripe customer without a newSubscription
$billable->createAsStripeCustomer();
// Retrieve the default payment method
$billable->defaultPaymentMethod();
// Retrieving Payment Methods
$billable->paymentMethods();
// Charge billable model
$billable->charge('99999999', 'pm_card_visa');
// Make user subscribe to plan
$billable->newSubscription('main', 'monthly')->create('pm_card_visa');
// Make user subscribe to 10 trialDays
$billable->newSubscription('main', 'monthly')->trialDays(10)->create('pm_card_visa');
// Make user subscribe to 10 trialDays and with Coupon amsterdam
$billable->newSubscription('main', 'monthly')->trialDays(10)->withCoupon('AMSTERDAM2019')->create('pm_card_visa');
```

## Tinker
```php
<?
// Faker
$faker = Faker\Factory::create();
$faker->name
// Log as user id 1
auth()->loginUsingId(1)
```



## Email
```php
<?
// Quick send emails
Mail::send('welcome', [], function($message) {
    $message->to('myawesomeemail@domain.com')->subject('Testing mails');
});
```

## Guzzle
```php
<?
// Quick send emails
$http = new \GuzzleHttp\Client;
try {
    $response = $http->post(config('services.passport.login_endpoint'), [
        'form_params' => [
            'grant_type' => 'password',
            'client_id' => config('services.passport.client_id'),
            'client_secret' => config('services.passport.client_secret'),
            'username' => $request->username,
            'password' => $request->password,
        ]
    ]);
    return $response;
} catch (\GuzzleHttp\Exception\BadResponseException $e) {
/*
    if ($e->getCode() === 400) {
        return response()->json('Invalid Request. Please enter a username or a password.', $e->getCode());
    } else if ($e->getCode() === 401) {
        return response()->json('Your credentials are incorrect. Please try again', $e->getCode());
}
    return response()->json('Something went wrong on the server.', $e->getCode());
*/
    return response($e->getResponse()->getBody()->getContents(), $e->getCode());
}

});
```

#### References
- [Laravel 6.x docs](https://laravel.com/api/6.x/index.html)
- [Source](https://quickadminpanel.com/blog/list-of-21-artisan-make-commands-with-parameters/)
- [Laravel in Docker for api development](Laravel-api.md)
