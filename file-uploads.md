## FilePond set-up

JavaScript
```js
        const PondNotes = FilePond.create(document.querySelector('.filepond-notes'));

        PondNotes.setOptions({
            server: {
                process: (fieldName, file, metadata, load, error, progress, abort, transfer, options) => {
                    @this.upload('images', file, load, error, progress)
                },
                revert: (filename, load) => {
                    @this.removeUpload('images', filename, load)
                },
                remove: (filename, load) => {
                    @this.removeFile('images', filename.name)
                }
            },
            allowMultiple: true
        });
```

#### Delete all uploaded files
```js
PondNotes.removeFiles();
```
