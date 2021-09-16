# Модуль хлебных крошек laravel >= 8.0
#### Работа с хлебными крошками на сайте. Вывод и сохранение хлебных хрошек.

## Установка модуля с помощью composer
```dotenv
composer require avxman/breadcrumbs
```

### Команды artisan
- Выгружаем все файлы
```dotenv
php artisan vendor:publish --tag="avxman-breadcrumbs-all"
```
- Выгружаем миграционные файлы
```dotenv
php artisan vendor:publish --tag="avxman-breadcrumbs-migrate"
```
- Выгружаем файлы моделек
```dotenv
php artisan vendor:publish --tag="avxman-breadcrumbs-model"
```
- Выгружаем шаблонные файлы
```dotenv
php artisan vendor:publish --tag="avxman-breadcrumbs-view"
```

### Примеры методов как получить результаты
```injectablephp
use App\Models\User;
use Avxman\Breadcrumb\Facades\BreadcrumbFacade;

$breadcrumbs = BreadcrumbFacade::init(User::class, 1)->setAddHome(false)->all()->toHtml();
$breadcrumbs = BreadcrumbFacade::init(User::class, 1)->all()->toHtml();
$breadcrumbs = BreadcrumbFacade::init(User::class, 1)->onlyLast()->toHtml();
$breadcrumbs = BreadcrumbFacade::init(User::class, 1)->exceptLast()->toHtml();
$breadcrumbs = BreadcrumbFacade::init(User::class, 1)->toCollection();
$breadcrumbs = BreadcrumbFacade::init(User::class, 1)->toArray();
$breadcrumbs = BreadcrumbFacade::init(User::class, 1)->toJson();
$breadcrumbs = BreadcrumbFacade::init(User::class, 1)->toHtml();
BreadcrumbFacade::save(
    collect()->push(
        ['url'=>'https://google.ua/', 'name'=>'Google'],
        ['url'=>null, 'name'=>'NEW']
    ),
    User::first());
$breadcrumbs = BreadcrumbFacade::init(User::class, 1)->toHtml();
```
