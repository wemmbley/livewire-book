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
