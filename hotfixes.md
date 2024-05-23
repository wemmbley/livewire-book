## После перерисовки компонента появился странный текст

Например, после перерисовки компонента появился текст в духе < wire:id="PCBHYpfm5UmFUu3yS7V6">. Такое происходит когда внутри livewire компонента есть другие livewire компоненты, и на выходе получается множественное наследование.

Решение: всем потомкам проставить уникальный wire:key, обязательно с префиксом либо суффиксом.
```html
<div wire:key="{{ Str::random() . '-leads' }}">
   ...
</div>
```
## Undefined variable $_instance

Попытка взаимодействия с методом/свойством компонента которого нет. Другими словами, вызов происходит в обычном blade файле, который не имеет под собой компонента который его бы рендерил в методе render(). Текущий файл был подключен обычным @include.

## Undefined @this 

Означает что либа лайвайра не успела загрузится, но была произведена попытка получить текущий инстанс компонента. Решается тем, чтобы обернуть все что связано с @this в ивент `livewire:initialized`.

```js
window.addEventListener('livewire:initialized', () => {
    @this.set(...);
}
```

## В модалке пустой select2

Если селект имеет параметры но при применеии select2 их нет, то вероятнее всего дело в `wire:ignore`, который используется для того что бы livewire не перерисовывал селект2. Для фикса необходимо отрисовывать селект2 при ивенте показа модалки, и удалять его при хайде.

```js
        document.addEventListener('livewire:initialized', function() {
            let $changeOwnerModal = $('#changeOwnerModal');

            $changeOwnerModal.on('show.bs.modal', function() {
                $changeOwnerModal.find('#userSelect').select2()
                    .on('change', function (e) {
                        @this.set('newContactOwner', $(this).val());
                    });
            });
            $changeOwnerModal.on('hidden.bs.modal', function() {
                $changeOwnerModal.find('#form').trigger("reset");
                $changeOwnerModal.find('#userSelect').select2('destroy');
            });
```
