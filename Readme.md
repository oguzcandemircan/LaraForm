# LaraForm

[![Latest Version on Packagist][ico-version]][link-packagist]
[![Total Downloads][ico-downloads]][link-downloads]

This is where your description should go. Take a look at [contributing.md](contributing.md) to see a to do list.

## Installation

Via Composer

``` bash
$ composer require oguzcandemircan/laraform
```

## Usage

```php
// App\Http\Request\User\CreateRequest.php

namespace App\Http\Requests\User;

use Illuminate\Foundation\Http\FormRequest;

class CreateRequest extends FormRequest
{   
    //public $route = 'users.store'
    
    /**
     * Determine if the user is authorized to make this request.
     *
     * @return bool
     */
    public function authorize()
    {
        return auth()->check();
    }

    /**
     * Get the validation rules that apply to the request.
     *
     * @return array
     */
    public function rules()
    {
        return [
            'email' => 'required|email',
            'name => 'required|min:3,
        ];
    }

    public function form($user)
    {   
        
        return html()->modelForm($user)->open()
        .html()->email('name')->placeholder('Your e-mail address')
        .html()->email('email')->placeholder('Your e-mail address')
        .html()->closeModelForm();
    }
}

// resources/views/user/create.blade.php
//{!! form('Users\StoreRequest')->method('POST')->action(route('users.store'))->generate($user) !!}
{!! form('Users\StoreRequest') !!}}
//or
{!! form('Users\StoreRequest', $user) !!}
```

Route:
```php
Route::post('users','User\UserController@store')->form('users.store');
```

## Change log

Please see the [changelog](changelog.md) for more information on what has changed recently.

## Testing

``` bash
$ composer test
```

## Contributing

Please see [contributing.md](contributing.md) for details and a todolist.

## Security

If you discover any security related issues, please email author email instead of using the issue tracker.

## Credits

- [Oğuzcan Demircan][https://github.com/oguzcandemircan]
- [All Contributors][link-contributors]

## License

license. Please see the [license file](license.md) for more information.

[ico-version]: https://img.shields.io/packagist/v/oguzcandemircan/laraform.svg?style=flat-square
[ico-downloads]: https://img.shields.io/packagist/dt/oguzcandemircan/laraform.svg?style=flat-square

[link-packagist]: https://packagist.org/packages/oguzcandemircan/laraform
[link-downloads]: https://packagist.org/packages/oguzcandemircan/laraform
[link-author]: https://github.com/oguzcandemircan
[link-contributors]: ../../contributors
