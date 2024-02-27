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
