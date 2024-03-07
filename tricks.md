## Очистка формы от ошибок валидации Laravel Blade

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

## Livewire. vs @this.
Разница в том, что @this указывает на текущий компонент (класс, из которого была вызвана текущая вьюха в методе render()), а Livewire указывает на глобальный скоуп. Например Livewire.on() будет прослушивать сигналы от всех компонентов, в то время как @this.on только от текущего.
