# Livewire события

Для того чтобы вызвать метод компонента с помощью JavaScript, нам необходимо обьявить публичный метод в компоненте, и добавить ему атрибут On с названием события.

```php
#[On('load-data')]
public function loadData() {
    dd('Event was called.');
}
```

Таким образом мы теперь можем вызвать в Blade шаблоне компонента JavaScript метод dispatch, и событие будет отправлено на бэк, вызвав наш метод.

```js
Livewire.dispatch('load-data');
```

## Аргументы события

Для того чтобы передать какие-либо данные в метод, мы используем второй аргумент dispatch – массив.

```js
Livewire.dispatch('load-data', ['test', true, 5]);
```

Таким образом, в наш метод передастся три аргумента.

```php
#[On('load-data')]
public function loadData(string $name, bool $status, int $number) {
    dd('Event was called.');
}
```

## Вызов события конкретного компонента

```js
Livewire.dispatch('', 'deals::deal-info.modal.status-in-progress', 'show-modal', data);
// 1 аргумент пуст, второй – имя компонента, третий – имя события
```

## JavaScript события

Для обьявления прослушивателя события

```js
@this.on('modal-work-in-progress', function (event) {
    // your code
}
```

Для вызова события 

```php
$this->dispatch('modal-work-in-progress');
```

## Вызов JS события посредством JS
```js
Livewire.dispatch('deals::deal-info.modal.status-in-progress', 'show-modal', data);
// 1 - имя компонента, 2 - название события
```
