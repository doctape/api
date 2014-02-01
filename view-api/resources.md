# Resources

## Upload

### Parameters

Endpoint: `POST /sandbox/upload`.

---

The upload can be done either asynchronously or synchronously.

In the asynchronous way, the form data can be submitted via AJAX to the endpoint, which responds with a json document containing an array of objects which specify the data of the uploaded files.

In the synchronous way, the form is submitted directly to the endpoint, and in addition to the parameters a `dt_callback_url` is specified. After the upload of the files is complete, the form data (without the files) is forwarded to the callback url containing an additional field `dt_docs` which contains the same information that is returned the asychronous way.

The array of objects containing the file data looks like this: `[{"field":form field name, "id":document id, "error":if set indicates error, "size":filesize}]`.

---

The set of parameters `P` for the upload consists of:

- required:
	- `app` (your app id)
	- `target` (the email address of the user)
- optional:
	- `expires` (unix timestamp when the upload link expires) 
	- `lazy` (when given, includes a pre-signed non-expiring embed url with the response)
	
The parameters shall be postet `multipart/form-data`-encoded into the body of the request, prefixed with `dt_`:

- required:
	- `dt_app`: `app`
	- `dt_target`: `target`
	- `dt_auth` or `dt_multiauth`: signature
- optional:
	- `dt_expires`: `expires`
	- `dt_lazy`: `lazy`

### Example

```
<h2>Upload documents</h2>

<form action="https://my.doctape.com/sandbox/upload" method="POST" enctype="multipart/form-data">

  <!-- APPFRONT DATA -->
  <input type="hidden" name="dt_app" value="{APPID}" />
  <input type="hidden" name="dt_multiauth" value="{SIGNATURE}" />
  <input type="hidden" name="dt_target" value="{EMAIL}" />
  <input type="hidden" name="dt_callback_url" value="http://localhost:8000/upload" />

  <!-- USER DATA -->
  <span>File 1</span><input type="file" name="file_1" /><br />
  <span>File 2</span><input type="file" name="file_2" /><br />
  <span>File 3</span><input type="file" name="file_3" /><br />
  <input type="test" name="note" value="example data"><br />
  <button type="submit">Save</button>

</form>
```

The form is send to https://my.doctape.com/sandbox/upload. This is where all files will be uploaded, processed and stored. Although processing might take some time, the form will be instantly forwarded/re-posted to the given callback_url, if given, otherwise just a response will be send.

- The four hidden input fields (dt_*) are needed to setup and authenticate the request
- The three file fields (file_*) hold the actually files that should be uploaded
- The text input (note) is just example custom data, which will be re-posted as is to your callback_url

---

These few lines are enough to setup doctape appfront. When this form is
submitted, it will be send to doctape. The documents will be detached, processed
and stored. The documents in the form are replaced by a field called
*dt\_docids* (read on to find more information about this). All fields prefixed
with *dt_* will be removed.

## Embedding/Accessing/Unlinking documents

### Advanced Signing Parameters

The set of parameters `P` for embedding / accessing / unlinking consists of:

- required:
	- `app` (your app id)
	- `target` (the doc id)
- optional:
	- `expires` (unix timestamp when the upload link expires) 
	- `scope` (required scope, currently for unlinking only)

The parameters shall be included as query-parameters, except for the `target` which is encoded in the url resource.

### Embeds

Endpoint: `GET /sandbox/widget/{target}`.

To display a document simply add the following iframe code to your content side:

```
<iframe src="https://my.doctape.com/sandbox/widget/{target}?app={app}&multiauth={signature}" width="640" height="480"></iframe>
```

**NOTE**: Although some documents may not be processed at the moment you embed
this code, you can use it anyway. We will show a self-updating loading screen
until the document processing is finished.

### Access original files

Endpoint: `GET /sandbox/doc/{target}/original`.

The response is a `binary/octet-stream` download of the original uploaded file.

### Access converted files

Endpoints:

- `GET /sandbox/doc/{target}/document.pdf`
- `GET /sandbox/doc/{target}/image.jpg`
- `GET /sandbox/doc/{target}/audio.mp3`
- `GET /sandbox/doc/{target}/video_640.mp4`
- `GET /sandbox/doc/{target}/video_1280.mp4`
- `GET /sandbox/doc/{target}/poster_640.jpg`
- `GET /sandbox/doc/{target}/poster_1280.jpg`
- `GET /sandbox/doc/{target}/thumb_120.jpg`
- `GET /sandbox/doc/{target}/thumb_320.jpg`

Some of these endpoints may or may not respond with a 404, depending on what was the result of the conversion. You can retrieve conversion details (document type, hd or sd and whether a thumbnail is available) via the meta data resource documented below.

### Access metadata

Endpoint: `GET /sandbox/doc/{target}`.

Example response:

```
{
  "error": null,
  "result": {
    "id": "2224c539-e5d6-425a-8e0d-9516db6dc462",
    "public_url": "http://dt.pe/w23Oj9",
    "name": "example017872",
    "extension": "jpg",
    "size": 730782,
    "time_added": 1358457759,
    "media_type": "image",
    "tags": ["+bobby", "#bobby/wallpaper"],
    "origin": "bobby/wallpaper",
    "shared": 0,
    "processing_status": "ok",
    "meta": {}
  }
}
```

### Unlink

_Note: The Simple Signing Scheme is not supported for this resource._

Endpoint: `POST /sandbox/unlink/{target}`.
Scope: `file.unlink`

Unlinking a document means revoking the access to the document for the app. The document is not deleted and will still be accessible to the user through his account.