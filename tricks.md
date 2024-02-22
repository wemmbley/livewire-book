# Очистка формы от ошибок валидации Laravel Blade

PHP Component:
```php
#[On('form-reset-errors')]
public function resetFormErrors()
{
    $this->resetErrorBag();
}
```

JavaScript:
```js
Livewire.dispatch('form-reset-errors');
```
