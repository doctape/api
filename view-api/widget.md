# Widget

To use the widget on your site, include this code in the head block on your website:

```
<link rel="stylesheet" type="text/css" href="https://my.doctape.com/widget/view.css" />
<script async type="text/javascript" src="https://my.doctape.com/widget/view.js"></script>
```

The widget can now be created in two ways:

## Programmatically create the Widget

The retrieved widget object is described below.

```
var widget = new DoctapeWidget(element, options);
```

### Options

- `multiple`: true if multiple files can be uploaded
- `app`: your app id
- `auth`: the signature you created server-side with the way described in _Signing_
- `target`: the users email address

## Create a Widget using HTML5 Data Attributes

The widget element will also emit the events described below via the DOM event mechanisms.

```
<div class="doctape-widget"
     data-doctape-multiple=""
     data-doctape-app=""
     data-doctape-auth=""
     data-doctape-target="">
</div>
```

### Options

- `multiple`: true if multiple files can be uploaded
- `app`: your app id
- `auth`: the signature you created server-side with the way described in _Signing_
- `target`: the users email address

## Object: Widget

### Methods

- `widget.getFiles`: retrieve a list of files currently in the widget
- `widget.addFile`: add a file to the widget. this can be an HTML5 `File` object or the object retrieved by `widget.getFiles`
- `widget.removeFile`: remove a file from the widget that was previously retrived by `widget.getFiles`

### Events

The events emitted by the widget can be retrieved by subscribing via the standard `widget.addEventListener` method. All events emitted on a specific file will also be fired on the widget.

- `init`: the widget was successfully initialized (data: `widget`, `element`)
- `collection.add`: a file was added to the collection (data: `collection`, `file`)
- `collection.remove`: a file was removed from the collection (data: `collection`, `file`)

## Object: File

### Attributes

- `id`: document identifier (only if uploaded successfully)
- `size`: document size in bytes
- `name`: document title
- `transferred`: how many bytes are already uploaded

### Methods

- `getThumbnailURL`: get the url of the thumbnail (only if uploaded successfully)
- `getMetaURL`: get the url of the metadata document (only if uploaded successfully)
- `getWidgetURL`: get the url of the embed widget (only if uploaded successfully)

### Events

The events emitted by the file can be retrieved by subscribing via the standard `file.addEventListener` method.

- `file.change`: a file's data changed (data: `file`)
- `file.progress`: a file's upload progressed (data: `file`)
- `file.error`: a file's upload threw an error (data: `file`)
- `file.aborted`: a file's upload was aborted (data: `file`)
- `file.processing.error`: a file's processing finsished with an error (data: `file`)
- `file.processing.success`: a file's processing finished successfully (data: `file`)